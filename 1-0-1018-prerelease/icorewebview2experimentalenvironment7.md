---
description: This interface is an extension of the ICoreWebView2Environment.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment7
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/28/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment7
---

# interface ICoreWebView2ExperimentalEnvironment7

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment7
  : public IUnknown
```

This interface is an extension of the [ICoreWebView2Environment](icorewebview2environment.md).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreatePrintSettings](#createprintsettings) | Creates the [ICoreWebView2ExperimentalPrintSettings](icorewebview2experimentalprintsettings.md) used by the `PrintToPdf` method.

An object implementing the ICoreWebView2ExperimentalEnvironment7 interface will also implement [ICoreWebView2Environment](icorewebview2environment.md).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### CreatePrintSettings

Creates the [ICoreWebView2ExperimentalPrintSettings](icorewebview2experimentalprintsettings.md) used by the `PrintToPdf` method.

> public HRESULT [CreatePrintSettings](#createprintsettings)([ICoreWebView2ExperimentalPrintSettings](icorewebview2experimentalprintsettings.md) ** printSettings)

