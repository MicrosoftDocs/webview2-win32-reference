---
description: A continuation of the ICoreWebView2_3 interface to support FrameCreated and DownloadStarting events.
title: WebView2 Win32 C++ ICoreWebView2_4
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_4
---

# interface ICoreWebView2_4

```
interface ICoreWebView2_4
  : public ICoreWebView2_3
```

A continuation of the [ICoreWebView2_3](icorewebview2_3.md) interface to support FrameCreated and DownloadStarting events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DownloadStarting](#add_downloadstarting) | Add an event handler for the `DownloadStarting` event.
[add_FrameCreated](#add_framecreated) | Raised when a new iframe is created.
[remove_DownloadStarting](#remove_downloadstarting) | Remove an event handler previously added with `add_DownloadStarting`.
[remove_FrameCreated](#remove_framecreated) | Remove an event handler previously added with add_FrameCreated.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### add_DownloadStarting

Add an event handler for the `DownloadStarting` event.

> public HRESULT [add_DownloadStarting](#add_downloadstarting)([ICoreWebView2DownloadStartingEventHandler](icorewebview2downloadstartingeventhandler.md) * eventHandler, EventRegistrationToken * token)

This event is raised when a download has begun, blocking the default download dialog, but not blocking the progress of the download.

The host can choose to cancel a download, change the result file path, and hide the default download dialog. If the host chooses to cancel the download, the download is not saved, no dialog is shown, and the state is changed to COREWEBVIEW2_DOWNLOAD_STATE_INTERRUPTED with interrupt reason COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_USER_CANCELED. Otherwise, the download is saved to the default path after the event completes, and default download dialog is shown if the host did not choose to hide it. The host can change the visibility of the download dialog using the `Handled` property. If the event is not handled, downloads complete normally with the default dialog shown.

```cpp
    // Register a handler for the `DownloadStarting` event.
    // This example hides the default download dialog and shows a dialog box instead.
    // The dialog box displays the default result file path and allows the user to specify a different path.
    // Selecting `OK` will save the download to the chosen path.
    // Selecting `CANCEL` will cancel the download.
    m_demoUri = L"https://demo.smartscreen.msft.net/";

    m_webView2_4 = m_webView.try_query<ICoreWebView2_4>();
    if (m_webView2_4) {
        CHECK_FAILURE(m_webView2_4->add_DownloadStarting(
            Callback<ICoreWebView2DownloadStartingEventHandler>(
                [this](
                    ICoreWebView2* sender,
                    ICoreWebView2DownloadStartingEventArgs* args) -> HRESULT
                {
                    // We avoid potential reentrancy from running a message loop in the download
                    // starting event handler by showing our download dialog via this lambda run
                    // asynchronously later outside of this event handler. Note that a long running
                    // synchronous UI prompt or other blocking item on the UI thread can potentially
                    // block the WebView2 from doing anything.
                    auto showDialog = [this, args]
                    {
                        // Hide the default download dialog.
                        CHECK_FAILURE(args->put_Handled(TRUE));

                        wil::com_ptr<ICoreWebView2DownloadOperation> download;
                        CHECK_FAILURE(args->get_DownloadOperation(&download));

                        INT64 totalBytesToReceive = 0;
                        CHECK_FAILURE(download->get_TotalBytesToReceive(&totalBytesToReceive));

                        wil::unique_cotaskmem_string uri;
                        CHECK_FAILURE(download->get_Uri(&uri));

                        wil::unique_cotaskmem_string mimeType;
                        CHECK_FAILURE(download->get_MimeType(&mimeType));

                        wil::unique_cotaskmem_string contentDisposition;
                        CHECK_FAILURE(download->get_ContentDisposition(&contentDisposition));

                        // Get the suggested path from the event args.
                        wil::unique_cotaskmem_string resultFilePath;
                        CHECK_FAILURE(args->get_ResultFilePath(&resultFilePath));

                        std::wstring prompt =
                            std::wstring(
                                L"Enter result file path or select `OK` to use default path. "
                                L"Select `Cancel` to cancel the download.");

                        std::wstring description = std::wstring(L"URI: ") + uri.get() + L"\r\n" +
                                                    L"Mime type: " + mimeType.get() + L"\r\n";
                        if (totalBytesToReceive >= 0)
                        {
                            description = description + L"Total bytes to receive: " +
                                          std::to_wstring(totalBytesToReceive) + L"\r\n";
                        }

                        TextInputDialog dialog(
                            m_appWindow->GetMainWindow(), L"Download Starting", prompt.c_str(),
                            description.c_str(), resultFilePath.get());
                        if (dialog.confirmed)
                        {
                            // If user selects `OK`, the download will complete normally.
                            // Result file path will be updated if a new one was provided.
                            CHECK_FAILURE(args->put_ResultFilePath(dialog.input.c_str()));
                            UpdateProgress(download.get());
                        }
                        else
                        {
                            // If user selects `Cancel`, the download will be canceled.
                            CHECK_FAILURE(args->put_Cancel(TRUE));
                        }
                    };

                    // Obtain a deferral for the event so that the CoreWebView2
                    // doesn't examine the properties we set on the event args until
                    // after we call the Complete method asynchronously later.
                    wil::com_ptr<ICoreWebView2Deferral> deferral;
                    CHECK_FAILURE(args->GetDeferral(&deferral));

                    // We avoid potential reentrancy from running a message loop in the download
                    // starting event handler by showing our download dialog later when we
                    // complete the deferral asynchronously.
                    m_appWindow->RunAsync([deferral, showDialog]() {
                        showDialog();
                        CHECK_FAILURE(deferral->Complete());
                    });

                    return S_OK;
                })
                .Get(),
            &m_downloadStartingToken));
    }
    else
    {
        // This scenario component is useless without this feature, but deleting an object in its own
        // constructor is...not advisable, so we'll just let this component do nothing until it goes away.
        FeatureNotAvailable();
    }
```

#### add_FrameCreated

Raised when a new iframe is created.

> public HRESULT [add_FrameCreated](#add_framecreated)([ICoreWebView2FrameCreatedEventHandler](icorewebview2framecreatedeventhandler.md) * eventHandler, EventRegistrationToken * token)

Use the CoreWebView2Frame.add_Destroyed to listen for when this iframe goes away.

#### remove_DownloadStarting

Remove an event handler previously added with `add_DownloadStarting`.

> public HRESULT [remove_DownloadStarting](#remove_downloadstarting)(EventRegistrationToken token)

#### remove_FrameCreated

Remove an event handler previously added with add_FrameCreated.

> public HRESULT [remove_FrameCreated](#remove_framecreated)(EventRegistrationToken token)

