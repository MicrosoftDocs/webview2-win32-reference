---
description: Represents a download operation.
title: WebView2 Win32 C++ ICoreWebView2DownloadOperation
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DownloadOperation
---

# interface ICoreWebView2DownloadOperation

```
interface ICoreWebView2DownloadOperation
  : public IUnknown
```

Represents a download operation.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_BytesReceivedChanged](#add_bytesreceivedchanged) | Add an event handler for the `BytesReceivedChanged` event.
[add_EstimatedEndTimeChanged](#add_estimatedendtimechanged) | Add an event handler for the `EstimatedEndTimeChanged` event.
[add_StateChanged](#add_statechanged) | Add an event handler for the `StateChanged` event.
[Cancel](#cancel) | Cancels the download.
[get_BytesReceived](#get_bytesreceived) | The number of bytes that have been written to the download file.
[get_CanResume](#get_canresume) | Returns true if an interrupted download can be resumed.
[get_ContentDisposition](#get_contentdisposition) | The Content-Disposition header value from the download's HTTP response.
[get_EstimatedEndTime](#get_estimatedendtime) | The estimated end time in [ISO 8601 Date and Time Format](https://www.iso.org/iso-8601-date-and-time-format.html).
[get_InterruptReason](#get_interruptreason) | The reason why connection with file host was broken.
[get_MimeType](#get_mimetype) | MIME type of the downloaded content.
[get_ResultFilePath](#get_resultfilepath) | The absolute path to the download file, including file name.
[get_State](#get_state) | The state of the download.
[get_TotalBytesToReceive](#get_totalbytestoreceive) | The expected size of the download in total number of bytes based on the HTTP Content-Length header.
[get_Uri](#get_uri) | The URI of the download.
[Pause](#pause) | Pauses the download.
[remove_BytesReceivedChanged](#remove_bytesreceivedchanged) | Remove an event handler previously added with `add_BytesReceivedChanged`.
[remove_EstimatedEndTimeChanged](#remove_estimatedendtimechanged) | Remove an event handler previously added with `add_EstimatedEndTimeChanged`.
[remove_StateChanged](#remove_statechanged) | Remove an event handler previously added with `add_StateChanged`.
[Resume](#resume) | Resumes a paused download.

Gives access to the download's metadata and supports a user canceling, pausing, or resuming the download.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### add_BytesReceivedChanged

Add an event handler for the `BytesReceivedChanged` event.

> public HRESULT [add_BytesReceivedChanged](#add_bytesreceivedchanged)([ICoreWebView2BytesReceivedChangedEventHandler](icorewebview2bytesreceivedchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

```cpp
    CHECK_FAILURE(download->add_BytesReceivedChanged(
        Callback<ICoreWebView2BytesReceivedChangedEventHandler>(
            [this](ICoreWebView2DownloadOperation* download, IUnknown* args) -> HRESULT {
                // Here developer can update UI to show progress of a download using
                // `download->get_BytesReceived` and
                // `download->get_TotalBytesToReceive`.
                return S_OK;
            })
            .Get(),
        &m_bytesReceivedChangedToken));
```

#### add_EstimatedEndTimeChanged

Add an event handler for the `EstimatedEndTimeChanged` event.

> public HRESULT [add_EstimatedEndTimeChanged](#add_estimatedendtimechanged)([ICoreWebView2EstimatedEndTimeChangedEventHandler](icorewebview2estimatedendtimechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_StateChanged

Add an event handler for the `StateChanged` event.

> public HRESULT [add_StateChanged](#add_statechanged)([ICoreWebView2StateChangedEventHandler](icorewebview2statechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

```cpp
    CHECK_FAILURE(download->add_StateChanged(
        Callback<ICoreWebView2StateChangedEventHandler>(
          [this](ICoreWebView2DownloadOperation* download,
            IUnknown* args) -> HRESULT {
                COREWEBVIEW2_DOWNLOAD_STATE downloadState;
                CHECK_FAILURE(download->get_State(&downloadState));
                switch (downloadState)
                {
                case COREWEBVIEW2_DOWNLOAD_STATE_IN_PROGRESS:
                    break;
                case COREWEBVIEW2_DOWNLOAD_STATE_INTERRUPTED:
                    // Here developer can take different actions based on `download->InterruptReason`.
                    // For example, show an error message to the end user.
                    CompleteDownload(download);
                    break;
                case COREWEBVIEW2_DOWNLOAD_STATE_COMPLETED:
                    CompleteDownload(download);
                    break;
                }
                return S_OK;
          })
          .Get(),
        &m_stateChangedToken));
```

#### Cancel

Cancels the download.

> public HRESULT [Cancel](#cancel)()

If canceled, the default download dialog shows that the download was canceled. Host should set the `Cancel` property from `ICoreWebView2SDownloadStartingEventArgs` if the download should be canceled without displaying the default download dialog.

#### get_BytesReceived

The number of bytes that have been written to the download file.

> public HRESULT [get_BytesReceived](#get_bytesreceived)(INT64 * bytesReceived)

#### get_CanResume

Returns true if an interrupted download can be resumed.

> public HRESULT [get_CanResume](#get_canresume)(BOOL * canResume)

Downloads with the following interrupt reasons may automatically resume without you calling any methods: `COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_NO_RANGE`, `COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_HASH_MISMATCH`, `COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_TOO_SHORT`. In these cases download progress may be restarted with `BytesReceived` reset to 0.

#### get_ContentDisposition

The Content-Disposition header value from the download's HTTP response.

> public HRESULT [get_ContentDisposition](#get_contentdisposition)(LPWSTR * contentDisposition)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_EstimatedEndTime

The estimated end time in [ISO 8601 Date and Time Format](https://www.iso.org/iso-8601-date-and-time-format.html).

> public HRESULT [get_EstimatedEndTime](#get_estimatedendtime)(LPWSTR * estimatedEndTime)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_InterruptReason

The reason why connection with file host was broken.

> public HRESULT [get_InterruptReason](#get_interruptreason)(COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON * interruptReason)

#### get_MimeType

MIME type of the downloaded content.

> public HRESULT [get_MimeType](#get_mimetype)(LPWSTR * mimeType)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_ResultFilePath

The absolute path to the download file, including file name.

> public HRESULT [get_ResultFilePath](#get_resultfilepath)(LPWSTR * resultFilePath)

Host can change this from ICoreWebView2DownloadStartingEventArgs.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_State

The state of the download.

> public HRESULT [get_State](#get_state)(COREWEBVIEW2_DOWNLOAD_STATE * downloadState)

A download can be in progress, interrupted, or completed. See `COREWEBVIEW2_DOWNLOAD_STATE` for descriptions of states.

#### get_TotalBytesToReceive

The expected size of the download in total number of bytes based on the HTTP Content-Length header.

> public HRESULT [get_TotalBytesToReceive](#get_totalbytestoreceive)(INT64 * totalBytesToReceive)

Returns -1 if the size is unknown.

#### get_Uri

The URI of the download.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * uri)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### Pause

Pauses the download.

> public HRESULT [Pause](#pause)()

If paused, the default download dialog shows that the download is paused. No effect if download is already paused. Pausing a download changes the state to `COREWEBVIEW2_DOWNLOAD_STATE_INTERRUPTED` with `InterruptReason` set to `COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_USER_PAUSED`.

#### remove_BytesReceivedChanged

Remove an event handler previously added with `add_BytesReceivedChanged`.

> public HRESULT [remove_BytesReceivedChanged](#remove_bytesreceivedchanged)(EventRegistrationToken token)

#### remove_EstimatedEndTimeChanged

Remove an event handler previously added with `add_EstimatedEndTimeChanged`.

> public HRESULT [remove_EstimatedEndTimeChanged](#remove_estimatedendtimechanged)(EventRegistrationToken token)

#### remove_StateChanged

Remove an event handler previously added with `add_StateChanged`.

> public HRESULT [remove_StateChanged](#remove_statechanged)(EventRegistrationToken token)

#### Resume

Resumes a paused download.

> public HRESULT [Resume](#resume)()

May also resume a download that was interrupted for another reason, if `CanResume` returns true. Resuming a download changes the state from `COREWEBVIEW2_DOWNLOAD_STATE_INTERRUPTED` to `COREWEBVIEW2_DOWNLOAD_STATE_IN_PROGRESS`.

