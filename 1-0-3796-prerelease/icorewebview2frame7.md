---
description: This is the ICoreWebView2Frame interface to support tracking of nested iframes.
title: WebView2 Win32 C++ ICoreWebView2Frame7
ms.date: 01/13/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Frame7
topic_type: 
- APIRef
api_name:
- ICoreWebView2Frame7
- ICoreWebView2Frame7.add_FrameCreated
- ICoreWebView2Frame7.remove_FrameCreated
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Frame7

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Frame7
  : public ICoreWebView2Frame6
```

This is the [ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) interface to support tracking of nested iframes.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_FrameCreated](#add_framecreated) | Adds an event handler for the `FrameCreated` event.
[remove_FrameCreated](#remove_framecreated) | Removes an event handler previously added with `add_FrameCreated`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.3240.44
WebView2 Win32 Prerelease |    1.0.3230

## Members

#### add_FrameCreated

Adds an event handler for the `FrameCreated` event.

> public HRESULT [add_FrameCreated](#add_framecreated)([ICoreWebView2FrameChildFrameCreatedEventHandler](icorewebview2framechildframecreatedeventhandler.md#icorewebview2framechildframecreatedeventhandler) * eventHandler, EventRegistrationToken * token)

Raised when a new direct descendant iframe is created. Handle this event to get access to [ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) objects. Use [ICoreWebView2Frame.add_Destroyed](icorewebview2frame.md#add_destroyed) to listen for when this iframe goes away.

```cpp
        frame7->add_FrameCreated(
            Callback<ICoreWebView2FrameChildFrameCreatedEventHandler>(
                [this, depth](
                    ICoreWebView2Frame* sender,
                    ICoreWebView2FrameCreatedEventArgs* args) noexcept -> HRESULT
                {
                    wil::com_ptr<ICoreWebView2Frame> webviewFrame;
                    CHECK_FAILURE(args->get_Frame(&webviewFrame));
                    wil::unique_cotaskmem_string name;
                    CHECK_FAILURE(webviewFrame->get_Name(&name));

                    InitializeFrameEventView(webviewFrame, depth + 1);

                    std::wstring message = L"{ \"kind\": \"event\", \"name\": "
                                           L"\"CoreWebView2Frame::FrameCreated\", \"args\": {";
                    message += L"\"frame name\": " + EncodeQuote(name.get());
                    message += L",\"depth\": " + std::to_wstring(depth);
                    auto frame5 = webviewFrame.try_query<ICoreWebView2Frame5>();
                    UINT32 frameId = 0;
                    if (frame5)
                    {
                        CHECK_FAILURE(frame5->get_FrameId(&frameId));
                        message += L",\"webview frame id\": " + std::to_wstring((int)frameId);
                    }
                    frame5 = wil::try_com_query<ICoreWebView2Frame5>(sender);
                    if (frame5)
                    {
                        CHECK_FAILURE(frame5->get_FrameId(&frameId));
                        message +=
                            L",\"sender webview frame id\": " + std::to_wstring((int)frameId);
                    }
                    message +=
                        L"}" + WebViewPropertiesToJsonString(m_webviewEventSource.get()) + L"}";
                    PostEventMessage(message);
                    return S_OK;
                })
                .Get(),
            &m_frameCreatedToken);
```

#### remove_FrameCreated

Removes an event handler previously added with `add_FrameCreated`.

> public HRESULT [remove_FrameCreated](#remove_framecreated)(EventRegistrationToken token)

