---
description: This interface is an extension of ICoreWebView2Experimental12 that support Favicons.
title: WebView2 Win32 C++ ICoreWebView2Experimental12
ms.date: 07/05/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental12
---

# interface ICoreWebView2Experimental12

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental12
  : public IUnknown
```

This interface is an extension of ICoreWebView2Experimental12 that support Favicons.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_FaviconChanged](#add_faviconchanged) | Add an event handler for the `FaviconChanged` event.
[get_FaviconUri](#get_faviconuri) | Get the current Uri of the favicon as a string.
[GetFavicon](#getfavicon) | Async function for getting the actual image data of the favicon.
[remove_FaviconChanged](#remove_faviconchanged) | Remove the event handler for `FaviconChanged` event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1222

## Members

#### add_FaviconChanged

Add an event handler for the `FaviconChanged` event.

> public HRESULT [add_FaviconChanged](#add_faviconchanged)(ICoreWebView2ExperimentalFaviconChangedEventHandler * eventHandler, EventRegistrationToken * token)

The `FaviconChanged` event is raised when the [favicon](https://developer.mozilla.org/en-US/docs/Glossary/Favicon) had a different URL then the previous URL. The FaviconChanged event will be raised for first navigating to a new document, whether or not a document declares a Favicon in HTML if the favicon is different from the previous fav icon. The event will be raised again if a favicon is declared in its HTML or has script to set its favicon. The favicon information can then be retrieved with `GetFavicon` and `FaviconUri`.

#### get_FaviconUri

Get the current Uri of the favicon as a string.

> public HRESULT [get_FaviconUri](#get_faviconuri)(LPWSTR * value)

If the value is null, then the return value is `E_POINTER`, otherwise it is `S_OK`. If a page has no favicon then the value is an empty string.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetFavicon

Async function for getting the actual image data of the favicon.

> public HRESULT [GetFavicon](#getfavicon)(COREWEBVIEW2_FAVICON_IMAGE_FORMAT format, ICoreWebView2ExperimentalGetFaviconCompletedHandler * completedHandler)

The image is copied to the `imageStream` object in `ICoreWebView2GetFaviconCompletedHandler`. If there is no image then no data would be copied into the imageStream. The `format` is the file format to return the image stream. `completedHandler` is executed at the end of the operation.

#### remove_FaviconChanged

Remove the event handler for `FaviconChanged` event.

> public HRESULT [remove_FaviconChanged](#remove_faviconchanged)(EventRegistrationToken token)

