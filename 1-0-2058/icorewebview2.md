---
description: 
title: WebView2 Win32 C++ ICoreWebView2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2
topic_type: 
- APIRef
api_name:
- ICoreWebView2
- ICoreWebView2.add_ContainsFullScreenElementChanged
- ICoreWebView2.add_ContentLoading
- ICoreWebView2.add_DocumentTitleChanged
- ICoreWebView2.add_FrameNavigationCompleted
- ICoreWebView2.add_FrameNavigationStarting
- ICoreWebView2.add_HistoryChanged
- ICoreWebView2.add_NavigationCompleted
- ICoreWebView2.add_NavigationStarting
- ICoreWebView2.add_NewWindowRequested
- ICoreWebView2.add_PermissionRequested
- ICoreWebView2.add_ProcessFailed
- ICoreWebView2.add_ScriptDialogOpening
- ICoreWebView2.add_SourceChanged
- ICoreWebView2.add_WebMessageReceived
- ICoreWebView2.add_WebResourceRequested
- ICoreWebView2.add_WindowCloseRequested
- ICoreWebView2.AddHostObjectToScript
- ICoreWebView2.AddScriptToExecuteOnDocumentCreated
- ICoreWebView2.AddWebResourceRequestedFilter
- ICoreWebView2.CallDevToolsProtocolMethod
- ICoreWebView2.CapturePreview
- ICoreWebView2.ExecuteScript
- ICoreWebView2.get_BrowserProcessId
- ICoreWebView2.get_CanGoBack
- ICoreWebView2.get_CanGoForward
- ICoreWebView2.get_ContainsFullScreenElement
- ICoreWebView2.get_DocumentTitle
- ICoreWebView2.get_Settings
- ICoreWebView2.get_Source
- ICoreWebView2.GetDevToolsProtocolEventReceiver
- ICoreWebView2.GoBack
- ICoreWebView2.GoForward
- ICoreWebView2.Navigate
- ICoreWebView2.NavigateToString
- ICoreWebView2.OpenDevToolsWindow
- ICoreWebView2.PostWebMessageAsJson
- ICoreWebView2.PostWebMessageAsString
- ICoreWebView2.Reload
- ICoreWebView2.remove_ContainsFullScreenElementChanged
- ICoreWebView2.remove_ContentLoading
- ICoreWebView2.remove_DocumentTitleChanged
- ICoreWebView2.remove_FrameNavigationCompleted
- ICoreWebView2.remove_FrameNavigationStarting
- ICoreWebView2.remove_HistoryChanged
- ICoreWebView2.remove_NavigationCompleted
- ICoreWebView2.remove_NavigationStarting
- ICoreWebView2.remove_NewWindowRequested
- ICoreWebView2.remove_PermissionRequested
- ICoreWebView2.remove_ProcessFailed
- ICoreWebView2.remove_ScriptDialogOpening
- ICoreWebView2.remove_SourceChanged
- ICoreWebView2.remove_WebMessageReceived
- ICoreWebView2.remove_WebResourceRequested
- ICoreWebView2.remove_WindowCloseRequested
- ICoreWebView2.RemoveHostObjectFromScript
- ICoreWebView2.RemoveScriptToExecuteOnDocumentCreated
- ICoreWebView2.RemoveWebResourceRequestedFilter
- ICoreWebView2.Stop
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2

