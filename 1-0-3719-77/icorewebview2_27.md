---
description: This interface is an extension of ICoreWebView2 that supports the ScreenCaptureStarting event.
title: WebView2 Win32 C++ ICoreWebView2_27
ms.date: 01/14/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_27
topic_type: 
- APIRef
api_name:
- ICoreWebView2_27
- ICoreWebView2_27.add_ScreenCaptureStarting
- ICoreWebView2_27.remove_ScreenCaptureStarting
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_27

```
interface ICoreWebView2_27
  : public ICoreWebView2_26
```

This interface is an extension of [ICoreWebView2](icorewebview2.md#icorewebview2) that supports the ScreenCaptureStarting event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ScreenCaptureStarting](#add_screencapturestarting) | Adds an event handler for the `ScreenCaptureStarting` event.
[remove_ScreenCaptureStarting](#remove_screencapturestarting) | Removes an event handler previously added with `add_ScreenCaptureStarting`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2903.40
WebView2 Win32 Prerelease |    1.0.2895

## Members

#### add_ScreenCaptureStarting

Adds an event handler for the `ScreenCaptureStarting` event.

> public HRESULT [add_ScreenCaptureStarting](#add_screencapturestarting)([ICoreWebView2ScreenCaptureStartingEventHandler](icorewebview2screencapturestartingeventhandler.md#icorewebview2screencapturestartingeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `ScreenCaptureStarting` event. `ScreenCaptureStarting` event is raised when the [Screen Capture API](https://www.w3.org/TR/screen-capture/) is requested by the user using getDisplayMedia(). 
```cpp
    m_webView2_27 = m_webView.try_query<ICoreWebView2_27>();
    if (m_webView2_27)
    {
        m_webView2_27->add_ScreenCaptureStarting(
            Callback<ICoreWebView2ScreenCaptureStartingEventHandler>(
                [this](ICoreWebView2* sender, ICoreWebView2ScreenCaptureStartingEventArgs* args)
                    -> HRESULT
                {
                    // Get Frame Info
                    wil::com_ptr<ICoreWebView2FrameInfo> frameInfo;
                    CHECK_FAILURE(args->get_OriginalSourceFrameInfo(&frameInfo));

                    wil::com_ptr<ICoreWebView2FrameInfo2> frameInfo2;
                    CHECK_FAILURE(frameInfo->QueryInterface(IID_PPV_ARGS(&frameInfo2)));

                    UINT32 source_frameId;
                    CHECK_FAILURE(frameInfo2->get_FrameId(&source_frameId));

                    BOOL cancel = m_mainFramePermission == FALSE;
                    CHECK_FAILURE(args->put_Cancel(cancel));
                    return S_OK;
                })
                .Get(),
            &m_screenCaptureStartingToken);
    }
```

#### remove_ScreenCaptureStarting

Removes an event handler previously added with `add_ScreenCaptureStarting`.

> public HRESULT [remove_ScreenCaptureStarting](#remove_screencapturestarting)(EventRegistrationToken token)

