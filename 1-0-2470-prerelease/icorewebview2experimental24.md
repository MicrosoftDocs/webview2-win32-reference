---
description: This is the ICoreWebView_24 Experimental interface.
title: WebView2 Win32 C++ ICoreWebView2Experimental24
ms.date: 04/22/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental24
topic_type: 
- APIRef
api_name:
- ICoreWebView2Experimental24
- ICoreWebView2Experimental24.PostWebMessageAsJsonWithAdditionalObjects
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Experimental24

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental24
  : public IUnknown
```

This is the ICoreWebView_24 Experimental interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[PostWebMessageAsJsonWithAdditionalObjects](#postwebmessageasjsonwithadditionalobjects) | Same as `PostWebMessageAsJson`, but also has support for posting DOM objects to page content.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2470

## Members

#### PostWebMessageAsJsonWithAdditionalObjects

Same as `PostWebMessageAsJson`, but also has support for posting DOM objects to page content.

> public HRESULT [PostWebMessageAsJsonWithAdditionalObjects](#postwebmessageasjsonwithadditionalobjects)(LPCWSTR webMessageAsJson, [ICoreWebView2ObjectCollectionView](icorewebview2objectcollectionview.md#icorewebview2objectcollectionview) * additionalObjects)

The `additionalObjects` property in the DOM MessageEvent fired on the page content is a ArrayLike list of DOM objects that can be posted to the web content. Currently these can be the following types and `null`:

Win32   |DOM type
--------- | ---------
ICoreWebView2FileSystemHandle   |[FileSystemHandle](https://developer.mozilla.org/docs/Web/API/FileSystemHandle)
nullptr   |null

The objects are posted the to web content following the structured-clone semantics, meaning only objects that can be cloned can be posted. They will also behave as if they had been created by the web content they are posted to. For example, if a FileSystemFileHandle is posted to a web content it can only be re-transferred via postMessage to other web content [with the same origin](https://fs.spec.whatwg.org/#filesystemhandle). Warning: An app needs to be mindful when using this API to post DOM objects as this API provides the web content with unusual access to sensitive Web Platform features such as filesystem access! Similar to PostWebMessageAsJson the app should check the `Source` of WebView2 right before posting the message to ensure the message and objects will only be sent to the target web content that it expects to receive the DOM objects.

