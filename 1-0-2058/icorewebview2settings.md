---
description: 
title: WebView2 Win32 C++ ICoreWebView2Settings
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings
- ICoreWebView2Settings.get_AreDefaultContextMenusEnabled
- ICoreWebView2Settings.get_AreDefaultScriptDialogsEnabled
- ICoreWebView2Settings.get_AreDevToolsEnabled
- ICoreWebView2Settings.get_AreHostObjectsAllowed
- ICoreWebView2Settings.get_IsBuiltInErrorPageEnabled
- ICoreWebView2Settings.get_IsScriptEnabled
- ICoreWebView2Settings.get_IsStatusBarEnabled
- ICoreWebView2Settings.get_IsWebMessageEnabled
- ICoreWebView2Settings.get_IsZoomControlEnabled
- ICoreWebView2Settings.put_AreDefaultContextMenusEnabled
- ICoreWebView2Settings.put_AreDefaultScriptDialogsEnabled
- ICoreWebView2Settings.put_AreDevToolsEnabled
- ICoreWebView2Settings.put_AreHostObjectsAllowed
- ICoreWebView2Settings.put_IsBuiltInErrorPageEnabled
- ICoreWebView2Settings.put_IsScriptEnabled
- ICoreWebView2Settings.put_IsStatusBarEnabled
- ICoreWebView2Settings.put_IsWebMessageEnabled
- ICoreWebView2Settings.put_IsZoomControlEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings

```
interface ICoreWebView2Settings
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AreDefaultContextMenusEnabled](#get_aredefaultcontextmenusenabled) | Gets the `AreDefaultContextMenusEnabled` property.
[get_AreDefaultScriptDialogsEnabled](#get_aredefaultscriptdialogsenabled) | Gets the `AreDefaultScriptDialogsEnabled` property.
[get_AreDevToolsEnabled](#get_aredevtoolsenabled) | Gets the `AreDevToolsEnabled` property.
[get_AreHostObjectsAllowed](#get_arehostobjectsallowed) | Gets the `AreHostObjectsAllowed` property.
[get_IsBuiltInErrorPageEnabled](#get_isbuiltinerrorpageenabled) | Gets the `IsBuiltInErrorPageEnabled` property.
[get_IsScriptEnabled](#get_isscriptenabled) | Gets the `IsScriptEnabled` property.
[get_IsStatusBarEnabled](#get_isstatusbarenabled) | Gets the `IsStatusBarEnabled` property.
[get_IsWebMessageEnabled](#get_iswebmessageenabled) | Gets the `IsWebMessageEnabled` property.
[get_IsZoomControlEnabled](#get_iszoomcontrolenabled) | Gets the `IsZoomControlEnabled` property.
[put_AreDefaultContextMenusEnabled](#put_aredefaultcontextmenusenabled) | Sets the `AreDefaultContextMenusEnabled` property.
[put_AreDefaultScriptDialogsEnabled](#put_aredefaultscriptdialogsenabled) | Sets the `AreDefaultScriptDialogsEnabled` property.
[put_AreDevToolsEnabled](#put_aredevtoolsenabled) | Sets the `AreDevToolsEnabled` property.
[put_AreHostObjectsAllowed](#put_arehostobjectsallowed) | Sets the `AreHostObjectsAllowed` property.
[put_IsBuiltInErrorPageEnabled](#put_isbuiltinerrorpageenabled) | Sets the `IsBuiltInErrorPageEnabled` property.
[put_IsScriptEnabled](#put_isscriptenabled) | Sets the `IsScriptEnabled` property.
[put_IsStatusBarEnabled](#put_isstatusbarenabled) | Sets the `IsStatusBarEnabled` property.
[put_IsWebMessageEnabled](#put_iswebmessageenabled) | Sets the `IsWebMessageEnabled` property.
[put_IsZoomControlEnabled](#put_iszoomcontrolenabled) | Sets the `IsZoomControlEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_AreDefaultContextMenusEnabled

