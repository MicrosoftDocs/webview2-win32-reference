---
description: 
title: WebView2 Win32 C++ ICoreWebView2Controller
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Controller
topic_type: 
- APIRef
api_name:
- ICoreWebView2Controller
- ICoreWebView2Controller.add_AcceleratorKeyPressed
- ICoreWebView2Controller.add_GotFocus
- ICoreWebView2Controller.add_LostFocus
- ICoreWebView2Controller.add_MoveFocusRequested
- ICoreWebView2Controller.add_ZoomFactorChanged
- ICoreWebView2Controller.Close
- ICoreWebView2Controller.get_Bounds
- ICoreWebView2Controller.get_CoreWebView2
- ICoreWebView2Controller.get_IsVisible
- ICoreWebView2Controller.get_ParentWindow
- ICoreWebView2Controller.get_ZoomFactor
- ICoreWebView2Controller.MoveFocus
- ICoreWebView2Controller.NotifyParentWindowPositionChanged
- ICoreWebView2Controller.put_Bounds
- ICoreWebView2Controller.put_IsVisible
- ICoreWebView2Controller.put_ParentWindow
- ICoreWebView2Controller.put_ZoomFactor
- ICoreWebView2Controller.remove_AcceleratorKeyPressed
- ICoreWebView2Controller.remove_GotFocus
- ICoreWebView2Controller.remove_LostFocus
- ICoreWebView2Controller.remove_MoveFocusRequested
- ICoreWebView2Controller.remove_ZoomFactorChanged
- ICoreWebView2Controller.SetBoundsAndZoomFactor
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Controller

