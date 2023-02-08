---
description: Extension of WebMessageReceivedEventArgs to provide access to additional WebMessage objects.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalWebMessageReceivedEventArgs
ms.date: 02/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalWebMessageReceivedEventArgs
---

# interface ICoreWebView2ExperimentalWebMessageReceivedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalWebMessageReceivedEventArgs
  : public IUnknown
```

Extension of WebMessageReceivedEventArgs to provide access to additional WebMessage objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AdditionalObjects](#get_additionalobjects) | Additional received WebMessage objects.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_AdditionalObjects

Additional received WebMessage objects.

> public HRESULT [get_AdditionalObjects](#get_additionalobjects)([ICoreWebView2ExperimentalObjectCollectionView](icorewebview2experimentalobjectcollectionview.md) ** value)

To pass `additionalObjects` via WebMessage to the app, use the `chrome.webview.postMessageWithAdditionalObjects` content API. Any DOM object type that can be natively representable that has been passed in to `additionalObjects` parameter will be accessible here. Currently a WebMessage object can be the following type:

* `ICoreWebView2File`. Entries in the collection can be `nullptr` if `null` or `undefined` was passed.

