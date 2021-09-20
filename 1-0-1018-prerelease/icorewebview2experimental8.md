---
description: Used to get ICoreWebView2ExperimentalProfile object.
title: WebView2 Win32 C++ ICoreWebView2Experimental8
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/20/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental8
---

# interface ICoreWebView2Experimental8

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental8
  : public IUnknown
```

Used to get [ICoreWebView2ExperimentalProfile](icorewebview2experimentalprofile.md) object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Profile](#get_profile) | The associated [ICoreWebView2ExperimentalProfile](icorewebview2experimentalprofile.md) object.

```cpp
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1018

## Members

#### get_Profile

The associated [ICoreWebView2ExperimentalProfile](icorewebview2experimentalprofile.md) object.

> public HRESULT [get_Profile](#get_profile)([ICoreWebView2ExperimentalProfile](icorewebview2experimentalprofile.md) ** value)

