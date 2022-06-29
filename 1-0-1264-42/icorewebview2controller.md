---
description: The owner of the `CoreWebView2` object that provides support for resizing, showing and hiding, focusing, and other functionality related to windowing and composition.
title: WebView2 Win32 C++ ICoreWebView2Controller
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Controller
---

# interface ICoreWebView2Controller

```
interface ICoreWebView2Controller
  : public IUnknown
```

The owner of the `CoreWebView2` object that provides support for resizing, showing and hiding, focusing, and other functionality related to windowing and composition.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_AcceleratorKeyPressed](#add_acceleratorkeypressed) | Adds an event handler for the `AcceleratorKeyPressed` event.
[add_GotFocus](#add_gotfocus) | Adds an event handler for the `GotFocus` event.
[add_LostFocus](#add_lostfocus) | Adds an event handler for the `LostFocus` event.
[add_MoveFocusRequested](#add_movefocusrequested) | Adds an event handler for the `MoveFocusRequested` event.
[add_ZoomFactorChanged](#add_zoomfactorchanged) | Adds an event handler for the `ZoomFactorChanged` event.
[Close](#close) | Closes the WebView and cleans up the underlying browser instance.
[get_Bounds](#get_bounds) | The WebView bounds.
[get_CoreWebView2](#get_corewebview2) | Gets the `CoreWebView2` associated with this `CoreWebView2Controller`.
[get_IsVisible](#get_isvisible) | The `IsVisible` property determines whether to show or hide the WebView2.
[get_ParentWindow](#get_parentwindow) | The parent window provided by the app that this WebView is using to render content.
[get_ZoomFactor](#get_zoomfactor) | The zoom factor for the WebView.
[MoveFocus](#movefocus) | Moves focus into WebView.
[NotifyParentWindowPositionChanged](#notifyparentwindowpositionchanged) | This is a notification separate from `Bounds` that tells WebView that the main WebView parent (or any ancestor) `HWND` moved.
[put_Bounds](#put_bounds) | Sets the `Bounds` property.
[put_IsVisible](#put_isvisible) | Sets the `IsVisible` property.
[put_ParentWindow](#put_parentwindow) | Sets the parent window for the WebView.
[put_ZoomFactor](#put_zoomfactor) | Sets the `ZoomFactor` property.
[remove_AcceleratorKeyPressed](#remove_acceleratorkeypressed) | Removes an event handler previously added with `add_AcceleratorKeyPressed`.
[remove_GotFocus](#remove_gotfocus) | Removes an event handler previously added with `add_GotFocus`.
[remove_LostFocus](#remove_lostfocus) | Removes an event handler previously added with `add_LostFocus`.
[remove_MoveFocusRequested](#remove_movefocusrequested) | Removes an event handler previously added with `add_MoveFocusRequested`.
[remove_ZoomFactorChanged](#remove_zoomfactorchanged) | Remove an event handler previously added with `add_ZoomFactorChanged`.
[SetBoundsAndZoomFactor](#setboundsandzoomfactor) | Updates `Bounds` and `ZoomFactor` properties at the same time.

The `CoreWebView2Controller` owns the `CoreWebView2`, and if all references to the `CoreWebView2Controller` go away, the WebView is closed.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.488
WebView2 Win32 Prerelease |    0.9.488

## Members

#### add_AcceleratorKeyPressed

Adds an event handler for the `AcceleratorKeyPressed` event.

> public HRESULT [add_AcceleratorKeyPressed](#add_acceleratorkeypressed)([ICoreWebView2AcceleratorKeyPressedEventHandler](icorewebview2acceleratorkeypressedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`AcceleratorKeyPressed` runs when an accelerator key or key combo is pressed or released while the WebView is focused. A key is considered an accelerator if either of the following conditions are true.

* Ctrl or Alt is currently being held.

* The pressed key does not map to a character.

A few specific keys are never considered accelerators, such as Shift. The `Escape` key is always considered an accelerator.

Auto-repeated key events caused by holding the key down also triggers this event. Filter out the auto-repeated key events by verifying the `KeyEventLParam` or `PhysicalKeyStatus` event args.

In windowed mode, the event handler is run synchronously. Until you run `Handled()` on the event args or the event handler returns, the browser process is blocked and outgoing cross-process COM requests fail with `RPC_E_CANTCALLOUT_ININPUTSYNCCALL`. All `CoreWebView2` API methods work, however.

In windowless mode, the event handler is run asynchronously. Further input do not reach the browser until the event handler returns or `Handled()` is run, but the browser process is not blocked, and outgoing COM requests work normally.

It is recommended to run `Handled(TRUE)` as early as are able to know that you want to handle the accelerator key.

```cpp
    // Register a handler for the AcceleratorKeyPressed event.
    CHECK_FAILURE(m_controller->add_AcceleratorKeyPressed(
        Callback<ICoreWebView2AcceleratorKeyPressedEventHandler>(
            [this](
                ICoreWebView2Controller* sender,
                ICoreWebView2AcceleratorKeyPressedEventArgs* args) -> HRESULT {
                COREWEBVIEW2_KEY_EVENT_KIND kind;
                CHECK_FAILURE(args->get_KeyEventKind(&kind));
                // We only care about key down events.
                if (kind == COREWEBVIEW2_KEY_EVENT_KIND_KEY_DOWN ||
                    kind == COREWEBVIEW2_KEY_EVENT_KIND_SYSTEM_KEY_DOWN)
                {
                    UINT key;
                    CHECK_FAILURE(args->get_VirtualKey(&key));
                    // Check if the key is one we want to handle.
                    std::function<void()> action = m_appWindow->GetAcceleratorKeyFunction(key);
                    if (action)
                    {
                        // Keep the browser from handling this key, whether it's autorepeated or
                        // not.
                        CHECK_FAILURE(args->put_Handled(TRUE));

                        // Filter out autorepeated keys.
                        COREWEBVIEW2_PHYSICAL_KEY_STATUS status;
                        CHECK_FAILURE(args->get_PhysicalKeyStatus(&status));
                        if (!status.WasKeyDown)
                        {
                            // Perform the action asynchronously to avoid blocking the
                            // browser process's event queue.
                            m_appWindow->RunAsync(action);
                        }
                    }
                }
                return S_OK;
            })
            .Get(),
        &m_acceleratorKeyPressedToken));
```

#### add_GotFocus

Adds an event handler for the `GotFocus` event.

> public HRESULT [add_GotFocus](#add_gotfocus)([ICoreWebView2FocusChangedEventHandler](icorewebview2focuschangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`GotFocus` runs when WebView has focus.

#### add_LostFocus

Adds an event handler for the `LostFocus` event.

> public HRESULT [add_LostFocus](#add_lostfocus)([ICoreWebView2FocusChangedEventHandler](icorewebview2focuschangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`LostFocus` runs when WebView loses focus. In the case where `MoveFocusRequested` event is run, the focus is still on WebView when `MoveFocusRequested` event runs. `LostFocus` only runs afterwards when code of the app or default action of `MoveFocusRequested` event set focus away from WebView.

#### add_MoveFocusRequested

Adds an event handler for the `MoveFocusRequested` event.

> public HRESULT [add_MoveFocusRequested](#add_movefocusrequested)([ICoreWebView2MoveFocusRequestedEventHandler](icorewebview2movefocusrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`MoveFocusRequested` runs when user tries to tab out of the WebView. The focus of the WebView has not changed when this event is run.

```cpp
    // Register a handler for the MoveFocusRequested event.
    // This event will be fired when the user tabs out of the webview.
    // The handler will focus another window in the app, depending on which
    // direction the focus is being shifted.
    CHECK_FAILURE(m_controller->add_MoveFocusRequested(
        Callback<ICoreWebView2MoveFocusRequestedEventHandler>(
            [this](
                ICoreWebView2Controller* sender,
                ICoreWebView2MoveFocusRequestedEventArgs* args) -> HRESULT {
                if (!g_autoTabHandle)
                {
                    COREWEBVIEW2_MOVE_FOCUS_REASON reason;
                    CHECK_FAILURE(args->get_Reason(&reason));

                    if (reason == COREWEBVIEW2_MOVE_FOCUS_REASON_NEXT)
                    {
                        TabForwards(-1);
                    }
                    else if (reason == COREWEBVIEW2_MOVE_FOCUS_REASON_PREVIOUS)
                    {
                        TabBackwards(m_tabbableWindows.size());
                    }
                    CHECK_FAILURE(args->put_Handled(TRUE));
                }
                return S_OK;
            })
            .Get(),
        &m_moveFocusRequestedToken));
```

#### add_ZoomFactorChanged

Adds an event handler for the `ZoomFactorChanged` event.

> public HRESULT [add_ZoomFactorChanged](#add_zoomfactorchanged)([ICoreWebView2ZoomFactorChangedEventHandler](icorewebview2zoomfactorchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ZoomFactorChanged` runs when the `ZoomFactor` property of the WebView changes. The event may run because the `ZoomFactor` property was modified, or due to the user manually modifying the zoom. When it is modified using the `ZoomFactor` property, the internal zoom factor is updated immediately and no `ZoomFactorChanged` event is triggered. WebView associates the last used zoom factor for each site. It is possible for the zoom factor to change when navigating to a different page. When the zoom factor changes due to a navigation change, the `ZoomFactorChanged` event runs right after the `ContentLoading` event.

```cpp
    // Register a handler for the ZoomFactorChanged event.
    // This handler just announces the new level of zoom on the window's title bar.
    CHECK_FAILURE(m_controller->add_ZoomFactorChanged(
        Callback<ICoreWebView2ZoomFactorChangedEventHandler>(
            [this](ICoreWebView2Controller* sender, IUnknown* args) -> HRESULT {
                double zoomFactor;
                CHECK_FAILURE(sender->get_ZoomFactor(&zoomFactor));

                UpdateDocumentTitle(m_appWindow, L" (Zoom: ", zoomFactor);
                return S_OK;
            })
        .Get(),
                &m_zoomFactorChangedToken));
```

#### Close

Closes the WebView and cleans up the underlying browser instance.

> public HRESULT [Close](#close)()

Cleaning up the browser instance releases the resources powering the WebView. The browser instance is shut down if no other WebViews are using it.

After running `Close`, most methods will fail and event handlers stop running. Specifically, the WebView releases the associated references to any associated event handlers when `Close` is run.

`Close` is implicitly run when the `CoreWebView2Controller` loses the final reference and is destructed. But it is best practice to explicitly run `Close` to avoid any accidental cycle of references between the WebView and the app code. Specifically, if you capture a reference to the WebView in an event handler you create a reference cycle between the WebView and the event handler. Run `Close` to break the cycle by releasing all event handlers. But to avoid the situation, it is best to both explicitly run `Close` on the WebView and to not capture a reference to the WebView to ensure the WebView is cleaned up correctly. `Close` is synchronous and won't trigger the `beforeunload` event.

```cpp
// Close the WebView and deinitialize related state. This doesn't close the app window.
bool AppWindow::CloseWebView(bool cleanupUserDataFolder)
{
    if (auto file = GetComponent<FileComponent>())
    {
        if (file->IsPrintToPdfInProgress())
        {
            int selection = MessageBox(m_mainWindow,
                L"Print to PDF is in progress. Continue closing?",
                L"Print to PDF", MB_YESNO);
            if (selection == IDNO)
            {
                return false;
            }
        }
    }
    // 1. Delete components.
    DeleteAllComponents();

    // 2. If cleanup needed and BrowserProcessExited event interface available,
    // register to cleanup upon browser exit.
    wil::com_ptr<ICoreWebView2Environment5> environment5;
    if (m_webViewEnvironment)
    {
        environment5 =
            m_webViewEnvironment.try_query<ICoreWebView2Environment5>();
    }
    if (cleanupUserDataFolder && environment5)
    {
        // Before closing the WebView, register a handler with code to run once the
        // browser process and associated processes are terminated.
        CHECK_FAILURE(environment5->add_BrowserProcessExited(
            Callback<ICoreWebView2BrowserProcessExitedEventHandler>(
                [environment5, this](
                    ICoreWebView2Environment* sender,
                    ICoreWebView2BrowserProcessExitedEventArgs* args) {
                    COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND kind;
                    UINT32 pid;
                    CHECK_FAILURE(args->get_BrowserProcessExitKind(&kind));
                    CHECK_FAILURE(args->get_BrowserProcessId(&pid));

                    // If a new WebView is created from this CoreWebView2Environment after
                    // the browser has exited but before our handler gets to run, a new
                    // browser process will be created and lock the user data folder
                    // again. Do not attempt to cleanup the user data folder in these
                    // cases. We check the PID of the exited browser process against the
                    // PID of the browser process to which our last CoreWebView2 attached.
                    if (pid == m_newestBrowserPid)
                    {
                        // Watch for graceful browser process exit. Let ProcessFailed event
                        // handler take care of failed browser process termination.
                        if (kind == COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_NORMAL)
                        {
                            CHECK_FAILURE(environment5->remove_BrowserProcessExited(
                                m_browserExitedEventToken));
                            // Release the environment only after the handler is invoked.
                            // Otherwise, there will be no environment to raise the event when
                            // the collection of WebView2 Runtime processes exit.
                            m_webViewEnvironment = nullptr;
                            RunAsync([this]() { CleanupUserDataFolder(); });
                        }
                    }
                    else
                    {
                        // The exiting process is not the last in use. Do not attempt cleanup
                        // as we might still have a webview open over the user data folder.
                        // Do not block from event handler.
                        AsyncMessageBox(
                            L"A new browser process prevented cleanup of the user data folder.",
                            L"Cleanup User Data Folder");
                    }

                    return S_OK;
                })
                .Get(),
            &m_browserExitedEventToken));
    }

    // 3. Close the webview.
    if (m_controller)
    {
        m_controller->Close();
        m_controller = nullptr;
        m_webView = nullptr;
        m_webView3 = nullptr;
    }

    // 4. If BrowserProcessExited event interface is not available, release
    // environment and proceed to cleanup immediately. If the interface is
    // available, release environment only if not waiting for the event.
    if (!environment5)
    {
        m_webViewEnvironment = nullptr;
        if (cleanupUserDataFolder)
        {
            CleanupUserDataFolder();
        }
    }
    else if (!cleanupUserDataFolder)
    {
        // Release the environment object here only if no cleanup is needed.
        // If cleanup is needed, the environment object release is deferred
        // until the browser process exits, otherwise the handler for the
        // BrowserProcessExited event will not be called.
        m_webViewEnvironment = nullptr;
    }

    // reset profile name
    m_profileName = L"";
    m_documentTitle = L"";
    return true;
}
```

#### get_Bounds

The WebView bounds.

> public HRESULT [get_Bounds](#get_bounds)(RECT * bounds)

Bounds are relative to the parent `HWND`. The app has two ways to position a WebView.

* Create a child `HWND` that is the WebView parent `HWND`. Position the window where the WebView should be. Use `(0, 0)` for the top-left corner (the offset) of the `Bounds` of the WebView.

* Use the top-most window of the app as the WebView parent HWND. For example, to position WebView correctly in the app, set the top-left corner of the Bound of the WebView.

The values of `Bounds` are limited by the coordinate space of the host.

#### get_CoreWebView2

Gets the `CoreWebView2` associated with this `CoreWebView2Controller`.

> public HRESULT [get_CoreWebView2](#get_corewebview2)([ICoreWebView2](icorewebview2.md) ** coreWebView2)

#### get_IsVisible

The `IsVisible` property determines whether to show or hide the WebView2.

> public HRESULT [get_IsVisible](#get_isvisible)(BOOL * isVisible)

If `IsVisible` is set to `FALSE`, the WebView2 is transparent and is not rendered. However, this does not affect the window containing the WebView2 (the `HWND` parameter that was passed to `CreateCoreWebView2Controller`). If you want that window to disappear too, run `ShowWindow` on it directly in addition to modifying the `IsVisible` property. WebView2 as a child window does not get window messages when the top window is minimized or restored. For performance reasons, developers should set the `IsVisible` property of the WebView to `FALSE` when the app window is minimized and back to `TRUE` when the app window is restored. The app window does this by handling `SIZE_MINIMIZED and SIZE_RESTORED` command upon receiving `WM_SIZE` message.

There are CPU and memory benefits when the page is hidden. For instance, Chromium has code that throttles activities on the page like animations and some tasks are run less frequently. Similarly, WebView2 will purge some caches to reduce memory usage.

```cpp
void ViewComponent::ToggleVisibility()
{
    BOOL visible;
    m_controller->get_IsVisible(&visible);
    m_isVisible = !visible;
    m_controller->put_IsVisible(m_isVisible);
}
```

#### get_ParentWindow

The parent window provided by the app that this WebView is using to render content.

> public HRESULT [get_ParentWindow](#get_parentwindow)(HWND * parentWindow)

This API initially returns the window passed into `CreateCoreWebView2Controller`.

#### get_ZoomFactor

The zoom factor for the WebView.

> public HRESULT [get_ZoomFactor](#get_zoomfactor)(double * zoomFactor)

> [!NOTE]
> Changing zoom factor may cause `window.innerWidth`, `window.innerHeight`, both, and page layout to change. A zoom factor that is applied by the host by running `ZoomFactor` becomes the new default zoom for the WebView. The zoom factor applies across navigations and is the zoom factor WebView is returned to when the user chooses Ctrl+0. When the zoom factor is changed by the user (resulting in the app receiving `ZoomFactorChanged`), that zoom applies only for the current page. Any user applied zoom is only for the current page and is reset on a navigation. Specifying a `zoomFactor` less than or equal to `0` is not allowed. WebView also has an internal supported zoom factor range. When a specified zoom factor is out of that range, it is normalized to be within the range, and a `ZoomFactorChanged` event is triggered for the real applied zoom factor. When the range normalization happens, the `ZoomFactor` property reports the zoom factor specified during the previous modification of the `ZoomFactor` property until the `ZoomFactorChanged` event is received after WebView applies the normalized zoom factor.

#### MoveFocus

Moves focus into WebView.

> public HRESULT [MoveFocus](#movefocus)(COREWEBVIEW2_MOVE_FOCUS_REASON reason)

WebView gets focus and focus is set to correspondent element in the page hosted in the WebView. For Programmatic reason, focus is set to previously focused element or the default element if no previously focused element exists. For `Next` reason, focus is set to the first element. For `Previous` reason, focus is set to the last element. WebView changes focus through user interaction including selecting into a WebView or Tab into it. For tabbing, the app runs MoveFocus with Next or Previous to align with Tab and Shift+Tab respectively when it decides the WebView is the next element that may exist in a tab. Or, the app runs `IsDialogMessage` as part of the associated message loop to allow the platform to auto handle tabbing. The platform rotates through all windows with `WS_TABSTOP`. When the WebView gets focus from `IsDialogMessage`, it is internally put the focus on the first or last element for tab and Shift+Tab respectively.

```cpp
    while (GetMessage(&msg, nullptr, 0, 0))
    {
        if (!TranslateAccelerator(msg.hwnd, hAccelTable, &msg))
        {
            // Calling IsDialogMessage handles Tab traversal automatically. If the
            // app wants the platform to auto handle tab, then call IsDialogMessage
            // before calling TranslateMessage/DispatchMessage. If the app wants to
            // handle tabbing itself, then skip calling IsDialogMessage and call
            // TranslateMessage/DispatchMessage directly.
            if (!g_autoTabHandle || !IsDialogMessage(GetAncestor(msg.hwnd, GA_ROOT), &msg))
            {
                TranslateMessage(&msg);
                DispatchMessage(&msg);
            }
        }
    }
```

```cpp
        if (wParam == VK_TAB)
        {
            // Find out if the window is one we've customized for tab handling
            for (size_t i = 0; i < m_tabbableWindows.size(); i++)
            {
                if (m_tabbableWindows[i].first == hWnd)
                {
                    if (GetKeyState(VK_SHIFT) < 0)
                    {
                        TabBackwards(i);
                    }
                    else
                    {
                        TabForwards(i);
                    }
                    return true;
                }
            }
        }
```

```cpp
void ControlComponent::TabForwards(size_t currentIndex)
{
    // Find first enabled window after the active one
    for (size_t i = currentIndex + 1; i < m_tabbableWindows.size(); i++)
    {
        HWND hwnd = m_tabbableWindows.at(i).first;
        if (IsWindowEnabled(hwnd))
        {
            SetFocus(hwnd);
            return;
        }
    }
    // If this is the last enabled window, tab forwards into the WebView.
    m_controller->MoveFocus(COREWEBVIEW2_MOVE_FOCUS_REASON_NEXT);
}

void ControlComponent::TabBackwards(size_t currentIndex)
{
    // Find first enabled window before the active one
    for (size_t i = currentIndex - 1; i >= 0 && i < m_tabbableWindows.size(); i--)
    {
        HWND hwnd = m_tabbableWindows.at(i).first;
        if (IsWindowEnabled(hwnd))
        {
            SetFocus(hwnd);
            return;
        }
    }
    // If this is the last enabled window, tab forwards into the WebView.
    CHECK_FAILURE(m_controller->MoveFocus(COREWEBVIEW2_MOVE_FOCUS_REASON_PREVIOUS));
}
```

#### NotifyParentWindowPositionChanged

This is a notification separate from `Bounds` that tells WebView that the main WebView parent (or any ancestor) `HWND` moved.

> public HRESULT [NotifyParentWindowPositionChanged](#notifyparentwindowpositionchanged)()

This is needed for accessibility and certain dialogs in WebView to work correctly.

```cpp
    if (message == WM_MOVE || message == WM_MOVING)
    {
        m_controller->NotifyParentWindowPositionChanged();
        return true;
    }
```

#### put_Bounds

Sets the `Bounds` property.

> public HRESULT [put_Bounds](#put_bounds)(RECT bounds)

```cpp
// Update the bounds of the WebView window to fit available space.
void ViewComponent::ResizeWebView()
{
    SIZE webViewSize = {
            LONG((m_webViewBounds.right - m_webViewBounds.left) * m_webViewRatio * m_webViewScale),
            LONG((m_webViewBounds.bottom - m_webViewBounds.top) * m_webViewRatio * m_webViewScale) };

    RECT desiredBounds = m_webViewBounds;
    desiredBounds.bottom = LONG(
        webViewSize.cy + m_webViewBounds.top);
    desiredBounds.right = LONG(
        webViewSize.cx + m_webViewBounds.left);

    m_controller->put_Bounds(desiredBounds);
    if (m_compositionController)
    {
        POINT webViewOffset = {m_webViewBounds.left, m_webViewBounds.top};

        if (m_dcompDevice)
        {
            CHECK_FAILURE(m_dcompRootVisual->SetOffsetX(float(webViewOffset.x)));
            CHECK_FAILURE(m_dcompRootVisual->SetOffsetY(float(webViewOffset.y)));
            CHECK_FAILURE(m_dcompRootVisual->SetClip(
                {0, 0, float(webViewSize.cx), float(webViewSize.cy)}));
            CHECK_FAILURE(m_dcompDevice->Commit());
        }
        else if (m_wincompCompositor)
        {
            if (m_wincompRootVisual != nullptr)
            {
                numerics::float2 size = {static_cast<float>(webViewSize.cx),
                                         static_cast<float>(webViewSize.cy)};
                m_wincompRootVisual.Size(size);

                numerics::float3 offset = {static_cast<float>(webViewOffset.x),
                                           static_cast<float>(webViewOffset.y), 0.0f};
                m_wincompRootVisual.Offset(offset);

                winrtComp::IInsetClip insetClip = m_wincompCompositor.CreateInsetClip();
                m_wincompRootVisual.Clip(insetClip.as<winrtComp::CompositionClip>());
            }
        }
    }
}
```

#### put_IsVisible

Sets the `IsVisible` property.

> public HRESULT [put_IsVisible](#put_isvisible)(BOOL isVisible)

```cpp
    if (message == WM_SIZE)
    {
        if (wParam == SIZE_MINIMIZED)
        {
            // Hide the webview when the app window is minimized.
            m_controller->put_IsVisible(FALSE);
            Suspend();
        }
        else if (wParam == SIZE_RESTORED)
        {
            // When the app window is restored, show the webview
            // (unless the user has toggle visibility off).
            if (m_isVisible)
            {
                Resume();
                m_controller->put_IsVisible(TRUE);
            }
        }
    }
```

#### put_ParentWindow

Sets the parent window for the WebView.

> public HRESULT [put_ParentWindow](#put_parentwindow)(HWND parentWindow)

This causes the WebView to re-parent the main WebView window to the newly provided window.

#### put_ZoomFactor

Sets the `ZoomFactor` property.

> public HRESULT [put_ZoomFactor](#put_zoomfactor)(double zoomFactor)

#### remove_AcceleratorKeyPressed

Removes an event handler previously added with `add_AcceleratorKeyPressed`.

> public HRESULT [remove_AcceleratorKeyPressed](#remove_acceleratorkeypressed)(EventRegistrationToken token)

#### remove_GotFocus

Removes an event handler previously added with `add_GotFocus`.

> public HRESULT [remove_GotFocus](#remove_gotfocus)(EventRegistrationToken token)

#### remove_LostFocus

Removes an event handler previously added with `add_LostFocus`.

> public HRESULT [remove_LostFocus](#remove_lostfocus)(EventRegistrationToken token)

#### remove_MoveFocusRequested

Removes an event handler previously added with `add_MoveFocusRequested`.

> public HRESULT [remove_MoveFocusRequested](#remove_movefocusrequested)(EventRegistrationToken token)

#### remove_ZoomFactorChanged

Remove an event handler previously added with `add_ZoomFactorChanged`.

> public HRESULT [remove_ZoomFactorChanged](#remove_zoomfactorchanged)(EventRegistrationToken token)

#### SetBoundsAndZoomFactor

Updates `Bounds` and `ZoomFactor` properties at the same time.

> public HRESULT [SetBoundsAndZoomFactor](#setboundsandzoomfactor)(RECT bounds, double zoomFactor)

This operation is atomic from the perspective of the host. After returning from this function, the `Bounds` and `ZoomFactor` properties are both updated if the function is successful, or neither is updated if the function fails. If `Bounds` and `ZoomFactor` are both updated by the same scale (for example, `Bounds` and `ZoomFactor` are both doubled), then the page does not display a change in `window.innerWidth` or `window.innerHeight` and the WebView renders the content at the new size and zoom without intermediate renderings. This function also updates just one of `ZoomFactor` or `Bounds` by passing in the new value for one and the current value for the other.

```cpp
void ViewComponent::SetScale(float scale)
{
    RECT bounds;
    CHECK_FAILURE(m_controller->get_Bounds(&bounds));
    double scaleChange = scale / m_webViewScale;

    bounds.bottom = LONG(
        (bounds.bottom - bounds.top) * scaleChange + bounds.top);
    bounds.right = LONG(
        (bounds.right - bounds.left) * scaleChange + bounds.left);

    m_webViewScale = scale;
    m_controller->SetBoundsAndZoomFactor(bounds, scale);
}
```

