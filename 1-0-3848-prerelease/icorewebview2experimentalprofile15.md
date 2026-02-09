---
description: A continuation of the ICoreWebView2Profile interface to manage Service Worker JS APIs.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile15
ms.date: 02/09/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile15
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfile15
- ICoreWebView2ExperimentalProfile15.get_AreWebViewScriptApisEnabledForServiceWorkers
- ICoreWebView2ExperimentalProfile15.put_AreWebViewScriptApisEnabledForServiceWorkers
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfile15

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile15
  : public IUnknown
```

A continuation of the [ICoreWebView2Profile](icorewebview2profile.md#icorewebview2profile) interface to manage Service Worker JS APIs.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AreWebViewScriptApisEnabledForServiceWorkers](#get_arewebviewscriptapisenabledforserviceworkers) | Gets the `AreWebViewScriptApisEnabledForServiceWorkers` property.
[put_AreWebViewScriptApisEnabledForServiceWorkers](#put_arewebviewscriptapisenabledforserviceworkers) | Enables or disables webview2 specific Service Worker JS APIs in the WebView2s associated with this Profile.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_AreWebViewScriptApisEnabledForServiceWorkers

Gets the `AreWebViewScriptApisEnabledForServiceWorkers` property.

> public HRESULT [get_AreWebViewScriptApisEnabledForServiceWorkers](#get_arewebviewscriptapisenabledforserviceworkers)(BOOL * value)

#### put_AreWebViewScriptApisEnabledForServiceWorkers

Enables or disables webview2 specific Service Worker JS APIs in the WebView2s associated with this Profile.

> public HRESULT [put_AreWebViewScriptApisEnabledForServiceWorkers](#put_arewebviewscriptapisenabledforserviceworkers)(BOOL value)

When set to `TRUE`, chrome and webview objects are available in Service Workers. chrome.webview exposes APIs to interact with the WebView from Service Workers. The default value is `FALSE`. This setting applies to all newly installed Service Workers within the profile and is not persisted across WebView2 sessions. 
```cpp
        CHECK_FAILURE(
            webViewExperimentalProfile15->get_AreWebViewScriptApisEnabledForServiceWorkers(
                &isEnabled));
        CHECK_FAILURE(
            webViewExperimentalProfile15->put_AreWebViewScriptApisEnabledForServiceWorkers(
                !isEnabled));
```

