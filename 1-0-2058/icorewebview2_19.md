---
description: 
title: WebView2 Win32 C++ ICoreWebView2_19
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_19
topic_type: 
- APIRef
api_name:
- ICoreWebView2_19
- ICoreWebView2_19.get_MemoryUsageTargetLevel
- ICoreWebView2_19.put_MemoryUsageTargetLevel
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_19

```
interface ICoreWebView2_19
  : public ICoreWebView2_18
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_MemoryUsageTargetLevel](#get_memoryusagetargetlevel) | Gets the `MemoryUsageTargetLevel` property.
[put_MemoryUsageTargetLevel](#put_memoryusagetargetlevel) | Sets the `MemoryUsageTargetLevel` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    1.0.1905

## Members

#### get_MemoryUsageTargetLevel

Gets the `MemoryUsageTargetLevel` property.

> public HRESULT [get_MemoryUsageTargetLevel](#get_memoryusagetargetlevel)(COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL * value)

#### put_MemoryUsageTargetLevel

Sets the `MemoryUsageTargetLevel` property.

> public HRESULT [put_MemoryUsageTargetLevel](#put_memoryusagetargetlevel)(COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL value)

