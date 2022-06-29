---
description: The caller implements this interface to receive the TrySuspend result.
title: WebView2 Win32 C++ ICoreWebView2TrySuspendCompletedHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2TrySuspendCompletedHandler
---

# interface ICoreWebView2TrySuspendCompletedHandler

```
interface ICoreWebView2TrySuspendCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the TrySuspend result.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the TrySuspend operation.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### Invoke

Provides the result of the TrySuspend operation.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, BOOL isSuccessful)

See [Sleeping Tabs FAQ](https://techcommunity.microsoft.com/t5/articles/sleeping-tabs-faq/m-p/1705434) for conditions that might prevent WebView from being suspended. In those situations, isSuccessful will be false and errorCode is S_OK.