```
interface ICoreWebView2
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ContainsFullScreenElementChanged](#add_containsfullscreenelementchanged) | Adds an event handler for the `ContainsFullScreenElementChanged` event.
[add_ContentLoading](#add_contentloading) | Adds an event handler for the `ContentLoading` event.
[add_DocumentTitleChanged](#add_documenttitlechanged) | Adds an event handler for the `DocumentTitleChanged` event.
[add_FrameNavigationCompleted](#add_framenavigationcompleted) | Adds an event handler for the `FrameNavigationCompleted` event.
[add_FrameNavigationStarting](#add_framenavigationstarting) | Adds an event handler for the `FrameNavigationStarting` event.
[add_HistoryChanged](#add_historychanged) | Adds an event handler for the `HistoryChanged` event.
[add_NavigationCompleted](#add_navigationcompleted) | Adds an event handler for the `NavigationCompleted` event.
[add_NavigationStarting](#add_navigationstarting) | Adds an event handler for the `NavigationStarting` event.
[add_NewWindowRequested](#add_newwindowrequested) | Adds an event handler for the `NewWindowRequested` event.
[add_PermissionRequested](#add_permissionrequested) | Adds an event handler for the `PermissionRequested` event.
[add_ProcessFailed](#add_processfailed) | Adds an event handler for the `ProcessFailed` event.
[add_ScriptDialogOpening](#add_scriptdialogopening) | Adds an event handler for the `ScriptDialogOpening` event.
[add_SourceChanged](#add_sourcechanged) | Adds an event handler for the `SourceChanged` event.
[add_WebMessageReceived](#add_webmessagereceived) | Adds an event handler for the `WebMessageReceived` event.
[add_WebResourceRequested](#add_webresourcerequested) | Adds an event handler for the `WebResourceRequested` event.
[add_WindowCloseRequested](#add_windowcloserequested) | Adds an event handler for the `WindowCloseRequested` event.
[AddHostObjectToScript](#addhostobjecttoscript) | 
[AddScriptToExecuteOnDocumentCreated](#addscripttoexecuteondocumentcreated) | 
[AddWebResourceRequestedFilter](#addwebresourcerequestedfilter) | 
[CallDevToolsProtocolMethod](#calldevtoolsprotocolmethod) | 
[CapturePreview](#capturepreview) | 
[ExecuteScript](#executescript) | 
[get_BrowserProcessId](#get_browserprocessid) | Gets the `BrowserProcessId` property.
[get_CanGoBack](#get_cangoback) | Gets the `CanGoBack` property.
[get_CanGoForward](#get_cangoforward) | Gets the `CanGoForward` property.
[get_ContainsFullScreenElement](#get_containsfullscreenelement) | Gets the `ContainsFullScreenElement` property.
[get_DocumentTitle](#get_documenttitle) | Gets the `DocumentTitle` property.
[get_Settings](#get_settings) | Gets the `Settings` property.
[get_Source](#get_source) | Gets the `Source` property.
[GetDevToolsProtocolEventReceiver](#getdevtoolsprotocoleventreceiver) | 
[GoBack](#goback) | 
[GoForward](#goforward) | 
[Navigate](#navigate) | 
[NavigateToString](#navigatetostring) | 
[OpenDevToolsWindow](#opendevtoolswindow) | 
[PostWebMessageAsJson](#postwebmessageasjson) | 
[PostWebMessageAsString](#postwebmessageasstring) | 
[Reload](#reload) | 
[remove_ContainsFullScreenElementChanged](#remove_containsfullscreenelementchanged) | Removes an event handler previously added with `add_ContainsFullScreenElementChanged`.
[remove_ContentLoading](#remove_contentloading) | Removes an event handler previously added with `add_ContentLoading`.
[remove_DocumentTitleChanged](#remove_documenttitlechanged) | Removes an event handler previously added with `add_DocumentTitleChanged`.
[remove_FrameNavigationCompleted](#remove_framenavigationcompleted) | Removes an event handler previously added with `add_FrameNavigationCompleted`.
[remove_FrameNavigationStarting](#remove_framenavigationstarting) | Removes an event handler previously added with `add_FrameNavigationStarting`.
[remove_HistoryChanged](#remove_historychanged) | Removes an event handler previously added with `add_HistoryChanged`.
[remove_NavigationCompleted](#remove_navigationcompleted) | Removes an event handler previously added with `add_NavigationCompleted`.
[remove_NavigationStarting](#remove_navigationstarting) | Removes an event handler previously added with `add_NavigationStarting`.
[remove_NewWindowRequested](#remove_newwindowrequested) | Removes an event handler previously added with `add_NewWindowRequested`.
[remove_PermissionRequested](#remove_permissionrequested) | Removes an event handler previously added with `add_PermissionRequested`.
[remove_ProcessFailed](#remove_processfailed) | Removes an event handler previously added with `add_ProcessFailed`.
[remove_ScriptDialogOpening](#remove_scriptdialogopening) | Removes an event handler previously added with `add_ScriptDialogOpening`.
[remove_SourceChanged](#remove_sourcechanged) | Removes an event handler previously added with `add_SourceChanged`.
[remove_WebMessageReceived](#remove_webmessagereceived) | Removes an event handler previously added with `add_WebMessageReceived`.
[remove_WebResourceRequested](#remove_webresourcerequested) | Removes an event handler previously added with `add_WebResourceRequested`.
[remove_WindowCloseRequested](#remove_windowcloserequested) | Removes an event handler previously added with `add_WindowCloseRequested`.
[RemoveHostObjectFromScript](#removehostobjectfromscript) | 
[RemoveScriptToExecuteOnDocumentCreated](#removescripttoexecuteondocumentcreated) | 
[RemoveWebResourceRequestedFilter](#removewebresourcerequestedfilter) | 
[Stop](#stop) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### add_ContainsFullScreenElementChanged

Adds an event handler for the `ContainsFullScreenElementChanged` event.

> public HRESULT [add_ContainsFullScreenElementChanged](#add_containsfullscreenelementchanged)([ICoreWebView2ContainsFullScreenElementChangedEventHandler](icorewebview2containsfullscreenelementchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_ContentLoading

Adds an event handler for the `ContentLoading` event.

> public HRESULT [add_ContentLoading](#add_contentloading)([ICoreWebView2ContentLoadingEventHandler](icorewebview2contentloadingeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_DocumentTitleChanged

Adds an event handler for the `DocumentTitleChanged` event.

> public HRESULT [add_DocumentTitleChanged](#add_documenttitlechanged)([ICoreWebView2DocumentTitleChangedEventHandler](icorewebview2documenttitlechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_FrameNavigationCompleted

Adds an event handler for the `FrameNavigationCompleted` event.

> public HRESULT [add_FrameNavigationCompleted](#add_framenavigationcompleted)([ICoreWebView2NavigationCompletedEventHandler](icorewebview2navigationcompletedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_FrameNavigationStarting

Adds an event handler for the `FrameNavigationStarting` event.

> public HRESULT [add_FrameNavigationStarting](#add_framenavigationstarting)([ICoreWebView2NavigationStartingEventHandler](icorewebview2navigationstartingeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_HistoryChanged

Adds an event handler for the `HistoryChanged` event.

> public HRESULT [add_HistoryChanged](#add_historychanged)([ICoreWebView2HistoryChangedEventHandler](icorewebview2historychangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_NavigationCompleted

Adds an event handler for the `NavigationCompleted` event.

> public HRESULT [add_NavigationCompleted](#add_navigationcompleted)([ICoreWebView2NavigationCompletedEventHandler](icorewebview2navigationcompletedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_NavigationStarting

Adds an event handler for the `NavigationStarting` event.

> public HRESULT [add_NavigationStarting](#add_navigationstarting)([ICoreWebView2NavigationStartingEventHandler](icorewebview2navigationstartingeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_NewWindowRequested

Adds an event handler for the `NewWindowRequested` event.

> public HRESULT [add_NewWindowRequested](#add_newwindowrequested)([ICoreWebView2NewWindowRequestedEventHandler](icorewebview2newwindowrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_PermissionRequested

Adds an event handler for the `PermissionRequested` event.

> public HRESULT [add_PermissionRequested](#add_permissionrequested)([ICoreWebView2PermissionRequestedEventHandler](icorewebview2permissionrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_ProcessFailed

Adds an event handler for the `ProcessFailed` event.

> public HRESULT [add_ProcessFailed](#add_processfailed)([ICoreWebView2ProcessFailedEventHandler](icorewebview2processfailedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_ScriptDialogOpening

Adds an event handler for the `ScriptDialogOpening` event.

> public HRESULT [add_ScriptDialogOpening](#add_scriptdialogopening)([ICoreWebView2ScriptDialogOpeningEventHandler](icorewebview2scriptdialogopeningeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_SourceChanged

Adds an event handler for the `SourceChanged` event.

> public HRESULT [add_SourceChanged](#add_sourcechanged)([ICoreWebView2SourceChangedEventHandler](icorewebview2sourcechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_WebMessageReceived

Adds an event handler for the `WebMessageReceived` event.

> public HRESULT [add_WebMessageReceived](#add_webmessagereceived)([ICoreWebView2WebMessageReceivedEventHandler](icorewebview2webmessagereceivedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_WebResourceRequested

Adds an event handler for the `WebResourceRequested` event.

> public HRESULT [add_WebResourceRequested](#add_webresourcerequested)([ICoreWebView2WebResourceRequestedEventHandler](icorewebview2webresourcerequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_WindowCloseRequested

Adds an event handler for the `WindowCloseRequested` event.

> public HRESULT [add_WindowCloseRequested](#add_windowcloserequested)([ICoreWebView2WindowCloseRequestedEventHandler](icorewebview2windowcloserequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### AddHostObjectToScript

> public HRESULT [AddHostObjectToScript](#addhostobjecttoscript)(LPCWSTR name, VARIANT rawObject)

#### AddScriptToExecuteOnDocumentCreated

> public HRESULT [AddScriptToExecuteOnDocumentCreated](#addscripttoexecuteondocumentcreated)(LPCWSTR javaScript, [ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler](icorewebview2addscripttoexecuteondocumentcreatedcompletedhandler.md) * handler)

#### AddWebResourceRequestedFilter

> public HRESULT [AddWebResourceRequestedFilter](#addwebresourcerequestedfilter)(LPCWSTR uri, COREWEBVIEW2_WEB_RESOURCE_CONTEXT ResourceContext)

#### CallDevToolsProtocolMethod

> public HRESULT [CallDevToolsProtocolMethod](#calldevtoolsprotocolmethod)(LPCWSTR methodName, LPCWSTR parametersAsJson, [ICoreWebView2CallDevToolsProtocolMethodCompletedHandler](icorewebview2calldevtoolsprotocolmethodcompletedhandler.md) * handler)

#### CapturePreview

> public HRESULT [CapturePreview](#capturepreview)(COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT imageFormat, IStream * imageStream, [ICoreWebView2CapturePreviewCompletedHandler](icorewebview2capturepreviewcompletedhandler.md) * handler)

#### ExecuteScript

> public HRESULT [ExecuteScript](#executescript)(LPCWSTR javaScript, [ICoreWebView2ExecuteScriptCompletedHandler](icorewebview2executescriptcompletedhandler.md) * handler)

#### get_BrowserProcessId

Gets the `BrowserProcessId` property.

> public HRESULT [get_BrowserProcessId](#get_browserprocessid)(UINT32 * value)

#### get_CanGoBack

Gets the `CanGoBack` property.

> public HRESULT [get_CanGoBack](#get_cangoback)(BOOL * value)

#### get_CanGoForward

Gets the `CanGoForward` property.

> public HRESULT [get_CanGoForward](#get_cangoforward)(BOOL * value)

#### get_ContainsFullScreenElement

Gets the `ContainsFullScreenElement` property.

> public HRESULT [get_ContainsFullScreenElement](#get_containsfullscreenelement)(BOOL * value)

#### get_DocumentTitle

Gets the `DocumentTitle` property.

> public HRESULT [get_DocumentTitle](#get_documenttitle)(LPWSTR * value)

#### get_Settings

Gets the `Settings` property.

> public HRESULT [get_Settings](#get_settings)([ICoreWebView2Settings](icorewebview2settings.md) ** value)

#### get_Source

Gets the `Source` property.

> public HRESULT [get_Source](#get_source)(LPWSTR * value)

#### GetDevToolsProtocolEventReceiver

> public HRESULT [GetDevToolsProtocolEventReceiver](#getdevtoolsprotocoleventreceiver)(LPCWSTR eventName, [ICoreWebView2DevToolsProtocolEventReceiver](icorewebview2devtoolsprotocoleventreceiver.md) ** value)

#### GoBack

> public HRESULT [GoBack](#goback)()

#### GoForward

> public HRESULT [GoForward](#goforward)()

#### Navigate

> public HRESULT [Navigate](#navigate)(LPCWSTR uri)

#### NavigateToString

> public HRESULT [NavigateToString](#navigatetostring)(LPCWSTR htmlContent)

#### OpenDevToolsWindow

> public HRESULT [OpenDevToolsWindow](#opendevtoolswindow)()

#### PostWebMessageAsJson

> public HRESULT [PostWebMessageAsJson](#postwebmessageasjson)(LPCWSTR webMessageAsJson)

#### PostWebMessageAsString

> public HRESULT [PostWebMessageAsString](#postwebmessageasstring)(LPCWSTR webMessageAsString)

#### Reload

> public HRESULT [Reload](#reload)()

#### remove_ContainsFullScreenElementChanged

Removes an event handler previously added with `add_ContainsFullScreenElementChanged`.

> public HRESULT [remove_ContainsFullScreenElementChanged](#remove_containsfullscreenelementchanged)(EventRegistrationToken token)

#### remove_ContentLoading

Removes an event handler previously added with `add_ContentLoading`.

> public HRESULT [remove_ContentLoading](#remove_contentloading)(EventRegistrationToken token)

#### remove_DocumentTitleChanged

Removes an event handler previously added with `add_DocumentTitleChanged`.

> public HRESULT [remove_DocumentTitleChanged](#remove_documenttitlechanged)(EventRegistrationToken token)

#### remove_FrameNavigationCompleted

Removes an event handler previously added with `add_FrameNavigationCompleted`.

> public HRESULT [remove_FrameNavigationCompleted](#remove_framenavigationcompleted)(EventRegistrationToken token)

#### remove_FrameNavigationStarting

Removes an event handler previously added with `add_FrameNavigationStarting`.

> public HRESULT [remove_FrameNavigationStarting](#remove_framenavigationstarting)(EventRegistrationToken token)

#### remove_HistoryChanged

Removes an event handler previously added with `add_HistoryChanged`.

> public HRESULT [remove_HistoryChanged](#remove_historychanged)(EventRegistrationToken token)

#### remove_NavigationCompleted

Removes an event handler previously added with `add_NavigationCompleted`.

> public HRESULT [remove_NavigationCompleted](#remove_navigationcompleted)(EventRegistrationToken token)

#### remove_NavigationStarting

Removes an event handler previously added with `add_NavigationStarting`.

> public HRESULT [remove_NavigationStarting](#remove_navigationstarting)(EventRegistrationToken token)

#### remove_NewWindowRequested

Removes an event handler previously added with `add_NewWindowRequested`.

> public HRESULT [remove_NewWindowRequested](#remove_newwindowrequested)(EventRegistrationToken token)

#### remove_PermissionRequested

Removes an event handler previously added with `add_PermissionRequested`.

> public HRESULT [remove_PermissionRequested](#remove_permissionrequested)(EventRegistrationToken token)

#### remove_ProcessFailed

Removes an event handler previously added with `add_ProcessFailed`.

> public HRESULT [remove_ProcessFailed](#remove_processfailed)(EventRegistrationToken token)

#### remove_ScriptDialogOpening

Removes an event handler previously added with `add_ScriptDialogOpening`.

> public HRESULT [remove_ScriptDialogOpening](#remove_scriptdialogopening)(EventRegistrationToken token)

#### remove_SourceChanged

Removes an event handler previously added with `add_SourceChanged`.

> public HRESULT [remove_SourceChanged](#remove_sourcechanged)(EventRegistrationToken token)

#### remove_WebMessageReceived

Removes an event handler previously added with `add_WebMessageReceived`.

> public HRESULT [remove_WebMessageReceived](#remove_webmessagereceived)(EventRegistrationToken token)

#### remove_WebResourceRequested

Removes an event handler previously added with `add_WebResourceRequested`.

> public HRESULT [remove_WebResourceRequested](#remove_webresourcerequested)(EventRegistrationToken token)

#### remove_WindowCloseRequested

Removes an event handler previously added with `add_WindowCloseRequested`.

> public HRESULT [remove_WindowCloseRequested](#remove_windowcloserequested)(EventRegistrationToken token)

#### RemoveHostObjectFromScript

> public HRESULT [RemoveHostObjectFromScript](#removehostobjectfromscript)(LPCWSTR name)

#### RemoveScriptToExecuteOnDocumentCreated

> public HRESULT [RemoveScriptToExecuteOnDocumentCreated](#removescripttoexecuteondocumentcreated)(LPCWSTR id)

#### RemoveWebResourceRequestedFilter

> public HRESULT [RemoveWebResourceRequestedFilter](#removewebresourcerequestedfilter)(LPCWSTR uri, COREWEBVIEW2_WEB_RESOURCE_CONTEXT ResourceContext)

#### Stop

> public HRESULT [Stop](#stop)()

