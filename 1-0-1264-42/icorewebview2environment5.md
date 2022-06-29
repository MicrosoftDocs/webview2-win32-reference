---
description: A continuation of the ICoreWebView2Environment4 interface that supports the `BrowserProcessExited` event.
title: WebView2 Win32 C++ ICoreWebView2Environment5
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment5
---

# interface ICoreWebView2Environment5

```
interface ICoreWebView2Environment5
  : public ICoreWebView2Environment4
```

A continuation of the [ICoreWebView2Environment4](icorewebview2environment4.md) interface that supports the `BrowserProcessExited` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_BrowserProcessExited](#add_browserprocessexited) | Add an event handler for the `BrowserProcessExited` event.
[remove_BrowserProcessExited](#remove_browserprocessexited) | Remove an event handler previously added with `add_BrowserProcessExited`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.992.28
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### add_BrowserProcessExited

Add an event handler for the `BrowserProcessExited` event.

> public HRESULT [add_BrowserProcessExited](#add_browserprocessexited)([ICoreWebView2BrowserProcessExitedEventHandler](icorewebview2browserprocessexitedeventhandler.md) * eventHandler, EventRegistrationToken * token)

The `BrowserProcessExited` event is raised when the collection of WebView2 Runtime processes for the browser process of this environment terminate due to browser process failure or normal shutdown (for example, when all associated WebViews are closed), after all resources have been released (including the user data folder). To learn about what these processes are, go to [Process model](/microsoft-edge/webview2/concepts/process-model).

A handler added with this method is called until removed with `remove_BrowserProcessExited`, even if a new browser process is bound to this environment after earlier `BrowserProcessExited` events are raised.

Multiple app processes can share a browser process by creating their webviews from a ICoreWebView2Environment with the same user data folder. When the entire collection of WebView2Runtime processes for the browser process exit, all associated ICoreWebView2Environment objects receive the `BrowserProcessExited` event. Multiple processes sharing the same browser process need to coordinate their use of the shared user data folder to avoid race conditions and unnecessary waits. For example, one process should not clear the user data folder at the same time that another process recovers from a crash by recreating its WebView controls; one process should not block waiting for the event if other app processes are using the same browser process (the browser process will not exit until those other processes have closed their webviews too).

Note this is an event from the ICoreWebView2Environment3 interface, not the ICoreWebView2 one. The difference between `BrowserProcessExited` and ICoreWebView2's `ProcessFailed` is that `BrowserProcessExited` is raised for any **browser process** exit (expected or unexpected, after all associated processes have exited too), while `ProcessFailed` is raised for **unexpected** process exits of any kind (browser, render, GPU, and all other types), or for main frame **render process** unresponsiveness. To learn more about the WebView2 Process Model, go to [Process model](/microsoft-edge/webview2/concepts/process-model).

In the case the browser process crashes, both `BrowserProcessExited` and `ProcessFailed` events are raised, but the order is not guaranteed. These events are intended for different scenarios. It is up to the app to coordinate the handlers so they do not try to perform reliability recovery while also trying to move to a new WebView2 Runtime version or remove the user data folder.

```cpp
// Close the WebView and deinitialize related state. This doesn't close the app window.
bool AppWindow::CloseWebView(bool cleanupUserDataFolder)
{
    if (auto file = GetComponent<FileComponent>())
    {
        if (file->IsPrintToPdfInProgress())
        {
            int selection = MessageBox(m_mainWindow,
                L"Print to PDF is in progress. Continue closing?",
                L"Print to PDF", MB_YESNO);
            if (selection == IDNO)
            {
                return false;
            }
        }
    }
    // 1. Delete components.
    DeleteAllComponents();

    // 2. If cleanup needed and BrowserProcessExited event interface available,
    // register to cleanup upon browser exit.
    wil::com_ptr<ICoreWebView2Environment5> environment5;
    if (m_webViewEnvironment)
    {
        environment5 =
            m_webViewEnvironment.try_query<ICoreWebView2Environment5>();
    }
    if (cleanupUserDataFolder && environment5)
    {
        // Before closing the WebView, register a handler with code to run once the
        // browser process and associated processes are terminated.
        CHECK_FAILURE(environment5->add_BrowserProcessExited(
            Callback<ICoreWebView2BrowserProcessExitedEventHandler>(
                [environment5, this](
                    ICoreWebView2Environment* sender,
                    ICoreWebView2BrowserProcessExitedEventArgs* args) {
                    COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND kind;
                    UINT32 pid;
                    CHECK_FAILURE(args->get_BrowserProcessExitKind(&kind));
                    CHECK_FAILURE(args->get_BrowserProcessId(&pid));

                    // If a new WebView is created from this CoreWebView2Environment after
                    // the browser has exited but before our handler gets to run, a new
                    // browser process will be created and lock the user data folder
                    // again. Do not attempt to cleanup the user data folder in these
                    // cases. We check the PID of the exited browser process against the
                    // PID of the browser process to which our last CoreWebView2 attached.
                    if (pid == m_newestBrowserPid)
                    {
                        // Watch for graceful browser process exit. Let ProcessFailed event
                        // handler take care of failed browser process termination.
                        if (kind == COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_NORMAL)
                        {
                            CHECK_FAILURE(environment5->remove_BrowserProcessExited(
                                m_browserExitedEventToken));
                            // Release the environment only after the handler is invoked.
                            // Otherwise, there will be no environment to raise the event when
                            // the collection of WebView2 Runtime processes exit.
                            m_webViewEnvironment = nullptr;
                            RunAsync([this]() { CleanupUserDataFolder(); });
                        }
                    }
                    else
                    {
                        // The exiting process is not the last in use. Do not attempt cleanup
                        // as we might still have a webview open over the user data folder.
                        // Do not block from event handler.
                        AsyncMessageBox(
                            L"A new browser process prevented cleanup of the user data folder.",
                            L"Cleanup User Data Folder");
                    }

                    return S_OK;
                })
                .Get(),
            &m_browserExitedEventToken));
    }

    // 3. Close the webview.
    if (m_controller)
    {
        m_controller->Close();
        m_controller = nullptr;
        m_webView = nullptr;
        m_webView3 = nullptr;
    }

    // 4. If BrowserProcessExited event interface is not available, release
    // environment and proceed to cleanup immediately. If the interface is
    // available, release environment only if not waiting for the event.
    if (!environment5)
    {
        m_webViewEnvironment = nullptr;
        if (cleanupUserDataFolder)
        {
            CleanupUserDataFolder();
        }
    }
    else if (!cleanupUserDataFolder)
    {
        // Release the environment object here only if no cleanup is needed.
        // If cleanup is needed, the environment object release is deferred
        // until the browser process exits, otherwise the handler for the
        // BrowserProcessExited event will not be called.
        m_webViewEnvironment = nullptr;
    }

    // reset profile name
    m_profileName = L"";
    m_documentTitle = L"";
    return true;
}
```

#### remove_BrowserProcessExited

Remove an event handler previously added with `add_BrowserProcessExited`.

> public HRESULT [remove_BrowserProcessExited](#remove_browserprocessexited)(EventRegistrationToken token)

