---
description: A continuation of the ICoreWebView2CompositionController interface.
title: WebView2 Win32 C++ ICoreWebView2CompositionController2
ms.date: 07/14/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CompositionController2
topic_type: 
- APIRef
api_name:
- ICoreWebView2CompositionController2
api_type:
- COM
---

# interface ICoreWebView2CompositionController2

```
interface ICoreWebView2CompositionController2
  : public ICoreWebView2CompositionController
```

A continuation of the [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md) interface.

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

