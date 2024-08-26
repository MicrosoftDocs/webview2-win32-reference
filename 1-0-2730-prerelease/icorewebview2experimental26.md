---
description: This interface is an extension of ICoreWebView2 that supports the ScreenCaptureStarting event.
title: WebView2 Win32 C++ ICoreWebView2Experimental26
ms.date: 08/26/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental26
topic_type: 
- APIRef
api_name:
- ICoreWebView2Experimental26
- ICoreWebView2Experimental26.add_ScreenCaptureStarting
- ICoreWebView2Experimental26.remove_ScreenCaptureStarting
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Experimental26

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental26
  : public IUnknown
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2646

## Members

#### add_ScreenCaptureStarting

Adds an event handler for the `ScreenCaptureStarting` event.

> public HRESULT [add_ScreenCaptureStarting](#add_screencapturestarting)([ICoreWebView2ExperimentalScreenCaptureStartingEventHandler](icorewebview2experimentalscreencapturestartingeventhandler.md#icorewebview2experimentalscreencapturestartingeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `ScreenCaptureStarting` event. `ScreenCaptureStarting` event is raised when the [Screen Capture API](https://www.w3.org/TR/screen-capture/) is requested by the user using getDisplayMedia(). 
```cpp
    m_webViewExperimental26 = m_webView.try_query<ICoreWebView2Experimental26>();
    if (m_webViewExperimental26)
    {
        m_webViewExperimental26->add_ScreenCaptureStarting(
            Callback<ICoreWebView2ExperimentalScreenCaptureStartingEventHandler>(
                [this](
                    ICoreWebView2* sender,
                    ICoreWebView2ExperimentalScreenCaptureStartingEventArgs* args) -> HRESULT
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

