---
description: 
title: WebView2 Win32 C++ ICoreWebView2Frame3
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Frame3
topic_type: 
- APIRef
api_name:
- ICoreWebView2Frame3
- ICoreWebView2Frame3.add_PermissionRequested
- ICoreWebView2Frame3.remove_PermissionRequested
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Frame3

```
interface ICoreWebView2Frame3
  : public ICoreWebView2Frame2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_PermissionRequested](#add_permissionrequested) | Adds an event handler for the `PermissionRequested` event.
[remove_PermissionRequested](#remove_permissionrequested) | Removes an event handler previously added with `add_PermissionRequested`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### add_PermissionRequested

Adds an event handler for the `PermissionRequested` event.

> public HRESULT [add_PermissionRequested](#add_permissionrequested)([ICoreWebView2FramePermissionRequestedEventHandler](icorewebview2framepermissionrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### remove_PermissionRequested

Removes an event handler previously added with `add_PermissionRequested`.

> public HRESULT [remove_PermissionRequested](#remove_permissionrequested)(EventRegistrationToken token)

