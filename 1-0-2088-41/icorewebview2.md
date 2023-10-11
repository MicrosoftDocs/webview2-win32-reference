---
description: WebView2 enables you to host web content using the latest Microsoft Edge browser and web technology.
title: WebView2 Win32 C++ ICoreWebView2
ms.date: 10/16/2023
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
[AddWebResourceRequestedFilter](#addwebresourcerequestedfilter) | Adds a URI and resource context filter for the `WebResourceRequested` event.
[CallDevToolsProtocolMethod](#calldevtoolsprotocolmethod) | Runs an asynchronous `DevToolsProtocol` method.
[CapturePreview](#capturepreview) | Capture an image of what WebView is displaying.
[ExecuteScript](#executescript) | Run JavaScript code from the javascript parameter in the current top-level document rendered in the WebView.
[get_BrowserProcessId](#get_browserprocessid) | The process ID of the browser process that hosts the WebView.
[get_CanGoBack](#get_cangoback) | `TRUE` if the WebView is able to navigate to a previous page in the navigation history.
[get_CanGoForward](#get_cangoforward) | `TRUE` if the WebView is able to navigate to a next page in the navigation history.
[get_ContainsFullScreenElement](#get_containsfullscreenelement) | Indicates if the WebView contains a fullscreen HTML element.
[get_DocumentTitle](#get_documenttitle) | The title for the current top-level document.
[get_Settings](#get_settings) | The ICoreWebView2Settings object contains various modifiable settings for the running WebView.
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
[remove_ProcessFailed](#remove_processfailed) | Remove an event handler previously added with `add_ProcessFailed`.
[remove_ScriptDialogOpening](#remove_scriptdialogopening) | Remove an event handler previously added with `add_ScriptDialogOpening`.
[remove_SourceChanged](#remove_sourcechanged) | Remove an event handler previously added with `add_SourceChanged`.
[remove_WebMessageReceived](#remove_webmessagereceived) | Remove an event handler previously added with `add_WebMessageReceived`.
[remove_WebResourceRequested](#remove_webresourcerequested) | Remove an event handler previously added with `add_WebResourceRequested`.
[remove_WindowCloseRequested](#remove_windowcloserequested) | Remove an event handler previously added with `add_WindowCloseRequested`.
[RemoveHostObjectFromScript](#removehostobjectfromscript) | Remove the host object specified by the name so that it is no longer accessible from JavaScript code in the WebView.
[RemoveScriptToExecuteOnDocumentCreated](#removescripttoexecuteondocumentcreated) | Remove the corresponding JavaScript added using `AddScriptToExecuteOnDocumentCreated` with the specified script ID.
[RemoveWebResourceRequestedFilter](#removewebresourcerequestedfilter) | Removes a matching WebResource filter that was previously added for the `WebResourceRequested` event.
[Stop](#stop) | Stop all navigations and pending resource fetches. Does not stop scripts.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### add_ContainsFullScreenElementChanged

Add an event handler for the `ContainsFullScreenElementChanged` event.

> public HRESULT [add_ContainsFullScreenElementChanged](#add_containsfullscreenelementchanged)([ICoreWebView2ContainsFullScreenElementChangedEventHandler](icorewebview2containsfullscreenelementchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ContainsFullScreenElementChanged` triggers when the `ContainsFullScreenElement` property changes. An HTML element inside the WebView may enter fullscreen to the size of the WebView or leave fullscreen. This event is useful when, for example, a video element requests to go fullscreen. The listener of `ContainsFullScreenElementChanged` may resize the WebView in response.

```cpp
    // Register a handler for the ContainsFullScreenChanged event.
    CHECK_FAILURE(m_webView->add_ContainsFullScreenElementChanged(
        Callback<ICoreWebView2ContainsFullScreenElementChangedEventHandler>(
            [this](ICoreWebView2* sender, IUnknown* args) -> HRESULT
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
                m_appWindow->SetDocumentTitle(title.get());
                return S_OK;
            })
            .Get(),
        &m_documentTitleChangedToken));
```

#### add_FrameNavigationCompleted

Add an event handler for the `FrameNavigationCompleted` event.

> public HRESULT [add_FrameNavigationCompleted](#add_framenavigationcompleted)([ICoreWebView2NavigationCompletedEventHandler](icorewebview2navigationcompletedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`FrameNavigationCompleted` triggers when a child frame has completely loaded (concurrently when `body.onload` has triggered) or loading stopped with error.

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
                    // The web page can cancel its own iframe loads, so we'll ignore that.
                    if (webErrorStatus != COREWEBVIEW2_WEB_ERROR_STATUS_OPERATION_CANCELED)
                    {
                        m_appWindow->AsyncMessageBox(
                            L"Iframe navigation failed: "
                                + WebErrorStatusToString(webErrorStatus),
                            L"Navigation Failure");
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

`FrameNavigationStarting` triggers when a child frame in the WebView requests permission to navigate to a different URI. Redirects trigger this operation as well, and the navigation id is the same as the original one.

Navigations will be blocked until all `FrameNavigationStarting` event handlers return.

```cpp
    // Register a handler for the FrameNavigationStarting event.
    // This handler will prevent a frame from navigating to a blocked domain.
    CHECK_FAILURE(m_webView->add_FrameNavigationStarting(
        Callback<ICoreWebView2NavigationStartingEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2NavigationStartingEventArgs* args)
                -> HRESULT {
                wil::unique_cotaskmem_string uri;
                CHECK_FAILURE(args->get_Uri(&uri));

                if (ShouldBlockUri(uri.get()))
                {
                    CHECK_FAILURE(args->put_Cancel(true));
                }
                return S_OK;
            })
            .Get(),
        &m_frameNavigationStartingToken));
```

#### add_HistoryChanged

Add an event handler for the `HistoryChanged` event.

> public HRESULT [add_HistoryChanged](#add_historychanged)([ICoreWebView2HistoryChangedEventHandler](icorewebview2historychangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`HistoryChanged` is raised for changes to joint session history, which consists of top-level and manual frame navigations. Use `HistoryChanged` to verify that the `CanGoBack` or `CanGoForward` value has changed. `HistoryChanged` also runs for using `GoBack` or `GoForward`. `HistoryChanged` runs after `SourceChanged` and `ContentLoading`. `CanGoBack` is false for navigations initiated through [ICoreWebView2Frame](icorewebview2frame.md) APIs if there has not yet been a user gesture.

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

`NavigationCompleted` runs when the WebView has completely loaded (concurrently when `body.onload` runs) or loading stopped with error.

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

`NavigationStarting` runs when the WebView main frame is requesting permission to navigate to a different URI. Redirects trigger this operation as well, and the navigation id is the same as the original one.

Navigations will be blocked until all `NavigationStarting` event handlers return.

```cpp
    // Register a handler for the NavigationStarting event.
    // This handler will check the domain being navigated to, and if the domain
    // matches a list of blocked sites, it will cancel the navigation and
    // possibly display a warning page.  It will also disable JavaScript on
    // selected websites.
    CHECK_FAILURE(m_webView->add_NavigationStarting(
        Callback<ICoreWebView2NavigationStartingEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2NavigationStartingEventArgs* args)
                -> HRESULT {
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
                if (m_settings2)
                {
                    static const PCWSTR url_compare_example = L"fourthcoffee.com";
                    wil::unique_bstr domain = GetDomainOfUri(uri.get());
                    const wchar_t* domains = domain.get();

                    if (wcscmp(url_compare_example, domains) == 0)
                    {
                        SetUserAgent(L"example_navigation_ua");
                    }
                }
                // [NavigationKind]
                wil::com_ptr<ICoreWebView2NavigationStartingEventArgs3> args3;
                if (SUCCEEDED(args->QueryInterface(IID_PPV_ARGS(&args3))))
                {
                    COREWEBVIEW2_NAVIGATION_KIND kind =
                        COREWEBVIEW2_NAVIGATION_KIND_NEW_DOCUMENT;
                    CHECK_FAILURE(args3->get_NavigationKind(&kind));
                }
                // ! [NavigationKind]
                return S_OK;
            })
            .Get(),
        &m_navigationStartingToken));
```

#### add_NewWindowRequested

Add an event handler for the `NewWindowRequested` event.

> public HRESULT [add_NewWindowRequested](#add_newwindowrequested)([ICoreWebView2NewWindowRequestedEventHandler](icorewebview2newwindowrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`NewWindowRequested` runs when content inside the WebView requests to open a new window, such as through `window.open`. The app can pass a target WebView that is considered the opened window or mark the event as `Handled`, in which case WebView2 does not open a window. If either `Handled` or `NewWindow` properties are not set, the target content will be opened on a popup window.

If a deferral is not taken on the event args, scripts that resulted in the new window that are requested are blocked until the event handler returns. If a deferral is taken, then scripts are blocked until the deferral is completed or new window is set.

For more details and considerations on the target WebView to be supplied at the opened window, see [ICoreWebView2NewWindowRequestedEventArgs::put_NewWindow](icorewebview2newwindowrequestedeventargs.md).

```cpp
    // Register a handler for the NewWindowRequested event.
    // This handler will defer the event, create a new app window, and then once the
    // new window is ready, it'll provide that new window's WebView as the response to
    // the request.
    CHECK_FAILURE(m_webView->add_NewWindowRequested(
        Callback<ICoreWebView2NewWindowRequestedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2NewWindowRequestedEventArgs* args)
            {
                if (!m_shouldHandleNewWindowRequest)
                {
                    args->put_Handled(FALSE);
                    return S_OK;
                }
                wil::com_ptr<ICoreWebView2ExperimentalNewWindowRequestedEventArgs2>
                    experimental_args;
                if (SUCCEEDED(args->QueryInterface(IID_PPV_ARGS(&experimental_args))))
                {
                    wil::com_ptr<ICoreWebView2FrameInfo> frame_info;
                    CHECK_FAILURE(experimental_args->get_OriginalSourceFrameInfo(&frame_info));
                    wil::unique_cotaskmem_string source;
                    CHECK_FAILURE(frame_info->get_Source(&source));
                    // The host can decide how to open based on source frame info,
                    // such as URI.
                    static const wchar_t* browser_launching_domain = L"www.example.com";
                    wil::unique_bstr source_domain = GetDomainOfUri(source.get());
                    const wchar_t* source_domain_as_wchar = source_domain.get();
                    if (wcscmp(browser_launching_domain, source_domain_as_wchar) == 0)
                    {
                        // Open the URI in the default browser.
                        wil::unique_cotaskmem_string target_uri;
                        CHECK_FAILURE(args->get_Uri(&target_uri));
                        ShellExecute(
                            nullptr, L"open", target_uri.get(), nullptr, nullptr,
                            SW_SHOWNORMAL);
                        CHECK_FAILURE(args->put_Handled(TRUE));
                        return S_OK;
                    }
                }

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
                windowRect.right =
                    left + (width < s_minNewWindowSize ? s_minNewWindowSize : width);
                windowRect.top = top;
                windowRect.bottom =
                    top + (height < s_minNewWindowSize ? s_minNewWindowSize : height);

                // passing "none" as uri as its a noinitialnavigation
                if (!useDefaultWindow)
                {
                    newAppWindow = new AppWindow(
                        m_creationModeId, GetWebViewOption(), L"none", m_userDataFolder, false,
                        nullptr, true, windowRect, !!shouldHaveToolbar);
                }
                else
                {
                    newAppWindow = new AppWindow(m_creationModeId, GetWebViewOption(), L"none");
                }
                newAppWindow->m_isPopupWindow = true;
                newAppWindow->m_onWebViewFirstInitialized = [args, deferral, newAppWindow]()
                {
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
    // This handler prompts the user to allow or deny the request, and remembers
    // the user's choice for later.
    CHECK_FAILURE(m_webView->add_PermissionRequested(
        Callback<ICoreWebView2PermissionRequestedEventHandler>(
            this, &SettingsComponent::OnPermissionRequested)
            .Get(),
        &m_permissionRequestedToken));
```

```cpp
HRESULT SettingsComponent::OnPermissionRequested(
    ICoreWebView2* sender, ICoreWebView2PermissionRequestedEventArgs* args)
{
    // Obtain a deferral for the event so that the CoreWebView2
    // doesn't examine the properties we set on the event args until
    // after we call the Complete method asynchronously later.
    wil::com_ptr<ICoreWebView2Deferral> deferral;
    CHECK_FAILURE(args->GetDeferral(&deferral));

    // Do not save state to the profile so that the PermissionRequested event is
    // always raised and the app is in control of all permission requests. In
    // this example, the app listens to all requests and caches permission on
    // its own to decide whether to show custom UI to the user.
    wil::com_ptr<ICoreWebView2PermissionRequestedEventArgs3> extended_args;
    CHECK_FAILURE(args->QueryInterface(IID_PPV_ARGS(&extended_args)));
    CHECK_FAILURE(extended_args->put_SavesInProfile(FALSE));

    // Do the rest asynchronously, to avoid calling MessageBox in an event handler.
    m_appWindow->RunAsync(
        [this, deferral, args = wil::com_ptr<ICoreWebView2PermissionRequestedEventArgs>(args)]
        {
            wil::unique_cotaskmem_string uri;
            COREWEBVIEW2_PERMISSION_KIND kind = COREWEBVIEW2_PERMISSION_KIND_UNKNOWN_PERMISSION;
            BOOL userInitiated = FALSE;
            CHECK_FAILURE(args->get_Uri(&uri));
            CHECK_FAILURE(args->get_PermissionKind(&kind));
            CHECK_FAILURE(args->get_IsUserInitiated(&userInitiated));

            COREWEBVIEW2_PERMISSION_STATE state = COREWEBVIEW2_PERMISSION_STATE_DEFAULT;

            auto cached_key = std::make_tuple(std::wstring(uri.get()), kind, userInitiated);
            auto cached_permission = m_cached_permissions.find(cached_key);
            if (cached_permission != m_cached_permissions.end())
            {
                state =
                    (cached_permission->second ? COREWEBVIEW2_PERMISSION_STATE_ALLOW
                                               : COREWEBVIEW2_PERMISSION_STATE_DENY);
            }
            else
            {
                std::wstring message = L"An iframe has requested device permission for ";
                message += PermissionKindToString(kind);
                message += L" to the website at ";
                message += uri.get();
                message += L"?\n\n";
                message += L"Do you want to grant permission?\n";
                message +=
                    (userInitiated ? L"This request came from a user gesture."
                                   : L"This request did not come from a user gesture.");

                int response = MessageBox(
                    nullptr, message.c_str(), L"Permission Request",
                    MB_YESNOCANCEL | MB_ICONWARNING);
                switch (response)
                {
                case IDYES:
                    m_cached_permissions[cached_key] = true;
                    state = COREWEBVIEW2_PERMISSION_STATE_ALLOW;
                    break;
                case IDNO:
                    m_cached_permissions[cached_key] = false;
                    state = COREWEBVIEW2_PERMISSION_STATE_DENY;
                    break;
                default:
                    state = COREWEBVIEW2_PERMISSION_STATE_DEFAULT;
                    break;
                }
            }
            CHECK_FAILURE(args->put_State(state));
            CHECK_FAILURE(deferral->Complete());
        });
    return S_OK;
}
```

#### add_ProcessFailed

Add an event handler for the `ProcessFailed` event.

> public HRESULT [add_ProcessFailed](#add_processfailed)([ICoreWebView2ProcessFailedEventHandler](icorewebview2processfailedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ProcessFailed` runs when any of the processes in the [WebView2 Process Group](/microsoft-edge/webview2/concepts/process-model?tabs=csharp#processes-in-the-webview2-runtime) encounters one of the following conditions:

Condition   |Details
--------- | ---------
Unexpected exit   |The process indicated by the event args has exited unexpectedly (usually due to a crash). The failure might or might not be recoverable and some failures are auto-recoverable.
Unresponsiveness   |The process indicated by the event args has become unresponsive to user input. This is only reported for renderer processes, and will run every few seconds until the process becomes responsive again.

> [!NOTE]
> When the failing process is the browser process, a `ICoreWebView2Environment5::BrowserProcessExited` event will run too.

Your application can use ICoreWebView2ProcessFailedEventArgs and ICoreWebView2ProcessFailedEventArgs2 to identify which condition and process the event is for, and to collect diagnostics and handle recovery if necessary. For more details about which cases need to be handled by your application, see `COREWEBVIEW2_PROCESS_FAILED_KIND`.

```cpp
    // Register a handler for the ProcessFailed event.
    // This handler checks the failure kind and tries to:
    //   * Recreate the webview for browser failure and render unresponsive.
    //   * Reload the webview for render failure.
    //   * Reload the webview for frame-only render failure impacting app content.
    //   * Log information about the failure for other failures.
    CHECK_FAILURE(m_webView->add_ProcessFailed(
        Callback<ICoreWebView2ProcessFailedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2ProcessFailedEventArgs* argsRaw)
                -> HRESULT {
                wil::com_ptr<ICoreWebView2ProcessFailedEventArgs> args = argsRaw;
                COREWEBVIEW2_PROCESS_FAILED_KIND kind;
                CHECK_FAILURE(args->get_ProcessFailedKind(&kind));
                if (kind == COREWEBVIEW2_PROCESS_FAILED_KIND_BROWSER_PROCESS_EXITED)
                {
                    // Do not run a message loop from within the event handler
                    // as that could lead to reentrancy and leave the event
                    // handler in stack indefinitely. Instead, schedule the
                    // appropriate work to take place after completion of the
                    // event handler.
                    ScheduleReinitIfSelectedByUser(
                        L"Browser process exited unexpectedly.  Recreate webview?",
                        L"Browser process exited");
                }
                else if (kind == COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_UNRESPONSIVE)
                {
                    ScheduleReinitIfSelectedByUser(
                        L"Browser render process has stopped responding.  Recreate webview?",
                        L"Web page unresponsive");
                }
                else if (kind == COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_EXITED)
                {
                    // Reloading the page will start a new render process if
                    // needed.
                    ScheduleReloadIfSelectedByUser(
                        L"Browser render process exited unexpectedly. Reload page?",
                        L"Web page unresponsive");
                }
                // Check the runtime event args implements the newer interface.
                auto args2 = args.try_query<ICoreWebView2ProcessFailedEventArgs2>();
                if (!args2)
                {
                    return S_OK;
                }
                if (kind == COREWEBVIEW2_PROCESS_FAILED_KIND_FRAME_RENDER_PROCESS_EXITED)
                {
                    // A frame-only renderer has exited unexpectedly. Check if
                    // reload is needed.
                    wil::com_ptr<ICoreWebView2FrameInfoCollection> frameInfos;
                    wil::com_ptr<ICoreWebView2FrameInfoCollectionIterator> iterator;
                    CHECK_FAILURE(args2->get_FrameInfosForFailedProcess(&frameInfos));
                    CHECK_FAILURE(frameInfos->GetIterator(&iterator));

                    BOOL hasCurrent = FALSE;
                    while (SUCCEEDED(iterator->get_HasCurrent(&hasCurrent)) && hasCurrent)
                    {
                        wil::com_ptr<ICoreWebView2FrameInfo> frameInfo;
                        CHECK_FAILURE(iterator->GetCurrent(&frameInfo));

                        wil::unique_cotaskmem_string nameRaw;
                        wil::unique_cotaskmem_string sourceRaw;
                        CHECK_FAILURE(frameInfo->get_Name(&nameRaw));
                        CHECK_FAILURE(frameInfo->get_Source(&sourceRaw));
                        if (IsAppContentUri(sourceRaw.get()))
                        {
                            ScheduleReloadIfSelectedByUser(
                                L"Browser render process for app frame exited unexpectedly. "
                                L"Reload page?",
                                L"App content frame unresponsive");
                            break;
                        }

                        BOOL hasNext = FALSE;
                        CHECK_FAILURE(iterator->MoveNext(&hasNext));
                    }
                }
                else
                {
                    // Show the process failure details. Apps can collect info for their logging
                    // purposes.
                    COREWEBVIEW2_PROCESS_FAILED_REASON reason;
                    wil::unique_cotaskmem_string processDescription;
                    int exitCode;

                    CHECK_FAILURE(args2->get_Reason(&reason));
                    CHECK_FAILURE(args2->get_ProcessDescription(&processDescription));
                    CHECK_FAILURE(args2->get_ExitCode(&exitCode));

                    std::wstringstream message;
                    message << L"Kind: "                << ProcessFailedKindToString(kind) << L"\n"
                            << L"Reason: "              << ProcessFailedReasonToString(reason) << L"\n"
                            << L"Exit code: "           << std::to_wstring(exitCode) << L"\n"
                            << L"Process description: " << processDescription.get() << std::endl;
                    m_appWindow->AsyncMessageBox( std::move(message.str()), L"Child process failed");
                }
                return S_OK;
            })
            .Get(),
        &m_processFailedToken));
```

#### add_ScriptDialogOpening

Add an event handler for the `ScriptDialogOpening` event.

> public HRESULT [add_ScriptDialogOpening](#add_scriptdialogopening)([ICoreWebView2ScriptDialogOpeningEventHandler](icorewebview2scriptdialogopeningeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ScriptDialogOpening` runs when a JavaScript dialog (`alert`, `confirm`, `prompt`, or `beforeunload`) displays for the webview. This event only triggers if the `ICoreWebView2Settings::AreDefaultScriptDialogsEnabled` property is set to `FALSE`. The `ScriptDialogOpening` event suppresses dialogs or replaces default dialogs with custom dialogs.

If a deferral is not taken on the event args, the subsequent scripts are blocked until the event handler returns. If a deferral is taken, the scripts are blocked until the deferral is completed.

```cpp
    // Register a handler for the ScriptDialogOpening event.
    // This handler will set up a custom prompt dialog for the user.  Because
    // running a message loop inside of an event handler causes problems, we
    // defer the event and handle it asynchronously.
    CHECK_FAILURE(m_webView->add_ScriptDialogOpening(
        Callback<ICoreWebView2ScriptDialogOpeningEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2ScriptDialogOpeningEventArgs* args)
                -> HRESULT {
                AppWindow* appWindow = m_appWindow;
                wil::com_ptr<ICoreWebView2ScriptDialogOpeningEventArgs> eventArgs = args;
                wil::com_ptr<ICoreWebView2Deferral> deferral;
                CHECK_FAILURE(args->GetDeferral(&deferral));
                appWindow->RunAsync([appWindow, eventArgs, deferral] {
                    wil::unique_cotaskmem_string uri;
                    COREWEBVIEW2_SCRIPT_DIALOG_KIND type;
                    wil::unique_cotaskmem_string message;
                    wil::unique_cotaskmem_string defaultText;

                    CHECK_FAILURE(eventArgs->get_Uri(&uri));
                    CHECK_FAILURE(eventArgs->get_Kind(&type));
                    CHECK_FAILURE(eventArgs->get_Message(&message));
                    CHECK_FAILURE(eventArgs->get_DefaultText(&defaultText));

                    std::wstring promptString =
                        std::wstring(L"The page at '") + uri.get() + L"' says:";
                    TextInputDialog dialog(
                        appWindow->GetMainWindow(), L"Script Dialog", promptString.c_str(),
                        message.get(), defaultText.get(),
                        /* readonly */ type != COREWEBVIEW2_SCRIPT_DIALOG_KIND_PROMPT);
                    if (dialog.confirmed)
                    {
                        CHECK_FAILURE(eventArgs->put_ResultText(dialog.input.c_str()));
                        CHECK_FAILURE(eventArgs->Accept());
                    }
                    deferral->Complete();
                });
                return S_OK;
            })
            .Get(),
        &m_scriptDialogOpeningToken));
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

When the page calls `postMessage`, the object parameter is converted to a JSON string and is posted asynchronously to the host process. This will result in the handler's `Invoke` method being called with the JSON string as a parameter.

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
            // Ignore messages from untrusted sources.
            return S_OK;
        }
        wil::unique_cotaskmem_string messageRaw;
        HRESULT hr = args->TryGetWebMessageAsString(&messageRaw);
        if (hr == E_INVALIDARG)
        {
            // Was not a string message. Ignore.
            return S_OK;
        }
        // Any other problems are fatal.
        CHECK_FAILURE(hr);
        std::wstring message = messageRaw.get();

        if (message.compare(0, 13, L"SetTitleText ") == 0)
        {
            m_appWindow->SetDocumentTitle(message.substr(13).c_str());
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
        else
        {
            // Ignore unrecognized messages, but log for further investigation
            // since it suggests a mismatch between the web content and the host.
            OutputDebugString(
                std::wstring(L"Unexpected message from main page:" + message).c_str());
        }
        return S_OK;
    }).Get(), &m_webMessageReceivedToken));
```

If the same page calls `postMessage` multiple times, the corresponding `WebMessageReceived` events are guaranteed to be fired in the same order. However, if multiple frames call `postMessage`, there is no guaranteed order. In addition, `WebMessageReceived` events caused by calls to `postMessage` are not guaranteed to be sequenced with events caused by DOM APIs. For example, if the page runs

```js
chrome.webview.postMessage("message");
window.open();
```

then the `NewWindowRequested` event might be fired before the `WebMessageReceived` event. If you need the `WebMessageReceived` event to happen before anything else, then in the `WebMessageReceived` handler you can post a message back to the page and have the page wait until it receives that message before continuing.

#### add_WebResourceRequested

Add an event handler for the `WebResourceRequested` event.

> public HRESULT [add_WebResourceRequested](#add_webresourcerequested)([ICoreWebView2WebResourceRequestedEventHandler](icorewebview2webresourcerequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`WebResourceRequested` runs when the WebView is performing a URL request to a matching URL and resource context filter that was added with `AddWebResourceRequestedFilter`. At least one filter must be added for the event to run.

The web resource requested may be blocked until the event handler returns if a deferral is not taken on the event args. If a deferral is taken, then the web resource requested is blocked until the deferral is completed.

If this event is subscribed in the add_NewWindowRequested handler it should be called after the new window is set. For more details see [ICoreWebView2NewWindowRequestedEventArgs::put_NewWindow](icorewebview2newwindowrequestedeventargs.md).

This event is by default raised for file, http, and https URI schemes. This is also raised for registered custom URI schemes. For more details see [ICoreWebView2CustomSchemeRegistration](icorewebview2customschemeregistration.md).

```cpp
        if (m_blockImages)
        {
            m_webView->AddWebResourceRequestedFilter(
                L"*", COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE);
            CHECK_FAILURE(m_webView->add_WebResourceRequested(
                Callback<ICoreWebView2WebResourceRequestedEventHandler>(
                    [this](
                        ICoreWebView2* sender,
                        ICoreWebView2WebResourceRequestedEventArgs* args) {
                        COREWEBVIEW2_WEB_RESOURCE_CONTEXT resourceContext;
                        CHECK_FAILURE(args->get_ResourceContext(&resourceContext));
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
                            nullptr, 403 /*NoContent*/, L"Blocked", L"Content-Type: image/jpeg",
                            &response));
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

```cpp
        if (m_replaceImages)
        {
            m_webView->AddWebResourceRequestedFilter(
                L"*", COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE);
            CHECK_FAILURE(m_webView->add_WebResourceRequested(
                Callback<ICoreWebView2WebResourceRequestedEventHandler>(
                    [this](
                        ICoreWebView2* sender,
                        ICoreWebView2WebResourceRequestedEventArgs* args) {
                        COREWEBVIEW2_WEB_RESOURCE_CONTEXT resourceContext;
                        CHECK_FAILURE(args->get_ResourceContext(&resourceContext));
                        // Ensure that the type is image
                        if (resourceContext != COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE)
                        {
                            return E_INVALIDARG;
                        }
                        // Override the response with an another image.
                        // If put_Response is not called, the request will continue as normal.
                        wil::com_ptr<IStream> stream;
                        CHECK_FAILURE(SHCreateStreamOnFileEx(
                            L"assets/EdgeWebView2-80.jpg", STGM_READ, FILE_ATTRIBUTE_NORMAL,
                            FALSE, nullptr, &stream));
                        wil::com_ptr<ICoreWebView2WebResourceResponse> response;
                        wil::com_ptr<ICoreWebView2Environment> environment;
                        wil::com_ptr<ICoreWebView2_2> webview2;
                        CHECK_FAILURE(m_webView->QueryInterface(IID_PPV_ARGS(&webview2)));
                        CHECK_FAILURE(webview2->get_Environment(&environment));
                        CHECK_FAILURE(environment->CreateWebResourceResponse(
                            stream.get(), 200, L"OK", L"Content-Type: image/jpeg", &response));
                        CHECK_FAILURE(args->put_Response(response.get()));
                        return S_OK;
                    })
                    .Get(),
                &m_webResourceRequestedTokenForImageReplacing));
        }
        else
        {
            CHECK_FAILURE(m_webView->remove_WebResourceRequested(
                m_webResourceRequestedTokenForImageReplacing));
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
        Callback<ICoreWebView2WindowCloseRequestedEventHandler>(
            [this](ICoreWebView2* sender, IUnknown* args)
            {
                if (m_isPopupWindow)
                {
                    CloseAppWindow();
                }
                return S_OK;
            })
            .Get(),
        nullptr));
```

#### AddHostObjectToScript

Add the provided host object to script running in the WebView with the specified name.

> public HRESULT [AddHostObjectToScript](#addhostobjecttoscript)(LPCWSTR name, VARIANT * object)

Host objects are exposed as host object proxies using `window.chrome.webview.hostObjects.{name}`. Host object proxies are promises and resolves to an object representing the host object. The promise is rejected if the app has not added an object with the name. When JavaScript code access a property or method of the object, a promise is return, which resolves to the value returned from the host for the property or method, or rejected in case of error, for example, no property or method on the object or parameters are not valid.

> [!NOTE]
> While simple types, `IDispatch` and array are supported, and `IUnknown` objects that also implement `IDispatch` are treated as `IDispatch`, generic `IUnknown`, `VT_DECIMAL`, or `VT_RECORD` variant is not supported. Remote JavaScript objects like callback functions are represented as an `VT_DISPATCH``VARIANT` with the object implementing `IDispatch`. The JavaScript callback method may be invoked using `DISPID_VALUE` for the `DISPID`. Such callback method invocations will return immediately and will not wait for the JavaScript function to run and so will not provide the return value of the JavaScript function. Nested arrays are supported up to a depth of 3. Arrays of by reference types are not supported. `VT_EMPTY` and `VT_NULL` are mapped into JavaScript as `null`. In JavaScript, `null` and undefined are mapped to `VT_EMPTY`.

Additionally, all host objects are exposed as `window.chrome.webview.hostObjects.sync.{name}`. Here the host objects are exposed as synchronous host object proxies. These are not promises and function runtimes or property access synchronously block running script waiting to communicate cross process for the host code to run. Accordingly the result may have reliability issues and it is recommended that you use the promise-based asynchronous `window.chrome.webview.hostObjects.{name}` API.

Synchronous host object proxies and asynchronous host object proxies may both use a proxy to the same host object. Remote changes made by one proxy propagates to any other proxy of that same host object whether the other proxies and synchronous or asynchronous.

While JavaScript is blocked on a synchronous run to native code, that native code is unable to run back to JavaScript. Attempts to do so fail with `HRESULT_FROM_WIN32(ERROR_POSSIBLE_DEADLOCK)`.

Host object proxies are JavaScript Proxy objects that intercept all property get, property set, and method invocations. Properties or methods that are a part of the Function or Object prototype are run locally. Additionally any property or method in the `chrome.webview.hostObjects.options.forceLocalProperties` array are also run locally. This defaults to including optional methods that have meaning in JavaScript like `toJSON` and `Symbol.toPrimitive`. Add more to the array as required.

The `chrome.webview.hostObjects.cleanupSome` method performs a best effort garbage collection on host object proxies.

The `chrome.webview.hostObjects.options` object provides the ability to change some functionality of host objects.

Options property   |Details
--------- | ---------
`forceLocalProperties`|This is an array of host object property names that will be run locally, instead of being called on the native host object. This defaults to `then`, `toJSON`, `Symbol.toString`, and `Symbol.toPrimitive`. You can add other properties to specify that they should be run locally on the javascript host object proxy.
`log`|This is a callback that will be called with debug information. For example, you can set this to `console.log.bind(console)` to have it print debug information to the console to help when troubleshooting host object usage. By default this is null.
`shouldSerializeDates`|By default this is false, and javascript Date objects will be sent to host objects as a string using `JSON.stringify`. You can set this property to true to have Date objects properly serialize as a `VT_DATE` when sending to the native host object, and have `VT_DATE` properties and return values create a javascript Date object.
`defaultSyncProxy`|When calling a method on a synchronous proxy, the result should also be a synchronous proxy. But in some cases, the sync/async context is lost (for example, when providing to native code a reference to a function, and then calling that function in native code). In these cases, the proxy will be asynchronous, unless this property is set.
`forceAsyncMethodMatches`|This is an array of regular expressions. When calling a method on a synchronous proxy, the method call will be performed asynchronously if the method name matches a string or regular expression in this array. Setting this value to `Async` will make any method that ends with Async be an asynchronous method call. If an async method doesn't match here and isn't forced to be asynchronous, the method will be invoked synchronously, blocking execution of the calling JavaScript and then returning the resolution of the promise, rather than returning a promise.
`ignoreMemberNotFoundError`|By default, an exception is thrown when attempting to get the value of a proxy property that doesn't exist on the corresponding native class. Setting this property to `true` switches the behavior to match Chakra WinRT projection (and general JavaScript) behavior of returning `undefined` with no error.

Host object proxies additionally have the following methods which run locally.

Method name   |Details
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

        // Demonstrate a property which uses Date types
        [propget] HRESULT DateProperty([out, retval] DATE * dateResult);
        [propput] HRESULT DateProperty([in] DATE dateValue);

        // Creates a date object on the native side and sets the DateProperty to it.
        HRESULT CreateNativeDate();

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

In the HTML document, use the COM object using `chrome.webview.hostObjects.sample`. Note that `CoreWebView2.AddHostObjectToScript` only applies to the top-level document and not to frames. To add host objects to frames use `CoreWebView2Frame.AddHostObjectToScript`.

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

        // Date property
        document.getElementById("setDateButton").addEventListener("click", () => {
            chrome.webview.hostObjects.options.shouldSerializeDates = true;
            chrome.webview.hostObjects.sync.sample.dateProperty = new Date();
            document.getElementById("dateOutput").textContent = "sample.dateProperty: " + chrome.webview.hostObjects.sync.sample.dateProperty;
        });
        document.getElementById("createRemoteDateButton").addEventListener("click", () => {
            chrome.webview.hostObjects.sync.sample.createNativeDate();
            document.getElementById("dateOutput").textContent = "sample.dateProperty: " + chrome.webview.hostObjects.sync.sample.dateProperty;
        });

```

Exposing host objects to script has security risk. For more information about best practices, navigate to [Best practices for developing secure WebView2 applications](/microsoft-edge/webview2/concepts/security).

#### AddScriptToExecuteOnDocumentCreated

Add the provided JavaScript to a list of scripts that should be run after the global object has been created, but before the HTML document has been parsed and before any other script included by the HTML document is run.

> public HRESULT [AddScriptToExecuteOnDocumentCreated](#addscripttoexecuteondocumentcreated)(LPCWSTR javaScript, [ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler](icorewebview2addscripttoexecuteondocumentcreatedcompletedhandler.md) * handler)

This method injects a script that runs on all top-level document and child frame page navigations. This method runs asynchronously, and you must wait for the completion handler to finish before the injected script is ready to run. When this method completes, the `Invoke` method of the handler is run with the `id` of the injected script. `id` is a string. To remove the injected script, use `RemoveScriptToExecuteOnDocumentCreated`.

If the method is run in add_NewWindowRequested handler it should be called before the new window is set. If called after setting the NewWindow property, the initial script may or may not apply to the initial navigation and may only apply to the subsequent navigation. For more details see ICoreWebView2NewWindowRequestedEventArgs::put_NewWindow.

> [!NOTE]
> If an HTML document is running in a sandbox of some kind using [sandbox](https://developer.mozilla.org/docs/Web/HTML/Element/iframe#attr-sandbox) properties or the [Content-Security-Policy](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy) HTTP header affects the script that runs. For example, if the `allow-modals` keyword is not set then requests to run the `alert` function are ignored.

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
            m_appWindow->AsyncMessageBox(
                m_lastInitializeScriptId, L"AddScriptToExecuteOnDocumentCreated Id");
            return S_OK;
        }).Get());

    }
}
```

#### AddWebResourceRequestedFilter

Adds a URI and resource context filter for the `WebResourceRequested` event.

> public HRESULT [AddWebResourceRequestedFilter](#addwebresourcerequestedfilter)(LPCWSTR const uri, COREWEBVIEW2_WEB_RESOURCE_CONTEXT const resourceContext)

A web resource request with a resource context that matches this filter's resource context and a URI that matches this filter's URI wildcard string will be raised via the `WebResourceRequested` event.

The `uri` parameter value is a wildcard string matched against the URI of the web resource request. This is a glob style wildcard string in which a `*` matches zero or more characters and a `?` matches exactly one character. These wildcard characters can be escaped using a backslash just before the wildcard character in order to represent the literal `*` or `?`.

The matching occurs over the URI as a whole string and not limiting wildcard matches to particular parts of the URI. The wildcard filter is compared to the URI after the URI has been normalized, any URI fragment has been removed, and non-ASCII hostnames have been converted to punycode.

Specifying a `nullptr` for the uri is equivalent to an empty string which matches no URIs.

For more information about resource context filters, navigate to [COREWEBVIEW2_WEB_RESOURCE_CONTEXT](/microsoft-edge/webview2/reference/win32/webview2-idl#corewebview2_web_resource_context).

URI Filter String   |Request URI   |Match   |Notes
--------- | --------- | --------- | ---------
`*`|`https://contoso.com/a/b/c`|Yes   |A single * will match all URIs
`*://contoso.com/*`|`https://contoso.com/a/b/c`|Yes   |Matches everything in contoso.com across all schemes
`*://contoso.com/*`|`https://example.com/?https://contoso.com/`|Yes   |But also matches a URI with just the same text anywhere in the URI
`example`|`https://contoso.com/example`|No   |The filter does not perform partial matches
`*example`|`https://contoso.com/example`|Yes   |The filter matches across URI parts
`*example`|`https://contoso.com/path/?example`|Yes   |The filter matches across URI parts
`*example`|`https://contoso.com/path/?query#example`|No   |The filter is matched against the URI with no fragment
`*example`|`https://example`|No   |The URI is normalized before filter matching so the actual URI used for comparison is `https://example/`
`*example/`|`https://example`|Yes   |Just like above, but this time the filter ends with a / just like the normalized URI
`https://xn--qei.example/`|`https://&#x2764;.example/`|Yes   |Non-ASCII hostnames are normalized to punycode before wildcard comparison
`https://&#x2764;.example/`|`https://xn--qei.example/`|No   |Non-ASCII hostnames are normalized to punycode before wildcard comparison

#### CallDevToolsProtocolMethod

Runs an asynchronous `DevToolsProtocol` method.

> public HRESULT [CallDevToolsProtocolMethod](#calldevtoolsprotocolmethod)(LPCWSTR methodName, LPCWSTR parametersAsJson, [ICoreWebView2CallDevToolsProtocolMethodCompletedHandler](icorewebview2calldevtoolsprotocolmethodcompletedhandler.md) * handler)

For more information about available methods, navigate to [DevTools Protocol Viewer](https://chromedevtools.github.io/devtools-protocol/tot) . The `methodName` parameter is the full name of the method in the `{domain}.{method}` format. The `parametersAsJson` parameter is a JSON formatted string containing the parameters for the corresponding method. The `Invoke` method of the `handler` is run when the method asynchronously completes. `Invoke` is run with the return object of the method as a JSON string. This function returns E_INVALIDARG if the `methodName` is unknown or the `parametersAsJson` has an error. In the case of such an error, the `returnObjectAsJson` parameter of the handler will include information about the error. Note even though WebView2 dispatches the CDP messages in the order called, CDP method calls may be processed out of order. If you require CDP methods to run in a particular order, you should wait for the previous method's completed handler to run before calling the next method.

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
            methodName.c_str(), methodParams.c_str(),
            Callback<ICoreWebView2CallDevToolsProtocolMethodCompletedHandler>(
                this, &ScriptComponent::CDPMethodCallback)
                .Get());
    }
}
```

#### CapturePreview

Capture an image of what WebView is displaying.

> public HRESULT [CapturePreview](#capturepreview)(COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT imageFormat, IStream * imageStream, [ICoreWebView2CapturePreviewCompletedHandler](icorewebview2capturepreviewcompletedhandler.md) * handler)

Specify the format of the image with the `imageFormat` parameter. The resulting image binary data is written to the provided `imageStream` parameter. When `CapturePreview` finishes writing to the stream, the `Invoke` method on the provided `handler` parameter is run. This method fails if called before the first ContentLoading event. For example if this is called in the NavigationStarting event for the first navigation it will fail. For subsequent navigations, the method may not fail, but will not capture an image of a given webpage until the ContentLoading event has been fired for it. Any call to this method prior to that will result in a capture of the page being navigated away from.

```cpp
// Show the user a file selection dialog, then save a screenshot of the WebView
// to the selected file.
void FileComponent::SaveScreenshot()
{
    WCHAR defaultName[MAX_PATH] = L"WebView2_Screenshot.png";
    OPENFILENAME openFileName = CreateOpenFileName(defaultName, L"PNG File\0*.png\0");
    if (GetSaveFileName(&openFileName))
    {
        wil::com_ptr<IStream> stream;
        CHECK_FAILURE(SHCreateStreamOnFileEx(
            defaultName, STGM_READWRITE | STGM_CREATE, FILE_ATTRIBUTE_NORMAL, TRUE, nullptr,
            &stream));

        CHECK_FAILURE(m_webView->CapturePreview(
            COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT_PNG, stream.get(),
            Callback<ICoreWebView2CapturePreviewCompletedHandler>(
                [appWindow{m_appWindow}](HRESULT error_code) -> HRESULT {
                    CHECK_FAILURE(error_code);
                    appWindow->AsyncMessageBox(L"Preview Captured", L"Preview Captured");
                    return S_OK;
                })
                .Get()));
    }
}
```

#### ExecuteScript

Run JavaScript code from the javascript parameter in the current top-level document rendered in the WebView.

> public HRESULT [ExecuteScript](#executescript)(LPCWSTR javaScript, [ICoreWebView2ExecuteScriptCompletedHandler](icorewebview2executescriptcompletedhandler.md) * handler)

The result of evaluating the provided JavaScript is used in this parameter. The result value is a JSON encoded string. If the result is undefined, contains a reference cycle, or otherwise is not able to be encoded into JSON, then the result is considered to be null, which is encoded in JSON as the string "null".

> [!NOTE]
> A function that has no explicit return value returns undefined. If the script that was run throws an unhandled exception, then the result is also "null". This method is applied asynchronously. If the method is run after the `NavigationStarting` event during a navigation, the script runs in the new document when loading it, around the time `ContentLoading` is run. This operation executes the script even if `ICoreWebView2Settings::IsScriptEnabled` is set to `FALSE`.

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
                [appWindow = m_appWindow](HRESULT error, PCWSTR result) -> HRESULT
        {
            if (error != S_OK) {
                ShowFailure(error, L"ExecuteScript failed");
            }
            appWindow->AsyncMessageBox(result, L"ExecuteScript Result");
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

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Settings

The ICoreWebView2Settings object contains various modifiable settings for the running WebView.

> public HRESULT [get_Settings](#get_settings)(ICoreWebView2Settings ** settings)

#### get_Source

The URI of the current top level document.

> public HRESULT [get_Source](#get_source)(LPWSTR * uri)

This value potentially changes as a part of the `SourceChanged` event that runs for some cases such as navigating to a different site or fragment navigations. It remains the same for other types of navigations such as page refreshes or `history.pushState` with the same URL as the current page.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

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

> public HRESULT [GetDevToolsProtocolEventReceiver](#getdevtoolsprotocoleventreceiver)(LPCWSTR eventName, [ICoreWebView2DevToolsProtocolEventReceiver](icorewebview2devtoolsprotocoleventreceiver.md) ** receiver)

The `eventName` parameter is the full name of the event in the format `{domain}.{event}`. For more information about DevTools Protocol events description and event args, navigate to [DevTools Protocol Viewer](https://chromedevtools.github.io/devtools-protocol/tot).

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
                [this, eventName](
                    ICoreWebView2* sender,
                    ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args) -> HRESULT
                {
                    wil::unique_cotaskmem_string parameterObjectAsJson;
                    CHECK_FAILURE(args->get_ParameterObjectAsJson(&parameterObjectAsJson));
                    std::wstring title = eventName;
                    std::wstring details = parameterObjectAsJson.get();
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
                    m_appWindow->AsyncMessageBox(details, L"CDP Event Fired: " + title);
                    return S_OK;
                })
                .Get(),
            &m_devToolsProtocolEventReceivedTokenMap[eventName]));
    }
}
```

#### GoBack

Navigates the WebView to the previous page in the navigation history.

> public HRESULT [GoBack](#goback)()

#### GoForward

Navigates the WebView to the next page in the navigation history.

> public HRESULT [GoForward](#goforward)()

#### Navigate

Cause a navigation of the top-level document to run to the specified URI.

> public HRESULT [Navigate](#navigate)(LPCWSTR uri)

For more information, navigate to [Navigation events](/microsoft-edge/webview2/concepts/navigation-events).

> [!NOTE]
> This operation starts a navigation and the corresponding `NavigationStarting` event triggers sometime after `Navigate` runs.

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
            // Otherwise treat it as a web search. 
            std::wstring urlEscaped(2048, ' ');
            DWORD dwEscaped = (DWORD)urlEscaped.length();
            UrlEscapeW(uri.c_str(), &urlEscaped[0], &dwEscaped, URL_ESCAPE_ASCII_URI_COMPONENT);
            hr = m_webView->Navigate(
                (L"https://bing.com/search?q=" +
                 std::regex_replace(urlEscaped, std::wregex(L"(?:%20)+"), L"+"))
                    .c_str());
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

The `htmlContent` parameter may not be larger than 2 MB (2 * 1024 * 1024 bytes) in total size. The origin of the new page is `about:blank`.

```cpp
SetVirtualHostNameToFolderMapping(
    L"appassets.example", L"assets",
    COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY);

WCHAR c_navString[] = LR"
<head><link rel='stylesheet' href ='http://appassets.example/wv2.css'/></head>
<body>
  <img src='http://appassets.example/wv2.png' />
  <p><a href='http://appassets.example/winrt_test.txt'>Click me</a></p>
</body>";
m_webView->NavigateToString(c_navString);
```

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

The main page receives the message by subscribing to the `message` event of the `window.chrome.webview` of the page document.

```cpp
window.chrome.webview.addEventListener('message', handler)
window.chrome.webview.removeEventListener('message', handler)
```

The event args is an instance of `MessageEvent`. The `ICoreWebView2Settings::IsWebMessageEnabled` setting must be `TRUE` or the web message will not be sent. The `data` property of the event arg is the `webMessage` string parameter parsed as a JSON string into a JavaScript object. The `source` property of the event arg is a reference to the `window.chrome.webview` object. For information about sending messages from the HTML document in the WebView to the host, navigate to [add_WebMessageReceived](/microsoft-edge/webview2/reference/win32/icorewebview2#add_webmessagereceived). The message is delivered asynchronously. If a navigation occurs before the message is posted to the page, the message is discarded.

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
            // Ignore messages from untrusted sources.
            return S_OK;
        }
        wil::unique_cotaskmem_string messageRaw;
        HRESULT hr = args->TryGetWebMessageAsString(&messageRaw);
        if (hr == E_INVALIDARG)
        {
            // Was not a string message. Ignore.
            return S_OK;
        }
        // Any other problems are fatal.
        CHECK_FAILURE(hr);
        std::wstring message = messageRaw.get();

        if (message.compare(0, 13, L"SetTitleText ") == 0)
        {
            m_appWindow->SetDocumentTitle(message.substr(13).c_str());
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
        else
        {
            // Ignore unrecognized messages, but log for further investigation
            // since it suggests a mismatch between the web content and the host.
            OutputDebugString(
                std::wstring(L"Unexpected message from main page:" + message).c_str());
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

Remove an event handler previously added with `add_ProcessFailed`.

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

The script ID should be the one returned by the `AddScriptToExecuteOnDocumentCreated`. Both use `AddScriptToExecuteOnDocumentCreated` and this method in `NewWindowRequested` event handler at the same time sometimes causes trouble. Since invalid scripts will be ignored, the script IDs you got may not be valid anymore.

#### RemoveWebResourceRequestedFilter

Removes a matching WebResource filter that was previously added for the `WebResourceRequested` event.

> public HRESULT [RemoveWebResourceRequestedFilter](#removewebresourcerequestedfilter)(LPCWSTR const uri, COREWEBVIEW2_WEB_RESOURCE_CONTEXT const resourceContext)

If the same filter was added multiple times, then it must be removed as many times as it was added for the removal to be effective. Returns `E_INVALIDARG` for a filter that was never added.

#### Stop

Stop all navigations and pending resource fetches. Does not stop scripts.

> public HRESULT [Stop](#stop)()

