---
description: WebView2 Win32 C++ Reference
title: WebView2 Win32 C++ Reference
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/08/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
---

# Reference (WebView2 Win32 C++)

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

The Microsoft Edge WebView2 control enables you to host web content in your application using [Microsoft Edge \(Chromium\)](https://www.microsoftedgeinsider.com) as the rendering engine.  For more information, see [Overview of Microsoft Edge WebView2](/microsoft-edge/webview2/index)) and [Getting Started with WebView2](/microsoft-edge/webview2/gettingstarted/win32).  [ICoreWebView2](icorewebview2.md) is a great place to start learning the details of the API.

## Globals

*   [Globals](webview2-idl.md)

## Interfaces

*   [ICoreWebView2](icorewebview2.md)
*   [ICoreWebView2_2](icorewebview2_2.md)
*   [ICoreWebView2_3](icorewebview2_3.md)
*   [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md)
*   [ICoreWebView2CompositionController2](icorewebview2compositioncontroller2.md)
*   [ICoreWebView2Controller](icorewebview2controller.md)
*   [ICoreWebView2Controller2](icorewebview2controller2.md)
*   [ICoreWebView2Controller3](icorewebview2controller3.md)
*   [ICoreWebView2Cookie](icorewebview2cookie.md)
*   [ICoreWebView2CookieList](icorewebview2cookielist.md)
*   [ICoreWebView2CookieManager](icorewebview2cookiemanager.md)
*   [ICoreWebView2Deferral](icorewebview2deferral.md)
*   [ICoreWebView2DevToolsProtocolEventReceiver](icorewebview2devtoolsprotocoleventreceiver.md)
*   [ICoreWebView2Environment](icorewebview2environment.md)
*   [ICoreWebView2Environment2](icorewebview2environment2.md)
*   [ICoreWebView2Environment3](icorewebview2environment3.md)
*   [ICoreWebView2Environment4](icorewebview2environment4.md)
*   [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md)
*   [ICoreWebView2HttpHeadersCollectionIterator](icorewebview2httpheaderscollectioniterator.md)
*   [ICoreWebView2HttpRequestHeaders](icorewebview2httprequestheaders.md)
*   [ICoreWebView2HttpResponseHeaders](icorewebview2httpresponseheaders.md)
*   [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md)
*   [ICoreWebView2Settings](icorewebview2settings.md)
*   [ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md)
*   [ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md)
*   [ICoreWebView2WebResourceResponseView](icorewebview2webresourceresponseview.md)
*   [ICoreWebView2WindowFeatures](icorewebview2windowfeatures.md)

### Event arguments

*   [ICoreWebView2AcceleratorKeyPressedEventArgs](icorewebview2acceleratorkeypressedeventargs.md)
*   [ICoreWebView2ContentLoadingEventArgs](icorewebview2contentloadingeventargs.md)
*   [ICoreWebView2DevToolsProtocolEventReceivedEventArgs](icorewebview2devtoolsprotocoleventreceivedeventargs.md)
*   [ICoreWebView2DOMContentLoadedEventArgs](icorewebview2domcontentloadedeventargs.md)
*   [ICoreWebView2MoveFocusRequestedEventArgs](icorewebview2movefocusrequestedeventargs.md)
*   [ICoreWebView2NavigationCompletedEventArgs](icorewebview2navigationcompletedeventargs.md)
*   [ICoreWebView2NavigationStartingEventArgs](icorewebview2navigationstartingeventargs.md)
*   [ICoreWebView2NewWindowRequestedEventArgs](icorewebview2newwindowrequestedeventargs.md)
*   [ICoreWebView2PermissionRequestedEventArgs](icorewebview2permissionrequestedeventargs.md)
*   [ICoreWebView2ProcessFailedEventArgs](icorewebview2processfailedeventargs.md)
*   [ICoreWebView2ScriptDialogOpeningEventArgs](icorewebview2scriptdialogopeningeventargs.md)
*   [ICoreWebView2SourceChangedEventArgs](icorewebview2sourcechangedeventargs.md)
*   [ICoreWebView2WebMessageReceivedEventArgs](icorewebview2webmessagereceivedeventargs.md)
*   [ICoreWebView2WebResourceRequestedEventArgs](icorewebview2webresourcerequestedeventargs.md)
*   [ICoreWebView2WebResourceResponseReceivedEventArgs](icorewebview2webresourceresponsereceivedeventargs.md)

### Delegates

*   [ICoreWebView2AcceleratorKeyPressedEventHandler](icorewebview2acceleratorkeypressedeventhandler.md)
*   [ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler](icorewebview2addscripttoexecuteondocumentcreatedcompletedhandler.md)
*   [ICoreWebView2CallDevToolsProtocolMethodCompletedHandler](icorewebview2calldevtoolsprotocolmethodcompletedhandler.md)
*   [ICoreWebView2CapturePreviewCompletedHandler](icorewebview2capturepreviewcompletedhandler.md)
*   [ICoreWebView2ContainsFullScreenElementChangedEventHandler](icorewebview2containsfullscreenelementchangedeventhandler.md)
*   [ICoreWebView2ContentLoadingEventHandler](icorewebview2contentloadingeventhandler.md)
*   [ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler](icorewebview2createcorewebview2compositioncontrollercompletedhandler.md)
*   [ICoreWebView2CreateCoreWebView2ControllerCompletedHandler](icorewebview2createcorewebview2controllercompletedhandler.md)
*   [ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler](icorewebview2createcorewebview2environmentcompletedhandler.md)
*   [ICoreWebView2CursorChangedEventHandler](icorewebview2cursorchangedeventhandler.md)
*   [ICoreWebView2DevToolsProtocolEventReceivedEventHandler](icorewebview2devtoolsprotocoleventreceivedeventhandler.md)
*   [ICoreWebView2DocumentTitleChangedEventHandler](icorewebview2documenttitlechangedeventhandler.md)
*   [ICoreWebView2DOMContentLoadedEventHandler](icorewebview2domcontentloadedeventhandler.md)
*   [ICoreWebView2ExecuteScriptCompletedHandler](icorewebview2executescriptcompletedhandler.md)
*   [ICoreWebView2FocusChangedEventHandler](icorewebview2focuschangedeventhandler.md)
*   [ICoreWebView2GetCookiesCompletedHandler](icorewebview2getcookiescompletedhandler.md)
*   [ICoreWebView2HistoryChangedEventHandler](icorewebview2historychangedeventhandler.md)
*   [ICoreWebView2MoveFocusRequestedEventHandler](icorewebview2movefocusrequestedeventhandler.md)
*   [ICoreWebView2NavigationCompletedEventHandler](icorewebview2navigationcompletedeventhandler.md)
*   [ICoreWebView2NavigationStartingEventHandler](icorewebview2navigationstartingeventhandler.md)
*   [ICoreWebView2NewBrowserVersionAvailableEventHandler](icorewebview2newbrowserversionavailableeventhandler.md)
*   [ICoreWebView2NewWindowRequestedEventHandler](icorewebview2newwindowrequestedeventhandler.md)
*   [ICoreWebView2PermissionRequestedEventHandler](icorewebview2permissionrequestedeventhandler.md)
*   [ICoreWebView2ProcessFailedEventHandler](icorewebview2processfailedeventhandler.md)
*   [ICoreWebView2RasterizationScaleChangedEventHandler](icorewebview2rasterizationscalechangedeventhandler.md)
*   [ICoreWebView2ScriptDialogOpeningEventHandler](icorewebview2scriptdialogopeningeventhandler.md)
*   [ICoreWebView2SourceChangedEventHandler](icorewebview2sourcechangedeventhandler.md)
*   [ICoreWebView2TrySuspendCompletedHandler](icorewebview2trysuspendcompletedhandler.md)
*   [ICoreWebView2WebMessageReceivedEventHandler](icorewebview2webmessagereceivedeventhandler.md)
*   [ICoreWebView2WebResourceRequestedEventHandler](icorewebview2webresourcerequestedeventhandler.md)
*   [ICoreWebView2WebResourceResponseReceivedEventHandler](icorewebview2webresourceresponsereceivedeventhandler.md)
*   [ICoreWebView2WebResourceResponseViewGetContentCompletedHandler](icorewebview2webresourceresponseviewgetcontentcompletedhandler.md)
*   [ICoreWebView2WindowCloseRequestedEventHandler](icorewebview2windowcloserequestedeventhandler.md)
*   [ICoreWebView2ZoomFactorChangedEventHandler](icorewebview2zoomfactorchangedeventhandler.md)
