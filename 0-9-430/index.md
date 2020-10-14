---
description: WebView2 Win32 C++ Reference
title: WebView2 Win32 C++ Reference
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Host, browser control, edge html
---

# Reference (WebView2)  

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

The Microsoft Edge WebView2 control enables you to host web content in your application using [Microsoft Edge \(Chromium\)](https://www.microsoftedgeinsider.com) as the rendering engine.  For more information, see [Overview of Microsoft Edge WebView2](/microsoft-edge/webview2/index)) and [Getting Started with WebView2](/microsoft-edge/webview2/gettingstarted/win32).  [ICoreWebView2](icorewebview2.md) is a great place to start learning the details of the API.  

## Globals  

*   [Globals](webview2-idl.md)  

## Interfaces  
*   [ICoreWebView2](ICoreWebView2.md)
*   [ICoreWebView2Deferral](ICoreWebView2Deferral.md)
*   [ICoreWebView2DevToolsProtocolEventReceiver](ICoreWebView2DevToolsProtocolEventReceiver.md)
*   [ICoreWebView2Environment](ICoreWebView2Environment.md)
*   [ICoreWebView2Host](ICoreWebView2Host.md)
*   [ICoreWebView2HttpHeadersCollectionIterator](ICoreWebView2HttpHeadersCollectionIterator.md)
*   [ICoreWebView2HttpRequestHeaders](ICoreWebView2HttpRequestHeaders.md)
*   [ICoreWebView2HttpResponseHeaders](ICoreWebView2HttpResponseHeaders.md)
*   [ICoreWebView2Settings](ICoreWebView2Settings.md)
*   [ICoreWebView2WebResourceRequest](ICoreWebView2WebResourceRequest.md)
*   [ICoreWebView2WebResourceResponse](ICoreWebView2WebResourceResponse.md)

### Event argument interfaces

*   [ICoreWebView2AcceleratorKeyPressedEventArgs](ICoreWebView2AcceleratorKeyPressedEventArgs.md)
*   [ICoreWebView2ContentLoadingEventArgs](ICoreWebView2ContentLoadingEventArgs.md)
*   [ICoreWebView2DevToolsProtocolEventReceivedEventArgs](ICoreWebView2DevToolsProtocolEventReceivedEventArgs.md)
*   [ICoreWebView2MoveFocusRequestedEventArgs](ICoreWebView2MoveFocusRequestedEventArgs.md)
*   [ICoreWebView2NavigationCompletedEventArgs](ICoreWebView2NavigationCompletedEventArgs.md)
*   [ICoreWebView2NavigationStartingEventArgs](ICoreWebView2NavigationStartingEventArgs.md)
*   [ICoreWebView2NewBrowserVersionAvailableEventArgs](ICoreWebView2NewBrowserVersionAvailableEventArgs.md)
*   [ICoreWebView2NewWindowRequestedEventArgs](ICoreWebView2NewWindowRequestedEventArgs.md)
*   [ICoreWebView2PermissionRequestedEventArgs](ICoreWebView2PermissionRequestedEventArgs.md)
*   [ICoreWebView2ProcessFailedEventArgs](ICoreWebView2ProcessFailedEventArgs.md)
*   [ICoreWebView2ScriptDialogOpeningEventArgs](ICoreWebView2ScriptDialogOpeningEventArgs.md)
*   [ICoreWebView2SourceChangedEventArgs](ICoreWebView2SourceChangedEventArgs.md)
*   [ICoreWebView2WebMessageReceivedEventArgs](ICoreWebView2WebMessageReceivedEventArgs.md)
*   [ICoreWebView2WebResourceRequestedEventArgs](ICoreWebView2WebResourceRequestedEventArgs.md)

### Delegate interfaces

*   [ICoreWebView2AcceleratorKeyPressedEventHandler](ICoreWebView2AcceleratorKeyPressedEventHandler.md)
*   [ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler](ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler.md)
*   [ICoreWebView2CallDevToolsProtocolMethodCompletedHandler](ICoreWebView2CallDevToolsProtocolMethodCompletedHandler.md)
*   [ICoreWebView2CapturePreviewCompletedHandler](ICoreWebView2CapturePreviewCompletedHandler.md)
*   [ICoreWebView2ContainsFullScreenElementChangedEventHandler](ICoreWebView2ContainsFullScreenElementChangedEventHandler.md)
*   [ICoreWebView2ContentLoadingEventHandler](ICoreWebView2ContentLoadingEventHandler.md)
*   [ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler](ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler.md)
*   [ICoreWebView2CreateCoreWebView2HostCompletedHandler](ICoreWebView2CreateCoreWebView2HostCompletedHandler.md)
*   [ICoreWebView2DevToolsProtocolEventReceivedEventHandler](ICoreWebView2DevToolsProtocolEventReceivedEventHandler.md)
*   [ICoreWebView2DocumentTitleChangedEventHandler](ICoreWebView2DocumentTitleChangedEventHandler.md)
*   [ICoreWebView2ExecuteScriptCompletedHandler](ICoreWebView2ExecuteScriptCompletedHandler.md)
*   [ICoreWebView2FocusChangedEventHandler](ICoreWebView2FocusChangedEventHandler.md)
*   [ICoreWebView2HistoryChangedEventHandler](ICoreWebView2HistoryChangedEventHandler.md)
*   [ICoreWebView2MoveFocusRequestedEventHandler](ICoreWebView2MoveFocusRequestedEventHandler.md)
*   [ICoreWebView2NavigationCompletedEventHandler](ICoreWebView2NavigationCompletedEventHandler.md)
*   [ICoreWebView2NavigationStartingEventHandler](ICoreWebView2NavigationStartingEventHandler.md)
*   [ICoreWebView2NewBrowserVersionAvailableEventHandler](ICoreWebView2NewBrowserVersionAvailableEventHandler.md)
*   [ICoreWebView2NewWindowRequestedEventHandler](ICoreWebView2NewWindowRequestedEventHandler.md)
*   [ICoreWebView2PermissionRequestedEventHandler](ICoreWebView2PermissionRequestedEventHandler.md)
*   [ICoreWebView2ProcessFailedEventHandler](ICoreWebView2ProcessFailedEventHandler.md)
*   [ICoreWebView2ScriptDialogOpeningEventHandler](ICoreWebView2ScriptDialogOpeningEventHandler.md)
*   [ICoreWebView2SourceChangedEventHandler](ICoreWebView2SourceChangedEventHandler.md)
*   [ICoreWebView2WebMessageReceivedEventHandler](ICoreWebView2WebMessageReceivedEventHandler.md)
*   [ICoreWebView2WebResourceRequestedEventHandler](ICoreWebView2WebResourceRequestedEventHandler.md)
*   [ICoreWebView2WindowCloseRequestedEventHandler](ICoreWebView2WindowCloseRequestedEventHandler.md)
*   [ICoreWebView2ZoomFactorChangedEventHandler](ICoreWebView2ZoomFactorChangedEventHandler.md)
