---
description: A continuation of the ICoreWebView2Settings interface to manage pinch zoom.
title: WebView2 Win32 C++ ICoreWebView2Settings5
ms.date: 06/19/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings5
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings5
- ICoreWebView2Settings5.get_IsPinchZoomEnabled
- ICoreWebView2Settings5.put_IsPinchZoomEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings5

```
interface ICoreWebView2Settings5
  : public ICoreWebView2Settings4
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md#icorewebview2settings) interface to manage pinch zoom.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsPinchZoomEnabled](#get_ispinchzoomenabled) | Gets the `IsPinchZoomEnabled` property.
[put_IsPinchZoomEnabled](#put_ispinchzoomenabled) | Pinch-zoom, referred to as "Page Scale" zoom, is performed as a post-rendering step, it changes the page scale factor property and scales the surface the web page is rendered onto when user performs a pinch zooming action.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### get_IsPinchZoomEnabled

Gets the `IsPinchZoomEnabled` property.

> public HRESULT [get_IsPinchZoomEnabled](#get_ispinchzoomenabled)(BOOL * value)

#### put_IsPinchZoomEnabled

Pinch-zoom, referred to as "Page Scale" zoom, is performed as a post-rendering step, it changes the page scale factor property and scales the surface the web page is rendered onto when user performs a pinch zooming action.

> public HRESULT [put_IsPinchZoomEnabled](#put_ispinchzoomenabled)(BOOL value)

It does not change the layout but rather changes the viewport and clips the web content, the content outside of the viewport isn't visible onscreen and users can't reach this content using mouse.

The `IsPinchZoomEnabled` property enables or disables the ability of the end user to use a pinching motion on touch input enabled devices to scale the web content in the WebView2. It defaults to `TRUE`. When set to `FALSE`, the end user cannot pinch zoom after the next navigation. Disabling/Enabling `IsPinchZoomEnabled` only affects the end user's ability to use pinch motions and does not change the page scale factor. This API only affects the Page Scale zoom and has no effect on the existing browser zoom properties (`IsZoomControlEnabled` and `ZoomFactor`) or other end user mechanisms for zooming.

```cpp
            CHECK_FEATURE_RETURN(m_settings5);

            BOOL pinchZoomEnabled;
            CHECK_FAILURE(m_settings5->get_IsPinchZoomEnabled(&pinchZoomEnabled));
            if (pinchZoomEnabled)
            {
                CHECK_FAILURE(m_settings5->put_IsPinchZoomEnabled(FALSE));
                MessageBox(
                    nullptr, L"Pinch Zoom is disabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings5->put_IsPinchZoomEnabled(TRUE));
                MessageBox(
                    nullptr, L"Pinch Zoom is enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

