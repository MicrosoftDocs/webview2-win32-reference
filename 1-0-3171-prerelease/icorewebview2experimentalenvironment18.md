---
description: Interface that provides methods related to the environment settings of CoreWebView2.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment18
ms.date: 03/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment18
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalEnvironment18
- ICoreWebView2ExperimentalEnvironment18.CreateFindOptions
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalEnvironment18

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment18
  : public IUnknown
```

Interface that provides methods related to the environment settings of CoreWebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateFindOptions](#createfindoptions) | Creates a new instance of a CoreWebView2FindOptions object.

This interface allows for the creation of new `FindOptions` objects.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3079

## Members

#### CreateFindOptions

Creates a new instance of a CoreWebView2FindOptions object.

> public HRESULT [CreateFindOptions](#createfindoptions)([ICoreWebView2ExperimentalFindOptions](icorewebview2experimentalfindoptions.md#icorewebview2experimentalfindoptions) ** value)

This find options object can be used to define parameters for a find session. Returns the newly created FindOptions object.

