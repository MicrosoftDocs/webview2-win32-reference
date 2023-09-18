---
description: 
title: WebView2 Win32 C++ ICoreWebView2DownloadOperation
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DownloadOperation
topic_type: 
- APIRef
api_name:
- ICoreWebView2DownloadOperation
- ICoreWebView2DownloadOperation.add_BytesReceivedChanged
- ICoreWebView2DownloadOperation.add_EstimatedEndTimeChanged
- ICoreWebView2DownloadOperation.add_StateChanged
- ICoreWebView2DownloadOperation.Cancel
- ICoreWebView2DownloadOperation.get_BytesReceived
- ICoreWebView2DownloadOperation.get_CanResume
- ICoreWebView2DownloadOperation.get_ContentDisposition
- ICoreWebView2DownloadOperation.get_EstimatedEndTime
- ICoreWebView2DownloadOperation.get_InterruptReason
- ICoreWebView2DownloadOperation.get_MimeType
- ICoreWebView2DownloadOperation.get_ResultFilePath
- ICoreWebView2DownloadOperation.get_State
- ICoreWebView2DownloadOperation.get_TotalBytesToReceive
- ICoreWebView2DownloadOperation.get_Uri
- ICoreWebView2DownloadOperation.Pause
- ICoreWebView2DownloadOperation.remove_BytesReceivedChanged
- ICoreWebView2DownloadOperation.remove_EstimatedEndTimeChanged
- ICoreWebView2DownloadOperation.remove_StateChanged
- ICoreWebView2DownloadOperation.Resume
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DownloadOperation

```
interface ICoreWebView2DownloadOperation
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_BytesReceivedChanged](#add_bytesreceivedchanged) | Adds an event handler for the `BytesReceivedChanged` event.
[add_EstimatedEndTimeChanged](#add_estimatedendtimechanged) | Adds an event handler for the `EstimatedEndTimeChanged` event.
[add_StateChanged](#add_statechanged) | Adds an event handler for the `StateChanged` event.
[Cancel](#cancel) | 
[get_BytesReceived](#get_bytesreceived) | Gets the `BytesReceived` property.
[get_CanResume](#get_canresume) | Gets the `CanResume` property.
[get_ContentDisposition](#get_contentdisposition) | Gets the `ContentDisposition` property.
[get_EstimatedEndTime](#get_estimatedendtime) | Gets the `EstimatedEndTime` property.
[get_InterruptReason](#get_interruptreason) | Gets the `InterruptReason` property.
[get_MimeType](#get_mimetype) | Gets the `MimeType` property.
[get_ResultFilePath](#get_resultfilepath) | Gets the `ResultFilePath` property.
[get_State](#get_state) | Gets the `State` property.
[get_TotalBytesToReceive](#get_totalbytestoreceive) | Gets the `TotalBytesToReceive` property.
[get_Uri](#get_uri) | Gets the `Uri` property.
[Pause](#pause) | 
[remove_BytesReceivedChanged](#remove_bytesreceivedchanged) | Removes an event handler previously added with `add_BytesReceivedChanged`.
[remove_EstimatedEndTimeChanged](#remove_estimatedendtimechanged) | Removes an event handler previously added with `add_EstimatedEndTimeChanged`.
[remove_StateChanged](#remove_statechanged) | Removes an event handler previously added with `add_StateChanged`.
[Resume](#resume) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### add_BytesReceivedChanged

Adds an event handler for the `BytesReceivedChanged` event.

> public HRESULT [add_BytesReceivedChanged](#add_bytesreceivedchanged)([ICoreWebView2BytesReceivedChangedEventHandler](icorewebview2bytesreceivedchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_EstimatedEndTimeChanged

Adds an event handler for the `EstimatedEndTimeChanged` event.

> public HRESULT [add_EstimatedEndTimeChanged](#add_estimatedendtimechanged)([ICoreWebView2EstimatedEndTimeChangedEventHandler](icorewebview2estimatedendtimechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_StateChanged

Adds an event handler for the `StateChanged` event.

> public HRESULT [add_StateChanged](#add_statechanged)([ICoreWebView2StateChangedEventHandler](icorewebview2statechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### Cancel

> public HRESULT [Cancel](#cancel)()

#### get_BytesReceived

Gets the `BytesReceived` property.

> public HRESULT [get_BytesReceived](#get_bytesreceived)(INT64 * value)

#### get_CanResume

Gets the `CanResume` property.

> public HRESULT [get_CanResume](#get_canresume)(BOOL * value)

#### get_ContentDisposition

Gets the `ContentDisposition` property.

> public HRESULT [get_ContentDisposition](#get_contentdisposition)(LPWSTR * value)

#### get_EstimatedEndTime

Gets the `EstimatedEndTime` property.

> public HRESULT [get_EstimatedEndTime](#get_estimatedendtime)(LPWSTR * value)

#### get_InterruptReason

Gets the `InterruptReason` property.

> public HRESULT [get_InterruptReason](#get_interruptreason)(COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON * value)

#### get_MimeType

Gets the `MimeType` property.

> public HRESULT [get_MimeType](#get_mimetype)(LPWSTR * value)

#### get_ResultFilePath

Gets the `ResultFilePath` property.

> public HRESULT [get_ResultFilePath](#get_resultfilepath)(LPWSTR * value)

#### get_State

Gets the `State` property.

> public HRESULT [get_State](#get_state)(COREWEBVIEW2_DOWNLOAD_STATE * value)

#### get_TotalBytesToReceive

Gets the `TotalBytesToReceive` property.

> public HRESULT [get_TotalBytesToReceive](#get_totalbytestoreceive)(INT64 * value)

#### get_Uri

Gets the `Uri` property.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

#### Pause

> public HRESULT [Pause](#pause)()

#### remove_BytesReceivedChanged

Removes an event handler previously added with `add_BytesReceivedChanged`.

> public HRESULT [remove_BytesReceivedChanged](#remove_bytesreceivedchanged)(EventRegistrationToken token)

#### remove_EstimatedEndTimeChanged

Removes an event handler previously added with `add_EstimatedEndTimeChanged`.

> public HRESULT [remove_EstimatedEndTimeChanged](#remove_estimatedendtimechanged)(EventRegistrationToken token)

#### remove_StateChanged

Removes an event handler previously added with `add_StateChanged`.

> public HRESULT [remove_StateChanged](#remove_statechanged)(EventRegistrationToken token)

#### Resume

> public HRESULT [Resume](#resume)()

