---
description: Additional options used to create WebView2 Environment.
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions8
ms.date: 06/19/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions8
topic_type: 
- APIRef
api_name:
- ICoreWebView2EnvironmentOptions8
- ICoreWebView2EnvironmentOptions8.get_ScrollBarStyle
- ICoreWebView2EnvironmentOptions8.put_ScrollBarStyle
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EnvironmentOptions8

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2EnvironmentOptions8
  : public IUnknown
```

Additional options used to create WebView2 Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ScrollBarStyle](#get_scrollbarstyle) | Gets the `ScrollBarStyle` property.
[put_ScrollBarStyle](#put_scrollbarstyle) | The ScrollBar style being set on the WebView2 Environment.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2526

## Members

#### get_ScrollBarStyle

Gets the `ScrollBarStyle` property.

> public HRESULT [get_ScrollBarStyle](#get_scrollbarstyle)(COREWEBVIEW2_SCROLLBAR_STYLE * value)

#### put_ScrollBarStyle

The ScrollBar style being set on the WebView2 Environment.

> public HRESULT [put_ScrollBarStyle](#put_scrollbarstyle)(COREWEBVIEW2_SCROLLBAR_STYLE value)

The default value is `COREWEBVIEW2_SCROLLBAR_STYLE_DEFAULT` which specifies the default browser ScrollBar style. The `color-scheme` CSS property needs to be set on the corresponding page to allow ScrollBar to follow light or dark theme. Please see [color-scheme](https://developer.mozilla.org/en-US/docs/Web/CSS/color-scheme#declaring_color_scheme_preferences) for how `color-scheme` can be set. CSS styles that modify the ScrollBar applied on top of native ScrollBar styling that is selected with `ScrollBarStyle`.

