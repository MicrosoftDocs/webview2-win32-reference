---
description: 
title: WebView2 Win32 C++ ICoreWebView2CustomSchemeRegistration
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CustomSchemeRegistration
topic_type: 
- APIRef
api_name:
- ICoreWebView2CustomSchemeRegistration
- ICoreWebView2CustomSchemeRegistration.get_HasAuthorityComponent
- ICoreWebView2CustomSchemeRegistration.get_TreatAsSecure
- ICoreWebView2CustomSchemeRegistration.put_HasAuthorityComponent
- ICoreWebView2CustomSchemeRegistration.put_TreatAsSecure
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CustomSchemeRegistration

```
interface ICoreWebView2CustomSchemeRegistration
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HasAuthorityComponent](#get_hasauthoritycomponent) | Gets the `HasAuthorityComponent` property.
[get_TreatAsSecure](#get_treatassecure) | Gets the `TreatAsSecure` property.
[put_HasAuthorityComponent](#put_hasauthoritycomponent) | Sets the `HasAuthorityComponent` property.
[put_TreatAsSecure](#put_treatassecure) | Sets the `TreatAsSecure` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1587.40
WebView2 Win32 Prerelease |    1.0.1619

## Members

#### get_HasAuthorityComponent

Gets the `HasAuthorityComponent` property.

> public HRESULT [get_HasAuthorityComponent](#get_hasauthoritycomponent)(BOOL * value)

#### get_TreatAsSecure

Gets the `TreatAsSecure` property.

> public HRESULT [get_TreatAsSecure](#get_treatassecure)(INT32 * value)

#### put_HasAuthorityComponent

Sets the `HasAuthorityComponent` property.

> public HRESULT [put_HasAuthorityComponent](#put_hasauthoritycomponent)(BOOL value)

#### put_TreatAsSecure

Sets the `TreatAsSecure` property.

> public HRESULT [put_TreatAsSecure](#put_treatassecure)(INT32 value)

