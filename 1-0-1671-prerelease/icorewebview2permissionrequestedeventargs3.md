---
description: This is a continuation of the ICoreWebView2PermissionRequestedEventArgs2 interface.
title: WebView2 Win32 C++ ICoreWebView2PermissionRequestedEventArgs3
ms.date: 03/13/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionRequestedEventArgs3
---

# interface ICoreWebView2PermissionRequestedEventArgs3

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2PermissionRequestedEventArgs3
  : public ICoreWebView2PermissionRequestedEventArgs2
```

This is a continuation of the ICoreWebView2PermissionRequestedEventArgs2 interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_SavesInProfile](#get_savesinprofile) | The permission state set from the `PermissionRequested` event is saved in the profile by default; it persists across sessions and becomes the new default behavior for future `PermissionRequested` events.
[put_SavesInProfile](#put_savesinprofile) | Sets the `SavesInProfile` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### get_SavesInProfile

The permission state set from the `PermissionRequested` event is saved in the profile by default; it persists across sessions and becomes the new default behavior for future `PermissionRequested` events.

> public HRESULT [get_SavesInProfile](#get_savesinprofile)(BOOL * value)

Browser heuristics can affect whether the event continues to be raised when the state is saved in the profile. Set the `SavesInProfile` property to `FALSE` to not persist the state beyond the current request, and to continue to receive `PermissionRequested` events for this origin and permission kind.

#### put_SavesInProfile

Sets the `SavesInProfile` property.

> public HRESULT [put_SavesInProfile](#put_savesinprofile)(BOOL value)

