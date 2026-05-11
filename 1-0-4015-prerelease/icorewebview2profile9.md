---
description: A continuation of the ICoreWebView2Profile interface to manage service workers, shared workers, and service worker script API settings.
title: WebView2 Win32 C++ ICoreWebView2Profile9
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile9
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile9
- ICoreWebView2Profile9.get_AreWebViewScriptApisEnabledForServiceWorkers
- ICoreWebView2Profile9.get_ServiceWorkerManager
- ICoreWebView2Profile9.get_SharedWorkerManager
- ICoreWebView2Profile9.put_AreWebViewScriptApisEnabledForServiceWorkers
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile9

```
interface ICoreWebView2Profile9
  : public ICoreWebView2Profile8
```

A continuation of the [ICoreWebView2Profile](icorewebview2profile.md#icorewebview2profile) interface to manage service workers, shared workers, and service worker script API settings.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AreWebViewScriptApisEnabledForServiceWorkers](#get_arewebviewscriptapisenabledforserviceworkers) | Gets the `AreWebViewScriptApisEnabledForServiceWorkers` property.
[get_ServiceWorkerManager](#get_serviceworkermanager) | Get the service worker manager to monitor service worker registrations and interact with the service workers associated with the current profile.
[get_SharedWorkerManager](#get_sharedworkermanager) | Get the shared worker manager to monitor shared worker creations and interact with the shared workers associated with the current profile.
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

#### get_ServiceWorkerManager

Get the service worker manager to monitor service worker registrations and interact with the service workers associated with the current profile.

> public HRESULT [get_ServiceWorkerManager](#get_serviceworkermanager)([ICoreWebView2ServiceWorkerManager](icorewebview2serviceworkermanager.md#icorewebview2serviceworkermanager) ** value)

```cpp
    auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
    CHECK_FEATURE_RETURN_EMPTY(webView2_13);

    wil::com_ptr<ICoreWebView2Profile> webView2Profile;
    CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
    auto webViewProfile9 = webView2Profile.try_query<ICoreWebView2Profile9>();
    CHECK_FEATURE_RETURN_EMPTY(webViewProfile9);
    CHECK_FAILURE(webViewProfile9->get_ServiceWorkerManager(&m_serviceWorkerManager));
```

#### get_SharedWorkerManager

Get the shared worker manager to monitor shared worker creations and interact with the shared workers associated with the current profile.

> public HRESULT [get_SharedWorkerManager](#get_sharedworkermanager)([ICoreWebView2SharedWorkerManager](icorewebview2sharedworkermanager.md#icorewebview2sharedworkermanager) ** value)

```cpp
    auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
    CHECK_FEATURE_RETURN_EMPTY(webView2_13);

    wil::com_ptr<ICoreWebView2Profile> webView2Profile;
    CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
    auto webViewProfile9 = webView2Profile.try_query<ICoreWebView2Profile9>();
    CHECK_FEATURE_RETURN_EMPTY(webViewProfile9);
    CHECK_FAILURE(webViewProfile9->get_SharedWorkerManager(&m_sharedWorkerManager));
```

#### put_AreWebViewScriptApisEnabledForServiceWorkers

Enables or disables webview2 specific Service Worker JS APIs in the WebView2s associated with this Profile.

> public HRESULT [put_AreWebViewScriptApisEnabledForServiceWorkers](#put_arewebviewscriptapisenabledforserviceworkers)(BOOL value)

When set to `TRUE`, chrome and webview objects are available in Service Workers. chrome.webview exposes APIs to interact with the WebView from Service Workers. The default value is `FALSE`. This setting applies to all newly installed Service Workers within the profile and is not persisted across WebView2 sessions. 
```cpp
        CHECK_FAILURE(
            webViewProfile9->get_AreWebViewScriptApisEnabledForServiceWorkers(&isEnabled));
        CHECK_FAILURE(
            webViewProfile9->put_AreWebViewScriptApisEnabledForServiceWorkers(!isEnabled));
```

