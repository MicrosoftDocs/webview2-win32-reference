---
description: This is an extension of the ICoreWebView2Settings Experimental interface for.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSettings4
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/23/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSettings4
---

# interface ICoreWebView2ExperimentalSettings4

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSettings4
  : public IUnknown
```

This is an extension of the [ICoreWebView2Settings](icorewebview2settings.md) Experimental interface for.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsPinchZoomEnabled](#get_ispinchzoomenabled) | Pinch-zoom, referred to as ???Page Scale??? zoom, is performed as a post-rendering step, it changes the page scale factor property and scales the surface the web page is rendered onto when user perfoms a pinch zooming action.
[put_IsPinchZoomEnabled](#put_ispinchzoomenabled) | Set the `IsPinchZoomEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.865

## Members

#### get_IsPinchZoomEnabled

Pinch-zoom, referred to as ???Page Scale??? zoom, is performed as a post-rendering step, it changes the page scale factor property and scales the surface the web page is rendered onto when user perfoms a pinch zooming action.

> public HRESULT [get_IsPinchZoomEnabled](#get_ispinchzoomenabled)(BOOL * enabled)

It does not change the layout but rather changes the viewport and clips the web content, the content outside of the viewport isn't visible onscreen and users can't reach this content using mouse.

The `IsPinchZoomEnabled` property enables or disables the ability of the end user to use a pinching motion on touch input enabled devices to scale the web content in the WebView2. It defaults to `TRUE`. When set to `FALSE`, the end user cannot pinch zoom. This API only affects the Page Scale zoom and has no effect on the existing browser zoom properties (`IsZoomControlEnabled` and `ZoomFactor`) or other end user mechanisms for zooming.

```cpp
            BOOL pinchZoomEnabled;
            wil::com_ptr<ICoreWebView2ExperimentalSettings4> experimentalSettings4;
            experimentalSettings4 = m_settings.try_query<ICoreWebView2ExperimentalSettings4>();
            CHECK_FAILURE(experimentalSettings4->get_IsPinchZoomEnabled(&pinchZoomEnabled));
            if (pinchZoomEnabled)
            {
                CHECK_FAILURE(experimentalSettings4->put_IsPinchZoomEnabled(FALSE));
                MessageBox(
                    nullptr, L"Pinch Zoom is disabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(experimentalSettings4->put_IsPinchZoomEnabled(TRUE));
                MessageBox(
                    nullptr, L"Pinch Zoom is enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_IsPinchZoomEnabled

Set the `IsPinchZoomEnabled` property.

> public HRESULT [put_IsPinchZoomEnabled](#put_ispinchzoomenabled)(BOOL enabled)

