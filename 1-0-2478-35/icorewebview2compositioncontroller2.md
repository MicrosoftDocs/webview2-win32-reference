---
description: A continuation of the ICoreWebView2CompositionController interface.
title: WebView2 Win32 C++ ICoreWebView2CompositionController2
ms.date: 05/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CompositionController2
topic_type: 
- APIRef
api_name:
- ICoreWebView2CompositionController2
- ICoreWebView2CompositionController2.get_AutomationProvider
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CompositionController2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2CompositionController2
  : public ICoreWebView2CompositionController
```

A continuation of the [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md#icorewebview2compositioncontroller) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AutomationProvider](#get_automationprovider) | Returns the Automation Provider for the WebView.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_AutomationProvider

Returns the Automation Provider for the WebView.

> public HRESULT [get_AutomationProvider](#get_automationprovider)(IUnknown ** provider)

This object implements IRawElementProviderSimple.

