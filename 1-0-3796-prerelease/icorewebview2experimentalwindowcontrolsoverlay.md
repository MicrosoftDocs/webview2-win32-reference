---
description: This is the ICoreWebView2ExperimentalWindowControlsOverlay.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalWindowControlsOverlay
ms.date: 01/13/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalWindowControlsOverlay
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalWindowControlsOverlay
- ICoreWebView2ExperimentalWindowControlsOverlay.get_BackgroundColor
- ICoreWebView2ExperimentalWindowControlsOverlay.get_Height
- ICoreWebView2ExperimentalWindowControlsOverlay.get_IsEnabled
- ICoreWebView2ExperimentalWindowControlsOverlay.put_BackgroundColor
- ICoreWebView2ExperimentalWindowControlsOverlay.put_Height
- ICoreWebView2ExperimentalWindowControlsOverlay.put_IsEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalWindowControlsOverlay

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalWindowControlsOverlay
  : public IUnknown
```

This is the ICoreWebView2ExperimentalWindowControlsOverlay.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_BackgroundColor](#get_backgroundcolor) | Gets the `BackgroundColor` property.
[get_Height](#get_height) | Gets the `Height` property.
[get_IsEnabled](#get_isenabled) | Gets the `IsEnabled` property.
[put_BackgroundColor](#put_backgroundcolor) | The `BackgroundColor` property allows you to set a background color for the overlay.
[put_Height](#put_height) | The `Height` property in pixels, allows you to set the height of the overlay and title bar area.
[put_IsEnabled](#put_isenabled) | The `IsEnabled` property allows you to opt in to using the WebView2 window controls overlay.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### get_BackgroundColor

Gets the `BackgroundColor` property.

> public HRESULT [get_BackgroundColor](#get_backgroundcolor)([COREWEBVIEW2_COLOR](corewebview2_color.md#corewebview2_color) * value)

#### get_Height

Gets the `Height` property.

> public HRESULT [get_Height](#get_height)(UINT32 * value)

#### get_IsEnabled

Gets the `IsEnabled` property.

> public HRESULT [get_IsEnabled](#get_isenabled)(BOOL * value)

#### put_BackgroundColor

The `BackgroundColor` property allows you to set a background color for the overlay.

> public HRESULT [put_BackgroundColor](#put_backgroundcolor)([COREWEBVIEW2_COLOR](corewebview2_color.md#corewebview2_color) value)

Based on the background color you choose, Webview2 will automatically calculate a foreground and hover color. Defaults to #f3f3f3

#### put_Height

The `Height` property in pixels, allows you to set the height of the overlay and title bar area.

> public HRESULT [put_Height](#put_height)(UINT32 value)

Defaults to 48px.

```cpp
    std::wstring sampleUri = appWindow->GetLocalUri(c_samplePath);
    WebViewCreateOption options = appWindow->GetWebViewOption();
    options.useWco = true;
    AppWindow* appWindowWco = new AppWindow(appWindow->GetCreationModeId(), options, sampleUri);
```

#### put_IsEnabled

The `IsEnabled` property allows you to opt in to using the WebView2 window controls overlay.

> public HRESULT [put_IsEnabled](#put_isenabled)(BOOL value)

Defaults to `FALSE`.

When this property is `TRUE`, WebView2 will draw its own minimize, maximize, and close buttons on the top right corner of the Webview2.

When using this you should configure your app window to not display its default window control buttons. You are responsible for creating a title bar for your app by using the available space to the left of the controls overlay. In doing so, you can utilize the [IsNonClientRegionSupportEnabled](https://learn.microsoft.com/en-us/microsoft-edge/webview2/reference/win32/icorewebview2settings9?view=webview2-1.0.2739.15) API to enable draggable regions for your custom title bar.

The Overlay buttons will sit on top of the HTML content, and will prevent mouse interactions with any elements directly below it, so you should avoid placing content there. To that end, there are four [CSS environment variables](https://learn.microsoft.com/en-us/microsoft-edge/progressive-web-apps-chromium/how-to/window-controls-overlay#use-css-environment-variables-to-stay-clear-of-the-overlay) defined to help you get the dimensions of the available titlebar area to the left of the overlay. Similarly the navigator object will contain a [WindowControlsOverlay](https://learn.microsoft.com/en-us/microsoft-edge/progressive-web-apps-chromium/how-to/window-controls-overlay#react-to-overlay-changes) property which can be used to get the titlebar area as a rect, and listen for changes to the size of that area.

```cpp
    std::wstring sampleUri = appWindow->GetLocalUri(c_samplePath);
    WebViewCreateOption options = appWindow->GetWebViewOption();
    options.useWco = true;
    AppWindow* appWindowWco = new AppWindow(appWindow->GetCreationModeId(), options, sampleUri);
```

