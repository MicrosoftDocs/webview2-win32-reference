---
description: This interface is an extension of ICoreWebView2_14 that supports status Favicons.
title: WebView2 Win32 C++ ICoreWebView2_15
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_15
---

# interface ICoreWebView2_15

```
interface ICoreWebView2_15
  : public ICoreWebView2_14
```

This interface is an extension of [ICoreWebView2_14](icorewebview2_14.md) that supports status Favicons.

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
WebView2 Win32 Prerelease |    

## Members

#### add_FaviconChanged

Add an event handler for the `FaviconChanged` event.

> public HRESULT [add_FaviconChanged](#add_faviconchanged)(ICoreWebView2FaviconChangedEventHandler * eventHandler, EventRegistrationToken * token)

The `FaviconChanged` event is raised when the [favicon](https://developer.mozilla.org/docs/Glossary/Favicon) had a different URL then the previous URL. The FaviconChanged event will be raised for first navigating to a new document, whether or not a document declares a Favicon in HTML if the favicon is different from the previous fav icon. The event will be raised again if a favicon is declared in its HTML or has script to set its favicon. The favicon information can then be retrieved with `GetFavicon` and `FaviconUri`.

#### get_FaviconUri

Get the current Uri of the favicon as a string.

> public HRESULT [get_FaviconUri](#get_faviconuri)(LPWSTR * value)

If the value is null, then the return value is `E_POINTER`, otherwise it is `S_OK`. If a page has no favicon then the value is an empty string.

#### GetFavicon

Async function for getting the actual image data of the favicon.

> public HRESULT [GetFavicon](#getfavicon)([COREWEBVIEW2_FAVICON_IMAGE_FORMAT](icorewebview2.md) format, [ICoreWebView2GetFaviconCompletedHandler](icorewebview2getfaviconcompletedhandler.md) * completedHandler)

The image is copied to the `imageStream` object in ICoreWebView2GetFaviconCompletedHandler. If there is no image then no data would be copied into the imageStream. The `format` is the file format to return the image stream. `completedHandler` is executed at the end of the operation.

```cpp
    // Register a handler for the FaviconUriChanged event.
    // This will provided the current favicon of the page, as well
    // as any changes that occour during the page lifetime
    if (m_webView2_15)
    {
        Gdiplus::GdiplusStartupInput gdiplusStartupInput;

        // Initialize GDI+.
        Gdiplus::GdiplusStartup(&gdiplusToken_, &gdiplusStartupInput, NULL);
        CHECK_FAILURE(m_webView2_15->add_FaviconChanged(
            Callback<ICoreWebView2FaviconChangedEventHandler>(
                [this](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    if (m_faviconChanged)
                    {
                        wil::unique_cotaskmem_string url;
                        Microsoft::WRL::ComPtr<ICoreWebView2_15> webview2;
                        CHECK_FAILURE(sender->QueryInterface(IID_PPV_ARGS(&webview2)));

                        CHECK_FAILURE(webview2->get_FaviconUri(&url));
                        std::wstring strUrl(url.get());

                        webview2->GetFavicon(
                            COREWEBVIEW2_FAVICON_IMAGE_FORMAT_PNG,
                            Callback<ICoreWebView2GetFaviconCompletedHandler>(
                                [this,
                                 strUrl](HRESULT errorCode, IStream* iconStream) -> HRESULT
                                {
                                    CHECK_FAILURE(errorCode);
                                    Gdiplus::Bitmap iconBitmap(iconStream);
                                    wil::unique_hicon icon;
                                    if (iconBitmap.GetHICON(&icon) == Gdiplus::Status::Ok)
                                    {
                                        m_favicon = std::move(icon);
                                        SendMessage(
                                            m_appWindow->GetMainWindow(), WM_SETICON,
                                            ICON_SMALL, (LPARAM)m_favicon.get());
                                        m_statusBar.Show(strUrl);
                                    }
                                    else
                                    {
                                        SendMessage(
                                            m_appWindow->GetMainWindow(), WM_SETICON,
                                            ICON_SMALL, (LPARAM)IDC_NO);
                                        m_statusBar.Show(L"No Icon");
                                    }

                                    return S_OK;
                                })
                                .Get());
                    }
                    return S_OK;
                })
                .Get(),
            &m_faviconChangedToken));
    }
```

#### remove_FaviconChanged

Remove the event handler for `FaviconChanged` event.

> public HRESULT [remove_FaviconChanged](#remove_faviconchanged)(EventRegistrationToken token)

