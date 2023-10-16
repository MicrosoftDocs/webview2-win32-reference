---
description: This interface is an extension of ICoreWebView2_16 that supports shared buffer based on file mapping.
title: WebView2 Win32 C++ ICoreWebView2_17
ms.date: 10/16/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_17
topic_type: 
- APIRef
api_name:
- ICoreWebView2_17
- ICoreWebView2_17.PostSharedBufferToScript
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_17

```
interface ICoreWebView2_17
  : public ICoreWebView2_16
```

This interface is an extension of [ICoreWebView2_16](icorewebview2_16.md) that supports shared buffer based on file mapping.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[PostSharedBufferToScript](#postsharedbuffertoscript) | Share a shared buffer object with script of the main frame in the WebView.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### PostSharedBufferToScript

Share a shared buffer object with script of the main frame in the WebView.

> public HRESULT [PostSharedBufferToScript](#postsharedbuffertoscript)([ICoreWebView2SharedBuffer](icorewebview2sharedbuffer.md) * sharedBuffer, COREWEBVIEW2_SHARED_BUFFER_ACCESS access, LPCWSTR additionalDataAsJson)

The script will receive a `sharedbufferreceived` event from chrome.webview. The event arg for that event will have the following methods and properties: `getBuffer()`: return an ArrayBuffer object with the backing content from the shared buffer. `additionalData`: an object as the result of parsing `additionalDataAsJson` as JSON string. This property will be `undefined` if `additionalDataAsJson` is nullptr or empty string. `source`: with a value set as `chrome.webview` object. If a string is provided as `additionalDataAsJson` but it is not a valid JSON string, the API will fail with `E_INVALIDARG`. If `access` is COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_ONLY, the script will only have read access to the buffer. If the script tries to modify the content in a read only buffer, it will cause an access violation in WebView renderer process and crash the renderer process. If the shared buffer is already closed, the API will fail with `RO_E_CLOSED`.

The script code should call `chrome.webview.releaseBuffer` with the shared buffer as the parameter to release underlying resources as soon as it does not need access to the shared buffer any more.

The application can post the same shared buffer object to multiple web pages or iframes, or post to the same web page or iframe multiple times. Each `PostSharedBufferToScript` will create a separate ArrayBuffer object with its own view of the memory and is separately released. The underlying shared memory will be released when all the views are released.

For example, if we want to send data to script for one time read only consumption.

```cpp
        wil::com_ptr<ICoreWebView2Environment12> environment;
        CHECK_FAILURE(
            m_appWindow->GetWebViewEnvironment()->QueryInterface(IID_PPV_ARGS(&environment)));

        wil::com_ptr<ICoreWebView2SharedBuffer> sharedBuffer;
        CHECK_FAILURE(environment->CreateSharedBuffer(bufferSize, &sharedBuffer));
        // Set data into the shared memory via IStream.
        wil::com_ptr<IStream> stream;
        CHECK_FAILURE(sharedBuffer->OpenStream(&stream));
        CHECK_FAILURE(stream->Write(data, sizeof(data), nullptr));
        PCWSTR additionalDataAsJson = L"{\"myBufferType\":\"bufferType1\"}";
        if (fromFrame)
        {
            m_webviewFrame4->PostSharedBufferToScript(
                sharedBuffer.get(), COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_ONLY,
                additionalDataAsJson);
        }
        else
        {
            m_webView17->PostSharedBufferToScript(
                sharedBuffer.get(), COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_ONLY,
                additionalDataAsJson);
        }
        // Explicitly close the one time shared buffer to ensure that the resource is released.
        sharedBuffer->Close();
```

In the HTML document,

```html
            window.chrome.webview.addEventListener("sharedbufferreceived", e => {
                SharedBufferReceived(e);});
```

```html
        let readOnlySharedBuffer;
        function ShowReadOnlySharedBuffer() {
            if (readOnlySharedBuffer) {
                DisplaySharedBufferData(readOnlySharedBuffer);
            } else {
                // Post a web message to ask host to share the one time read only buffer.
                chrome.webview.postMessage("RequestOneTimeShareBuffer");
            }
        }

        function DisplaySharedBufferData(buffer) {
            document.getElementById("shared-buffer-data").value =
                new TextDecoder().decode(new Uint8Array(buffer));
        }

        function SharedBufferReceived(e) {
            if (e.additionalData && e.additionalData.myBufferType == "bufferType1") {
                readOnlySharedBuffer = e.getBuffer();
            } else {
                sharedBuffer = e.getBuffer();
            }
            DisplaySharedBufferData(e.getBuffer());
        }
        
        function ReleaseBuffer(buffer) {
          window.chrome.webview.releaseBuffer(buffer);
        }
```

Sharing a buffer to script has security risk. You should only share buffer with trusted site. If a buffer is shared to a untrusted site, possible sensitive information could be leaked. If a buffer is shared as modifiable by the script and the script modifies it in an unexpected way, it could result in corrupted data that might even crash the application.

