---
description: This interface is an extension of the ICoreWebView2CompositionController.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCompositionController4
ms.date: 04/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCompositionController4
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalCompositionController4
- ICoreWebView2ExperimentalCompositionController4.CreateCoreWebView2PointerInfoFromPointerId
- ICoreWebView2ExperimentalCompositionController4.get_AutomationProvider
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalCompositionController4

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalCompositionController4
  : public IUnknown
```

This interface is an extension of the [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md#icorewebview2compositioncontroller).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateCoreWebView2PointerInfoFromPointerId](#createcorewebview2pointerinfofrompointerid) | A helper function to convert a pointerId received from the system into an ICoreWebView2ExperimentalPointerInfo.
[get_AutomationProvider](#get_automationprovider) | Returns the UI Automation Provider for the WebView.

An object implementing ICoreWebView2ExperimentalCompositionController4 interface will also implement [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md#icorewebview2compositioncontroller).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.790

## Members

#### CreateCoreWebView2PointerInfoFromPointerId

A helper function to convert a pointerId received from the system into an ICoreWebView2ExperimentalPointerInfo.

> public HRESULT [CreateCoreWebView2PointerInfoFromPointerId](#createcorewebview2pointerinfofrompointerid)(UINT32 PointerId, HWND ParentWindow, [COREWEBVIEW2_MATRIX_4X4](corewebview2_matrix_4x4.md#corewebview2_matrix_4x4) transform, [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md#icorewebview2pointerinfo) ** value)

parentWindow is the HWND that contains the WebView. This can be any HWND in the hwnd tree that contains the WebView. The [COREWEBVIEW2_MATRIX_4X4](corewebview2_matrix_4x4.md#corewebview2_matrix_4x4) is the transform from that HWND to the WebView. The returned ICoreWebView2ExperimentalPointerInfo is used in SendPointerInfo. The pointer type must be either pen or touch or the function will fail.

#### get_AutomationProvider

Returns the UI Automation Provider for the WebView.

> public HRESULT [get_AutomationProvider](#get_automationprovider)(IUnknown ** value)

