---
description: 
title: WebView2 Win32 C++ ICoreWebView2Settings3
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings3
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings3
- ICoreWebView2Settings3.get_AreBrowserAcceleratorKeysEnabled
- ICoreWebView2Settings3.put_AreBrowserAcceleratorKeysEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings3

```
interface ICoreWebView2Settings3
  : public ICoreWebView2Settings2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AreBrowserAcceleratorKeysEnabled](#get_arebrowseracceleratorkeysenabled) | Gets the `AreBrowserAcceleratorKeysEnabled` property.
[put_AreBrowserAcceleratorKeysEnabled](#put_arebrowseracceleratorkeysenabled) | Sets the `AreBrowserAcceleratorKeysEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.864.35
WebView2 Win32 Prerelease |    1.0.865

## Members

#### get_AreBrowserAcceleratorKeysEnabled

Gets the `AreBrowserAcceleratorKeysEnabled` property.

> public HRESULT [get_AreBrowserAcceleratorKeysEnabled](#get_arebrowseracceleratorkeysenabled)(BOOL * value)

#### put_AreBrowserAcceleratorKeysEnabled

Sets the `AreBrowserAcceleratorKeysEnabled` property.

> public HRESULT [put_AreBrowserAcceleratorKeysEnabled](#put_arebrowseracceleratorkeysenabled)(BOOL value)

