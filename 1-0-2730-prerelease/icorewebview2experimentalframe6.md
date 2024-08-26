---
description: This is an extension of the ICoreWebView2Frame interface that supports ScreenCaptureStarting.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrame6
ms.date: 08/26/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrame6
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFrame6
- ICoreWebView2ExperimentalFrame6.add_ScreenCaptureStarting
- ICoreWebView2ExperimentalFrame6.remove_ScreenCaptureStarting
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFrame6

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrame6
  : public IUnknown
```

This is an extension of the [ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) interface that supports ScreenCaptureStarting.

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

> public HRESULT [add_ScreenCaptureStarting](#add_screencapturestarting)([ICoreWebView2ExperimentalFrameScreenCaptureStartingEventHandler](icorewebview2experimentalframescreencapturestartingeventhandler.md#icorewebview2experimentalframescreencapturestartingeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `ScreenCaptureStarting` event. `ScreenCaptureStarting` is raised when content in an iframe or any of its descendant iframes requests permission to use the Screen Capture API from getDisplayMedia().

This relates to the `ScreenCaptureStarting` event on the `CoreWebView2`. Both these events will be raised in the case of an iframe requesting screen capture. The `CoreWebView2Frame`'s event handlers will be invoked before the event handlers on the `CoreWebView2`. If the `Handled` property of the `ScreenCaptureStartingEventArgs` is set to TRUE within the`CoreWebView2Frame` event handler, then the event will not be raised on the `CoreWebView2`, and its event handlers will not be invoked.

```cpp
    m_webView4 = m_webView.try_query<ICoreWebView2_4>();
    if (m_webView4)
    {
        CHECK_FAILURE(m_webView4->add_FrameCreated(
            Callback<ICoreWebView2FrameCreatedEventHandler>(
                [this](
                    ICoreWebView2* sender, ICoreWebView2FrameCreatedEventArgs* args) -> HRESULT
                {
                    wil::com_ptr<ICoreWebView2Frame> webviewFrame;
                    CHECK_FAILURE(args->get_Frame(&webviewFrame));

                    auto frame5 = webviewFrame.try_query<ICoreWebView2Frame5>();

                    UINT32 frameId;
                    frame5->get_FrameId(&frameId);

                    m_screenCaptureFrameIdPermission[frameId] = TRUE;

                    wil::com_ptr<ICoreWebView2Frame2> webviewFrame2 =
                        webviewFrame.try_query<ICoreWebView2Frame2>();
                    if (!webviewFrame2)
                    {
                        return S_OK;
                    }

                    bool cancel_on_frame = false;

                    CHECK_FAILURE(webviewFrame2->add_WebMessageReceived(
                        Microsoft::WRL::Callback<
                            ICoreWebView2FrameWebMessageReceivedEventHandler>(
                            [this, frameId](
                                ICoreWebView2Frame* sender,
                                ICoreWebView2WebMessageReceivedEventArgs* args) -> HRESULT
                            {
                                BOOL cancel = false;

                                wil::unique_cotaskmem_string messageRaw;
                                HRESULT hr = args->TryGetWebMessageAsString(&messageRaw);
                                if (hr == E_INVALIDARG)
                                {
                                    // Was not a string message. Ignore.
                                    return hr;
                                }
                                // Any other problems are fatal.
                                CHECK_FAILURE(hr);
                                std::wstring message = messageRaw.get();

                                if (message == L"EnableScreenCapture")
                                {
                                    cancel = false;
                                }
                                else if (message == L"DisableScreenCapture")
                                {
                                    cancel = true;
                                }
                                else
                                {
                                    // Ignore unrecognized messages, but log for further
                                    // investigation since it suggests a mismatch between the
                                    // web content and the host.
                                    OutputDebugString(
                                        std::wstring(
                                            L"Unexpected message from main page:" + message)
                                            .c_str());
                                }

                                m_screenCaptureFrameIdPermission[frameId] = (cancel == FALSE);

                                return S_OK;
                            })
                            .Get(),
                        nullptr));

                    m_experimentalFrame6 =
                        webviewFrame.try_query<ICoreWebView2ExperimentalFrame6>();

                    m_experimentalFrame6->add_ScreenCaptureStarting(
                        Callback<
                            ICoreWebView2ExperimentalFrameScreenCaptureStartingEventHandler>(
                            [this](
                                ICoreWebView2Frame* sender,
                                ICoreWebView2ExperimentalScreenCaptureStartingEventArgs* args)
                                -> HRESULT
                            {
                                args->put_Handled(TRUE);

                                bool cancel = FALSE;

                                // Get Frame Info
                                wil::com_ptr<ICoreWebView2FrameInfo> frameInfo;
                                CHECK_FAILURE(args->get_OriginalSourceFrameInfo(&frameInfo));

                                wil::com_ptr<ICoreWebView2FrameInfo2> frameInfo2;
                                CHECK_FAILURE(
                                    frameInfo->QueryInterface(IID_PPV_ARGS(&frameInfo2)));

                                // Frame Source
                                wil::unique_cotaskmem_string frameSource;
                                CHECK_FAILURE(frameInfo->get_Source(&frameSource));

                                UINT32 source_frameId;
                                CHECK_FAILURE(frameInfo2->get_FrameId(&source_frameId));

                                cancel =
                                    (m_screenCaptureFrameIdPermission[source_frameId] == FALSE);

                                CHECK_FAILURE(args->put_Cancel(cancel));
                                return S_OK;
                            })
                            .Get(),
                        &m_frameScreenCaptureStartingToken);

                    return S_OK;
                })
                .Get(),
            &m_frameCreatedToken));
    }
    else
    {
        FeatureNotAvailable();
    }
```

#### remove_ScreenCaptureStarting

Removes an event handler previously added with `add_ScreenCaptureStarting`.

> public HRESULT [remove_ScreenCaptureStarting](#remove_screencapturestarting)(EventRegistrationToken token)

