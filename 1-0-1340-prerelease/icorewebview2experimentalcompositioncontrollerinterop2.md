---
description: Experimental Interop interface for the CoreWebView2CompositionController WinRT object to allow WinRT end developers to be able to use the COM interfaces as parameters for some methods.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCompositionControllerInterop2
ms.date: 09/06/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCompositionControllerInterop2
---

# interface ICoreWebView2ExperimentalCompositionControllerInterop2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalCompositionControllerInterop2
  : public IUnknown
```

Experimental Interop interface for the CoreWebView2CompositionController WinRT object to allow WinRT end developers to be able to use the COM interfaces as parameters for some methods.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[DragEnter](#dragenter) | This function corresponds to [IDropTarget::DragEnter][WindowsWin32ApiOleidlNfOleidlIdroptargetDragenter].
[DragLeave](#dragleave) | This function corresponds to [IDropTarget::DragLeave][WindowsWin32ApiOleidlNfOleidlIdroptargetDragleave].
[DragOver](#dragover) | This function corresponds to [IDropTarget::DragOver][WindowsWin32ApiOleidlNfOleidlIdroptargetDragover].
[Drop](#drop) | This function corresponds to [IDropTarget::Drop][WindowsWin32ApiOleidlNfOleidlIdroptargetDrop].

This interface is implemented by the Microsoft.Web.WebView2.Core.CoreWebView2CompositionController runtime class.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1340

## Members

#### DragEnter

This function corresponds to [IDropTarget::DragEnter][WindowsWin32ApiOleidlNfOleidlIdroptargetDragenter].

> public HRESULT [DragEnter](#dragenter)(IDataObject * dataObject, DWORD keyState, POINT point, DWORD * effect)

This function has a dependency on AllowExternalDrop property of CoreWebView2Controller and return E_FAIL to callers to indicate this operation is not allowed if AllowExternalDrop property is set to false.

The hosting application must register as an IDropTarget and implement and forward DragEnter calls to this function.

In addition, the hosting application needs to create an IDropTargetHelper and call the corresponding [IDropTargetHelper::DragEnter][WindowsWin32ApiShobjidlCoreNfShobjidlCoreIdroptargethelperDragenter] function on that object before forwarding the call to WebView.

point parameter must be modified to include the WebView's offset and be in the WebView's client coordinates (Similar to how SendMouseInput works).

[WindowsWin32ApiOleidlNfOleidlIdroptargetDragenter]: /windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter "IDropTarget::DragEnter (oleidl.h) - Win32 apps | Microsoft Docs"

[WindowsWin32ApiShobjidlCoreNfShobjidlCoreIdroptargethelperDragenter]: /windows/win32/api/shobjidl_core/nf-shobjidl_core-idroptargethelper-dragenter "IDropTargetHelper::DragEnter (shobjidl_core.h) - Win32 apps | Microsoft Docs"

```cpp
HRESULT DropTarget::DragEnter(
    IDataObject* dataObject, DWORD keyState, POINTL cursorPosition, DWORD* effect)
{
    POINT point = {cursorPosition.x, cursorPosition.y};
    // Convert the screen point to client coordinates add the WebView's offset.
    m_viewComponent->OffsetPointToWebView(&point);
    return m_webViewExperimentalCompositionController3->DragEnter(
        dataObject, keyState, point, effect);
}
```

#### DragLeave

This function corresponds to [IDropTarget::DragLeave][WindowsWin32ApiOleidlNfOleidlIdroptargetDragleave].

> public HRESULT [DragLeave](#dragleave)()

This function has a dependency on AllowExternalDrop property of CoreWebView2Controller and return E_FAIL to callers to indicate this operation is not allowed if AllowExternalDrop property is set to false.

The hosting application must register as an IDropTarget and implement and forward DragLeave calls to this function.

In addition, the hosting application needs to create an IDropTargetHelper and call the corresponding [IDropTargetHelper::DragLeave][WindowsWin32ApiShobjidlCoreNfShobjidlCoreIdroptargethelperDragleave] function on that object before forwarding the call to WebView.

[WindowsWin32ApiOleidlNfOleidlIdroptargetDragleave]: /windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave "IDropTarget::DragLeave (oleidl.h) - Win32 apps | Microsoft Docs"

[WindowsWin32ApiShobjidlCoreNfShobjidlCoreIdroptargethelperDragleave]: /windows/win32/api/shobjidl_core/nf-shobjidl_core-idroptargethelper-dragleave "IDropTargetHelper::DragLeave (shobjidl_core.h) - Win32 apps | Microsoft Docs"

```cpp
HRESULT DropTarget::DragLeave()
{
    return m_webViewExperimentalCompositionController3->DragLeave();
}
```

#### DragOver

This function corresponds to [IDropTarget::DragOver][WindowsWin32ApiOleidlNfOleidlIdroptargetDragover].

> public HRESULT [DragOver](#dragover)(DWORD keyState, POINT point, DWORD * effect)

This function has a dependency on AllowExternalDrop property of CoreWebView2Controller and return E_FAIL to callers to indicate this operation is not allowed if AllowExternalDrop property is set to false.

The hosting application must register as an IDropTarget and implement and forward DragOver calls to this function.

In addition, the hosting application needs to create an IDropTargetHelper and call the corresponding [IDropTargetHelper::DragOver][WindowsWin32ApiShobjidlCoreNfShobjidlCoreIdroptargethelperDragover] function on that object before forwarding the call to WebView.

point parameter must be modified to include the WebView's offset and be in the WebView's client coordinates (Similar to how SendMouseInput works).

[WindowsWin32ApiOleidlNfOleidlIdroptargetDragover]: /windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover "IDropTarget::DragOver (oleidl.h) - Win32 apps | Microsoft Docs"

[WindowsWin32ApiShobjidlCoreNfShobjidlCoreIdroptargethelperDragover]: /windows/win32/api/shobjidl_core/nf-shobjidl_core-idroptargethelper-dragover "IDropTargetHelper::DragOver (shobjidl_core.h) - Win32 apps | Microsoft Docs"

```cpp
HRESULT DropTarget::DragOver(DWORD keyState, POINTL cursorPosition, DWORD* effect)
{
    POINT point = {cursorPosition.x, cursorPosition.y};
    // Convert the screen point to client coordinates add the WebView's offset.
    // This returns whether the resultant point is over the WebView visual.
    m_viewComponent->OffsetPointToWebView(&point);
    return m_webViewExperimentalCompositionController3->DragOver(
        keyState, point, effect);
}
```

#### Drop

This function corresponds to [IDropTarget::Drop][WindowsWin32ApiOleidlNfOleidlIdroptargetDrop].

> public HRESULT [Drop](#drop)(IDataObject * dataObject, DWORD keyState, POINT point, DWORD * effect)

This function has a dependency on AllowExternalDrop property of CoreWebView2Controller and return E_FAIL to callers to indicate this operation is not allowed if AllowExternalDrop property is set to false.

The hosting application must register as an IDropTarget and implement and forward Drop calls to this function.

In addition, the hosting application needs to create an IDropTargetHelper and call the corresponding [IDropTargetHelper::Drop][WindowsWin32ApiShobjidlCoreNfShobjidlCoreIdroptargethelperDrop] function on that object before forwarding the call to WebView.

point parameter must be modified to include the WebView's offset and be in the WebView's client coordinates (Similar to how SendMouseInput works).

[WindowsWin32ApiOleidlNfOleidlIdroptargetDrop]: /windows/win32/api/oleidl/nf-oleidl-idroptarget-drop "IDropTarget::Drop (oleidl.h) - Win32 apps | Microsoft Docs"

[WindowsWin32ApiShobjidlCoreNfShobjidlCoreIdroptargethelperDrop]: /windows/win32/api/shobjidl_core/nf-shobjidl_core-idroptargethelper-drop "IDropTargetHelper::Drop (shobjidl_core.h) - Win32 apps | Microsoft Docs"

```cpp
HRESULT DropTarget::Drop(
    IDataObject* dataObject, DWORD keyState, POINTL cursorPosition, DWORD* effect)
{
    POINT point = {cursorPosition.x, cursorPosition.y};
    // Convert the screen point to client coordinates add the WebView's offset.
    // This returns whether the resultant point is over the WebView visual.
    m_viewComponent->OffsetPointToWebView(&point);
    return m_webViewExperimentalCompositionController3->Drop(dataObject, keyState, point, effect);
}
```

