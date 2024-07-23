---
description: Provides a set of properties for a frame in the ICoreWebView2.
title: WebView2 Win32 C++ ICoreWebView2FrameInfo
ms.date: 07/23/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameInfo
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameInfo
- ICoreWebView2FrameInfo.get_Name
- ICoreWebView2FrameInfo.get_Source
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameInfo

```
interface ICoreWebView2FrameInfo
  : public IUnknown
```

Provides a set of properties for a frame in the [ICoreWebView2](icorewebview2.md#icorewebview2).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Name](#get_name) | The value of iframe's window.name property.
[get_Source](#get_source) | The URI of the document in the frame.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.818.41
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_Name

The value of iframe's window.name property.

> public HRESULT [get_Name](#get_name)(LPWSTR * value)

The default value equals to iframe html tag declaring it, as in `<iframe name="frame-name">...</iframe>`. The returned string is empty when the frame has no name attribute and no assigned value for window.name.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Source

The URI of the document in the frame.

> public HRESULT [get_Source](#get_source)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

