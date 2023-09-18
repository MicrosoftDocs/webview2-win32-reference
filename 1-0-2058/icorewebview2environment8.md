---
description: 
title: WebView2 Win32 C++ ICoreWebView2Environment8
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment8
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment8
- ICoreWebView2Environment8.add_ProcessInfosChanged
- ICoreWebView2Environment8.GetProcessInfos
- ICoreWebView2Environment8.remove_ProcessInfosChanged
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment8

```
interface ICoreWebView2Environment8
  : public ICoreWebView2Environment7
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ProcessInfosChanged](#add_processinfoschanged) | Adds an event handler for the `ProcessInfosChanged` event.
[GetProcessInfos](#getprocessinfos) | 
[remove_ProcessInfosChanged](#remove_processinfoschanged) | Removes an event handler previously added with `add_ProcessInfosChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### add_ProcessInfosChanged

Adds an event handler for the `ProcessInfosChanged` event.

> public HRESULT [add_ProcessInfosChanged](#add_processinfoschanged)([ICoreWebView2ProcessInfosChangedEventHandler](icorewebview2processinfoschangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### GetProcessInfos

> public HRESULT [GetProcessInfos](#getprocessinfos)(ICoreWebView2ProcessInfoCollection ** value)

#### remove_ProcessInfosChanged

Removes an event handler previously added with `add_ProcessInfosChanged`.

> public HRESULT [remove_ProcessInfosChanged](#remove_processinfoschanged)(EventRegistrationToken token)

