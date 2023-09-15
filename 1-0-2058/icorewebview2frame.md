---
description: 
title: WebView2 Win32 C++ ICoreWebView2Frame
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Frame
topic_type: 
- APIRef
api_name:
- ICoreWebView2Frame
- ICoreWebView2Frame.add_Destroyed
- ICoreWebView2Frame.add_NameChanged
- ICoreWebView2Frame.get_Name
- ICoreWebView2Frame.IsDestroyed
- ICoreWebView2Frame.remove_Destroyed
- ICoreWebView2Frame.remove_NameChanged
- ICoreWebView2Frame.RemoveHostObjectFromScript
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Frame

```
interface ICoreWebView2Frame
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_Destroyed](#add_destroyed) | Adds an event handler for the `Destroyed` event.
[add_NameChanged](#add_namechanged) | Adds an event handler for the `NameChanged` event.
[get_Name](#get_name) | Gets the `Name` property.
[IsDestroyed](#isdestroyed) | 
[remove_Destroyed](#remove_destroyed) | Removes an event handler previously added with `add_Destroyed`.
[remove_NameChanged](#remove_namechanged) | Removes an event handler previously added with `add_NameChanged`.
[RemoveHostObjectFromScript](#removehostobjectfromscript) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### add_Destroyed

Adds an event handler for the `Destroyed` event.

> public HRESULT [add_Destroyed](#add_destroyed)([ICoreWebView2FrameDestroyedEventHandler](icorewebview2framedestroyedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_NameChanged

Adds an event handler for the `NameChanged` event.

> public HRESULT [add_NameChanged](#add_namechanged)([ICoreWebView2FrameNameChangedEventHandler](icorewebview2framenamechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### get_Name

Gets the `Name` property.

> public HRESULT [get_Name](#get_name)(LPWSTR * value)

#### IsDestroyed

> public HRESULT [IsDestroyed](#isdestroyed)(INT32 * value)

#### remove_Destroyed

Removes an event handler previously added with `add_Destroyed`.

> public HRESULT [remove_Destroyed](#remove_destroyed)(EventRegistrationToken token)

#### remove_NameChanged

Removes an event handler previously added with `add_NameChanged`.

> public HRESULT [remove_NameChanged](#remove_namechanged)(EventRegistrationToken token)

#### RemoveHostObjectFromScript

> public HRESULT [RemoveHostObjectFromScript](#removehostobjectfromscript)(LPCWSTR name)

