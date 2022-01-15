---
description: This is the ICoreWebView2Frame2 Experimental interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrame2
ms.date: 01/14/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrame2
---

# interface ICoreWebView2ExperimentalFrame2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrame2
  : public IUnknown
```

This is the ICoreWebView2Frame2 Experimental interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_WebMessageReceived](#add_webmessagereceived) | Add an event handler for the `WebMessageReceived` event.
[PostWebMessageAsJson](#postwebmessageasjson) | Posts the specified webMessage to the frame.
[PostWebMessageAsString](#postwebmessageasstring) | Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.
[remove_WebMessageReceived](#remove_webmessagereceived) | Remove an event handler previously added with `add_WebMessageReceived`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### add_WebMessageReceived

Add an event handler for the `WebMessageReceived` event.

> public HRESULT [add_WebMessageReceived](#add_webmessagereceived)([ICoreWebView2ExperimentalFrameWebMessageReceivedEventHandler](icorewebview2experimentalframewebmessagereceivedeventhandler.md) * handler, EventRegistrationToken * token)

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
            CHECK_FAILURE(frameExperimental->add_WebMessageReceived(
                Microsoft::WRL::Callback<
                    ICoreWebView2ExperimentalFrameWebMessageReceivedEventHandler>(
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
                            wil::com_ptr<ICoreWebView2ExperimentalFrame2> frameExperimental;
                            if (sender->QueryInterface(IID_PPV_ARGS(&frameExperimental)) ==
                                S_OK)
                            {
                                CHECK_FAILURE(
                                    frameExperimental->PostWebMessageAsJson(reply.c_str()));
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

#### PostWebMessageAsJson

Posts the specified webMessage to the frame.

> public HRESULT [PostWebMessageAsJson](#postwebmessageasjson)(LPCWSTR webMessageAsJson)

The frame receives the message by subscribing to the `message` event of the `window.chrome.webview` of the frame document.

```cpp
window.chrome.webview.addEventListener('message', handler)
window.chrome.webview.removeEventListener('message', handler)
```

The event args is an instances of `MessageEvent`. The `ICoreWebView2Settings::IsWebMessageEnabled` setting must be `TRUE` or this method fails with `E_INVALIDARG`. The `data` property of the event args is the `webMessage` string parameter parsed as a JSON string into a JavaScript object. The `source` property of the event args is a reference to the `window.chrome.webview` object. For information about sending messages from the HTML document in the WebView to the host, navigate to [add_WebMessageReceived]. The message is delivered asynchronously. If a navigation occurs before the message is posted to the page, the message is discarded.

#### PostWebMessageAsString

Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.

> public HRESULT [PostWebMessageAsString](#postwebmessageasstring)(LPCWSTR webMessageAsString)

This behaves in exactly the same manner as `PostWebMessageAsJson`, but the `data` property of the event args of the `window.chrome.webview` message is a string with the same value as `webMessageAsString`. Use this instead of `PostWebMessageAsJson` if you want to communicate using simple strings rather than JSON objects.

#### remove_WebMessageReceived

Remove an event handler previously added with `add_WebMessageReceived`.

> public HRESULT [remove_WebMessageReceived](#remove_webmessagereceived)(EventRegistrationToken token)

