---
description: Event args for the `DragStarting` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDragStartingEventArgs
ms.date: 01/13/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDragStartingEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalDragStartingEventArgs
- ICoreWebView2ExperimentalDragStartingEventArgs.get_AllowedDropEffects
- ICoreWebView2ExperimentalDragStartingEventArgs.get_Data
- ICoreWebView2ExperimentalDragStartingEventArgs.get_Handled
- ICoreWebView2ExperimentalDragStartingEventArgs.get_Position
- ICoreWebView2ExperimentalDragStartingEventArgs.GetDeferral
- ICoreWebView2ExperimentalDragStartingEventArgs.put_Handled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalDragStartingEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDragStartingEventArgs
  : public IUnknown
```

Event args for the `DragStarting` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AllowedDropEffects](#get_alloweddropeffects) | The [OLE DROPEFFECT](https://learn.microsoft.com/en-us/windows/win32/com/dropeffect-constants) values this drag data supports.
[get_Data](#get_data) | The data to be dragged.
[get_Handled](#get_handled) | Gets the `Handled` property.
[get_Position](#get_position) | The position at which drag was detected given in WebView2 relative coordinates.
[GetDeferral](#getdeferral) | Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.
[put_Handled](#put_handled) | Indicates whether this event has been handled by the app.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_AllowedDropEffects

The [OLE DROPEFFECT](https://learn.microsoft.com/en-us/windows/win32/com/dropeffect-constants) values this drag data supports.

> public HRESULT [get_AllowedDropEffects](#get_alloweddropeffects)(DWORD * value)

#### get_Data

The data to be dragged.

> public HRESULT [get_Data](#get_data)(IDataObject ** value)

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_Position

The position at which drag was detected given in WebView2 relative coordinates.

> public HRESULT [get_Position](#get_position)(POINT * value)

#### GetDeferral

Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) ** value)

Use this operation to complete the CoreWebView2DragStartingEventArgs.

Until the deferral is completed, subsequent attempts to initiate drag in the WebView2 will fail and if the cursor was changed as part of drag it will not restore.

#### put_Handled

Indicates whether this event has been handled by the app.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

If the app handles this event, WebView2 will not initiate drag drop. If the app does not handle the event, WebView2 will initiate its own drag drop logic.

