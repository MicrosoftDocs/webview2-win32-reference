---
description: A continuation of the ICoreWebView2Profile interface to manage service and shared workers.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile13
ms.date: 10/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile13
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfile13
- ICoreWebView2ExperimentalProfile13.get_ServiceWorkerManager
- ICoreWebView2ExperimentalProfile13.get_SharedWorkerManager
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfile13

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile13
  : public IUnknown
```

A continuation of the [ICoreWebView2Profile](icorewebview2profile.md#icorewebview2profile) interface to manage service and shared workers.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ServiceWorkerManager](#get_serviceworkermanager) | Get the service worker manager to monitor service worker registrations and interact with the service workers associated with the current profile.
[get_SharedWorkerManager](#get_sharedworkermanager) | Get the shared worker manager to monitor shared worker creations and interact with the shared workers associated with the current profile.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### get_ServiceWorkerManager

Get the service worker manager to monitor service worker registrations and interact with the service workers associated with the current profile.

> public HRESULT [get_ServiceWorkerManager](#get_serviceworkermanager)([ICoreWebView2ExperimentalServiceWorkerManager](icorewebview2experimentalserviceworkermanager.md#icorewebview2experimentalserviceworkermanager) ** value)

```cpp
    auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
    CHECK_FEATURE_RETURN_EMPTY(webView2_13);

    wil::com_ptr<ICoreWebView2Profile> webView2Profile;
    CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
    auto webViewExperimentalProfile13 =
        webView2Profile.try_query<ICoreWebView2ExperimentalProfile13>();
    CHECK_FEATURE_RETURN_EMPTY(webViewExperimentalProfile13);
    CHECK_FAILURE(
        webViewExperimentalProfile13->get_ServiceWorkerManager(&m_serviceWorkerManager));
```

#### get_SharedWorkerManager

Get the shared worker manager to monitor shared worker creations and interact with the shared workers associated with the current profile.

> public HRESULT [get_SharedWorkerManager](#get_sharedworkermanager)([ICoreWebView2ExperimentalSharedWorkerManager](icorewebview2experimentalsharedworkermanager.md#icorewebview2experimentalsharedworkermanager) ** value)

```cpp
    auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
    CHECK_FEATURE_RETURN_EMPTY(webView2_13);

    wil::com_ptr<ICoreWebView2Profile> webView2Profile;
    CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
    auto webViewExperimentalProfile13 =
        webView2Profile.try_query<ICoreWebView2ExperimentalProfile13>();
    CHECK_FEATURE_RETURN_EMPTY(webViewExperimentalProfile13);
    CHECK_FAILURE(
        webViewExperimentalProfile13->get_SharedWorkerManager(&m_sharedWorkerManager));
```

