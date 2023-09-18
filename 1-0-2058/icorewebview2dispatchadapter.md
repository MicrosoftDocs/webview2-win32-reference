---
description: 
title: WebView2 Win32 C++ ICoreWebView2DispatchAdapter
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DispatchAdapter
topic_type: 
- APIRef
api_name:
- ICoreWebView2DispatchAdapter
- ICoreWebView2DispatchAdapter.Clean
- ICoreWebView2DispatchAdapter.UnwrapObject
- ICoreWebView2DispatchAdapter.WrapNamedObject
- ICoreWebView2DispatchAdapter.WrapObject
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DispatchAdapter

```
interface ICoreWebView2DispatchAdapter
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Clean](#clean) | 
[UnwrapObject](#unwrapobject) | 
[WrapNamedObject](#wrapnamedobject) | 
[WrapObject](#wrapobject) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Clean

> public HRESULT [Clean](#clean)()

#### UnwrapObject

> public HRESULT [UnwrapObject](#unwrapobject)(VARIANT wrapped, VARIANT * value)

#### WrapNamedObject

> public HRESULT [WrapNamedObject](#wrapnamedobject)(LPCWSTR name, IICoreWebView2DispatchAdapter * adapter, VARIANT * value)

#### WrapObject

> public HRESULT [WrapObject](#wrapobject)(VARIANT unwrapped, IICoreWebView2DispatchAdapter * adapter, VARIANT * value)

