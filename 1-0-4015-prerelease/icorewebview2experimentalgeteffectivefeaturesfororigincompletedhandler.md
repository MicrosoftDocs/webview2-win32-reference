---
description: Receives the result of the `GetEffectiveFeaturesForOrigin` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalGetEffectiveFeaturesForOriginCompletedHandler
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalGetEffectiveFeaturesForOriginCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalGetEffectiveFeaturesForOriginCompletedHandler
- ICoreWebView2ExperimentalGetEffectiveFeaturesForOriginCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalGetEffectiveFeaturesForOriginCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalGetEffectiveFeaturesForOriginCompletedHandler
  : public IUnknown
```

Receives the result of the `GetEffectiveFeaturesForOrigin` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3965

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalOriginFeatureSettingCollectionView](icorewebview2experimentaloriginfeaturesettingcollectionview.md#icorewebview2experimentaloriginfeaturesettingcollectionview) * result)

