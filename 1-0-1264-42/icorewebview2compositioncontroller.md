---
description: This interface is an extension of the ICoreWebView2Controller interface to support visual hosting.
title: WebView2 Win32 C++ ICoreWebView2CompositionController
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CompositionController
---

# interface ICoreWebView2CompositionController

```
interface ICoreWebView2CompositionController
  : public IUnknown
```

This interface is an extension of the ICoreWebView2Controller interface to support visual hosting.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_CursorChanged](#add_cursorchanged) | Add an event handler for the CursorChanged event.
[get_Cursor](#get_cursor) | The current cursor that WebView thinks it should be.
[get_RootVisualTarget](#get_rootvisualtarget) | The RootVisualTarget is a visual in the hosting app's visual tree.
[get_SystemCursorId](#get_systemcursorid) | The current system cursor ID reported by the underlying rendering engine for WebView.
[put_RootVisualTarget](#put_rootvisualtarget) | Set the RootVisualTarget property.
[remove_CursorChanged](#remove_cursorchanged) | Remove an event handler previously added with add_CursorChanged.
[SendMouseInput](#sendmouseinput) | If eventKind is COREWEBVIEW2_MOUSE_EVENT_KIND_HORIZONTAL_WHEEL or COREWEBVIEW2_MOUSE_EVENT_KIND_WHEEL, then mouseData specifies the amount of wheel movement.
[SendPointerInput](#sendpointerinput) | SendPointerInput accepts touch or pen pointer input of types defined in COREWEBVIEW2_POINTER_EVENT_KIND.

An object implementing the ICoreWebView2CompositionController interface will also implement ICoreWebView2Controller. Callers are expected to use ICoreWebView2Controller for resizing, visibility, focus, and so on, and then use ICoreWebView2CompositionController to connect to a composition tree and provide input meant for the WebView.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### add_CursorChanged

Add an event handler for the CursorChanged event.

> public HRESULT [add_CursorChanged](#add_cursorchanged)([ICoreWebView2CursorChangedEventHandler](icorewebview2cursorchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

The event is raised when WebView thinks the cursor should be changed. For example, when the mouse cursor is currently the default cursor but is then moved over text, it may try to change to the IBeam cursor.

It is expected for the developer to send COREWEBVIEW2_MOUSE_EVENT_KIND_LEAVE messages (in addition to COREWEBVIEW2_MOUSE_EVENT_KIND_MOVE messages) through the SendMouseInput API. This is to ensure that the mouse is actually within the WebView that sends out CursorChanged events.

```cpp
        // Register a handler for the CursorChanged event.
        CHECK_FAILURE(m_compositionController->add_CursorChanged(
            Callback<ICoreWebView2CursorChangedEventHandler>(
                [this](ICoreWebView2CompositionController* sender, IUnknown* args)
                    -> HRESULT {
                    HRESULT hr = S_OK;
                    HCURSOR cursor;
                    if (!m_useCursorId)
                    {
                        CHECK_FAILURE(sender->get_Cursor(&cursor));
                    }
                    else
                    {
                        UINT32 cursorId;
                        CHECK_FAILURE(m_compositionController->get_SystemCursorId(&cursorId));
                        cursor = ::LoadCursor(nullptr, MAKEINTRESOURCE(cursorId));
                        if (cursor == nullptr)
                        {
                            hr = HRESULT_FROM_WIN32(GetLastError());
                        }
                    }

                    if (SUCCEEDED(hr))
                    {
                        SetClassLongPtr(
                            m_appWindow->GetMainWindow(), GCLP_HCURSOR, (LONG_PTR)cursor);
                    }
                    return hr;
                })
                .Get(),
            &m_cursorChangedToken));
```

#### get_Cursor

The current cursor that WebView thinks it should be.

> public HRESULT [get_Cursor](#get_cursor)(HCURSOR * cursor)

The cursor should be set in WM_SETCURSOR through ::SetCursor or set on the corresponding parent/ancestor HWND of the WebView through ::SetClassLongPtr. The HCURSOR can be freed so CopyCursor/DestroyCursor is recommended to keep your own copy if you are doing more than immediately setting the cursor.

#### get_RootVisualTarget

The RootVisualTarget is a visual in the hosting app's visual tree.

> public HRESULT [get_RootVisualTarget](#get_rootvisualtarget)(IUnknown ** target)

This visual is where the WebView will connect its visual tree. The app uses this visual to position the WebView within the app. The app still needs to use the Bounds property to size the WebView. The RootVisualTarget property can be an IDCompositionVisual or a Windows::UI::Composition::ContainerVisual. WebView will connect its visual tree to the provided visual before returning from the property setter. The app needs to commit on its device setting the RootVisualTarget property. The RootVisualTarget property supports being set to nullptr to disconnect the WebView from the app's visual tree. 
```cpp
            // Set the host app visual that the WebView will connect its visual
            // tree to.
            BuildDCompTreeUsingVisual();
            if (m_isDcompTargetMode)
            {
                if (!m_dcompTarget)
                {
                    m_dcompTarget = Make<DCompTargetImpl>(this);
                }
                CHECK_FAILURE(
                    m_compositionController->put_RootVisualTarget(m_dcompTarget.get()));
            }
            else
            {
                CHECK_FAILURE(
                    m_compositionController->put_RootVisualTarget(m_dcompWebViewVisual.get()));
            }
            CHECK_FAILURE(m_dcompDevice->Commit());
```

```cpp
// Create host app visual that the WebView will connect to.
//   - Create a IDCompositionTarget for the host window
//   - Create a visual and set that as the IDCompositionTarget's root
//   - Create another visual and add that to the IDCompositionTarget's root.
//     This visual will be the visual root for the WebView.
void ViewComponent::BuildDCompTreeUsingVisual()
{
    CHECK_FAILURE_BOOL(m_dcompDevice != nullptr);

    if (m_dcompWebViewVisual == nullptr)
    {
        CHECK_FAILURE(m_dcompDevice->CreateTargetForHwnd(
            m_appWindow->GetMainWindow(), TRUE, &m_dcompHwndTarget));
        CHECK_FAILURE(m_dcompDevice->CreateVisual(&m_dcompRootVisual));
        CHECK_FAILURE(m_dcompHwndTarget->SetRoot(m_dcompRootVisual.get()));
        CHECK_FAILURE(m_dcompDevice->CreateVisual(&m_dcompWebViewVisual));
        CHECK_FAILURE(m_dcompRootVisual->AddVisual(m_dcompWebViewVisual.get(), TRUE, nullptr));
    }
}
```

#### get_SystemCursorId

The current system cursor ID reported by the underlying rendering engine for WebView.

> public HRESULT [get_SystemCursorId](#get_systemcursorid)(UINT32 * systemCursorId)

For example, most of the time, when the cursor is over text, this will return the int value for IDC_IBEAM. The systemCursorId is only valid if the rendering engine reports a default Windows cursor resource value. Navigate to [LoadCursorW](/windows/win32/api/winuser/nf-winuser-loadcursorw) for more details. Otherwise, if custom CSS cursors are being used, this will return 0. To actually use systemCursorId in LoadCursor or LoadImage, MAKEINTRESOURCE must be called on it first.

```cpp
                        UINT32 cursorId;
                        CHECK_FAILURE(m_compositionController->get_SystemCursorId(&cursorId));
                        cursor = ::LoadCursor(nullptr, MAKEINTRESOURCE(cursorId));
                        if (cursor == nullptr)
                        {
                            hr = HRESULT_FROM_WIN32(GetLastError());
                        }
```

#### put_RootVisualTarget

Set the RootVisualTarget property.

> public HRESULT [put_RootVisualTarget](#put_rootvisualtarget)(IUnknown * target)

#### remove_CursorChanged

Remove an event handler previously added with add_CursorChanged.

> public HRESULT [remove_CursorChanged](#remove_cursorchanged)(EventRegistrationToken token)

#### SendMouseInput

If eventKind is COREWEBVIEW2_MOUSE_EVENT_KIND_HORIZONTAL_WHEEL or COREWEBVIEW2_MOUSE_EVENT_KIND_WHEEL, then mouseData specifies the amount of wheel movement.

> public HRESULT [SendMouseInput](#sendmouseinput)(COREWEBVIEW2_MOUSE_EVENT_KIND eventKind, COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS virtualKeys, UINT32 mouseData, POINT point)

A positive value indicates that the wheel was rotated forward, away from the user; a negative value indicates that the wheel was rotated backward, toward the user. One wheel click is defined as WHEEL_DELTA, which is 120. If eventKind is COREWEBVIEW2_MOUSE_EVENT_KIND_X_BUTTON_DOUBLE_CLICK COREWEBVIEW2_MOUSE_EVENT_KIND_X_BUTTON_DOWN, or COREWEBVIEW2_MOUSE_EVENT_KIND_X_BUTTON_UP, then mouseData specifies which X buttons were pressed or released. This value should be 1 if the first X button is pressed/released and 2 if the second X button is pressed/released. If eventKind is COREWEBVIEW2_MOUSE_EVENT_KIND_LEAVE, then virtualKeys, mouseData, and point should all be zero. If eventKind is any other value, then mouseData should be zero. Point is expected to be in the client coordinate space of the WebView. To track mouse events that start in the WebView and can potentially move outside of the WebView and host application, calling SetCapture and ReleaseCapture is recommended. To dismiss hover popups, it is also recommended to send COREWEBVIEW2_MOUSE_EVENT_KIND_LEAVE messages. 
```cpp
bool ViewComponent::OnMouseMessage(UINT message, WPARAM wParam, LPARAM lParam)
{
    // Manually relay mouse messages to the WebView
    if (m_dcompDevice || m_wincompCompositor)
    {
        POINT point;
        POINTSTOPOINT(point, lParam);
        if (message == WM_MOUSEWHEEL || message == WM_MOUSEHWHEEL)
        {
            // Mouse wheel messages are delivered in screen coordinates.
            // SendMouseInput expects client coordinates for the WebView, so convert
            // the point from screen to client.
            ::ScreenToClient(m_appWindow->GetMainWindow(), &point);
        }
        // Send the message to the WebView if the mouse location is inside the
        // bounds of the WebView, if the message is telling the WebView the
        // mouse has left the client area, or if we are currently capturing
        // mouse events.
        bool isMouseInWebView = PtInRect(&m_webViewBounds, point);
        if (isMouseInWebView || message == WM_MOUSELEAVE || m_isCapturingMouse)
        {
            DWORD mouseData = 0;
            switch (message)
            {
            case WM_MOUSEWHEEL:
            case WM_MOUSEHWHEEL:
                mouseData = GET_WHEEL_DELTA_WPARAM(wParam);
                break;
            case WM_XBUTTONDBLCLK:
            case WM_XBUTTONDOWN:
            case WM_XBUTTONUP:
                mouseData = GET_XBUTTON_WPARAM(wParam);
                break;
            case WM_MOUSEMOVE:
                if (!m_isTrackingMouse)
                {
                    // WebView needs to know when the mouse leaves the client area
                    // so that it can dismiss hover popups. TrackMouseEvent will
                    // provide a notification when the mouse leaves the client area.
                    TrackMouseEvents(TME_LEAVE);
                    m_isTrackingMouse = true;
                }
                break;
            case WM_MOUSELEAVE:
                m_isTrackingMouse = false;
                break;
            }

            // We need to capture the mouse in case the user drags the
            // mouse outside of the window bounds and we still need to send
            // mouse messages to the WebView process. This is useful for
            // scenarios like dragging the scroll bar or panning a map.
            // This is very similar to the Pointer Message case where a
            // press started inside of the WebView.
            if (message == WM_LBUTTONDOWN || message == WM_MBUTTONDOWN ||
                message == WM_RBUTTONDOWN || message == WM_XBUTTONDOWN)
            {
                if (isMouseInWebView && ::GetCapture() != m_appWindow->GetMainWindow())
                {
                    m_isCapturingMouse = true;
                    ::SetCapture(m_appWindow->GetMainWindow());
                }
            }
            else if (message == WM_LBUTTONUP || message == WM_MBUTTONUP ||
                message == WM_RBUTTONUP || message == WM_XBUTTONUP)
            {
                if (::GetCapture() == m_appWindow->GetMainWindow())
                {
                    m_isCapturingMouse = false;
                    ::ReleaseCapture();
                }
            }

            // Adjust the point from app client coordinates to webview client coordinates.
            // WM_MOUSELEAVE messages don't have a point, so don't adjust the point.
            if (message != WM_MOUSELEAVE)
            {
                point.x -= m_webViewBounds.left;
                point.y -= m_webViewBounds.top;
            }

            CHECK_FAILURE(m_compositionController->SendMouseInput(
                static_cast<COREWEBVIEW2_MOUSE_EVENT_KIND>(message),
                static_cast<COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS>(GET_KEYSTATE_WPARAM(wParam)),
                mouseData, point));
            return true;
        }
        else if (message == WM_MOUSEMOVE && m_isTrackingMouse)
        {
            // When the mouse moves outside of the WebView, but still inside the app
            // turn off mouse tracking and send the WebView a leave event.
            m_isTrackingMouse = false;
            TrackMouseEvents(TME_LEAVE | TME_CANCEL);
            OnMouseMessage(WM_MOUSELEAVE, 0, 0);
        }
    }
    return false;
}
```

#### SendPointerInput

SendPointerInput accepts touch or pen pointer input of types defined in COREWEBVIEW2_POINTER_EVENT_KIND.

> public HRESULT [SendPointerInput](#sendpointerinput)(COREWEBVIEW2_POINTER_EVENT_KIND eventKind, [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md) * pointerInfo)

Any pointer input from the system must be converted into an [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md) first.

