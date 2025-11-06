---
description: This interface is an extension of ICoreWebView2 to configure the window controls overlay.
title: WebView2 Win32 C++ ICoreWebView2Experimental31
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental31
topic_type: 
- APIRef
api_name:
- ICoreWebView2Experimental31
- ICoreWebView2Experimental31.get_WindowControlsOverlay
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Experimental31

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental31
  : public IUnknown
```

This interface is an extension of [ICoreWebView2](icorewebview2.md#icorewebview2) to configure the window controls overlay.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_WindowControlsOverlay](#get_windowcontrolsoverlay) | This getter API provides access to the window controls overlay object.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### get_WindowControlsOverlay

This getter API provides access to the window controls overlay object.

> public HRESULT [get_WindowControlsOverlay](#get_windowcontrolsoverlay)([ICoreWebView2ExperimentalWindowControlsOverlay](icorewebview2experimentalwindowcontrolsoverlay.md#icorewebview2experimentalwindowcontrolsoverlay) ** value)

```cpp
    std::wstring sampleUri = appWindow->GetLocalUri(c_samplePath);
    WebViewCreateOption options = appWindow->GetWebViewOption();
    options.useWco = true;
    AppWindow* appWindowWco = new AppWindow(appWindow->GetCreationModeId(), options, sampleUri);
```