```
interface ICoreWebView2Controller
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_AcceleratorKeyPressed](#add_acceleratorkeypressed) | Adds an event handler for the `AcceleratorKeyPressed` event.
[add_GotFocus](#add_gotfocus) | Adds an event handler for the `GotFocus` event.
[add_LostFocus](#add_lostfocus) | Adds an event handler for the `LostFocus` event.
[add_MoveFocusRequested](#add_movefocusrequested) | Adds an event handler for the `MoveFocusRequested` event.
[add_ZoomFactorChanged](#add_zoomfactorchanged) | Adds an event handler for the `ZoomFactorChanged` event.
[Close](#close) | 
[get_Bounds](#get_bounds) | Gets the `Bounds` property.
[get_CoreWebView2](#get_corewebview2) | Gets the `CoreWebView2` property.
[get_IsVisible](#get_isvisible) | Gets the `IsVisible` property.
[get_ParentWindow](#get_parentwindow) | Gets the `ParentWindow` property.
[get_ZoomFactor](#get_zoomfactor) | Gets the `ZoomFactor` property.
[MoveFocus](#movefocus) | 
[NotifyParentWindowPositionChanged](#notifyparentwindowpositionchanged) | 
[put_Bounds](#put_bounds) | Sets the `Bounds` property.
[put_IsVisible](#put_isvisible) | Sets the `IsVisible` property.
[put_ParentWindow](#put_parentwindow) | Sets the `ParentWindow` property.
[put_ZoomFactor](#put_zoomfactor) | Sets the `ZoomFactor` property.
[remove_AcceleratorKeyPressed](#remove_acceleratorkeypressed) | Removes an event handler previously added with `add_AcceleratorKeyPressed`.
[remove_GotFocus](#remove_gotfocus) | Removes an event handler previously added with `add_GotFocus`.
[remove_LostFocus](#remove_lostfocus) | Removes an event handler previously added with `add_LostFocus`.
[remove_MoveFocusRequested](#remove_movefocusrequested) | Removes an event handler previously added with `add_MoveFocusRequested`.
[remove_ZoomFactorChanged](#remove_zoomfactorchanged) | Removes an event handler previously added with `add_ZoomFactorChanged`.
[SetBoundsAndZoomFactor](#setboundsandzoomfactor) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.488
WebView2 Win32 Prerelease |    0.9.488

## Members

#### add_AcceleratorKeyPressed

Adds an event handler for the `AcceleratorKeyPressed` event.

> public HRESULT [add_AcceleratorKeyPressed](#add_acceleratorkeypressed)([ICoreWebView2AcceleratorKeyPressedEventHandler](icorewebview2acceleratorkeypressedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_GotFocus

Adds an event handler for the `GotFocus` event.

> public HRESULT [add_GotFocus](#add_gotfocus)([ICoreWebView2FocusChangedEventHandler](icorewebview2focuschangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_LostFocus

Adds an event handler for the `LostFocus` event.

> public HRESULT [add_LostFocus](#add_lostfocus)([ICoreWebView2FocusChangedEventHandler](icorewebview2focuschangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_MoveFocusRequested

Adds an event handler for the `MoveFocusRequested` event.

> public HRESULT [add_MoveFocusRequested](#add_movefocusrequested)([ICoreWebView2MoveFocusRequestedEventHandler](icorewebview2movefocusrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_ZoomFactorChanged

Adds an event handler for the `ZoomFactorChanged` event.

> public HRESULT [add_ZoomFactorChanged](#add_zoomfactorchanged)([ICoreWebView2ZoomFactorChangedEventHandler](icorewebview2zoomfactorchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### Close

> public HRESULT [Close](#close)()

#### get_Bounds

Gets the `Bounds` property.

> public HRESULT [get_Bounds](#get_bounds)(RECT * value)

#### get_CoreWebView2

Gets the `CoreWebView2` property.

> public HRESULT [get_CoreWebView2](#get_corewebview2)([ICoreWebView2](icorewebview2.md) ** value)

#### get_IsVisible

Gets the `IsVisible` property.

> public HRESULT [get_IsVisible](#get_isvisible)(BOOL * value)

#### get_ParentWindow

Gets the `ParentWindow` property.

> public HRESULT [get_ParentWindow](#get_parentwindow)(HWND ** value)

#### get_ZoomFactor

Gets the `ZoomFactor` property.

> public HRESULT [get_ZoomFactor](#get_zoomfactor)(double * value)

#### MoveFocus

> public HRESULT [MoveFocus](#movefocus)(COREWEBVIEW2_MOVE_FOCUS_REASON reason)

#### NotifyParentWindowPositionChanged

> public HRESULT [NotifyParentWindowPositionChanged](#notifyparentwindowpositionchanged)()

#### put_Bounds

Sets the `Bounds` property.

> public HRESULT [put_Bounds](#put_bounds)(RECT value)

#### put_IsVisible

Sets the `IsVisible` property.

> public HRESULT [put_IsVisible](#put_isvisible)(BOOL value)

#### put_ParentWindow

Sets the `ParentWindow` property.

> public HRESULT [put_ParentWindow](#put_parentwindow)(HWND * value)

#### put_ZoomFactor

Sets the `ZoomFactor` property.

> public HRESULT [put_ZoomFactor](#put_zoomfactor)(double value)

#### remove_AcceleratorKeyPressed

Removes an event handler previously added with `add_AcceleratorKeyPressed`.

> public HRESULT [remove_AcceleratorKeyPressed](#remove_acceleratorkeypressed)(EventRegistrationToken token)

#### remove_GotFocus

Removes an event handler previously added with `add_GotFocus`.

> public HRESULT [remove_GotFocus](#remove_gotfocus)(EventRegistrationToken token)

#### remove_LostFocus

Removes an event handler previously added with `add_LostFocus`.

> public HRESULT [remove_LostFocus](#remove_lostfocus)(EventRegistrationToken token)

#### remove_MoveFocusRequested

Removes an event handler previously added with `add_MoveFocusRequested`.

> public HRESULT [remove_MoveFocusRequested](#remove_movefocusrequested)(EventRegistrationToken token)

#### remove_ZoomFactorChanged

Removes an event handler previously added with `add_ZoomFactorChanged`.

> public HRESULT [remove_ZoomFactorChanged](#remove_zoomfactorchanged)(EventRegistrationToken token)

#### SetBoundsAndZoomFactor

> public HRESULT [SetBoundsAndZoomFactor](#setboundsandzoomfactor)(RECT Bounds, double ZoomFactor)

