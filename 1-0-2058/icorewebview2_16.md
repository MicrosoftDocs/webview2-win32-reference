---
description: 
title: WebView2 Win32 C++ ICoreWebView2_16
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_16
topic_type: 
- APIRef
api_name:
- ICoreWebView2_16
- ICoreWebView2_16.Print
- ICoreWebView2_16.PrintToPdfStream
- ICoreWebView2_16.ShowPrintUI
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_16

```
interface ICoreWebView2_16
  : public ICoreWebView2_15
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Print](#print) | 
[PrintToPdfStream](#printtopdfstream) | 
[ShowPrintUI](#showprintui) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1518.46
WebView2 Win32 Prerelease |    1.0.1549

## Members

#### Print

> public HRESULT [Print](#print)([ICoreWebView2PrintSettings](icorewebview2printsettings.md) * printSettings, [ICoreWebView2PrintCompletedHandler](icorewebview2printcompletedhandler.md) * handler)

#### PrintToPdfStream

> public HRESULT [PrintToPdfStream](#printtopdfstream)([ICoreWebView2PrintSettings](icorewebview2printsettings.md) * printSettings, [ICoreWebView2PrintToPdfStreamCompletedHandler](icorewebview2printtopdfstreamcompletedhandler.md) * handler)

#### ShowPrintUI

> public HRESULT [ShowPrintUI](#showprintui)(COREWEBVIEW2_PRINT_DIALOG_KIND printDialogKind)

