---
description: This is the ICoreWebView2Environment Experimental interface for detecting critical update.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment15
ms.date: 08/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment15
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalEnvironment15
- ICoreWebView2ExperimentalEnvironment15.add_RestartRequested
- ICoreWebView2ExperimentalEnvironment15.remove_RestartRequested
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalEnvironment15

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment15
  : public IUnknown
```

This is the [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) Experimental interface for detecting critical update.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_RestartRequested](#add_restartrequested) | Adds an event handler for the `RestartRequested` event.
[remove_RestartRequested](#remove_restartrequested) | Removes an event handler previously added with `add_RestartRequested`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2895

## Members

#### add_RestartRequested

Adds an event handler for the `RestartRequested` event.

> public HRESULT [add_RestartRequested](#add_restartrequested)([ICoreWebView2ExperimentalRestartRequestedEventHandler](icorewebview2experimentalrestartrequestedeventhandler.md#icorewebview2experimentalrestartrequestedeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `RestartRequested` event. `RestartRequested` event is raised when there is a need to restart WebView2 process in order to apply certain beneficial updates.

`RestartRequested` gives developers the awareness of these necessary WebView2 restarts, allowing developers to resolve issues faster than waiting for end users to restart the app. Developer might want to give end users the ability to save their state before restarting. For apps with multiple processes that host WebView2s that share the same user data folder you need to make sure all WebView2 instances are closed and the associated WebView2 Runtime browser process exits. See `BrowserProcessExited` for more details.

```cpp
    // After the environment is successfully created,
    // register a handler for
    auto exp_env15 = m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment15>();
    CHECK_FAILURE(exp_env15->add_RestartRequested(
        Callback<ICoreWebView2ExperimentalRestartRequestedEventHandler>(
            [this](
                ICoreWebView2Environment* sender,
                ICoreWebView2ExperimentalRestartRequestedEventArgs* args) -> HRESULT
            {
                COREWEBVIEW2_RESTART_REQUESTED_PRIORITY priority;
                args->get_Priority(&priority);
                if (priority == COREWEBVIEW2_RESTART_REQUESTED_PRIORITY_NORMAL)
                {
                    // Remaind user to restart the app when they get a chance.
                    // Don't force user to restart.
                    MessageBox(
                        m_mainWindow, L"Please restart your app when you get a chance",
                        L"WebView Restart Requested", MB_OK);
                }
                else if (priority == COREWEBVIEW2_RESTART_REQUESTED_PRIORITY_HIGH)
                {
                    // Don't block the event handler with a message box
                    RunAsync(
                        [this]()
                        {
                            std::wstring message = L"We detected there is a critical "
                                                   L"update for WebView2 runtime.";
                            if (m_webView)
                            {
                                message += L"Do you want to restart the app? \n\n";
                                message += L"Click No if you only want to re-create the "
                                           L"webviews. \n";
                                message += L"Click Cancel for no action. \n";
                            }
                            int response = MessageBox(
                                m_mainWindow, message.c_str(), L"Critical Update Avaliable",
                                m_webView ? MB_YESNOCANCEL : MB_OK);

                            if (response == IDYES)
                            {
                                RestartApp();
                            }
                            else if (response == IDNO)
                            {
                                ReinitializeWebViewWithNewBrowser();
                            }
                            else
                            {
                                // do nothing
                            }
                        });
                }

                return S_OK;
            })
            .Get(),
        nullptr));
```

#### remove_RestartRequested

Removes an event handler previously added with `add_RestartRequested`.

> public HRESULT [remove_RestartRequested](#remove_restartrequested)(EventRegistrationToken token)

