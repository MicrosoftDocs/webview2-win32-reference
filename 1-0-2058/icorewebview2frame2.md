---
description: 
title: WebView2 Win32 C++ ICoreWebView2Frame2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Frame2
topic_type: 
- APIRef
api_name:
- ICoreWebView2Frame2
- ICoreWebView2Frame2.add_ContentLoading
- ICoreWebView2Frame2.add_DOMContentLoaded
- ICoreWebView2Frame2.add_NavigationCompleted
- ICoreWebView2Frame2.add_NavigationStarting
- ICoreWebView2Frame2.add_WebMessageReceived
- ICoreWebView2Frame2.ExecuteScript
- ICoreWebView2Frame2.PostWebMessageAsJson
- ICoreWebView2Frame2.PostWebMessageAsString
- ICoreWebView2Frame2.remove_ContentLoading
- ICoreWebView2Frame2.remove_DOMContentLoaded
- ICoreWebView2Frame2.remove_NavigationCompleted
- ICoreWebView2Frame2.remove_NavigationStarting
- ICoreWebView2Frame2.remove_WebMessageReceived
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Frame2

```
interface ICoreWebView2Frame2
  : public ICoreWebView2Frame
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ContentLoading](#add_contentloading) | Adds an event handler for the `ContentLoading` event.
[add_DOMContentLoaded](#add_domcontentloaded) | Adds an event handler for the `DOMContentLoaded` event.
[add_NavigationCompleted](#add_navigationcompleted) | Adds an event handler for the `NavigationCompleted` event.
[add_NavigationStarting](#add_navigationstarting) | Adds an event handler for the `NavigationStarting` event.
[add_WebMessageReceived](#add_webmessagereceived) | Adds an event handler for the `WebMessageReceived` event.
[ExecuteScript](#executescript) | 
[PostWebMessageAsJson](#postwebmessageasjson) | 
[PostWebMessageAsString](#postwebmessageasstring) | 
[remove_ContentLoading](#remove_contentloading) | Removes an event handler previously added with `add_ContentLoading`.
[remove_DOMContentLoaded](#remove_domcontentloaded) | Removes an event handler previously added with `add_DOMContentLoaded`.
[remove_NavigationCompleted](#remove_navigationcompleted) | Removes an event handler previously added with `add_NavigationCompleted`.
[remove_NavigationStarting](#remove_navigationstarting) | Removes an event handler previously added with `add_NavigationStarting`.
[remove_WebMessageReceived](#remove_webmessagereceived) | Removes an event handler previously added with `add_WebMessageReceived`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### add_ContentLoading

Adds an event handler for the `ContentLoading` event.

> public HRESULT [add_ContentLoading](#add_contentloading)([ICoreWebView2FrameContentLoadingEventHandler](icorewebview2framecontentloadingeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_DOMContentLoaded

Adds an event handler for the `DOMContentLoaded` event.

> public HRESULT [add_DOMContentLoaded](#add_domcontentloaded)([ICoreWebView2FrameDOMContentLoadedEventHandler](icorewebview2framedomcontentloadedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_NavigationCompleted

Adds an event handler for the `NavigationCompleted` event.

> public HRESULT [add_NavigationCompleted](#add_navigationcompleted)([ICoreWebView2FrameNavigationCompletedEventHandler](icorewebview2framenavigationcompletedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_NavigationStarting

Adds an event handler for the `NavigationStarting` event.

> public HRESULT [add_NavigationStarting](#add_navigationstarting)([ICoreWebView2FrameNavigationStartingEventHandler](icorewebview2framenavigationstartingeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_WebMessageReceived

Adds an event handler for the `WebMessageReceived` event.

> public HRESULT [add_WebMessageReceived](#add_webmessagereceived)([ICoreWebView2FrameWebMessageReceivedEventHandler](icorewebview2framewebmessagereceivedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### ExecuteScript

> public HRESULT [ExecuteScript](#executescript)(LPCWSTR javaScript, [ICoreWebView2ExecuteScriptCompletedHandler](icorewebview2executescriptcompletedhandler.md) * handler)

#### PostWebMessageAsJson

> public HRESULT [PostWebMessageAsJson](#postwebmessageasjson)(LPCWSTR webMessageAsJson)

#### PostWebMessageAsString

> public HRESULT [PostWebMessageAsString](#postwebmessageasstring)(LPCWSTR webMessageAsString)

#### remove_ContentLoading

Removes an event handler previously added with `add_ContentLoading`.

> public HRESULT [remove_ContentLoading](#remove_contentloading)(EventRegistrationToken token)

#### remove_DOMContentLoaded

Removes an event handler previously added with `add_DOMContentLoaded`.

> public HRESULT [remove_DOMContentLoaded](#remove_domcontentloaded)(EventRegistrationToken token)

#### remove_NavigationCompleted

Removes an event handler previously added with `add_NavigationCompleted`.

> public HRESULT [remove_NavigationCompleted](#remove_navigationcompleted)(EventRegistrationToken token)

#### remove_NavigationStarting

Removes an event handler previously added with `add_NavigationStarting`.

> public HRESULT [remove_NavigationStarting](#remove_navigationstarting)(EventRegistrationToken token)

#### remove_WebMessageReceived

Removes an event handler previously added with `add_WebMessageReceived`.

> public HRESULT [remove_WebMessageReceived](#remove_webmessagereceived)(EventRegistrationToken token)