Gets the `AreDefaultContextMenusEnabled` property.

> public HRESULT [get_AreDefaultContextMenusEnabled](#get_aredefaultcontextmenusenabled)(BOOL * value)

#### get_AreDefaultScriptDialogsEnabled

Gets the `AreDefaultScriptDialogsEnabled` property.

> public HRESULT [get_AreDefaultScriptDialogsEnabled](#get_aredefaultscriptdialogsenabled)(BOOL * value)

#### get_AreDevToolsEnabled

Gets the `AreDevToolsEnabled` property.

> public HRESULT [get_AreDevToolsEnabled](#get_aredevtoolsenabled)(BOOL * value)

#### get_AreHostObjectsAllowed

Gets the `AreHostObjectsAllowed` property.

> public HRESULT [get_AreHostObjectsAllowed](#get_arehostobjectsallowed)(BOOL * value)

#### get_IsBuiltInErrorPageEnabled

Gets the `IsBuiltInErrorPageEnabled` property.

> public HRESULT [get_IsBuiltInErrorPageEnabled](#get_isbuiltinerrorpageenabled)(BOOL * value)

#### get_IsScriptEnabled

Gets the `IsScriptEnabled` property.

> public HRESULT [get_IsScriptEnabled](#get_isscriptenabled)(BOOL * value)

#### get_IsStatusBarEnabled

Gets the `IsStatusBarEnabled` property.

> public HRESULT [get_IsStatusBarEnabled](#get_isstatusbarenabled)(BOOL * value)

#### get_IsWebMessageEnabled

Gets the `IsWebMessageEnabled` property.

> public HRESULT [get_IsWebMessageEnabled](#get_iswebmessageenabled)(BOOL * value)

#### get_IsZoomControlEnabled

Gets the `IsZoomControlEnabled` property.

> public HRESULT [get_IsZoomControlEnabled](#get_iszoomcontrolenabled)(BOOL * value)

#### put_AreDefaultContextMenusEnabled

Sets the `AreDefaultContextMenusEnabled` property.

> public HRESULT [put_AreDefaultContextMenusEnabled](#put_aredefaultcontextmenusenabled)(BOOL value)

#### put_AreDefaultScriptDialogsEnabled

Sets the `AreDefaultScriptDialogsEnabled` property.

> public HRESULT [put_AreDefaultScriptDialogsEnabled](#put_aredefaultscriptdialogsenabled)(BOOL value)

#### put_AreDevToolsEnabled

Sets the `AreDevToolsEnabled` property.

> public HRESULT [put_AreDevToolsEnabled](#put_aredevtoolsenabled)(BOOL value)

#### put_AreHostObjectsAllowed

Sets the `AreHostObjectsAllowed` property.

> public HRESULT [put_AreHostObjectsAllowed](#put_arehostobjectsallowed)(BOOL value)

#### put_IsBuiltInErrorPageEnabled

Sets the `IsBuiltInErrorPageEnabled` property.

> public HRESULT [put_IsBuiltInErrorPageEnabled](#put_isbuiltinerrorpageenabled)(BOOL value)

#### put_IsScriptEnabled

Sets the `IsScriptEnabled` property.

> public HRESULT [put_IsScriptEnabled](#put_isscriptenabled)(BOOL value)

#### put_IsStatusBarEnabled

Sets the `IsStatusBarEnabled` property.

> public HRESULT [put_IsStatusBarEnabled](#put_isstatusbarenabled)(BOOL value)

#### put_IsWebMessageEnabled

Sets the `IsWebMessageEnabled` property.

> public HRESULT [put_IsWebMessageEnabled](#put_iswebmessageenabled)(BOOL value)

#### put_IsZoomControlEnabled

Sets the `IsZoomControlEnabled` property.

> public HRESULT [put_IsZoomControlEnabled](#put_iszoomcontrolenabled)(BOOL value)

