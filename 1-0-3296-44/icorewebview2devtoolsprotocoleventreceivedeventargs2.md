---
description: This is a continuation of the ICoreWebView2DevToolsProtocolEventReceivedEventArgs interface that provides the session ID of the target where the event originates from.
title: WebView2 Win32 C++ ICoreWebView2DevToolsProtocolEventReceivedEventArgs2
ms.date: 05/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DevToolsProtocolEventReceivedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2DevToolsProtocolEventReceivedEventArgs2
- ICoreWebView2DevToolsProtocolEventReceivedEventArgs2.get_SessionId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DevToolsProtocolEventReceivedEventArgs2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2DevToolsProtocolEventReceivedEventArgs2
  : public ICoreWebView2DevToolsProtocolEventReceivedEventArgs
```

This is a continuation of the [ICoreWebView2DevToolsProtocolEventReceivedEventArgs](icorewebview2devtoolsprotocoleventreceivedeventargs.md#icorewebview2devtoolsprotocoleventreceivedeventargs) interface that provides the session ID of the target where the event originates from.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_SessionId](#get_sessionid) | The sessionId of the target where the event originates from.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_SessionId

The sessionId of the target where the event originates from.

> public HRESULT [get_SessionId](#get_sessionid)(LPWSTR * value)

Empty string is returned as sessionId if the event comes from the default session for the top page.

```cpp
                    wil::com_ptr<ICoreWebView2DevToolsProtocolEventReceivedEventArgs2> args2;
                    if (SUCCEEDED(args->QueryInterface(IID_PPV_ARGS(&args2))))
                    {
                        wil::unique_cotaskmem_string sessionId;
                        CHECK_FAILURE(args2->get_SessionId(&sessionId));
                        if (sessionId.get() && *sessionId.get())
                        {
                            title = eventName + L" (session:" + sessionId.get() + L")";
                            std::wstring targetId = m_devToolsSessionMap[sessionId.get()];
                            std::wstring targetLabel = m_devToolsTargetLabelMap[targetId];
                            details = L"From " + targetLabel + L" (session:" + sessionId.get() +
                                      L")\r\n" + details;
                        }
                    }
```

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

