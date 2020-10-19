---
description: This interface is continuation of the [ICoreWebView2ExperimentalCompositionController](icorewebview2experimentalcompositioncontroller.md) interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCompositionController2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/19/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCompositionController2
---

# interface ICoreWebView2ExperimentalCompositionController2 

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalCompositionController2
  : public IUnknown
```

This interface is continuation of the [ICoreWebView2ExperimentalCompositionController](icorewebview2experimentalcompositioncontroller.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_SystemCursorId](#get_systemcursorid) | The current system cursor ID reported by the underlying rendering engine for WebView.

## Members

#### get_SystemCursorId 

The current system cursor ID reported by the underlying rendering engine for WebView.

> public HRESULT [get_SystemCursorId](#get_systemcursorid)(UINT32 * systemCursorId)

For example, most of the time, when the cursor is over text, this will return the int value for IDC_IBEAM. The systemCursorId is only valid if the rendering engine reports a default Windows cursor resource value. Navigate to [LoadCursorW](/windows/win32/api/winuser/nf-winuser-loadcursorw) for more details. Otherwise, if custom CSS cursors are being used, this will return 0. To actually use systemCursorId in LoadCursor or LoadImage, MAKEINTRESOURCE must be called on it first.

```cpp
                        UINT32 cursorId;
                        wil::com_ptr<ICoreWebView2ExperimentalCompositionController2> compositionController2 =
                            m_controller.query<ICoreWebView2ExperimentalCompositionController2>();
                        CHECK_FAILURE(compositionController2->get_SystemCursorId(&cursorId));
                        cursor = ::LoadCursor(nullptr, MAKEINTRESOURCE(cursorId));
                        if (cursor == nullptr)
                        {
                            hr = HRESULT_FROM_WIN32(GetLastError());
                        }
```

