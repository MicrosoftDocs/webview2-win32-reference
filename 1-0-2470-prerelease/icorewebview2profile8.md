---
description: This is the profile interface that manages profile deletion.
title: WebView2 Win32 C++ ICoreWebView2Profile8
ms.date: 03/18/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile8
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile8
- ICoreWebView2Profile8.add_Deleted
- ICoreWebView2Profile8.Delete
- ICoreWebView2Profile8.remove_Deleted
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile8

```
interface ICoreWebView2Profile8
  : public ICoreWebView2Profile7
```

This is the profile interface that manages profile deletion.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_Deleted](#add_deleted) | Add an event handler for the `Deleted` event.
[Delete](#delete) | After the API is called, the profile will be marked for deletion.
[remove_Deleted](#remove_deleted) | Removes an event handler previously added with `add_Deleted`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### add_Deleted

Add an event handler for the `Deleted` event.

> public HRESULT [add_Deleted](#add_deleted)([ICoreWebView2ProfileDeletedEventHandler](icorewebview2profiledeletedeventhandler.md#icorewebview2profiledeletedeventhandler) * eventHandler, EventRegistrationToken * token)

The `Deleted` event is raised when the profile is marked for deletion. When this event is raised, the CoreWebView2Profile and its corresponding CoreWebView2s have been closed, and cannot be used anymore.

```cpp
    auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
    CHECK_FEATURE_RETURN_EMPTY(webView2_13);
    wil::com_ptr<ICoreWebView2Profile> webView2Profile;
    CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
    CHECK_FEATURE_RETURN_EMPTY(webView2Profile);
    auto webView2Profile8 = webView2Profile.try_query<ICoreWebView2Profile8>();
    CHECK_FEATURE_RETURN_EMPTY(webView2Profile8);
    CHECK_FAILURE(webView2Profile8->add_Deleted(
        Microsoft::WRL::Callback<ICoreWebView2ProfileDeletedEventHandler>(
            [this](ICoreWebView2Profile* sender, IUnknown* args)
            {
                RunAsync(
                    [this]()
                    {
                        std::wstring message = L"The profile has been marked for deletion. Any "
                                               L"associated webview2 objects will be closed.";
                        MessageBox(m_mainWindow, message.c_str(), L"webview2 closed", MB_OK);
                        CloseAppWindow();
                    });
                return S_OK;
            })
            .Get(),
        nullptr));
```

#### Delete

After the API is called, the profile will be marked for deletion.

> public HRESULT [Delete](#delete)()

The local profile's directory will be deleted at browser process exit. If it fails to delete, because something else is holding the files open, WebView2 will try to delete the profile at all future browser process starts until successful. The corresponding CoreWebView2s will be closed and the CoreWebView2Profile.Deleted event will be raised. See `CoreWebView2Profile.Deleted` for more information. If you try to create a new profile with the same name as an existing profile that has been marked as deleted but hasn't yet been deleted, profile creation will fail with HRESULT_FROM_WIN32(ERROR_DELETE_PENDING).

```cpp
            CHECK_FEATURE_RETURN(m_webView2_13);
            wil::com_ptr<ICoreWebView2Profile> webView2ProfileBase;
            m_webView2_13->get_Profile(&webView2ProfileBase);
            CHECK_FEATURE_RETURN(webView2ProfileBase);
            auto webView2Profile = webView2ProfileBase.try_query<ICoreWebView2Profile8>();
            CHECK_FEATURE_RETURN(webView2Profile);
            webView2Profile->Delete();
```

#### remove_Deleted

Removes an event handler previously added with `add_Deleted`.

> public HRESULT [remove_Deleted](#remove_deleted)(EventRegistrationToken token)

