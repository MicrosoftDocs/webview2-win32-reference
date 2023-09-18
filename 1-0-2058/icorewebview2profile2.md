---
description: 
title: WebView2 Win32 C++ ICoreWebView2Profile2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile2
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile2
- ICoreWebView2Profile2.ClearBrowsingData
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile2

```
interface ICoreWebView2Profile2
  : public ICoreWebView2Profile
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[ClearBrowsingData](#clearbrowsingdata) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### ClearBrowsingData

> public HRESULT [ClearBrowsingData](#clearbrowsingdata)(COREWEBVIEW2_BROWSING_DATA_KINDS dataKinds, [ICoreWebView2ClearBrowsingDataCompletedHandler](icorewebview2clearbrowsingdatacompletedhandler.md) * handler)

