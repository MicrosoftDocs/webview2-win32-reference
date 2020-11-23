---
description: WebView2 enables you to host web content using the latest Microsoft Edge browser and web technology.
title: WebView2 Win32 C++ ICoreWebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2
---

# interface ICoreWebView2 

```
interface ICoreWebView2
  : public IUnknown
```

WebView2 enables you to host web content using the latest Microsoft Edge browser and web technology.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ContainsFullScreenElementChanged](#add_containsfullscreenelementchanged) | Add an event handler for the `ContainsFullScreenElementChanged` event.
[add_ContentLoading](#add_contentloading) | Add an event handler for the `ContentLoading` event.
[add_DocumentTitleChanged](#add_documenttitlechanged) | Add an event handler for the `DocumentTitleChanged` event.
[add_FrameNavigationCompleted](#add_framenavigationcompleted) | Add an event handler for the `FrameNavigationCompleted` event.
[add_FrameNavigationStarting](#add_framenavigationstarting) | Add an event handler for the `FrameNavigationStarting` event.
[add_HistoryChanged](#add_historychanged) | Add an event handler for the `HistoryChanged` event.
[add_NavigationCompleted](#add_navigationcompleted) | Add an event handler for the `NavigationCompleted` event.
[add_NavigationStarting](#add_navigationstarting) | Add an event handler for the `NavigationStarting` event.
[add_NewWindowRequested](#add_newwindowrequested) | Add an event handler for the `NewWindowRequested` event.
[add_PermissionRequested](#add_permissionrequested) | Add an event handler for the `PermissionRequested` event.
[add_ProcessFailed](#add_processfailed) | Add an event handler for the `ProcessFailed` event.
[add_ScriptDialogOpening](#add_scriptdialogopening) | Add an event handler for the `ScriptDialogOpening` event.
[add_SourceChanged](#add_sourcechanged) | Add an event handler for the `SourceChanged` event.
[add_WebMessageReceived](#add_webmessagereceived) | Add an event handler for the `WebMessageReceived` event.
[add_WebResourceRequested](#add_webresourcerequested) | Add an event handler for the `WebResourceRequested` event.
[add_WindowCloseRequested](#add_windowcloserequested) | Add an event handler for the `WindowCloseRequested` event.
[AddHostObjectToScript](#addhostobjecttoscript) | Add the provided host object to script running in the WebView with the specified name.
[AddScriptToExecuteOnDocumentCreated](#addscripttoexecuteondocumentcreated) | Add the provided JavaScript to a list of scripts that should be run after the global object has been created, but before the HTML document has been parsed and before any other script included by the HTML document is run.
[AddWebResourceRequestedFilter](#addwebresourcerequestedfilter) | Adds a URI and resource context filter to the `WebResourceRequested` event.
[CallDevToolsProtocolMethod](#calldevtoolsprotocolmethod) | Runs an asynchronous `DevToolsProtocol` method.
[CapturePreview](#capturepreview) | Capture an image of what WebView is displaying.
[ExecuteScript](#executescript) | Run JavaScript code from the javascript parameter in the current top-level document rendered in the WebView.
[get_BrowserProcessId](#get_browserprocessid) | The process ID of the browser process that hosts the WebView.
[get_CanGoBack](#get_cangoback) | `TRUE` if the WebView is able to navigate to a previous page in the navigation history.
[get_CanGoForward](#get_cangoforward) | `TRUE` if the WebView is able to navigate to a next page in the navigation history.
[get_ContainsFullScreenElement](#get_containsfullscreenelement) | Indicates if the WebView contains a fullscreen HTML element.
[get_DocumentTitle](#get_documenttitle) | The title for the current top-level document.
[get_Settings](#get_settings) | The `[ICoreWebView2Settings](icorewebview2settings.md)` object contains various modifiable settings for the running WebView.
[get_Source](#get_source) | The URI of the current top level document.
[GetDevToolsProtocolEventReceiver](#getdevtoolsprotocoleventreceiver) | Get a DevTools Protocol event receiver that allows you to subscribe to a DevTools Protocol event.
[GoBack](#goback) | Navigates the WebView to the previous page in the navigation history.
[GoForward](#goforward) | Navigates the WebView to the next page in the navigation history.
[Navigate](#navigate) | Cause a navigation of the top-level document to run to the specified URI.
[NavigateToString](#navigatetostring) | Initiates a navigation to htmlContent as source HTML of a new document.
[OpenDevToolsWindow](#opendevtoolswindow) | Opens the DevTools window for the current document in the WebView.
[PostWebMessageAsJson](#postwebmessageasjson) | Post the specified webMessage to the top level document in this WebView.
[PostWebMessageAsString](#postwebmessageasstring) | Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.
[Reload](#reload) | Reload the current page.
[remove_ContainsFullScreenElementChanged](#remove_containsfullscreenelementchanged) | Remove an event handler previously added with `add_ContainsFullScreenElementChanged`.
[remove_ContentLoading](#remove_contentloading) | Remove an event handler previously added with `add_ContentLoading`.
[remove_DocumentTitleChanged](#remove_documenttitlechanged) | Remove an event handler previously added with `add_DocumentTitleChanged`.
[remove_FrameNavigationCompleted](#remove_framenavigationcompleted) | Remove an event handler previously added with `add_FrameNavigationCompleted`.
[remove_FrameNavigationStarting](#remove_framenavigationstarting) | Remove an event handler previously added with `add_FrameNavigationStarting`.
[remove_HistoryChanged](#remove_historychanged) | Remove an event handler previously added with `add_HistoryChanged`.
[remove_NavigationCompleted](#remove_navigationcompleted) | Remove an event handler previously added with `add_NavigationCompleted`.
[remove_NavigationStarting](#remove_navigationstarting) | Remove an event handler previously added with `add_NavigationStarting`.
[remove_NewWindowRequested](#remove_newwindowrequested) | Remove an event handler previously added with `add_NewWindowRequested`.
[remove_PermissionRequested](#remove_permissionrequested) | Remove an event handler previously added with `add_PermissionRequested`.
[remove_ProcessFailed](#remove_processfailed) | Remove an event handler previously added with add_ProcessFailed.
[remove_ScriptDialogOpening](#remove_scriptdialogopening) | Remove an event handler previously added with `add_ScriptDialogOpening`.
[remove_SourceChanged](#remove_sourcechanged) | Remove an event handler previously added with `add_SourceChanged`.
[remove_WebMessageReceived](#remove_webmessagereceived) | Remove an event handler previously added with `add_WebMessageReceived`.
[remove_WebResourceRequested](#remove_webresourcerequested) | Remove an event handler previously added with `add_WebResourceRequested`.
[remove_WindowCloseRequested](#remove_windowcloserequested) | Remove an event handler previously added with `add_WindowCloseRequested`.
[RemoveHostObjectFromScript](#removehostobjectfromscript) | Remove the host object specified by the name so that it is no longer accessible from JavaScript code in the WebView.
[RemoveScriptToExecuteOnDocumentCreated](#removescripttoexecuteondocumentcreated) | Remove the corresponding JavaScript added using `AddScriptToExecuteOnDocumentCreated` with the specified script ID.
[RemoveWebResourceRequestedFilter](#removewebresourcerequestedfilter) | Removes a matching WebResource filter that was previously added for the `WebResourceRequested` event.
[Stop](#stop) | Stop all navigations and pending resource fetches. Does not stop scripts.
[COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT](#corewebview2_capture_preview_image_format) | Specifies the image format for the `[ICoreWebView2::CapturePreview](#capturepreview)` method.
[COREWEBVIEW2_COOKIE_SAME_SITE_KIND](#corewebview2_cookie_same_site_kind) | Kind of cookie SameSite status used in the ICoreWebView2Cookie interface.
[COREWEBVIEW2_KEY_EVENT_KIND](#corewebview2_key_event_kind) | Specifies the key event type that triggered an `AcceleratorKeyPressed` event.
[COREWEBVIEW2_MOVE_FOCUS_REASON](#corewebview2_move_focus_reason) | Specifies the reason for moving focus.
[COREWEBVIEW2_PERMISSION_KIND](#corewebview2_permission_kind) | Indicates the type of a permission request.
[COREWEBVIEW2_PERMISSION_STATE](#corewebview2_permission_state) | Specifies the response to a permission request.
[COREWEBVIEW2_PHYSICAL_KEY_STATUS](#corewebview2_physical_key_status) | Contains the information packed into the `LPARAM` sent to a Win32 key event.
[COREWEBVIEW2_PROCESS_FAILED_KIND](#corewebview2_process_failed_kind) | Specifies the process failure type used in the `ICoreWebView2ProcessFailedEventHandler` interface.
[COREWEBVIEW2_SCRIPT_DIALOG_KIND](#corewebview2_script_dialog_kind) | Specifies the JavaScript dialog type used in the `ICoreWebView2ScriptDialogOpeningEventHandler` interface.
[COREWEBVIEW2_WEB_ERROR_STATUS](#corewebview2_web_error_status) | Indicates the error status values for web navigations.
[COREWEBVIEW2_WEB_RESOURCE_CONTEXT](#corewebview2_web_resource_context) | Specifies the web resource request contexts.

## Members

#### add_ContainsFullScreenElementChanged 

Add an event handler for the `ContainsFullScreenElementChanged` event.

> public HRESULT [add_ContainsFullScreenElementChanged](#add_containsfullscreenelementchanged)([ICoreWebView2ContainsFullScreenElementChangedEventHandler](icorewebview2containsfullscreenelementchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ContainsFullScreenElementChanged` triggers when the `ContainsFullScreenElement` property changes. An HTML element inside the WebView may enter fullscreen to the size of the WebView or leave fullscreen. This event is useful when, for example, a video element requests to go fullscreen. The listener of `ContainsFullScreenElementChanged` may resize the WebView in response.

```cpp
    // Register a handler for the ContainsFullScreenChanged event.
    CHECK_FAILURE(m_webView->add_ContainsFullScreenElementChanged(
        Callback<ICoreWebView2ContainsFullScreenElementChangedEventHandler>(
            [this](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                if (m_fullScreenAllowed)
                {
                    CHECK_FAILURE(
                        sender->get_ContainsFullScreenElement(&m_containsFullscreenElement));
                    if (m_containsFullscreenElement)
                    {
                        EnterFullScreen();
                    }
                    else
                    {
                        ExitFullScreen();
                    }
                }
                return S_OK;
            })
            .Get(),
        nullptr));
```

#### add_ContentLoading 

Add an event handler for the `ContentLoading` event.

> public HRESULT [add_ContentLoading](#add_contentloading)([ICoreWebView2ContentLoadingEventHandler](icorewebview2contentloadingeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ContentLoading` triggers before any content is loaded, including scripts added with `AddScriptToExecuteOnDocumentCreated`. `ContentLoading` does not trigger if a same page navigation occurs (such as through `fragment` navigations or `history.pushState` navigations). This operation follows the `NavigationStarting` and `SourceChanged` events and precedes the `HistoryChanged` and `NavigationCompleted` events.

#### add_DocumentTitleChanged 

Add an event handler for the `DocumentTitleChanged` event.

> public HRESULT [add_DocumentTitleChanged](#add_documenttitlechanged)([ICoreWebView2DocumentTitleChangedEventHandler](icorewebview2documenttitlechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`DocumentTitleChanged` runs when the `DocumentTitle` property of the WebView changes and may run before or after the `NavigationCompleted` event.

```cpp
    // Register a handler for the DocumentTitleChanged event.
    // This handler just announces the new title on the window's title bar.
    CHECK_FAILURE(m_webView->add_DocumentTitleChanged(
        Callback<ICoreWebView2DocumentTitleChangedEventHandler>(
            [this](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                wil::unique_cotaskmem_string title;
                CHECK_FAILURE(sender->get_DocumentTitle(&title));
                SetWindowText(m_appWindow->GetMainWindow(), title.get());
                return S_OK;
            })
            .Get(),
        &m_documentTitleChangedToken));
```

#### add_FrameNavigationCompleted 

Add an event handler for the `FrameNavigationCompleted` event.

> public HRESULT [add_FrameNavigationCompleted](#add_framenavigationcompleted)([ICoreWebView2NavigationCompletedEventHandler](icorewebview2navigationcompletedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`FrameNavigationCompleted` triggers when a child frame has completely loaded (`body.onload` has triggered) or loading stopped with error.

```cpp
    // Register a handler for the FrameNavigationCompleted event.
    // Check whether the navigation succeeded, and if not, do something.
    CHECK_FAILURE(m_webView->add_FrameNavigationCompleted(
        Callback<ICoreWebView2NavigationCompletedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2NavigationCompletedEventArgs* args)
                -> HRESULT {
                BOOL success;
                CHECK_FAILURE(args->get_IsSuccess(&success));
                if (!success)
                {
                    COREWEBVIEW2_WEB_ERROR_STATUS webErrorStatus;
                    CHECK_FAILURE(args->get_WebErrorStatus(&webErrorStatus));
                    std::wstring error_msg = WebErrorStatusToString(webErrorStatus);
                    MessageBox(nullptr,
                       (std::wstring(L"IFrame navigation failed with the ") +
                         L"give in error " + error_msg).c_str(),
                       L"Navigation Failure", MB_OK);
                    if (webErrorStatus == COREWEBVIEW2_WEB_ERROR_STATUS_DISCONNECTED)
                    {
                        // Do something here if you want to handle a specific error case.
                        // In most cases this isn't necessary, because the WebView will
                        // display its own error page automatically.
                    }
                }
                return S_OK;
            })
            .Get(),
        &m_frameNavigationCompletedToken));
```

#### add_FrameNavigationStarting 

Add an event handler for the `FrameNavigationStarting` event.

> public HRESULT [add_FrameNavigationStarting](#add_framenavigationstarting)([ICoreWebView2NavigationStartingEventHandler](icorewebview2navigationstartingeventhandler.md) * eventHandler, EventRegistrationToken * token)

`FrameNavigationStarting` triggers when a child frame in the WebView requests permission to navigate to a different URI. Redirects trigger this operation as well.

You may block corresponding navigations until the event handler returns.

```cpp
    // Register a handler for the FrameNavigationStarting event.
    // This handler will prevent a frame from navigating to a blocked domain.
    CHECK_FAILURE(m_webView->add_FrameNavigationStarting(
        Callback<ICoreWebView2NavigationStartingEventHandler>(
            [this](ICoreWebView2* sender,
                   ICoreWebView2NavigationStartingEventArgs* args) -> HRESULT
    {
        wil::unique_cotaskmem_string uri;
        CHECK_FAILURE(args->get_Uri(&uri));

        if (ShouldBlockUri(uri.get()))
        {
            CHECK_FAILURE(args->put_Cancel(true));
        }
        return S_OK;
    }).Get(), &m_frameNavigationStartingToken));
```

#### add_HistoryChanged 

Add an event handler for the `HistoryChanged` event.

> public HRESULT [add_HistoryChanged](#add_historychanged)([ICoreWebView2HistoryChangedEventHandler](icorewebview2historychangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`HistoryChanged` listens to the change of navigation history for the top level document. Use `HistoryChanged` to verify that the `CanGoBack` or `CanGoForward` value has changed. `HistoryChanged` also runs for using `GoBack`or `GoForward`. `HistoryChanged` runs after `SourceChanged` and `ContentLoading`.

```cpp
    // Register a handler for the HistoryChanged event.
    // Update the Back, Forward buttons.
    CHECK_FAILURE(m_webView->add_HistoryChanged(
        Callback<ICoreWebView2HistoryChangedEventHandler>(
            [this](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                BOOL canGoBack;
                BOOL canGoForward;
                sender->get_CanGoBack(&canGoBack);
                sender->get_CanGoForward(&canGoForward);
                m_toolbar->SetItemEnabled(Toolbar::Item_BackButton, canGoBack);
                m_toolbar->SetItemEnabled(Toolbar::Item_ForwardButton, canGoForward);

                return S_OK;
            })
            .Get(),
        &m_historyChangedToken));
```

#### add_NavigationCompleted 

Add an event handler for the `NavigationCompleted` event.

> public HRESULT [add_NavigationCompleted](#add_navigationcompleted)([ICoreWebView2NavigationCompletedEventHandler](icorewebview2navigationcompletedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`NavigationCompleted` runs when the WebView has completely loaded (`body.onload` runs) or loading stopped with error.

```cpp
    // Register a handler for the NavigationCompleted event.
    // Check whether the navigation succeeded, and if not, do something.
    // Also update the Cancel buttons.
    CHECK_FAILURE(m_webView->add_NavigationCompleted(
        Callback<ICoreWebView2NavigationCompletedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2NavigationCompletedEventArgs* args)
                -> HRESULT {
                BOOL success;
                CHECK_FAILURE(args->get_IsSuccess(&success));
                if (!success)
                {
                    COREWEBVIEW2_WEB_ERROR_STATUS webErrorStatus;
                    CHECK_FAILURE(args->get_WebErrorStatus(&webErrorStatus));
                    if (webErrorStatus == COREWEBVIEW2_WEB_ERROR_STATUS_DISCONNECTED)
                    {
                        // Do something here if you want to handle a specific error case.
                        // In most cases this isn't necessary, because the WebView will
                        // display its own error page automatically.
                    }
                }
                m_toolbar->SetItemEnabled(Toolbar::Item_CancelButton, false);
                m_toolbar->SetItemEnabled(Toolbar::Item_ReloadButton, true);
                return S_OK;
            })
            .Get(),
        &m_navigationCompletedToken));
```

#### add_NavigationStarting 

Add an event handler for the `NavigationStarting` event.

> public HRESULT [add_NavigationStarting](#add_navigationstarting)([ICoreWebView2NavigationStartingEventHandler](icorewebview2navigationstartingeventhandler.md) * eventHandler, EventRegistrationToken * token)

`NavigationStarting` runs when the WebView main frame is requesting permission to navigate to a different URI. Redirects trigger this operation as well.

You may block corresponding navigations until the event handler returns.

```cpp
    // Register a handler for the NavigationStarting event.
    // This handler will check the domain being navigated to, and if the domain
    // matches a list of blocked sites, it will cancel the navigation and
    // possibly display a warning page.  It will also disable JavaScript on
    // selected websites.
    CHECK_FAILURE(m_webView->add_NavigationStarting(
        Callback<ICoreWebView2NavigationStartingEventHandler>(
            [this](ICoreWebView2* sender,
                   ICoreWebView2NavigationStartingEventArgs* args) -> HRESULT
    {
        wil::unique_cotaskmem_string uri;
        CHECK_FAILURE(args->get_Uri(&uri));

        if (ShouldBlockUri(uri.get()))
        {
            CHECK_FAILURE(args->put_Cancel(true));

            // If the user clicked a link to navigate, show a warning page.
            BOOL userInitiated;
            CHECK_FAILURE(args->get_IsUserInitiated(&userInitiated));
            static const PCWSTR htmlContent =
              L"<h1>Domain Blocked</h1>"
              L"<p>You've attempted to navigate to a domain in the blocked "
              L"sites list. Press back to return to the previous page.</p>";
            CHECK_FAILURE(sender->NavigateToString(htmlContent));
        }
        // Changes to settings will apply at the next navigation, which includes the
        // navigation after a NavigationStarting event.  We can use this to change
        // settings according to what site we're visiting.
        if (ShouldBlockScriptForUri(uri.get()))
        {
            m_settings->put_IsScriptEnabled(FALSE);
        }
        else
        {
            m_settings->put_IsScriptEnabled(m_isScriptEnabled);
        }
        return S_OK;
    }).Get(), &m_navigationStartingToken));
```

#### add_NewWindowRequested 

Add an event handler for the `NewWindowRequested` event.

> public HRESULT [add_NewWindowRequested](#add_newwindowrequested)([ICoreWebView2NewWindowRequestedEventHandler](icorewebview2newwindowrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`NewWindowRequested` runs when content inside the WebView requests to open a new window, such as through `window.open`. The app passes a target WebView that is considered the opened window.

If a deferral is not taken on the event args, scripts that resulted in the new window that are requested are blocked until the event handler returns. If a deferral is taken, then scripts are blocked until the deferral is completed.

```cpp
    // Register a handler for the NewWindowRequested event.
    // This handler will defer the event, create a new app window, and then once the
    // new window is ready, it'll provide that new window's WebView as the response to
    // the request.
    CHECK_FAILURE(m_webView->add_NewWindowRequested(
        Callback<ICoreWebView2NewWindowRequestedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2NewWindowRequestedEventArgs* args) {
                wil::com_ptr<ICoreWebView2Deferral> deferral;
                CHECK_FAILURE(args->GetDeferral(&deferral));
                AppWindow* newAppWindow;

                wil::com_ptr<ICoreWebView2WindowFeatures> windowFeatures;
                CHECK_FAILURE(args->get_WindowFeatures(&windowFeatures));

                RECT windowRect = {0};
                UINT32 left = 0;
                UINT32 top = 0;
                UINT32 height = 0;
                UINT32 width = 0;
                BOOL shouldHaveToolbar = true;

                BOOL hasPosition = FALSE;
                BOOL hasSize = FALSE;
                CHECK_FAILURE(windowFeatures->get_HasPosition(&hasPosition));
                CHECK_FAILURE(windowFeatures->get_HasSize(&hasSize));

                bool useDefaultWindow = true;

                if (!!hasPosition && !!hasSize)
                {
                    CHECK_FAILURE(windowFeatures->get_Left(&left));
                    CHECK_FAILURE(windowFeatures->get_Top(&top));
                    CHECK_FAILURE(windowFeatures->get_Height(&height));
                    CHECK_FAILURE(windowFeatures->get_Width(&width));
                    useDefaultWindow = false;
                }
                CHECK_FAILURE(windowFeatures->get_ShouldDisplayToolbar(&shouldHaveToolbar));

                windowRect.left = left;
                windowRect.right = left + (width < s_minNewWindowSize ? s_minNewWindowSize : width);
                windowRect.top = top;
                windowRect.bottom = top + (height < s_minNewWindowSize ? s_minNewWindowSize : height);
                
                // passing "none" as uri as its a noinitialnavigation
                if (!useDefaultWindow)
                {
                  newAppWindow = new AppWindow(m_creationModeId, L"none", false, nullptr, true, windowRect, !!shouldHaveToolbar);
                }
                else
                {
                  newAppWindow = new AppWindow(m_creationModeId, L"none");
                }
                newAppWindow->m_isPopupWindow = true;
                newAppWindow->m_onWebViewFirstInitialized = [args, deferral, newAppWindow]() {
                    CHECK_FAILURE(args->put_NewWindow(newAppWindow->m_webView.get()));
                    CHECK_FAILURE(args->put_Handled(TRUE));
                    CHECK_FAILURE(deferral->Complete());
                };

                return S_OK;
            })
            .Get(),
        nullptr));
```

#### add_PermissionRequested 

Add an event handler for the `PermissionRequested` event.

> public HRESULT [add_PermissionRequested](#add_permissionrequested)([ICoreWebView2PermissionRequestedEventHandler](icorewebview2permissionrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`PermissionRequested` runs when content in a WebView requests permission to access some privileged resources.

If a deferral is not taken on the event args, the subsequent scripts are blocked until the event handler returns. If a deferral is taken, the scripts are blocked until the deferral is completed.

```cpp
    // Register a handler for the PermissionRequested event.
    // This handler prompts the user to allow or deny the request.
    CHECK_FAILURE(m_webView->add_PermissionRequested(
        Callback<ICoreWebView2PermissionRequestedEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2PermissionRequestedEventArgs* args) -> HRESULT
    {
        wil::unique_cotaskmem_string uri;
        COREWEBVIEW2_PERMISSION_KIND kind = COREWEBVIEW2_PERMISSION_KIND_UNKNOWN_PERMISSION;
        BOOL userInitiated = FALSE;

        CHECK_FAILURE(args->get_Uri(&uri));
        CHECK_FAILURE(args->get_PermissionKind(&kind));
        CHECK_FAILURE(args->get_IsUserInitiated(&userInitiated));

        std::wstring message = L"Do you want to grant permission for ";
        message += NameOfPermissionKind(kind);
        message += L" to the website at ";
        message += uri.get();
        message += L"?\n\n";
        message += (userInitiated
            ? L"This request came from a user gesture."
            : L"This request did not come from a user gesture.");

        int response = MessageBox(nullptr, message.c_str(), L"Permission Request",
                                   MB_YESNOCANCEL | MB_ICONWARNING);

        COREWEBVIEW2_PERMISSION_STATE state =
              response == IDYES ? COREWEBVIEW2_PERMISSION_STATE_ALLOW
            : response == IDNO  ? COREWEBVIEW2_PERMISSION_STATE_DENY
            :                     COREWEBVIEW2_PERMISSION_STATE_DEFAULT;
        CHECK_FAILURE(args->put_State(state));

        return S_OK;
    }).Get(), &m_permissionRequestedToken));
```

#### add_ProcessFailed 

Add an event handler for the `ProcessFailed` event.

> public HRESULT [add_ProcessFailed](#add_processfailed)([ICoreWebView2ProcessFailedEventHandler](icorewebview2processfailedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ProcessFailed` runs when a WebView process ends unexpectedly or becomes unresponsive.

```cpp
    // Register a handler for the ProcessFailed event.
    // This handler checks if the browser process failed, and asks the user if
    // they want to recreate the webview.
    CHECK_FAILURE(m_webView->add_ProcessFailed(
        Callback<ICoreWebView2ProcessFailedEventHandler>(
            [this](ICoreWebView2* sender,
                ICoreWebView2ProcessFailedEventArgs* args) -> HRESULT
    {
        COREWEBVIEW2_PROCESS_FAILED_KIND failureType;
        CHECK_FAILURE(args->get_ProcessFailedKind(&failureType));
        if (failureType == COREWEBVIEW2_PROCESS_FAILED_KIND_BROWSER_PROCESS_EXITED)
        {
            int button = MessageBox(
                m_appWindow->GetMainWindow(),
                L"Browser process exited unexpectedly.  Recreate webview?",
                L"Browser process exited",
                MB_YESNO);
            if (button == IDYES)
            {
                m_appWindow->ReinitializeWebView();
            }
        }
        else if (failureType == COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_UNRESPONSIVE)
        {
            int button = MessageBox(
                m_appWindow->GetMainWindow(),
                L"Browser render process has stopped responding.  Recreate webview?",
                L"Web page unresponsive", MB_YESNO);
            if (button == IDYES)
            {
                m_appWindow->ReinitializeWebView();
            }
        }
        else if (failureType == COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_EXITED)
        {
            int button = MessageBox(
                m_appWindow->GetMainWindow(),
                L"Browser render process exited unexpectedly. Reload page?",
                L"Web page unresponsive", MB_YESNO);
            if (button == IDYES)
            {
                CHECK_FAILURE(m_webView->Reload());
            }
        }
        return S_OK;
    }).Get(), &m_processFailedToken));
```

#### add_ScriptDialogOpening 

Add an event handler for the `ScriptDialogOpening` event.

> public HRESULT [add_ScriptDialogOpening](#add_scriptdialogopening)([ICoreWebView2ScriptDialogOpeningEventHandler](icorewebview2scriptdialogopeningeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ScriptDialogOpening` runs when a JavaScript dialog (`alert`, `confirm`, `prompt`, or `beforeunload`) displays for the webview. This event only triggers if the `ICoreWebView2Settings::AreDefaultScriptDialogsEnabled` property is set to `FALSE`. The `ScriptDialogOpening` event suppresses dialogs or replaces default dialogs with custom dialogs.

If a deferral is not taken on the event args, the subsequent scripts are blocked until the event handler returns. If a deferral is taken, the scripts are blocked until the deferral is completed.

```cpp
    // Register a handler for the ScriptDialogOpening event.
    // This handler will set up a custom prompt dialog for the user,
    // and may defer the event if the setting to defer dialogs is enabled.
    CHECK_FAILURE(m_webView->add_ScriptDialogOpening(
        Callback<ICoreWebView2ScriptDialogOpeningEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2ScriptDialogOpeningEventArgs* args) -> HRESULT
    {
        wil::com_ptr<ICoreWebView2ScriptDialogOpeningEventArgs> eventArgs = args;
        auto showDialog = [this, eventArgs]
        {
            wil::unique_cotaskmem_string uri;
            COREWEBVIEW2_SCRIPT_DIALOG_KIND type;
            wil::unique_cotaskmem_string message;
            wil::unique_cotaskmem_string defaultText;

            CHECK_FAILURE(eventArgs->get_Uri(&uri));
            CHECK_FAILURE(eventArgs->get_Kind(&type));
            CHECK_FAILURE(eventArgs->get_Message(&message));
            CHECK_FAILURE(eventArgs->get_DefaultText(&defaultText));

            std::wstring promptString = std::wstring(L"The page at '")
                + uri.get() + L"' says:";
            TextInputDialog dialog(
                m_appWindow->GetMainWindow(),
                L"Script Dialog",
                promptString.c_str(),
                message.get(),
                defaultText.get(),
                /* readonly */ type != COREWEBVIEW2_SCRIPT_DIALOG_KIND_PROMPT);
            if (dialog.confirmed)
            {
                CHECK_FAILURE(eventArgs->put_ResultText(dialog.input.c_str()));
                CHECK_FAILURE(eventArgs->Accept());
            }
        };

        if (m_deferScriptDialogs)
        {
            wil::com_ptr<ICoreWebView2Deferral> deferral;
            CHECK_FAILURE(args->GetDeferral(&deferral));
            m_completeDeferredDialog = [showDialog, deferral]
            {
                showDialog();
                CHECK_FAILURE(deferral->Complete());
            };
        }
        else
        {
            showDialog();
        }

        return S_OK;
    }).Get(), &m_scriptDialogOpeningToken));
```

#### add_SourceChanged 

Add an event handler for the `SourceChanged` event.

> public HRESULT [add_SourceChanged](#add_sourcechanged)([ICoreWebView2SourceChangedEventHandler](icorewebview2sourcechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`SourceChanged` triggers when the `Source` property changes. `SourceChanged` runs when navigating to a different site or fragment navigations. It does not trigger for other types of navigations such as page refreshes or `history.pushState` with the same URL as the current page. `SourceChanged` runs before `ContentLoading` for navigation to a new document.

```cpp
    // Register a handler for the SourceChanged event.
    // This handler will read the webview's source URI and update
    // the app's address bar.
    CHECK_FAILURE(m_webView->add_SourceChanged(
        Callback<ICoreWebView2SourceChangedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2SourceChangedEventArgs* args)
                -> HRESULT {
                wil::unique_cotaskmem_string uri;
                sender->get_Source(&uri);
                if (wcscmp(uri.get(), L"about:blank") == 0)
                {
                    uri = wil::make_cotaskmem_string(L"");
                }
                SetWindowText(GetAddressBar(), uri.get());

                return S_OK;
            })
            .Get(),
        &m_sourceChangedToken));
```

#### add_WebMessageReceived 

Add an event handler for the `WebMessageReceived` event.

> public HRESULT [add_WebMessageReceived](#add_webmessagereceived)([ICoreWebView2WebMessageReceivedEventHandler](icorewebview2webmessagereceivedeventhandler.md) * handler, EventRegistrationToken * token)

`WebMessageReceived` runs when the `ICoreWebView2Settings::IsWebMessageEnabled` setting is set and the top-level document of the WebView runs `window.chrome.webview.postMessage`. The `postMessage` function is `void postMessage(object)` where object is any object supported by JSON conversion.

```html
        window.chrome.webview.addEventListener('message', arg => {
            if ("SetColor" in arg.data) {
                document.getElementById("colorable").style.color = arg.data.SetColor;
            }
            if ("WindowBounds" in arg.data) {
                document.getElementById("window-bounds").value = arg.data.WindowBounds;
            }
        });

        function SetTitleText() {
            let titleText = document.getElementById("title-text");
            window.chrome.webview.postMessage(`SetTitleText ${titleText.value}`);
        }
        function GetWindowBounds() {
            window.chrome.webview.postMessage("GetWindowBounds");
        }
```
 When `postMessage` is run, the `Invoke` method of the `handler` is run with the `object` parameter of the `postMessage` converted to a JSON string.

```cpp
    // Setup the web message received event handler before navigating to
    // ensure we don't miss any messages.
    CHECK_FAILURE(m_webView->add_WebMessageReceived(
        Microsoft::WRL::Callback<ICoreWebView2WebMessageReceivedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2WebMessageReceivedEventArgs* args)
    {
        wil::unique_cotaskmem_string uri;
        CHECK_FAILURE(args->get_Source(&uri));

        // Always validate that the origin of the message is what you expect.
        if (uri.get() != m_sampleUri)
        {
            return S_OK;
        }
        wil::unique_cotaskmem_string messageRaw;
        CHECK_FAILURE(args->TryGetWebMessageAsString(&messageRaw));
        std::wstring message = messageRaw.get();

        if (message.compare(0, 13, L"SetTitleText ") == 0)
        {
            m_appWindow->SetTitleText(message.substr(13).c_str());
        }
        else if (message.compare(L"GetWindowBounds") == 0)
        {
            RECT bounds = m_appWindow->GetWindowBounds();
            std::wstring reply =
                L"{\"WindowBounds\":\"Left:" + std::to_wstring(bounds.left)
                + L"\\nTop:" + std::to_wstring(bounds.top)
                + L"\\nRight:" + std::to_wstring(bounds.right)
                + L"\\nBottom:" + std::to_wstring(bounds.bottom)
                + L"\"}";
            CHECK_FAILURE(sender->PostWebMessageAsJson(reply.c_str()));
        }
        return S_OK;
    }).Get(), &m_webMessageReceivedToken));
```

#### add_WebResourceRequested 

Add an event handler for the `WebResourceRequested` event.

> public HRESULT [add_WebResourceRequested](#add_webresourcerequested)([ICoreWebView2WebResourceRequestedEventHandler](icorewebview2webresourcerequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`WebResourceRequested` runs when the WebView is performing a URL request to a matching URL and resource context filter that was added with `AddWebResourceRequestedFilter`. At least one filter must be added for the event to run.

The web resource requested may be blocked until the event handler returns if a deferral is not taken on the event args. If a deferral is taken, then the web resource requested is blocked until the deferral is completed.

```cpp
        if (m_blockImages)
        {
            m_webView->AddWebResourceRequestedFilter(L"*", COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE);
            CHECK_FAILURE(m_webView->add_WebResourceRequested(
                Callback<ICoreWebView2WebResourceRequestedEventHandler>(
                    [this](
                        ICoreWebView2* sender,
                        ICoreWebView2WebResourceRequestedEventArgs* args) {
                        COREWEBVIEW2_WEB_RESOURCE_CONTEXT resourceContext;
                        CHECK_FAILURE(
                            args->get_ResourceContext(&resourceContext));
                        // Ensure that the type is image
                        if (resourceContext != COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE)
                        {
                            return E_INVALIDARG;
                        }
                        // Override the response with an empty one to block the image.
                        // If put_Response is not called, the request will continue as normal.
                        wil::com_ptr<ICoreWebView2WebResourceResponse> response;
                        wil::com_ptr<ICoreWebView2Environment> environment;
                        wil::com_ptr<ICoreWebView2_2> webview2;
                        CHECK_FAILURE(m_webView->QueryInterface(IID_PPV_ARGS(&webview2)));
                        CHECK_FAILURE(webview2->get_Environment(&environment));
                        CHECK_FAILURE(environment->CreateWebResourceResponse(
                            nullptr, 403 /*NoContent*/, L"Blocked", L"", &response));
                        CHECK_FAILURE(args->put_Response(response.get()));
                        return S_OK;
                    })
                    .Get(),
                &m_webResourceRequestedTokenForImageBlocking));
        }
        else
        {
            CHECK_FAILURE(m_webView->remove_WebResourceRequested(
                m_webResourceRequestedTokenForImageBlocking));
        }
```

#### add_WindowCloseRequested 

Add an event handler for the `WindowCloseRequested` event.

> public HRESULT [add_WindowCloseRequested](#add_windowcloserequested)([ICoreWebView2WindowCloseRequestedEventHandler](icorewebview2windowcloserequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`WindowCloseRequested` triggers when content inside the WebView requested to close the window, such as after `window.close` is run. The app should close the WebView and related app window if that makes sense to the app.

```cpp
    // Register a handler for the WindowCloseRequested event.
    // This handler will close the app window if it is not the main window.
    CHECK_FAILURE(m_webView->add_WindowCloseRequested(
        Callback<ICoreWebView2WindowCloseRequestedEventHandler>([this](
                                                                    ICoreWebView2* sender,
                                                                    IUnknown* args) {
            if (m_isPopupWindow)
            {
                CloseAppWindow();
            }
            return S_OK;
        }).Get(),
        nullptr));
```

#### AddHostObjectToScript 

Add the provided host object to script running in the WebView with the specified name.

> public HRESULT [AddHostObjectToScript](#addhostobjecttoscript)(LPCWSTR name, VARIANT * object)

Host objects are exposed as host object proxies using `window.chrome.webview.hostObjects.{name}`. Host object proxies are promises and resolves to an object representing the host object. The promise is rejected if the app has not added an object with the name. When JavaScript code access a property or method of the object, a promise is return, which resolves to the value returned from the host for the property or method, or rejected in case of error, for example, no property or method on the object or parameters are not valid.

> [!NOTE] While simple types, `IDispatch` and array are supported, generic `IUnknown`, `VT_DECIMAL`, or `VT_RECORD` variant is not supported. Remote JavaScript objects like callback functions are represented as an `VT_DISPATCH``VARIANT` with the object implementing `IDispatch`. The JavaScript callback method may be invoked using `DISPID_VALUE` for the `DISPID`. Nested arrays are supported up to a depth of 3. Arrays of by reference types are not supported. `VT_EMPTY` and `VT_NULL` are mapped into JavaScript as `null`. In JavaScript, `null` and undefined are mapped to `VT_EMPTY`.

Additionally, all host objects are exposed as `window.chrome.webview.hostObjects.sync.{name}`. Here the host objects are exposed as synchronous host object proxies. These are not promises and function runtimes or property access synchronously block running script waiting to communicate cross process for the host code to run. Accordingly the result may have reliability issues and it is recommended that you use the promise-based asynchronous `window.chrome.webview.hostObjects.{name}` API.

Synchronous host object proxies and asynchronous host object proxies may both use a proxy to the same host object. Remote changes made by one proxy propagates to any other proxy of that same host object whether the other proxies and synchronous or asynchronous.

While JavaScript is blocked on a synchronous run to native code, that native code is unable to run back to JavaScript. Attempts to do so fail with `HRESULT_FROM_WIN32(ERROR_POSSIBLE_DEADLOCK)`.

Host object proxies are JavaScript Proxy objects that intercept all property get, property set, and method invocations. Properties or methods that are a part of the Function or Object prototype are run locally. Additionally any property or method in the `chrome.webview.hostObjects.options.forceLocalProperties` array are also run locally. This defaults to including optional methods that have meaning in JavaScript like `toJSON` and `Symbol.toPrimitive`. Add more to the array as required.

The `chrome.webview.hostObjects.cleanupSome` method performs a best effort garbage collection on host object proxies.

Host object proxies additionally have the following methods which run locally.

Method name  |Details
--------- | ---------
`applyHostFunction`, `getHostProperty`, `setHostProperty`|Perform a method invocation, property get, or property set on the host object. Use the methods to explicitly force a method or property to run remotely if a conflicting local method or property exists. For instance, `proxy.toString()` runs the local `toString` method on the proxy object. But proxy.applyHostFunction('toString') runs `toString` on the host proxied object instead.
`getLocalProperty`, `setLocalProperty`|Perform property get, or property set locally. Use the methods to force getting or setting a property on the host object proxy rather than on the host object it represents. For instance, `proxy.unknownProperty` gets the property named `unknownProperty` from the host proxied object. But proxy.getLocalProperty('unknownProperty') gets the value of the property `unknownProperty` on the proxy object.
`sync`|Asynchronous host object proxies expose a sync method which returns a promise for a synchronous host object proxy for the same host object. For example, `chrome.webview.hostObjects.sample.methodCall()` returns an asynchronous host object proxy. Use the `sync` method to obtain a synchronous host object proxy instead: `const syncProxy = await chrome.webview.hostObjects.sample.methodCall().sync()`.
`async`|Synchronous host object proxies expose an async method which blocks and returns an asynchronous host object proxy for the same host object. For example, `chrome.webview.hostObjects.sync.sample.methodCall()` returns a synchronous host object proxy. Running the `async` method on this blocks and then returns an asynchronous host object proxy for the same host object: `const asyncProxy = chrome.webview.hostObjects.sync.sample.methodCall().async()`.
`then`|Asynchronous host object proxies have a `then` method. Allows proxies to be awaitable. `then` returns a promise that resolves with a representation of the host object. If the proxy represents a JavaScript literal, a copy of that is returned locally. If the proxy represents a function, a non-awaitable proxy is returned. If the proxy represents a JavaScript object with a mix of literal properties and function properties, the a copy of the object is returned with some properties as host object proxies.

All other property and method invocations (other than the above Remote object proxy methods, `forceLocalProperties` list, and properties on Function and Object prototypes) are run remotely. Asynchronous host object proxies return a promise representing asynchronous completion of remotely invoking the method, or getting the property. The promise resolves after the remote operations complete and the promises resolve to the resulting value of the operation. Synchronous host object proxies work similarly, but block running JavaScript and wait for the remote operation to complete.

Setting a property on an asynchronous host object proxy works slightly differently. The set returns immediately and the return value is the value that is set. This is a requirement of the JavaScript Proxy object. If you need to asynchronously wait for the property set to complete, use the `setHostProperty` method which returns a promise as described above. Synchronous object property set property synchronously blocks until the property is set.

For example, suppose you have a COM object with the following interface.

```idl
    [uuid(3a14c9c0-bc3e-453f-a314-4ce4a0ec81d8), object, local]
    interface IHostObjectSample : IUnknown
    {
        // Demonstrate basic method call with some parameters and a return value.
        HRESULT MethodWithParametersAndReturnValue([in] BSTR stringParameter, [in] INT integerParameter, [out, retval] BSTR* stringResult);

        // Demonstrate getting and setting a property.
        [propget] HRESULT Property([out, retval] BSTR* stringResult);
        [propput] HRESULT Property([in] BSTR stringValue);

        [propget] HRESULT IndexedProperty(INT index, [out, retval] BSTR * stringResult);
        [propput] HRESULT IndexedProperty(INT index, [in] BSTR stringValue);

        // Demonstrate native calling back into JavaScript.
        HRESULT CallCallbackAsynchronously([in] IDispatch* callbackParameter);

    };
```
 Add an instance of this interface into your JavaScript with `AddHostObjectToScript`. In this case, name it `sample`.

```cpp
            VARIANT remoteObjectAsVariant = {};
            m_hostObject.query_to<IDispatch>(&remoteObjectAsVariant.pdispVal);
            remoteObjectAsVariant.vt = VT_DISPATCH;

            // We can call AddHostObjectToScript multiple times in a row without
            // calling RemoveHostObject first. This will replace the previous object
            // with the new object. In our case this is the same object and everything
            // is fine.
            CHECK_FAILURE(
                m_webView->AddHostObjectToScript(L"sample", &remoteObjectAsVariant));
            remoteObjectAsVariant.pdispVal->Release();
```
 In the HTML document, use the COM object using `chrome.webview.hostObjects.sample`.

```html
        document.getElementById("getPropertyAsyncButton").addEventListener("click", async () => {
        const propertyValue = await chrome.webview.hostObjects.sample.property;
        document.getElementById("getPropertyAsyncOutput").textContent = propertyValue;
        });

        document.getElementById("getPropertySyncButton").addEventListener("click", () => {
        const propertyValue = chrome.webview.hostObjects.sync.sample.property;
        document.getElementById("getPropertySyncOutput").textContent = propertyValue;
        });

        document.getElementById("setPropertyAsyncButton").addEventListener("click", async () => {
        const propertyValue = document.getElementById("setPropertyAsyncInput").value;
        // The following line will work but it will return immediately before the property value has actually been set.
        // If you need to set the property and wait for the property to change value, use the setHostProperty function.
        chrome.webview.hostObjects.sample.property = propertyValue;
        document.getElementById("setPropertyAsyncOutput").textContent = "Set";
        });

        document.getElementById("setPropertyExplicitAsyncButton").addEventListener("click", async () => {
        const propertyValue = document.getElementById("setPropertyExplicitAsyncInput").value;
        // If you care about waiting until the property has actually changed value use the setHostProperty function.
        await chrome.webview.hostObjects.sample.setHostProperty("property", propertyValue);
        document.getElementById("setPropertyExplicitAsyncOutput").textContent = "Set";
        });

        document.getElementById("setPropertySyncButton").addEventListener("click", () => {
        const propertyValue = document.getElementById("setPropertySyncInput").value;
        chrome.webview.hostObjects.sync.sample.property = propertyValue;
        document.getElementById("setPropertySyncOutput").textContent = "Set";
        });

        document.getElementById("getIndexedPropertyAsyncButton").addEventListener("click", async () => {
        const index = parseInt(document.getElementById("getIndexedPropertyAsyncParam").value);
        const resultValue = await chrome.webview.hostObjects.sample.IndexedProperty[index];
        document.getElementById("getIndexedPropertyAsyncOutput").textContent = resultValue;
        });
        document.getElementById("setIndexedPropertyAsyncButton").addEventListener("click", async () => {
        const index = parseInt(document.getElementById("setIndexedPropertyAsyncParam1").value);
        const value = document.getElementById("setIndexedPropertyAsyncParam2").value;;
        chrome.webview.hostObjects.sample.IndexedProperty[index] = value;
        document.getElementById("setIndexedPropertyAsyncOutput").textContent = "Set";
        });
        document.getElementById("invokeMethodAsyncButton").addEventListener("click", async () => {
        const paramValue1 = document.getElementById("invokeMethodAsyncParam1").value;
        const paramValue2 = parseInt(document.getElementById("invokeMethodAsyncParam2").value);
        const resultValue = await chrome.webview.hostObjects.sample.MethodWithParametersAndReturnValue(paramValue1, paramValue2);
        document.getElementById("invokeMethodAsyncOutput").textContent = resultValue;
        });

        document.getElementById("invokeMethodSyncButton").addEventListener("click", () => {
        const paramValue1 = document.getElementById("invokeMethodSyncParam1").value;
        const paramValue2 = parseInt(document.getElementById("invokeMethodSyncParam2").value);
        const resultValue = chrome.webview.hostObjects.sync.sample.MethodWithParametersAndReturnValue(paramValue1, paramValue2);
        document.getElementById("invokeMethodSyncOutput").textContent = resultValue;
        });

        let callbackCount = 0;
        document.getElementById("invokeCallbackButton").addEventListener("click", async () => {
        chrome.webview.hostObjects.sample.CallCallbackAsynchronously(() => {
        document.getElementById("invokeCallbackOutput").textContent = "Native object called the callback " + (++callbackCount) + " time(s).";
        });
        });
```
 Exposing host objects to script has security risk. For more information about best practices, navigate to [Best practices for developing secure WebView2 applications][MicrosoftEdgeWebview2ConceptsSecurity].

[MicrosoftEdgeWebview2ConceptsSecurity]: /microsoft-edge/webview2/concepts/security "Best practices for developing secure WebView2 applications | Microsoft Docs"

#### AddScriptToExecuteOnDocumentCreated 

Add the provided JavaScript to a list of scripts that should be run after the global object has been created, but before the HTML document has been parsed and before any other script included by the HTML document is run.

> public HRESULT [AddScriptToExecuteOnDocumentCreated](#addscripttoexecuteondocumentcreated)(LPCWSTR javaScript, ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler * handler)

This method injects a script that runs on all top-level document and child frame page navigations. This method runs asynchronously, and you must wait for the completion handler to finish before the injected script is ready to run. When this method completes, the `Invoke` method of the handler is run with the `id` of the injected script. `id` is a string. To remove the injected script, use `RemoveScriptToExecuteOnDocumentCreated`.

> [!NOTE] If an HTML document is running in a sandbox of some kind using [sandbox][MdnDocsWebHtmlElementIframeAttrSandbox] properties or the [Content-Security-Policy][MdnDocsWebHttpHeadersContentSecurityPolicy] HTTP header affects the script that runs. For example, if the `allow-modals` keyword is not set then requests to run the `alert` function are ignored.

```cpp
// Prompt the user for some script and register it to execute whenever a new page loads.
void ScriptComponent::AddInitializeScript()
{
    TextInputDialog dialog(
        m_appWindow->GetMainWindow(),
        L"Add Initialize Script",
        L"Initialization Script:",
        L"Enter the JavaScript code to run as the initialization script that "
            L"runs before any script in the HTML document.",
    // This example script stops child frames from opening new windows.  Because
    // the initialization script runs before any script in the HTML document, we
    // can trust the results of our checks on window.parent and window.top.
        L"if (window.parent !== window.top) {\r\n"
        L"    delete window.open;\r\n"
        L"}");
    if (dialog.confirmed)
    {
        m_webView->AddScriptToExecuteOnDocumentCreated(
            dialog.input.c_str(),
            Callback<ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler>(
                [this](HRESULT error, PCWSTR id) -> HRESULT
        {
            m_lastInitializeScriptId = id;
            MessageBox(nullptr, id, L"AddScriptToExecuteOnDocumentCreated Id", MB_OK);
            return S_OK;
        }).Get());

    }
}
```
 [MdnDocsWebHtmlElementIframeAttrSandbox]: [https://developer.mozilla.org/docs/Web/HTML/Element/iframe#attr-sandbox](https://developer.mozilla.org/docs/Web/HTML/Element/iframe#attr-sandbox) "sandbox - &lt;iframe&gt;: The Inline Frame element | MDN"

[MdnDocsWebHttpHeadersContentSecurityPolicy]: [https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy) "Content-Security-Policy | MDN"

#### AddWebResourceRequestedFilter 

Adds a URI and resource context filter to the `WebResourceRequested` event.

> public HRESULT [AddWebResourceRequestedFilter](#addwebresourcerequestedfilter)(LPCWSTR const uri, COREWEBVIEW2_WEB_RESOURCE_CONTEXT const resourceContext)

The `URI` parameter value may be set to a wildcard string (`*`: zero or more, `?`: exactly one). `nullptr` is equivalent to `L""`. For more information about resource context filters, navigate to [COREWEBVIEW2_WEB_RESOURCE_CONTEXT].

#### CallDevToolsProtocolMethod 

Runs an asynchronous `DevToolsProtocol` method.

> public HRESULT [CallDevToolsProtocolMethod](#calldevtoolsprotocolmethod)(LPCWSTR methodName, LPCWSTR parametersAsJson, ICoreWebView2CallDevToolsProtocolMethodCompletedHandler * handler)

For more information about available methods, navigate to [DevTools Protocol Viewer][GithubChromedevtoolsDevtoolsProtocolTot] . The `methodName` parameter is the full name of the method in the `{domain}.{method}` format. The `parametersAsJson` parameter is a JSON formatted string containing the parameters for the corresponding method. The `Invoke` method of the `handler` is run when the method asynchronously completes. `Invoke` is run with the return object of the method as a JSON string.

```cpp
// Prompt the user for the name and parameters of a CDP method, then call it.
void ScriptComponent::CallCdpMethod()
{
    TextInputDialog dialog(
        m_appWindow->GetMainWindow(),
        L"Call CDP Method",
        L"CDP method name:",
        L"Enter the CDP method name to call, followed by a space,\r\n"
            L"followed by the parameters in JSON format.",
        L"Runtime.evaluate {\"expression\":\"alert(\\\"test\\\")\"}");
    if (dialog.confirmed)
    {
        size_t delimiterPos = dialog.input.find(L' ');
        std::wstring methodName = dialog.input.substr(0, delimiterPos);
        std::wstring methodParams =
            (delimiterPos < dialog.input.size()
                ? dialog.input.substr(delimiterPos + 1)
                : L"{}");

        m_webView->CallDevToolsProtocolMethod(
            methodName.c_str(),
            methodParams.c_str(),
            Callback<ICoreWebView2CallDevToolsProtocolMethodCompletedHandler>(
                [](HRESULT error, PCWSTR resultJson) -> HRESULT
                {
                    MessageBox(nullptr, resultJson, L"CDP Method Result", MB_OK);
                    return S_OK;
                }).Get());
    }
}
```

[GithubChromedevtoolsDevtoolsProtocolTot]: [https://chromedevtools.github.io/devtools-protocol/tot](https://chromedevtools.github.io/devtools-protocol/tot) "latest (tip-of-tree) protocol - Chrome DevTools Protocol | GitHub"

#### CapturePreview 

Capture an image of what WebView is displaying.

> public HRESULT [CapturePreview](#capturepreview)([COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT](#corewebview2_capture_preview_image_format) imageFormat, IStream * imageStream, [ICoreWebView2CapturePreviewCompletedHandler](icorewebview2capturepreviewcompletedhandler.md) * handler)

Specify the format of the image with the `imageFormat` parameter. The resulting image binary data is written to the provided `imageStream` parameter. When `CapturePreview` finishes writing to the stream, the `Invoke` method on the provided `handler` parameter is run.

```cpp
// Show the user a file selection dialog, then save a screenshot of the WebView
// to the selected file.
void FileComponent::SaveScreenshot()
{
    OPENFILENAME openFileName = {};
    openFileName.lStructSize = sizeof(openFileName);
    openFileName.hwndOwner = nullptr;
    openFileName.hInstance = nullptr;
    WCHAR fileName[MAX_PATH] = L"WebView2_Screenshot.png";
    openFileName.lpstrFile = fileName;
    openFileName.lpstrFilter = L"PNG File\0*.png\0";
    openFileName.nMaxFile = ARRAYSIZE(fileName);
    openFileName.Flags = OFN_OVERWRITEPROMPT;

    if (GetSaveFileName(&openFileName))
    {
        wil::com_ptr<IStream> stream;
        CHECK_FAILURE(SHCreateStreamOnFileEx(
            fileName, STGM_READWRITE | STGM_CREATE, FILE_ATTRIBUTE_NORMAL, TRUE, nullptr,
            &stream));

        HWND mainWindow = m_appWindow->GetMainWindow();

        CHECK_FAILURE(m_webView->CapturePreview(
            COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT_PNG, stream.get(),
            Callback<ICoreWebView2CapturePreviewCompletedHandler>(
                [mainWindow](HRESULT error_code) -> HRESULT {
                    CHECK_FAILURE(error_code);

                    MessageBox(mainWindow, L"Preview Captured", L"Preview Captured", MB_OK);
                    return S_OK;
                })
                .Get()));
    }
}
```

#### ExecuteScript 

Run JavaScript code from the javascript parameter in the current top-level document rendered in the WebView.

> public HRESULT [ExecuteScript](#executescript)(LPCWSTR javaScript, [ICoreWebView2ExecuteScriptCompletedHandler](icorewebview2executescriptcompletedhandler.md) * handler)

The result of evaluating the provided JavaScript is used in this parameter. The result value is a JSON encoded string. If the result is undefined, contains a reference cycle, or otherwise is not able to be encoded into JSON, the JSON `null` value is returned as the `null` string.

> [!NOTE] A function that has no explicit return value returns undefined. If the script that was run throws an unhandled exception, then the result is also `null`. This method is applied asynchronously. If the method is run after the `NavigationStarting` event during a navigation, the script runs in the new document when loading it, around the time `ContentLoading` is run. This operation works even if `ICoreWebView2Settings::IsScriptEnabled` is set to `FALSE`.

```cpp
// Prompt the user for some script and then execute it.
void ScriptComponent::InjectScript()
{
    TextInputDialog dialog(
        m_appWindow->GetMainWindow(),
        L"Inject Script",
        L"Enter script code:",
        L"Enter the JavaScript code to run in the webview.",
        L"window.getComputedStyle(document.body).backgroundColor");
    if (dialog.confirmed)
    {
        m_webView->ExecuteScript(dialog.input.c_str(),
            Callback<ICoreWebView2ExecuteScriptCompletedHandler>(
                [](HRESULT error, PCWSTR result) -> HRESULT
        {
            if (error != S_OK) {
                ShowFailure(error, L"ExecuteScript failed");
            }
            MessageBox(nullptr, result, L"ExecuteScript Result", MB_OK);
            return S_OK;
        }).Get());
    }
}
```

#### get_BrowserProcessId 

The process ID of the browser process that hosts the WebView.

> public HRESULT [get_BrowserProcessId](#get_browserprocessid)(UINT32 * value)

#### get_CanGoBack 

`TRUE` if the WebView is able to navigate to a previous page in the navigation history.

> public HRESULT [get_CanGoBack](#get_cangoback)(BOOL * canGoBack)

If `CanGoBack` changes value, the `HistoryChanged` event runs.

#### get_CanGoForward 

`TRUE` if the WebView is able to navigate to a next page in the navigation history.

> public HRESULT [get_CanGoForward](#get_cangoforward)(BOOL * canGoForward)

If `CanGoForward` changes value, the `HistoryChanged` event runs.

#### get_ContainsFullScreenElement 

Indicates if the WebView contains a fullscreen HTML element.

> public HRESULT [get_ContainsFullScreenElement](#get_containsfullscreenelement)(BOOL * containsFullScreenElement)

#### get_DocumentTitle 

The title for the current top-level document.

> public HRESULT [get_DocumentTitle](#get_documenttitle)(LPWSTR * title)

If the document has no explicit title or is otherwise empty, a default that may or may not match the URI of the document is used.

#### get_Settings 

The `[ICoreWebView2Settings](icorewebview2settings.md)` object contains various modifiable settings for the running WebView.

> public HRESULT [get_Settings](#get_settings)([ICoreWebView2Settings](icorewebview2settings.md) ** settings)

#### get_Source 

The URI of the current top level document.

> public HRESULT [get_Source](#get_source)(LPWSTR * uri)

This value potentially changes as a part of the `SourceChanged` event that runs for some cases such as navigating to a different site or fragment navigations. It remains the same for other types of navigations such as page refreshes or `history.pushState` with the same URL as the current page.

```cpp
    // Register a handler for the SourceChanged event.
    // This handler will read the webview's source URI and update
    // the app's address bar.
    CHECK_FAILURE(m_webView->add_SourceChanged(
        Callback<ICoreWebView2SourceChangedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2SourceChangedEventArgs* args)
                -> HRESULT {
                wil::unique_cotaskmem_string uri;
                sender->get_Source(&uri);
                if (wcscmp(uri.get(), L"about:blank") == 0)
                {
                    uri = wil::make_cotaskmem_string(L"");
                }
                SetWindowText(GetAddressBar(), uri.get());

                return S_OK;
            })
            .Get(),
        &m_sourceChangedToken));
```

#### GetDevToolsProtocolEventReceiver 

Get a DevTools Protocol event receiver that allows you to subscribe to a DevTools Protocol event.

> public HRESULT [GetDevToolsProtocolEventReceiver](#getdevtoolsprotocoleventreceiver)(LPCWSTR eventName, ICoreWebView2DevToolsProtocolEventReceiver ** receiver)

The `eventName` parameter is the full name of the event in the format `{domain}.{event}`. For more information about DevTools Protocol events description and event args, navigate to [DevTools Protocol Viewer][GithubChromedevtoolsDevtoolsProtocolTot].

```cpp
// Prompt the user to name a CDP event, and then subscribe to that event.
void ScriptComponent::SubscribeToCdpEvent()
{
    TextInputDialog dialog(
        m_appWindow->GetMainWindow(),
        L"Subscribe to CDP Event",
        L"CDP event name:",
        L"Enter the name of the CDP event to subscribe to.\r\n"
            L"You may also have to call the \"enable\" method of the\r\n"
            L"event's domain to receive events (for example \"Log.enable\").\r\n",
        L"Log.entryAdded");
    if (dialog.confirmed)
    {
        std::wstring eventName = dialog.input;
        wil::com_ptr<ICoreWebView2DevToolsProtocolEventReceiver> receiver;
        CHECK_FAILURE(
            m_webView->GetDevToolsProtocolEventReceiver(eventName.c_str(), &receiver));

        // If we are already subscribed to this event, unsubscribe first.
        auto preexistingToken = m_devToolsProtocolEventReceivedTokenMap.find(eventName);
        if (preexistingToken != m_devToolsProtocolEventReceivedTokenMap.end())
        {
            CHECK_FAILURE(receiver->remove_DevToolsProtocolEventReceived(
                preexistingToken->second));
        }

        CHECK_FAILURE(receiver->add_DevToolsProtocolEventReceived(
            Callback<ICoreWebView2DevToolsProtocolEventReceivedEventHandler>(
                [eventName](
                    ICoreWebView2* sender,
                    ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args) -> HRESULT {
                    wil::unique_cotaskmem_string parameterObjectAsJson;
                    CHECK_FAILURE(args->get_ParameterObjectAsJson(&parameterObjectAsJson));
                    MessageBox(
                        nullptr, parameterObjectAsJson.get(),
                        (L"CDP Event Fired: " + eventName).c_str(), MB_OK);
                    return S_OK;
                })
                .Get(),
            &m_devToolsProtocolEventReceivedTokenMap[eventName]));
    }
}
```

[GithubChromedevtoolsDevtoolsProtocolTot]: [https://chromedevtools.github.io/devtools-protocol/tot](https://chromedevtools.github.io/devtools-protocol/tot) "latest (tip-of-tree) protocol - Chrome DevTools Protocol | GitHub"

#### GoBack 

Navigates the WebView to the previous page in the navigation history.

> public HRESULT [GoBack](#goback)()

#### GoForward 

Navigates the WebView to the next page in the navigation history.

> public HRESULT [GoForward](#goforward)()

#### Navigate 

Cause a navigation of the top-level document to run to the specified URI.

> public HRESULT [Navigate](#navigate)(LPCWSTR uri)

For more information, navigate to [Navigation events][MicrosoftEdgeWebview2ConceptsNavigationevents].

[MicrosoftEdgeWebview2ConceptsNavigationevents]: /microsoft-edge/webview2/concepts/navigation-events "Navigation events | Microsoft Docs"

> [!NOTE] This operation starts a navigation and the corresponding `NavigationStarting` event triggers sometime after `Navigate` runs.

```cpp
void ControlComponent::NavigateToAddressBar()
{
    int length = GetWindowTextLength(GetAddressBar());
    std::wstring uri(length, 0);
    PWSTR buffer = const_cast<PWSTR>(uri.data());
    GetWindowText(GetAddressBar(), buffer, length + 1);

    HRESULT hr = m_webView->Navigate(uri.c_str());
    if (hr == E_INVALIDARG)
    {
        // An invalid URI was provided.
        if (uri.find(L' ') == std::wstring::npos
            && uri.find(L'.') != std::wstring::npos)
        {
            // If it contains a dot and no spaces, try tacking http:// on the front.
            hr = m_webView->Navigate((L"http://" + uri).c_str());
        }
        else
        {
            // Otherwise treat it as a web search. We aren't bothering to escape
            // URL syntax characters such as & and #
            hr = m_webView->Navigate((L"https://bing.com/search?q=" + uri).c_str());
        }
    }
    if (hr != E_INVALIDARG) {
        CHECK_FAILURE(hr);
    }
}
```

#### NavigateToString 

Initiates a navigation to htmlContent as source HTML of a new document.

> public HRESULT [NavigateToString](#navigatetostring)(LPCWSTR htmlContent)

The `htmlContent` parameter may not be larger than 2 MB in total size. The origin of the new page is `about:blank`.

```cpp
            static const PCWSTR htmlContent =
              L"<h1>Domain Blocked</h1>"
              L"<p>You've attempted to navigate to a domain in the blocked "
              L"sites list. Press back to return to the previous page.</p>";
            CHECK_FAILURE(sender->NavigateToString(htmlContent));
```

#### OpenDevToolsWindow 

Opens the DevTools window for the current document in the WebView.

> public HRESULT [OpenDevToolsWindow](#opendevtoolswindow)()

Does nothing if run when the DevTools window is already open.

#### PostWebMessageAsJson 

Post the specified webMessage to the top level document in this WebView.

> public HRESULT [PostWebMessageAsJson](#postwebmessageasjson)(LPCWSTR webMessageAsJson)

Runs the message event of the `window.chrome.webview` of the top-level document. JavaScript in that document may subscribe and unsubscribe to the event using the following code.

```cpp
window.chrome.webview.addEventListener('message', handler)
window.chrome.webview.removeEventListener('message', handler)
```

The event args is an instance of `MessageEvent`. The `ICoreWebView2Settings::IsWebMessageEnabled` setting must be `TRUE` or this method fails with `E_INVALIDARG`. The `data` property of the event arg is the `webMessage` string parameter parsed as a JSON string into a JavaScript object. The `source` property of the event arg is a reference to the `window.chrome.webview` object. For information about sending messages from the HTML document in the WebView to the host, navigate to [add_WebMessageReceived]. The message is sent asynchronously. If a navigation occurs before the message is posted to the page, the message is not sent.

```cpp
    // Setup the web message received event handler before navigating to
    // ensure we don't miss any messages.
    CHECK_FAILURE(m_webView->add_WebMessageReceived(
        Microsoft::WRL::Callback<ICoreWebView2WebMessageReceivedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2WebMessageReceivedEventArgs* args)
    {
        wil::unique_cotaskmem_string uri;
        CHECK_FAILURE(args->get_Source(&uri));

        // Always validate that the origin of the message is what you expect.
        if (uri.get() != m_sampleUri)
        {
            return S_OK;
        }
        wil::unique_cotaskmem_string messageRaw;
        CHECK_FAILURE(args->TryGetWebMessageAsString(&messageRaw));
        std::wstring message = messageRaw.get();

        if (message.compare(0, 13, L"SetTitleText ") == 0)
        {
            m_appWindow->SetTitleText(message.substr(13).c_str());
        }
        else if (message.compare(L"GetWindowBounds") == 0)
        {
            RECT bounds = m_appWindow->GetWindowBounds();
            std::wstring reply =
                L"{\"WindowBounds\":\"Left:" + std::to_wstring(bounds.left)
                + L"\\nTop:" + std::to_wstring(bounds.top)
                + L"\\nRight:" + std::to_wstring(bounds.right)
                + L"\\nBottom:" + std::to_wstring(bounds.bottom)
                + L"\"}";
            CHECK_FAILURE(sender->PostWebMessageAsJson(reply.c_str()));
        }
        return S_OK;
    }).Get(), &m_webMessageReceivedToken));
```

#### PostWebMessageAsString 

Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.

> public HRESULT [PostWebMessageAsString](#postwebmessageasstring)(LPCWSTR webMessageAsString)

This behaves in exactly the same manner as `PostWebMessageAsJson`, but the `data` property of the event arg of the `window.chrome.webview` message is a string with the same value as `webMessageAsString`. Use this instead of `PostWebMessageAsJson` if you want to communicate using simple strings rather than JSON objects.

#### Reload 

Reload the current page.

> public HRESULT [Reload](#reload)()

This is similar to navigating to the URI of current top level document including all navigation events firing and respecting any entries in the HTTP cache. But, the back or forward history are not modified.

#### remove_ContainsFullScreenElementChanged 

Remove an event handler previously added with `add_ContainsFullScreenElementChanged`.

> public HRESULT [remove_ContainsFullScreenElementChanged](#remove_containsfullscreenelementchanged)(EventRegistrationToken token)

#### remove_ContentLoading 

Remove an event handler previously added with `add_ContentLoading`.

> public HRESULT [remove_ContentLoading](#remove_contentloading)(EventRegistrationToken token)

#### remove_DocumentTitleChanged 

Remove an event handler previously added with `add_DocumentTitleChanged`.

> public HRESULT [remove_DocumentTitleChanged](#remove_documenttitlechanged)(EventRegistrationToken token)

#### remove_FrameNavigationCompleted 

Remove an event handler previously added with `add_FrameNavigationCompleted`.

> public HRESULT [remove_FrameNavigationCompleted](#remove_framenavigationcompleted)(EventRegistrationToken token)

#### remove_FrameNavigationStarting 

Remove an event handler previously added with `add_FrameNavigationStarting`.

> public HRESULT [remove_FrameNavigationStarting](#remove_framenavigationstarting)(EventRegistrationToken token)

#### remove_HistoryChanged 

Remove an event handler previously added with `add_HistoryChanged`.

> public HRESULT [remove_HistoryChanged](#remove_historychanged)(EventRegistrationToken token)

#### remove_NavigationCompleted 

Remove an event handler previously added with `add_NavigationCompleted`.

> public HRESULT [remove_NavigationCompleted](#remove_navigationcompleted)(EventRegistrationToken token)

#### remove_NavigationStarting 

Remove an event handler previously added with `add_NavigationStarting`.

> public HRESULT [remove_NavigationStarting](#remove_navigationstarting)(EventRegistrationToken token)

#### remove_NewWindowRequested 

Remove an event handler previously added with `add_NewWindowRequested`.

> public HRESULT [remove_NewWindowRequested](#remove_newwindowrequested)(EventRegistrationToken token)

#### remove_PermissionRequested 

Remove an event handler previously added with `add_PermissionRequested`.

> public HRESULT [remove_PermissionRequested](#remove_permissionrequested)(EventRegistrationToken token)

#### remove_ProcessFailed 

Remove an event handler previously added with add_ProcessFailed.

> public HRESULT [remove_ProcessFailed](#remove_processfailed)(EventRegistrationToken token)

#### remove_ScriptDialogOpening 

Remove an event handler previously added with `add_ScriptDialogOpening`.

> public HRESULT [remove_ScriptDialogOpening](#remove_scriptdialogopening)(EventRegistrationToken token)

#### remove_SourceChanged 

Remove an event handler previously added with `add_SourceChanged`.

> public HRESULT [remove_SourceChanged](#remove_sourcechanged)(EventRegistrationToken token)

#### remove_WebMessageReceived 

Remove an event handler previously added with `add_WebMessageReceived`.

> public HRESULT [remove_WebMessageReceived](#remove_webmessagereceived)(EventRegistrationToken token)

#### remove_WebResourceRequested 

Remove an event handler previously added with `add_WebResourceRequested`.

> public HRESULT [remove_WebResourceRequested](#remove_webresourcerequested)(EventRegistrationToken token)

#### remove_WindowCloseRequested 

Remove an event handler previously added with `add_WindowCloseRequested`.

> public HRESULT [remove_WindowCloseRequested](#remove_windowcloserequested)(EventRegistrationToken token)

#### RemoveHostObjectFromScript 

Remove the host object specified by the name so that it is no longer accessible from JavaScript code in the WebView.

> public HRESULT [RemoveHostObjectFromScript](#removehostobjectfromscript)(LPCWSTR name)

While new access attempts are denied, if the object is already obtained by JavaScript code in the WebView, the JavaScript code continues to have access to that object. Run this method for a name that is already removed or never added fails.

#### RemoveScriptToExecuteOnDocumentCreated 

Remove the corresponding JavaScript added using `AddScriptToExecuteOnDocumentCreated` with the specified script ID.

> public HRESULT [RemoveScriptToExecuteOnDocumentCreated](#removescripttoexecuteondocumentcreated)(LPCWSTR id)

#### RemoveWebResourceRequestedFilter 

Removes a matching WebResource filter that was previously added for the `WebResourceRequested` event.

> public HRESULT [RemoveWebResourceRequestedFilter](#removewebresourcerequestedfilter)(LPCWSTR const uri, [COREWEBVIEW2_WEB_RESOURCE_CONTEXT](#corewebview2_web_resource_context) const resourceContext)

If the same filter was added multiple times, then it must be removed as many times as it was added for the removal to be effective. Returns `E_INVALIDARG` for a filter that was never added.

#### Stop 

Stop all navigations and pending resource fetches. Does not stop scripts.

> public HRESULT [Stop](#stop)()

#### COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT 

Specifies the image format for the `[ICoreWebView2::CapturePreview](#capturepreview)` method.

> enum [COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT](#corewebview2_capture_preview_image_format)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT_PNG            | Indicates that the PNG image format is used.
COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT_JPEG            | Indicates the JPEG image format is used.

#### COREWEBVIEW2_COOKIE_SAME_SITE_KIND 

Kind of cookie SameSite status used in the [ICoreWebView2Cookie](icorewebview2cookie.md) interface.

> enum [COREWEBVIEW2_COOKIE_SAME_SITE_KIND](#corewebview2_cookie_same_site_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_COOKIE_SAME_SITE_KIND_NONE            | None SameSite type. No restrictions on cross-site requests.
COREWEBVIEW2_COOKIE_SAME_SITE_KIND_LAX            | Lax SameSite type. The cookie will be sent with "same-site" requests, and with "cross-site" top level navigation.
COREWEBVIEW2_COOKIE_SAME_SITE_KIND_STRICT            | Strict SameSite type. The cookie will only be sent along with "same-site" requests.

These fields match those as specified in [https://developer.mozilla.org/docs/Web/HTTP/Cookies#](https://developer.mozilla.org/docs/Web/HTTP/Cookies#). Learn more about SameSite cookies here: [https://tools.ietf.org/html/draft-west-first-party-cookies-07](https://tools.ietf.org/html/draft-west-first-party-cookies-07)

#### COREWEBVIEW2_KEY_EVENT_KIND 

Specifies the key event type that triggered an `AcceleratorKeyPressed` event.

> enum [COREWEBVIEW2_KEY_EVENT_KIND](#corewebview2_key_event_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_KEY_EVENT_KIND_KEY_DOWN            | Specifies that the key event type corresponds to window message `WM_KEYDOWN`.
COREWEBVIEW2_KEY_EVENT_KIND_KEY_UP            | Specifies that the key event type corresponds to window message `WM_KEYUP`.
COREWEBVIEW2_KEY_EVENT_KIND_SYSTEM_KEY_DOWN            | Specifies that the key event type corresponds to window message `WM_SYSKEYDOWN`.
COREWEBVIEW2_KEY_EVENT_KIND_SYSTEM_KEY_UP            | Specifies that the key event type corresponds to window message `WM_SYSKEYUP`.

#### COREWEBVIEW2_MOVE_FOCUS_REASON 

Specifies the reason for moving focus.

> enum [COREWEBVIEW2_MOVE_FOCUS_REASON](#corewebview2_move_focus_reason)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MOVE_FOCUS_REASON_PROGRAMMATIC            | Specifies that the code is setting focus into WebView.
COREWEBVIEW2_MOVE_FOCUS_REASON_NEXT            | Specifies that the focus is moving due to Tab traversal forward.
COREWEBVIEW2_MOVE_FOCUS_REASON_PREVIOUS            | Specifies that the focus is moving due to Tab traversal backward.

#### COREWEBVIEW2_PERMISSION_KIND 

Indicates the type of a permission request.

> enum [COREWEBVIEW2_PERMISSION_KIND](#corewebview2_permission_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PERMISSION_KIND_UNKNOWN_PERMISSION            | Indicates an unknown permission.
COREWEBVIEW2_PERMISSION_KIND_MICROPHONE            | Indicates permission to capture audio.
COREWEBVIEW2_PERMISSION_KIND_CAMERA            | Indicates permission to capture video.
COREWEBVIEW2_PERMISSION_KIND_GEOLOCATION            | Indicates permission to access geolocation.
COREWEBVIEW2_PERMISSION_KIND_NOTIFICATIONS            | Indicates permission to send web notifications.
COREWEBVIEW2_PERMISSION_KIND_OTHER_SENSORS            | Indicates permission to access generic sensor.
COREWEBVIEW2_PERMISSION_KIND_CLIPBOARD_READ            | Indicates permission to read the system clipboard without a user gesture.

#### COREWEBVIEW2_PERMISSION_STATE 

Specifies the response to a permission request.

> enum [COREWEBVIEW2_PERMISSION_STATE](#corewebview2_permission_state)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PERMISSION_STATE_DEFAULT            | Specifies that the default browser behavior is used, which normally prompt users for decision.
COREWEBVIEW2_PERMISSION_STATE_ALLOW            | Specifies that the permission request is granted.
COREWEBVIEW2_PERMISSION_STATE_DENY            | Specifies that the permission request is denied.

#### COREWEBVIEW2_PHYSICAL_KEY_STATUS 

Contains the information packed into the `LPARAM` sent to a Win32 key event.

> typedef [COREWEBVIEW2_PHYSICAL_KEY_STATUS](#corewebview2_physical_key_status)

For more information about `WM_KEYDOWN`, navigate to [WM_KEYDOWN message][WindowsWin32InputdevWmKeydown].

[WindowsWin32InputdevWmKeydown]: /windows/win32/inputdev/wm-keydown "WM_KEYDOWN message | Microsoft Docs"

#### COREWEBVIEW2_PROCESS_FAILED_KIND 

Specifies the process failure type used in the `ICoreWebView2ProcessFailedEventHandler` interface.

> enum [COREWEBVIEW2_PROCESS_FAILED_KIND](#corewebview2_process_failed_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PROCESS_FAILED_KIND_BROWSER_PROCESS_EXITED            | Indicates that the browser process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_EXITED            | Indicates that the render process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_UNRESPONSIVE            | Indicates that the render process is unresponsive.

#### COREWEBVIEW2_SCRIPT_DIALOG_KIND 

Specifies the JavaScript dialog type used in the `ICoreWebView2ScriptDialogOpeningEventHandler` interface.

> enum [COREWEBVIEW2_SCRIPT_DIALOG_KIND](#corewebview2_script_dialog_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SCRIPT_DIALOG_KIND_ALERT            | Indicates that the dialog uses the `window.alert` JavaScript function.
COREWEBVIEW2_SCRIPT_DIALOG_KIND_CONFIRM            | Indicates that the dialog uses the `window.confirm` JavaScript function.
COREWEBVIEW2_SCRIPT_DIALOG_KIND_PROMPT            | Indicates that the dialog uses the `window.prompt` JavaScript function.
COREWEBVIEW2_SCRIPT_DIALOG_KIND_BEFOREUNLOAD            | Indicates that the dialog uses the `beforeunload` JavaScript event.

#### COREWEBVIEW2_WEB_ERROR_STATUS 

Indicates the error status values for web navigations.

> enum [COREWEBVIEW2_WEB_ERROR_STATUS](#corewebview2_web_error_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_WEB_ERROR_STATUS_UNKNOWN            | Indicates that an unknown error occurred.
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_COMMON_NAME_IS_INCORRECT            | Indicates that the SSL certificate common name does not match the web address.
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_EXPIRED            | Indicates that the SSL certificate has expired.
COREWEBVIEW2_WEB_ERROR_STATUS_CLIENT_CERTIFICATE_CONTAINS_ERRORS            | Indicates that the SSL client certificate contains errors.
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_REVOKED            | Indicates that the SSL certificate has been revoked.
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_IS_INVALID            | Indicates that the SSL certificate is not valid.
COREWEBVIEW2_WEB_ERROR_STATUS_SERVER_UNREACHABLE            | Indicates that the host is unreachable.
COREWEBVIEW2_WEB_ERROR_STATUS_TIMEOUT            | Indicates that the connection has timed out.
COREWEBVIEW2_WEB_ERROR_STATUS_ERROR_HTTP_INVALID_SERVER_RESPONSE            | Indicates that the server returned an invalid or unrecognized response.
COREWEBVIEW2_WEB_ERROR_STATUS_CONNECTION_ABORTED            | Indicates that the connection was stopped.
COREWEBVIEW2_WEB_ERROR_STATUS_CONNECTION_RESET            | Indicates that the connection was reset.
COREWEBVIEW2_WEB_ERROR_STATUS_DISCONNECTED            | Indicates that the Internet connection has been lost.
COREWEBVIEW2_WEB_ERROR_STATUS_CANNOT_CONNECT            | Indicates that a connection to the destination was not established.
COREWEBVIEW2_WEB_ERROR_STATUS_HOST_NAME_NOT_RESOLVED            | Indicates that the provided host name was not able to be resolved.
COREWEBVIEW2_WEB_ERROR_STATUS_OPERATION_CANCELED            | Indicates that the operation was canceled.
COREWEBVIEW2_WEB_ERROR_STATUS_REDIRECT_FAILED            | Indicates that the request redirect failed.
COREWEBVIEW2_WEB_ERROR_STATUS_UNEXPECTED_ERROR            | Indicates that an unexpected error occurred.

#### COREWEBVIEW2_WEB_RESOURCE_CONTEXT 

Specifies the web resource request contexts.

> enum [COREWEBVIEW2_WEB_RESOURCE_CONTEXT](#corewebview2_web_resource_context)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_ALL            | Specifies all resources.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_DOCUMENT            | Specifies a document resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_STYLESHEET            | Specifies a CSS resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE            | Specifies an image resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_MEDIA            | Specifies another media resource such as a video.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_FONT            | Specifies a font resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_SCRIPT            | Specifies a script resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_XML_HTTP_REQUEST            | Specifies an XML HTTP request.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_FETCH            | Specifies a Fetch API communication.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_TEXT_TRACK            | Specifies a TextTrack resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_EVENT_SOURCE            | Specifies an EventSource API communication.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_WEBSOCKET            | Specifies a WebSocket API communication.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_MANIFEST            | Specifies a Web App Manifest.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_SIGNED_EXCHANGE            | Specifies a Signed HTTP Exchange.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_PING            | Specifies a Ping request.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_CSP_VIOLATION_REPORT            | Specifies a CSP Violation Report.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_OTHER            | Specifies an other resource.

