---
description: A continuation of the ICoreWebView2Controller interface.
title: WebView2 Win32 C++ ICoreWebView2Controller2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/01/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Controller2
---

# interface ICoreWebView2Controller2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Controller2
  : public ICoreWebView2Controller
```

A continuation of the [ICoreWebView2Controller](icorewebview2controller.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DefaultBackgroundColor](#get_defaultbackgroundcolor) | The `DefaultBackgroundColor` property allows developers to set the color that shows when WebView has not loaded any web content and when a webpage does not specify a background color.
[put_DefaultBackgroundColor](#put_defaultbackgroundcolor) | Sets the `DefaultBackgroundColor` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### get_DefaultBackgroundColor

The `DefaultBackgroundColor` property allows developers to set the color that shows when WebView has not loaded any web content and when a webpage does not specify a background color.

> public HRESULT [get_DefaultBackgroundColor](#get_defaultbackgroundcolor)(COREWEBVIEW2_COLOR * backgroundColor)

Color is specified by the COREWEBVIEW2_COLOR value meaning the background color can also be transparent. The WebView background color will show before the initial navigation, between navigations before the next page has rendered, and for pages with no `background` style properties set. To clarify the latter case, WebView will always honor a webpage's background content. `DefaultBackgroundColor` will only show in the absence of css `background` style properties. In that case, WebView will render web content over the `DefaultBackgroundColor` color. For a transparent background, web content will render over hosting app content. WebView's default background color is white to resemble the browser experience. It is important to note that while COREWEBVIEW2_COLOR has `A` an alpha value, semi-transparent colors are not supported by this API and setting `DefaultBackgroundColor` to a semi-transparent color will fail with E_INVALIDARG. The only supported alpha values are 0 and 255, all other values will result in E_INVALIDARG. `DefaultBackgroundColor` can only be an opaque color or transparent.

The `DefaultBackgroundColor` property enables a smoother UI experience. Developers can choose the color that shows between loading pages and eliminate any 'white flash.' For websites with no specified background color, developers can display web contents over a color of their choosing. They can also do away with the background color entirely with transparency and have the 'in between pages color' just be hosting content, or have hosting app content be the backdrop for webpages without a background color specified.

```cpp
void ViewComponent::SetBackgroundColor(COLORREF color, bool transparent)
{
    COREWEBVIEW2_COLOR wvColor;
    wvColor.R = GetRValue(color);
    wvColor.G = GetGValue(color);
    wvColor.B = GetBValue(color);
    wvColor.A = transparent ? 0 : 255;
    wil::com_ptr<ICoreWebView2Controller2> controller2 =
        m_controller.query<ICoreWebView2Controller2>();
    controller2->put_DefaultBackgroundColor(wvColor);
}
```

#### put_DefaultBackgroundColor

Sets the `DefaultBackgroundColor` property.

> public HRESULT [put_DefaultBackgroundColor](#put_defaultbackgroundcolor)(COREWEBVIEW2_COLOR backgroundColor)

