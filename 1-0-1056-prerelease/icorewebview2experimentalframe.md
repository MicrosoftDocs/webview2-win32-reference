---
description: This is the ICoreWebView2Frame Experimental interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrame
ms.date: 10/28/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrame
---

# interface ICoreWebView2ExperimentalFrame

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrame
  : public IUnknown
```

This is the [ICoreWebView2Frame](icorewebview2frame.md) Experimental interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ContentLoading](#add_contentloading) | Add an event handler for the `ContentLoading` event.
[add_DOMContentLoaded](#add_domcontentloaded) | Add an event handler for the DOMContentLoaded event.
[add_NavigationCompleted](#add_navigationcompleted) | Add an event handler for the `NavigationCompleted` event.
[add_NavigationStarting](#add_navigationstarting) | Add an event handler for the `NavigationStarting` event.
[ExecuteScript](#executescript) | Run JavaScript code from the javascript parameter in the current frame.
[remove_ContentLoading](#remove_contentloading) | Remove an event handler previously added with `add_ContentLoading`.
[remove_DOMContentLoaded](#remove_domcontentloaded) | Remove an event handler previously added with add_DOMContentLoaded.
[remove_NavigationCompleted](#remove_navigationcompleted) | Remove an event handler previously added with `add_NavigationCompleted`.
[remove_NavigationStarting](#remove_navigationstarting) | Remove an event handler previously added with `add_NavigationStarting`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.865

## Members

#### add_ContentLoading

Add an event handler for the `ContentLoading` event.

> public HRESULT [add_ContentLoading](#add_contentloading)([ICoreWebView2ExperimentalFrameContentLoadingEventHandler](icorewebview2experimentalframecontentloadingeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ContentLoading` triggers before any content is loaded, including scripts added with `AddScriptToExecuteOnDocumentCreated`. `ContentLoading` does not trigger if a same page navigation occurs (such as through `fragment` navigations or `history.pushState` navigations). This operation follows the `NavigationStarting` and precedes `NavigationCompleted` events.

#### add_DOMContentLoaded

Add an event handler for the DOMContentLoaded event.

> public HRESULT [add_DOMContentLoaded](#add_domcontentloaded)([ICoreWebView2ExperimentalFrameDOMContentLoadedEventHandler](icorewebview2experimentalframedomcontentloadedeventhandler.md) * eventHandler, EventRegistrationToken * token)

DOMContentLoaded is raised when the iframe html document has been parsed. This aligns with the document's DOMContentLoaded event in html.

#### add_NavigationCompleted

Add an event handler for the `NavigationCompleted` event.

> public HRESULT [add_NavigationCompleted](#add_navigationcompleted)([ICoreWebView2ExperimentalFrameNavigationCompletedEventHandler](icorewebview2experimentalframenavigationcompletedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`NavigationCompleted` runs when the CoreWebView2Frame has completely loaded (concurrently when `body.onload` runs) or loading stopped with error.

#### add_NavigationStarting

Add an event handler for the `NavigationStarting` event.

> public HRESULT [add_NavigationStarting](#add_navigationstarting)([ICoreWebView2ExperimentalFrameNavigationStartingEventHandler](icorewebview2experimentalframenavigationstartingeventhandler.md) * eventHandler, EventRegistrationToken * token)

A frame navigation will raise a `NavigationStarting` event and a `CoreWebView2.FrameNavigationStarting` event. All of the `FrameNavigationStarting` event handlers for the current frame will be run before the `NavigationStarting` event handlers. All of the event handlers share a common `NavigationStartingEventArgs` object. Whichever event handler is last to change the `NavigationStartingEventArgs.Cancel` property will decide if the frame navigation will be cancelled. Redirects raise this event as well, and the navigation id is the same as the original one.

Navigations will be blocked until all `NavigationStarting` and `CoreWebView2.FrameNavigationStarting` event handlers return.

#### ExecuteScript

Run JavaScript code from the javascript parameter in the current frame.

> public HRESULT [ExecuteScript](#executescript)(LPCWSTR javaScript, [ICoreWebView2ExecuteScriptCompletedHandler](icorewebview2executescriptcompletedhandler.md) * handler)

The result of evaluating the provided JavaScript is passed to the completion handler. The result value is a JSON encoded string. If the result is undefined, contains a reference cycle, or otherwise is not able to be encoded into JSON, then the result is considered to be null, which is encoded in JSON as the string "null".

> [!NOTE]
> A function that has no explicit return value returns undefined. If the script that was run throws an unhandled exception, then the result is also "null". This method is applied asynchronously. If the method is run before `ContentLoading`, the script will not be executed and the string "null" will be returned. This operation executes the script even if `ICoreWebView2Settings::IsScriptEnabled` is set to `FALSE`.

```cpp
    wil::com_ptr<ICoreWebView2_4> webview2_4 = m_webView.try_query<ICoreWebView2_4>();
    if (webview2_4)
    {
        CHECK_FAILURE(webview2_4->add_FrameCreated(
            Callback<ICoreWebView2FrameCreatedEventHandler>(
                [](ICoreWebView2* sender, ICoreWebView2FrameCreatedEventArgs* args) -> HRESULT {
                    wil::com_ptr<ICoreWebView2Frame> webviewFrame;
                    CHECK_FAILURE(args->get_Frame(&webviewFrame));
                    wil::com_ptr<ICoreWebView2ExperimentalFrame> frameExperimental =
                        webviewFrame.try_query<ICoreWebView2ExperimentalFrame>();
                    if (frameExperimental)
                    {
                        frameExperimental->add_DOMContentLoaded(
                            Callback<
                                ICoreWebView2ExperimentalFrameDOMContentLoadedEventHandler>(
                                [](ICoreWebView2Frame* frame,
                                   ICoreWebView2DOMContentLoadedEventArgs* args) -> HRESULT {
                                    wil::com_ptr<ICoreWebView2ExperimentalFrame>
                                        frameExperimental;
                                    frame->QueryInterface(IID_PPV_ARGS(&frameExperimental));
                                    frameExperimental->ExecuteScript(
                                        LR"~(
                                        let content = document.createElement("h2");
                                        content.style.color = 'blue';
                                        content.textContent = "This text was added to the iframe by the host app";
                                        document.body.appendChild(content);
                                        )~",
                                        Callback<ICoreWebView2ExecuteScriptCompletedHandler>(
                                            [](HRESULT error, PCWSTR result) -> HRESULT {
                                                // Handle ExecuteScript error and result here if needed
                                                // or pass nullptr as callback parametr otherwise.
                                                return S_OK;
                                            })
                                            .Get());
                                    return S_OK;
                                })
                                .Get(),
                            NULL);
                    }
                    return S_OK;
                })
                .Get(),
            NULL));
    }
```

#### remove_ContentLoading

Remove an event handler previously added with `add_ContentLoading`.

> public HRESULT [remove_ContentLoading](#remove_contentloading)(EventRegistrationToken token)

#### remove_DOMContentLoaded

Remove an event handler previously added with add_DOMContentLoaded.

> public HRESULT [remove_DOMContentLoaded](#remove_domcontentloaded)(EventRegistrationToken token)

#### remove_NavigationCompleted

Remove an event handler previously added with `add_NavigationCompleted`.

> public HRESULT [remove_NavigationCompleted](#remove_navigationcompleted)(EventRegistrationToken token)

#### remove_NavigationStarting

Remove an event handler previously added with `add_NavigationStarting`.

> public HRESULT [remove_NavigationStarting](#remove_navigationstarting)(EventRegistrationToken token)

