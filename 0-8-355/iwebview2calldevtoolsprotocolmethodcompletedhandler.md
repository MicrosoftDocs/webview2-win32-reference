---
description: The caller implements this interface to receive CallDevToolsProtocolMethod completion results.
title: WebView2 Win32 C++ IWebView2CallDevToolsProtocolMethodCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge
---

# interface IWebView2CallDevToolsProtocolMethodCompletedHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface IWebView2CallDevToolsProtocolMethodCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive CallDevToolsProtocolMethod completion results.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

## Members

#### Invoke 

Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode,LPCWSTR returnObjectAsJson)

