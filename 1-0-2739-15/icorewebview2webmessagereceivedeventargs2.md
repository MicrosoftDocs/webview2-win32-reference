---
description: Extension of WebMessageReceivedEventArgs to provide access to additional WebMessage objects.
title: WebView2 Win32 C++ ICoreWebView2WebMessageReceivedEventArgs2
ms.date: 08/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebMessageReceivedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2WebMessageReceivedEventArgs2
- ICoreWebView2WebMessageReceivedEventArgs2.get_AdditionalObjects
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WebMessageReceivedEventArgs2

```
interface ICoreWebView2WebMessageReceivedEventArgs2
  : public ICoreWebView2WebMessageReceivedEventArgs
```

Extension of WebMessageReceivedEventArgs to provide access to additional WebMessage objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AdditionalObjects](#get_additionalobjects) | Additional received WebMessage objects.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1774.30
WebView2 Win32 Prerelease |    1.0.1777

## Members

#### get_AdditionalObjects

Additional received WebMessage objects.

> public HRESULT [get_AdditionalObjects](#get_additionalobjects)([ICoreWebView2ObjectCollectionView](icorewebview2objectcollectionview.md#icorewebview2objectcollectionview) ** value)

To pass `additionalObjects` via WebMessage to the app, use the `chrome.webview.postMessageWithAdditionalObjects` content API. Any DOM object type that can be natively representable that has been passed in to `additionalObjects` parameter will be accessible here. Currently a WebMessage object can be the [ICoreWebView2File](icorewebview2file.md#icorewebview2file) type. Entries in the collection can be `nullptr` if `null` or `undefined` was passed.

