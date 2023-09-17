---
description: The caller implements this interface to receive the result of loading an browser Extension.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfileAddBrowserExtensionCompletedHandler
ms.date: 09/17/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfileAddBrowserExtensionCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfileAddBrowserExtensionCompletedHandler
- ICoreWebView2ExperimentalProfileAddBrowserExtensionCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfileAddBrowserExtensionCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfileAddBrowserExtensionCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the result of loading an browser Extension.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the `AddBrowserExtension` operation.g.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### Invoke

Provides the result of the `AddBrowserExtension` operation.g.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalBrowserExtension](icorewebview2experimentalbrowserextension.md) * extension)

