---
description: A continuation of the ICoreWebView2Environment7 interface that supports the `ProcessInfosChanged` event.
title: WebView2 Win32 C++ ICoreWebView2Environment8
ms.date: 02/09/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment8
---

# interface ICoreWebView2Environment8

```
interface ICoreWebView2Environment8
  : public ICoreWebView2Environment7
```

A continuation of the [ICoreWebView2Environment7](icorewebview2environment7.md) interface that supports the `ProcessInfosChanged` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ProcessInfosChanged](#add_processinfoschanged) | Adds an event handler for the `ProcessInfosChanged` event.
[GetProcessInfos](#getprocessinfos) | Returns the [ICoreWebView2ProcessInfoCollection](icorewebview2processinfocollection.md) Provide a list of all process using same user data folder except for crashpad process.
[remove_ProcessInfosChanged](#remove_processinfoschanged) | Remove an event handler previously added with `add_ProcessInfosChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### add_ProcessInfosChanged

Adds an event handler for the `ProcessInfosChanged` event.

> public HRESULT [add_ProcessInfosChanged](#add_processinfoschanged)([ICoreWebView2ProcessInfosChangedEventHandler](icorewebview2processinfoschangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

```cpp
        CHECK_FAILURE(environment8->add_ProcessInfosChanged(
            Callback<ICoreWebView2ProcessInfosChangedEventHandler>(
                [this](ICoreWebView2Environment* sender, IUnknown* args) -> HRESULT {
                    wil::com_ptr<ICoreWebView2Environment8> webviewEnvironment;
                    sender->QueryInterface(IID_PPV_ARGS(&webviewEnvironment));
                    CHECK_FAILURE(
                        webviewEnvironment->GetProcessInfos(&m_processCollection));
                    return S_OK;
                })
                .Get(),
            &m_processInfosChangedToken));
```

#### GetProcessInfos

Returns the [ICoreWebView2ProcessInfoCollection](icorewebview2processinfocollection.md) Provide a list of all process using same user data folder except for crashpad process.

> public HRESULT [GetProcessInfos](#getprocessinfos)([ICoreWebView2ProcessInfoCollection](icorewebview2processinfocollection.md) ** value)

#### remove_ProcessInfosChanged

Remove an event handler previously added with `add_ProcessInfosChanged`.

> public HRESULT [remove_ProcessInfosChanged](#remove_processinfoschanged)(EventRegistrationToken token)

