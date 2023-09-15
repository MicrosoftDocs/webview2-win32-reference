---
description: 
title: WebView2 Win32 C++ ICoreWebView2_3
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_3
topic_type: 
- APIRef
api_name:
- ICoreWebView2_3
- ICoreWebView2_3.ClearVirtualHostNameToFolderMapping
- ICoreWebView2_3.get_IsSuspended
- ICoreWebView2_3.Resume
- ICoreWebView2_3.SetVirtualHostNameToFolderMapping
- ICoreWebView2_3.TrySuspend
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_3

```
interface ICoreWebView2_3
  : public ICoreWebView2_2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[ClearVirtualHostNameToFolderMapping](#clearvirtualhostnametofoldermapping) | 
[get_IsSuspended](#get_issuspended) | Gets the `IsSuspended` property.
[Resume](#resume) | 
[SetVirtualHostNameToFolderMapping](#setvirtualhostnametofoldermapping) | 
[TrySuspend](#trysuspend) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### ClearVirtualHostNameToFolderMapping

> public HRESULT [ClearVirtualHostNameToFolderMapping](#clearvirtualhostnametofoldermapping)(LPCWSTR hostName)

#### get_IsSuspended

Gets the `IsSuspended` property.

> public HRESULT [get_IsSuspended](#get_issuspended)(BOOL * value)

#### Resume

> public HRESULT [Resume](#resume)()

#### SetVirtualHostNameToFolderMapping

> public HRESULT [SetVirtualHostNameToFolderMapping](#setvirtualhostnametofoldermapping)(LPCWSTR hostName, LPCWSTR folderPath, COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND accessKind)

#### TrySuspend

> public HRESULT [TrySuspend](#trysuspend)([ICoreWebView2TrySuspendCompletedHandler](icorewebview2trysuspendcompletedhandler.md) * handler)

