---
description: 
title: WebView2 Win32 C++ ICoreWebView2_4
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_4
topic_type: 
- APIRef
api_name:
- ICoreWebView2_4
- ICoreWebView2_4.add_DownloadStarting
- ICoreWebView2_4.add_FrameCreated
- ICoreWebView2_4.remove_DownloadStarting
- ICoreWebView2_4.remove_FrameCreated
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_4

```
interface ICoreWebView2_4
  : public ICoreWebView2_3
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DownloadStarting](#add_downloadstarting) | Adds an event handler for the `DownloadStarting` event.
[add_FrameCreated](#add_framecreated) | Adds an event handler for the `FrameCreated` event.
[remove_DownloadStarting](#remove_downloadstarting) | Removes an event handler previously added with `add_DownloadStarting`.
[remove_FrameCreated](#remove_framecreated) | Removes an event handler previously added with `add_FrameCreated`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### add_DownloadStarting

Adds an event handler for the `DownloadStarting` event.

> public HRESULT [add_DownloadStarting](#add_downloadstarting)([ICoreWebView2DownloadStartingEventHandler](icorewebview2downloadstartingeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_FrameCreated

Adds an event handler for the `FrameCreated` event.

> public HRESULT [add_FrameCreated](#add_framecreated)([ICoreWebView2FrameCreatedEventHandler](icorewebview2framecreatedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### remove_DownloadStarting

Removes an event handler previously added with `add_DownloadStarting`.

> public HRESULT [remove_DownloadStarting](#remove_downloadstarting)(EventRegistrationToken token)

#### remove_FrameCreated

Removes an event handler previously added with `add_FrameCreated`.

> public HRESULT [remove_FrameCreated](#remove_framecreated)(EventRegistrationToken token)

