---
description: 
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDevToolsProtocolEventReceivedEventArgs
ms.date: 02/08/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDevToolsProtocolEventReceivedEventArgs
---

# interface ICoreWebView2ExperimentalDevToolsProtocolEventReceivedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDevToolsProtocolEventReceivedEventArgs
  : public ICoreWebView2DevToolsProtocolEventReceivedEventArgs
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_SessionId](#get_sessionid) | The sessionId of the target where the event originates from.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### get_SessionId

The sessionId of the target where the event originates from.

> public HRESULT [get_SessionId](#get_sessionid)(LPWSTR * sessionId)

Empty string is returned as sessionId if the event comes from the default session for the top page. 
```cpp
                    wil::com_ptr<
                        ICoreWebView2ExperimentalDevToolsProtocolEventReceivedEventArgs>
                        args2;
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

