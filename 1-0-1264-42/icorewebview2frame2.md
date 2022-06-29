---
description: A continuation of the ICoreWebView2Frame interface with navigation events, executing script and posting web messages.
title: WebView2 Win32 C++ ICoreWebView2Frame2
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Frame2
---

# interface ICoreWebView2Frame2

```
interface ICoreWebView2Frame2
  : public ICoreWebView2Frame
```

A continuation of the ICoreWebView2Frame interface with navigation events, executing script and posting web messages.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ContentLoading](#add_contentloading) | Add an event handler for the `ContentLoading` event.
[add_DOMContentLoaded](#add_domcontentloaded) | Add an event handler for the DOMContentLoaded event.
[add_NavigationCompleted](#add_navigationcompleted) | Add an event handler for the `NavigationCompleted` event.
[add_NavigationStarting](#add_navigationstarting) | Add an event handler for the `NavigationStarting` event.
[add_WebMessageReceived](#add_webmessagereceived) | Add an event handler for the `WebMessageReceived` event.
[ExecuteScript](#executescript) | Run JavaScript code from the javascript parameter in the current frame.
[PostWebMessageAsJson](#postwebmessageasjson) | Posts the specified webMessage to the frame.
[PostWebMessageAsString](#postwebmessageasstring) | Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.
[remove_ContentLoading](#remove_contentloading) | Remove an event handler previously added with `add_ContentLoading`.
[remove_DOMContentLoaded](#remove_domcontentloaded) | Remove an event handler previously added with add_DOMContentLoaded.
[remove_NavigationCompleted](#remove_navigationcompleted) | Remove an event handler previously added with `add_NavigationCompleted`.
[remove_NavigationStarting](#remove_navigationstarting) | Remove an event handler previously added with `add_NavigationStarting`.
[remove_WebMessageReceived](#remove_webmessagereceived) | Remove an event handler previously added with `add_WebMessageReceived`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### add_ContentLoading

Add an event handler for the `ContentLoading` event.

> public HRESULT [add_ContentLoading](#add_contentloading)(ICoreWebView2FrameContentLoadingEventHandler * eventHandler, EventRegistrationToken * token)

`ContentLoading` triggers before any content is loaded, including scripts added with `AddScriptToExecuteOnDocumentCreated`. `ContentLoading` does not trigger if a same page navigation occurs (such as through `fragment` navigations or `history.pushState` navigations). This operation follows the `NavigationStarting` and precedes `NavigationCompleted` events.

#### add_DOMContentLoaded

Add an event handler for the DOMContentLoaded event.

> public HRESULT [add_DOMContentLoaded](#add_domcontentloaded)(ICoreWebView2FrameDOMContentLoadedEventHandler * eventHandler, EventRegistrationToken * token)

DOMContentLoaded is raised when the iframe html document has been parsed. This aligns with the document's DOMContentLoaded event in html.

#### add_NavigationCompleted

Add an event handler for the `NavigationCompleted` event.

> public HRESULT [add_NavigationCompleted](#add_navigationcompleted)(ICoreWebView2FrameNavigationCompletedEventHandler * eventHandler, EventRegistrationToken * token)

`NavigationCompleted` runs when the CoreWebView2Frame has completely loaded (concurrently when `body.onload` runs) or loading stopped with error.

#### add_NavigationStarting

Add an event handler for the `NavigationStarting` event.

> public HRESULT [add_NavigationStarting](#add_navigationstarting)(ICoreWebView2FrameNavigationStartingEventHandler * eventHandler, EventRegistrationToken * token)

A frame navigation will raise a `NavigationStarting` event and a `CoreWebView2.FrameNavigationStarting` event. All of the `FrameNavigationStarting` event handlers for the current frame will be run before the `NavigationStarting` event handlers. All of the event handlers share a common `NavigationStartingEventArgs` object. Whichever event handler is last to change the `NavigationStartingEventArgs.Cancel` property will decide if the frame navigation will be cancelled. Redirects raise this event as well, and the navigation id is the same as the original one.

Navigations will be blocked until all `NavigationStarting` and `CoreWebView2.FrameNavigationStarting` event handlers return.

#### add_WebMessageReceived

Add an event handler for the `WebMessageReceived` event.

> public HRESULT [add_WebMessageReceived](#add_webmessagereceived)([ICoreWebView2FrameWebMessageReceivedEventHandler](icorewebview2framewebmessagereceivedeventhandler.md) * handler, EventRegistrationToken * token)

`WebMessageReceived` runs when the `ICoreWebView2Settings::IsWebMessageEnabled` setting is set and the frame document runs `window.chrome.webview.postMessage`. The `postMessage` function is `void postMessage(object)` where object is any object supported by JSON conversion.

```html
        window.chrome.webview.addEventListener('message', arg => {
            if ("SetColor" in arg.data) {
                document.getElementById("colorable").style.color = arg.data.SetColor;
            }
            if ("WindowBounds" in arg.data) {
                document.getElementById("window-bounds").value = arg.data.WindowBounds;
            }
        });

        function SetTitleText() {
            let titleText = document.getElementById("title-text");
            window.chrome.webview.postMessage(`SetTitleText ${titleText.value}`);
        }
        function GetWindowBounds() {
            window.chrome.webview.postMessage("GetWindowBounds");
        }
```

When the frame calls `postMessage`, the object parameter is converted to a JSON string and is posted asynchronously to the host process. This will result in the handlers `Invoke` method being called with the JSON string as its parameter.

```cpp
            // Setup the web message received event handler before navigating to
            // ensure we don't miss any messages.
            CHECK_FAILURE(webviewFrame2->add_WebMessageReceived(
                Microsoft::WRL::Callback<ICoreWebView2FrameWebMessageReceivedEventHandler>(
                    [this](
                        ICoreWebView2Frame* sender,
                        ICoreWebView2WebMessageReceivedEventArgs* args) {
                        wil::unique_cotaskmem_string uri;
                        CHECK_FAILURE(args->get_Source(&uri));

                        // Always validate that the origin of the message is what you expect.
                        if (uri.get() != m_sampleUri)
                        {
                            // Ignore messages from untrusted sources.
                            return S_OK;
                        }
                        wil::unique_cotaskmem_string messageRaw;
                        HRESULT hr = args->TryGetWebMessageAsString(&messageRaw);
                        if (hr == E_INVALIDARG)
                        {
                            // Was not a string message. Ignore.
                            return S_OK;
                        }
                        // Any other problems are fatal.
                        CHECK_FAILURE(hr);
                        std::wstring message = messageRaw.get();

                        if (message.compare(0, 13, L"SetTitleText ") == 0)
                        {
                            m_appWindow->SetDocumentTitle(message.substr(13).c_str());
                        }
                        else if (message.compare(L"GetWindowBounds") == 0)
                        {
                            RECT bounds = m_appWindow->GetWindowBounds();
                            std::wstring reply = L"{\"WindowBounds\":\"Left:" +
                                                 std::to_wstring(bounds.left) + L"\\nTop:" +
                                                 std::to_wstring(bounds.top) + L"\\nRight:" +
                                                 std::to_wstring(bounds.right) + L"\\nBottom:" +
                                                 std::to_wstring(bounds.bottom) + L"\"}";
                            wil::com_ptr<ICoreWebView2Frame2> webviewFrame2;
                            if (sender->QueryInterface(IID_PPV_ARGS(&webviewFrame2)) == S_OK)
                            {
                                CHECK_FAILURE(
                                    webviewFrame2->PostWebMessageAsJson(reply.c_str()));
                            }
                        }
                        else
                        {
                            // Ignore unrecognized messages, but log for further investigation
                            // since it suggests a mismatch between the web content and the host.
                            OutputDebugString(
                                std::wstring(L"Unexpected message from frame:" + message).c_str());
                        }
                        return S_OK;
                    })
                    .Get(),
                NULL));
```

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
                    wil::com_ptr<ICoreWebView2Frame2> frame2 =
                        webviewFrame.try_query<ICoreWebView2Frame2>();
                    if (frame2)
                    {
                        frame2->add_DOMContentLoaded(
                            Callback<ICoreWebView2FrameDOMContentLoadedEventHandler>(
                                [](ICoreWebView2Frame* frame,
                                   ICoreWebView2DOMContentLoadedEventArgs* args) -> HRESULT {
                                    wil::com_ptr<ICoreWebView2Frame2> frame2;
                                    frame->QueryInterface(IID_PPV_ARGS(&frame2));
                                    frame2->ExecuteScript(
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
            &m_frameCreatedToken));
    }
```

#### PostWebMessageAsJson

Posts the specified webMessage to the frame.

> public HRESULT [PostWebMessageAsJson](#postwebmessageasjson)(LPCWSTR webMessageAsJson)

The frame receives the message by subscribing to the `message` event of the `window.chrome.webview` of the frame document.

```cpp
window.chrome.webview.addEventListener('message', handler)
window.chrome.webview.removeEventListener('message', handler)
```

The event args is an instances of `MessageEvent`. The `ICoreWebView2Settings::IsWebMessageEnabled` setting must be `TRUE` or this method fails with `E_INVALIDARG`. The `data` property of the event args is the `webMessage` string parameter parsed as a JSON string into a JavaScript object. The `source` property of the event args is a reference to the `window.chrome.webview` object. For information about sending messages from the HTML document in the WebView to the host, navigate to [add_WebMessageReceived](/microsoft-edge/webview2/reference/win32/icorewebview2#add_webmessagereceived). The message is delivered asynchronously. If a navigation occurs before the message is posted to the page, the message is discarded.

#### PostWebMessageAsString

Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.

> public HRESULT [PostWebMessageAsString](#postwebmessageasstring)(LPCWSTR webMessageAsString)

This behaves in exactly the same manner as `PostWebMessageAsJson`, but the `data` property of the event args of the `window.chrome.webview` message is a string with the same value as `webMessageAsString`. Use this instead of `PostWebMessageAsJson` if you want to communicate using simple strings rather than JSON objects.

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

#### remove_WebMessageReceived

Remove an event handler previously added with `add_WebMessageReceived`.

> public HRESULT [remove_WebMessageReceived](#remove_webmessagereceived)(EventRegistrationToken token)

