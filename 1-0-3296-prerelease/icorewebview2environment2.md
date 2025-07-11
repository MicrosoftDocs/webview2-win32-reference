---
description: A continuation of the ICoreWebView2Environment interface.
title: WebView2 Win32 C++ ICoreWebView2Environment2
ms.date: 05/06/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment2
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment2
- ICoreWebView2Environment2.CreateWebResourceRequest
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Environment2
  : public ICoreWebView2Environment
```

A continuation of the [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateWebResourceRequest](#createwebresourcerequest) | Create a new web resource request object.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### CreateWebResourceRequest

Create a new web resource request object.

> public HRESULT [CreateWebResourceRequest](#createwebresourcerequest)(LPCWSTR uri, LPCWSTR Method, IStream * postData, LPCWSTR Headers, [ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md#icorewebview2webresourcerequest) ** value)

URI parameter must be absolute URI. The headers string is the raw request header string delimited by CRLF (optional in last header). It's also possible to create this object with null headers string and then use the [ICoreWebView2HttpRequestHeaders](icorewebview2httprequestheaders.md#icorewebview2httprequestheaders) to construct the headers line by line. For information on other parameters see [ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md#icorewebview2webresourcerequest).

```cpp
        wil::com_ptr<ICoreWebView2Environment2> webviewEnvironment2;
        CHECK_FAILURE(appWindow->GetWebViewEnvironment()->QueryInterface(
            IID_PPV_ARGS(&webviewEnvironment2)));
        wil::com_ptr<ICoreWebView2WebResourceRequest> webResourceRequest;
        wil::com_ptr<IStream> postDataStream = SHCreateMemStream(
            reinterpret_cast<const BYTE*>(postDataBytes.get()), sizeNeededForMultiByte);

        // This is acts as a form submit to https://www.w3schools.com/action_page.php
        CHECK_FAILURE(webviewEnvironment2->CreateWebResourceRequest(
            L"https://www.w3schools.com/action_page.php", L"POST", postDataStream.get(),
            L"Content-Type: application/x-www-form-urlencoded", &webResourceRequest));
        wil::com_ptr<ICoreWebView2_2> webview2;
        CHECK_FAILURE(m_appWindow->GetWebView()->QueryInterface(IID_PPV_ARGS(&webview2)));
        CHECK_FAILURE(webview2->NavigateWithWebResourceRequest(webResourceRequest.get()));
```

