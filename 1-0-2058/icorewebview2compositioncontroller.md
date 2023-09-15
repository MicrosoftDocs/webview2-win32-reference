---
description: 
title: WebView2 Win32 C++ ICoreWebView2CompositionController
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CompositionController
topic_type: 
- APIRef
api_name:
- ICoreWebView2CompositionController
- ICoreWebView2CompositionController.add_CursorChanged
- ICoreWebView2CompositionController.get_RootVisualTarget
- ICoreWebView2CompositionController.put_RootVisualTarget
- ICoreWebView2CompositionController.remove_CursorChanged
- ICoreWebView2CompositionController.SendMouseInput
- ICoreWebView2CompositionController.SendPointerInput
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CompositionController

```
interface ICoreWebView2CompositionController
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_CursorChanged](#add_cursorchanged) | Adds an event handler for the `CursorChanged` event.
[get_RootVisualTarget](#get_rootvisualtarget) | Gets the `RootVisualTarget` property.
[put_RootVisualTarget](#put_rootvisualtarget) | Sets the `RootVisualTarget` property.
[remove_CursorChanged](#remove_cursorchanged) | Removes an event handler previously added with `add_CursorChanged`.
[SendMouseInput](#sendmouseinput) | 
[SendPointerInput](#sendpointerinput) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### add_CursorChanged

Adds an event handler for the `CursorChanged` event.

> public HRESULT [add_CursorChanged](#add_cursorchanged)([ICoreWebView2CursorChangedEventHandler](icorewebview2cursorchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### get_RootVisualTarget

Gets the `RootVisualTarget` property.

> public HRESULT [get_RootVisualTarget](#get_rootvisualtarget)(VARIANT * value)

#### put_RootVisualTarget

Sets the `RootVisualTarget` property.

> public HRESULT [put_RootVisualTarget](#put_rootvisualtarget)(VARIANT value)

#### remove_CursorChanged

Removes an event handler previously added with `add_CursorChanged`.

> public HRESULT [remove_CursorChanged](#remove_cursorchanged)(EventRegistrationToken token)

#### SendMouseInput

> public HRESULT [SendMouseInput](#sendmouseinput)(COREWEBVIEW2_MOUSE_EVENT_KIND eventKind, COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS virtualKeys, UINT32 mouseData, POINT point)

#### SendPointerInput

> public HRESULT [SendPointerInput](#sendpointerinput)(COREWEBVIEW2_POINTER_EVENT_KIND eventKind, [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md) * pointerInfo)

