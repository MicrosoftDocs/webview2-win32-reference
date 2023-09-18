---
description: 
title: WebView2 Win32 C++ ICoreWebView2Environment
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment
- ICoreWebView2Environment.add_NewBrowserVersionAvailable
- ICoreWebView2Environment.CreateCoreWebView2Controller
- ICoreWebView2Environment.CreateWebResourceResponse
- ICoreWebView2Environment.get_BrowserVersionString
- ICoreWebView2Environment.remove_NewBrowserVersionAvailable
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment

```
interface ICoreWebView2Environment
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_NewBrowserVersionAvailable](#add_newbrowserversionavailable) | Adds an event handler for the `NewBrowserVersionAvailable` event.
[CreateCoreWebView2Controller](#createcorewebview2controller) | 
[CreateWebResourceResponse](#createwebresourceresponse) | 
[get_BrowserVersionString](#get_browserversionstring) | Gets the `BrowserVersionString` property.
[remove_NewBrowserVersionAvailable](#remove_newbrowserversionavailable) | Removes an event handler previously added with `add_NewBrowserVersionAvailable`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### add_NewBrowserVersionAvailable

Adds an event handler for the `NewBrowserVersionAvailable` event.

> public HRESULT [add_NewBrowserVersionAvailable](#add_newbrowserversionavailable)([ICoreWebView2NewBrowserVersionAvailableEventHandler](icorewebview2newbrowserversionavailableeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### CreateCoreWebView2Controller

> public HRESULT [CreateCoreWebView2Controller](#createcorewebview2controller)(HWND * ParentWindow, [ICoreWebView2CreateCoreWebView2ControllerCompletedHandler](icorewebview2createcorewebview2controllercompletedhandler.md) * handler)

#### CreateWebResourceResponse

> public HRESULT [CreateWebResourceResponse](#createwebresourceresponse)(IStream * Content, INT32 StatusCode, LPCWSTR ReasonPhrase, LPCWSTR Headers, [ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md) ** value)

#### get_BrowserVersionString

Gets the `BrowserVersionString` property.

> public HRESULT [get_BrowserVersionString](#get_browserversionstring)(LPWSTR * value)

#### remove_NewBrowserVersionAvailable

Removes an event handler previously added with `add_NewBrowserVersionAvailable`.

> public HRESULT [remove_NewBrowserVersionAvailable](#remove_newbrowserversionavailable)(EventRegistrationToken token)

