---
description: Iterator for a collection of HTTP headers.
title: WebView2 Win32 C++ ICoreWebView2HttpHeadersCollectionIterator
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2HttpHeadersCollectionIterator
---

# interface ICoreWebView2HttpHeadersCollectionIterator

```
interface ICoreWebView2HttpHeadersCollectionIterator
  : public IUnknown
```

Iterator for a collection of HTTP headers.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HasCurrentHeader](#get_hascurrentheader) | `TRUE` when the iterator has not run out of headers.
[GetCurrentHeader](#getcurrentheader) | Get the name and value of the current HTTP header of the iterator.
[MoveNext](#movenext) | Move the iterator to the next HTTP header in the collection.

For more information, navigate to ICoreWebView2HttpRequestHeaders and ICoreWebView2HttpResponseHeaders.

```cpp
std::wstring RequestHeadersToJsonString(ICoreWebView2HttpRequestHeaders* requestHeaders)
{
    wil::com_ptr<ICoreWebView2HttpHeadersCollectionIterator> iterator;
    CHECK_FAILURE(requestHeaders->GetIterator(&iterator));
    BOOL hasCurrent = FALSE;
    std::wstring result = L"[";

    while (SUCCEEDED(iterator->get_HasCurrentHeader(&hasCurrent)) && hasCurrent)
    {
        wil::unique_cotaskmem_string name;
        wil::unique_cotaskmem_string value;

        CHECK_FAILURE(iterator->GetCurrentHeader(&name, &value));
        result += L"{\"name\": " + EncodeQuote(name.get())
            + L", \"value\": " + EncodeQuote(value.get()) + L"}";

        BOOL hasNext = FALSE;
        CHECK_FAILURE(iterator->MoveNext(&hasNext));
        if (hasNext)
        {
            result += L", ";
        }
    }

    return result + L"]";
}
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_HasCurrentHeader

`TRUE` when the iterator has not run out of headers.

> public HRESULT [get_HasCurrentHeader](#get_hascurrentheader)(BOOL * hasCurrent)

If the collection over which the iterator is iterating is empty or if the iterator has gone past the end of the collection then this is `FALSE`.

#### GetCurrentHeader

Get the name and value of the current HTTP header of the iterator.

> public HRESULT [GetCurrentHeader](#getcurrentheader)(LPWSTR * name, LPWSTR * value)

If the previous `MoveNext` operation set the `hasNext` parameter to `FALSE`, this method fails.

The caller must free the returned strings with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### MoveNext

Move the iterator to the next HTTP header in the collection.

> public HRESULT [MoveNext](#movenext)(BOOL * hasNext)

> [!NOTE]
 > If no more HTTP headers exist, the `hasNext` parameter is set to `FALSE`. After this occurs the `GetCurrentHeader` method fails.

