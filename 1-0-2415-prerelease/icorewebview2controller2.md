---
description: A continuation of the ICoreWebView2Controller interface.
title: WebView2 Win32 C++ ICoreWebView2Controller2
ms.date: 02/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Controller2
topic_type: 
- APIRef
api_name:
- ICoreWebView2Controller2
- ICoreWebView2Controller2.get_DefaultBackgroundColor
- ICoreWebView2Controller2.put_DefaultBackgroundColor
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Controller2

```
interface ICoreWebView2Controller2
  : public ICoreWebView2Controller
```

A continuation of the [ICoreWebView2Controller](icorewebview2controller.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DefaultBackgroundColor](#get_defaultbackgroundcolor) | The `DefaultBackgroundColor` property is the color WebView renders underneath all web content.
[put_DefaultBackgroundColor](#put_defaultbackgroundcolor) | Sets the `DefaultBackgroundColor` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### get_DefaultBackgroundColor

The `DefaultBackgroundColor` property is the color WebView renders underneath all web content.

> public HRESULT [get_DefaultBackgroundColor](#get_defaultbackgroundcolor)([COREWEBVIEW2_COLOR](corewebview2_color.md) * backgroundColor)

This means WebView renders this color when there is no web content loaded such as before the initial navigation or between navigations. This also means web pages with undefined css background properties or background properties containing transparent pixels will render their contents over this color. Web pages with defined and opaque background properties that span the page will obscure the `DefaultBackgroundColor` and display normally. The default value for this property is white to resemble the native browser experience.

The Color is specified by the [COREWEBVIEW2_COLOR](corewebview2_color.md) that represents an RGBA value. The `A` represents an Alpha value, meaning `DefaultBackgroundColor` can be transparent. In the case of a transparent `DefaultBackgroundColor` WebView will render hosting app content as the background. This Alpha value is not supported on Windows 7. Any `A` value other than 255 will result in E_INVALIDARG on Windows 7. It is supported on all other WebView compatible platforms.

Semi-transparent colors are not currently supported by this API and setting `DefaultBackgroundColor` to a semi-transparent color will fail with E_INVALIDARG. The only supported alpha values are 0 and 255, all other values will result in E_INVALIDARG. `DefaultBackgroundColor` can only be an opaque color or transparent.

This value may also be set by using the `WEBVIEW2_DEFAULT_BACKGROUND_COLOR` environment variable. There is a known issue with background color where setting the color by API can still leave the app with a white flicker before the `DefaultBackgroundColor` takes effect. Setting the color via environment variable solves this issue. The value must be a hex value that can optionally prepend a 0x. The value must account for the alpha value which is represented by the first 2 digits. So any hex value fewer than 8 digits will assume a prepended 00 to the hex value and result in a transparent color. `get_DefaultBackgroundColor` will return the result of this environment variable if used. This environment variable can only set the `DefaultBackgroundColor` once. Subsequent updates to background color must be done through API call.

```cpp
void ViewComponent::SetBackgroundColor(COLORREF color, bool transparent)
{
    m_webViewColor.R = GetRValue(color);
    m_webViewColor.G = GetGValue(color);
    m_webViewColor.B = GetBValue(color);
    m_webViewColor.A = transparent ? 0 : 255;
    wil::com_ptr<ICoreWebView2Controller2> controller2 =
        m_controller.query<ICoreWebView2Controller2>();
    controller2->put_DefaultBackgroundColor(m_webViewColor);
}
```

#### put_DefaultBackgroundColor

Sets the `DefaultBackgroundColor` property.

> public HRESULT [put_DefaultBackgroundColor](#put_defaultbackgroundcolor)([COREWEBVIEW2_COLOR](corewebview2_color.md) backgroundColor)

