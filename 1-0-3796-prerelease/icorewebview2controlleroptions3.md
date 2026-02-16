---
description: Controller option used to expose the DefaultBackgroundColor property early in the loading process.
title: WebView2 Win32 C++ ICoreWebView2ControllerOptions3
ms.date: 01/13/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ControllerOptions3
topic_type: 
- APIRef
api_name:
- ICoreWebView2ControllerOptions3
- ICoreWebView2ControllerOptions3.get_DefaultBackgroundColor
- ICoreWebView2ControllerOptions3.put_DefaultBackgroundColor
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ControllerOptions3

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ControllerOptions3
  : public ICoreWebView2ControllerOptions2
```

Controller option used to expose the DefaultBackgroundColor property early in the loading process.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DefaultBackgroundColor](#get_defaultbackgroundcolor) | Gets the `DefaultBackgroundColor` property.
[put_DefaultBackgroundColor](#put_defaultbackgroundcolor) | This property allows users to initialize the `DefaultBackgroundColor` early, preventing a white flash that can occur while WebView2 is loading when the background color is set to something other than white.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.3296.44
WebView2 Win32 Prerelease |    1.0.3296

## Members

#### get_DefaultBackgroundColor

Gets the `DefaultBackgroundColor` property.

> public HRESULT [get_DefaultBackgroundColor](#get_defaultbackgroundcolor)([COREWEBVIEW2_COLOR](corewebview2_color.md#corewebview2_color) * value)

#### put_DefaultBackgroundColor

This property allows users to initialize the `DefaultBackgroundColor` early, preventing a white flash that can occur while WebView2 is loading when the background color is set to something other than white.

> public HRESULT [put_DefaultBackgroundColor](#put_defaultbackgroundcolor)([COREWEBVIEW2_COLOR](corewebview2_color.md#corewebview2_color) value)

With early initialization, the color remains consistent from the start. After initialization, `CoreWebView2Controller.DefaultBackgroundColor` will return the value set using this API.

The `CoreWebView2Controller.DefaultBackgroundColor` can be set via the WEBVIEW2_DEFAULT_BACKGROUND_COLOR environment variable, which will remain supported for cases where this solution is being used. It is encouraged to transition away from the environment variable and use this API solution to apply the property. It is important to highlight that when set, the enviroment variable overrides ControllerOptions::DefaultBackgroundColor and becomes the initial value of Controller::DefaultBackgroundColor.

The `DefaultBackgroundColor` is the color that renders underneath all web content. This means WebView2 renders this color when there is no web content loaded. When no background color is defined in WebView2, it uses the `DefaultBackgroundColor` property to render the background. By default, this color is set to white.

This API only supports opaque colors and full transparency. It will fail for colors with alpha values that don't equal 0 or 255. When WebView2 is set to be fully transparent, it does not render a background, allowing the content from windows behind it to be visible.

