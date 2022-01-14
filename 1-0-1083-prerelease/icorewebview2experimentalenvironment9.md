---
description: This interface is an extension of the ICoreWebView2Environment that supports ProcessInfosChanged event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment9
ms.date: 01/14/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment9
---

# interface ICoreWebView2ExperimentalEnvironment9

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment9
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ProcessInfosChanged](#add_processinfoschanged) | Adds an event handler for the `ProcessInfosChanged` event.
[GetProcessInfos](#getprocessinfos) | Returns the [ICoreWebView2ExperimentalProcessInfoCollection](icorewebview2experimentalprocessinfocollection.md) Provide a list of all process using same user data folder except for crashpad process.
[remove_ProcessInfosChanged](#remove_processinfoschanged) | Remove an event handler previously added with `add_ProcessInfosChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### add_ProcessInfosChanged

Adds an event handler for the `ProcessInfosChanged` event.

> public HRESULT [add_ProcessInfosChanged](#add_processinfoschanged)([ICoreWebView2ExperimentalProcessInfosChangedEventHandler](icorewebview2experimentalprocessinfoschangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

```cpp
        CHECK_FAILURE(environment9->add_ProcessInfosChanged(
            Callback<ICoreWebView2ExperimentalProcessInfosChangedEventHandler>(
                [this](ICoreWebView2Environment* sender, IUnknown* args) -> HRESULT {
                    wil::com_ptr<ICoreWebView2ExperimentalEnvironment9> webviewEnvironment;
                    sender->QueryInterface(IID_PPV_ARGS(&webviewEnvironment));
                    CHECK_FAILURE(
                        webviewEnvironment->GetProcessInfos(&m_processCollection));
                    return S_OK;
                })
                .Get(),
            &m_processInfosChangedToken));
```

#### GetProcessInfos

Returns the [ICoreWebView2ExperimentalProcessInfoCollection](icorewebview2experimentalprocessinfocollection.md) Provide a list of all process using same user data folder except for crashpad process.

> public HRESULT [GetProcessInfos](#getprocessinfos)([ICoreWebView2ExperimentalProcessInfoCollection](icorewebview2experimentalprocessinfocollection.md) ** value)

#### remove_ProcessInfosChanged

Remove an event handler previously added with `add_ProcessInfosChanged`.

> public HRESULT [remove_ProcessInfosChanged](#remove_processinfoschanged)(EventRegistrationToken token)

