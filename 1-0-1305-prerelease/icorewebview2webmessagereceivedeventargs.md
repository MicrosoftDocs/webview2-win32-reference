---
description: Event args for the `WebMessageReceived` event.
title: WebView2 Win32 C++ ICoreWebView2WebMessageReceivedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebMessageReceivedEventArgs
---

# interface ICoreWebView2WebMessageReceivedEventArgs

```
interface ICoreWebView2WebMessageReceivedEventArgs
  : public IUnknown
```

Event args for the `WebMessageReceived` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Source](#get_source) | The URI of the document that sent this web message.
[get_WebMessageAsJson](#get_webmessageasjson) | The message posted from the WebView content to the host converted to a JSON string.
[TryGetWebMessageAsString](#trygetwebmessageasstring) | If the message posted from the WebView content to the host is a string type, this method returns the value of that string.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Source

The URI of the document that sent this web message.

> public HRESULT [get_Source](#get_source)(LPWSTR * source)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_WebMessageAsJson

The message posted from the WebView content to the host converted to a JSON string.

> public HRESULT [get_WebMessageAsJson](#get_webmessageasjson)(LPWSTR * webMessageAsJson)

Run this operation to communicate using JavaScript objects.

For example, the following `postMessage` runs result in the following `WebMessageAsJson` values.

```json
postMessage({'a': 'b'})      L"{\"a\": \"b\"}"
postMessage(1.2)             L"1.2"
postMessage('example')       L"\"example\""
```

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### TryGetWebMessageAsString

If the message posted from the WebView content to the host is a string type, this method returns the value of that string.

> public HRESULT [TryGetWebMessageAsString](#trygetwebmessageasstring)(LPWSTR * webMessageAsString)

If the message posted is some other kind of JavaScript type this method fails with the following error.

```text
E_INVALIDARG
```

Run this operation to communicate using simple strings.

For example, the following `postMessage` runs result in the following `WebMessageAsString` values.

```json
postMessage({'a': 'b'})      E_INVALIDARG
postMessage(1.2)             E_INVALIDARG
postMessage('example')       L"example"
```

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

