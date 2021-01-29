---
description: The ICoreWebView2Controller Experimental interface to manage rasterization scale.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalController
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/29/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalController
---

# interface ICoreWebView2ExperimentalController

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalController
  : public IUnknown
```

The [ICoreWebView2Controller](icorewebview2controller.md) Experimental interface to manage rasterization scale.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_RasterizationScaleChanged](#add_rasterizationscalechanged) | Add an event handler for the RasterizationScaleChanged event.
[get_BoundsMode](#get_boundsmode) | BoundsMode affects how setting the Bounds and RasterizationScale properties work.
[get_RasterizationScale](#get_rasterizationscale) | The rasterization scale for the WebView.
[get_ShouldDetectMonitorScaleChanges](#get_shoulddetectmonitorscalechanges) | ShouldDetectMonitorScaleChanges property determines whether the WebView attempts to track monitor DPI scale changes.
[put_BoundsMode](#put_boundsmode) | Set the BoundsMode property.
[put_RasterizationScale](#put_rasterizationscale) | Set the rasterization scale property.
[put_ShouldDetectMonitorScaleChanges](#put_shoulddetectmonitorscalechanges) | Set the ShouldDetectMonitorScaleChanges property.
[remove_RasterizationScaleChanged](#remove_rasterizationscalechanged) | Remove an event handler previously added with add_RasterizationScaleChanged.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    
WebView2 Win32 Prerelease |    1.0.721

## Members

#### add_RasterizationScaleChanged

Add an event handler for the RasterizationScaleChanged event.

> public HRESULT [add_RasterizationScaleChanged](#add_rasterizationscalechanged)([ICoreWebView2ExperimentalRasterizationScaleChangedEventHandler](icorewebview2experimentalrasterizationscalechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

The event is raised when the WebView detects that the monitor DPI scale has changed, ShouldDetectMonitorScaleChanges is true, and the WebView has changed the RasterizationScale property.

```cpp
        CHECK_FAILURE(m_controllerExperimental->add_RasterizationScaleChanged(
            Callback<ICoreWebView2ExperimentalRasterizationScaleChangedEventHandler>(
                [this](ICoreWebView2ExperimentalController* sender, IUnknown* args) -> HRESULT {
                    double rasterizationScale;
                    CHECK_FAILURE(m_controllerExperimental->get_RasterizationScale(&rasterizationScale));

                    std::wstring message = L"WebView2APISample (RasterizationScale: " +
                        std::to_wstring(int(rasterizationScale * 100)) + L"%)";
                    SetWindowText(m_appWindow->GetMainWindow(), message.c_str());
                    return S_OK;
                })
            .Get(), &m_rasterizationScaleChangedToken));
```

#### get_BoundsMode

BoundsMode affects how setting the Bounds and RasterizationScale properties work.

> public HRESULT [get_BoundsMode](#get_boundsmode)(COREWEBVIEW2_BOUNDS_MODE * boundsMode)

Bounds mode can either be in COREWEBVIEW2_BOUNDS_MODE_USE_RAW_PIXELS mode or COREWEBVIEW2_BOUNDS_MODE_USE_RASTERIZATION_SCALE mode.

When the mode is in COREWEBVIEW2_BOUNDS_MODE_USE_RAW_PIXELS, setting the bounds property will set the size of the WebView in raw screen pixels. Changing the rasterization scale in this mode won't change the raw pixel size of the WebView and will only change the rasterization scale.

When the mode is in COREWEBVIEW2_BOUNDS_MODE_USE_RASTERIZATION_SCALE, setting the bounds property will change the logical size of the WebView which can be described by the following equation: 
```text
Logical size * rasterization scale = Raw Pixel size
```
 In this case, changing the rasterization scale will keep the logical size the same and change the raw pixel size.

```cpp
void ViewComponent::SetBoundsMode(COREWEBVIEW2_BOUNDS_MODE boundsMode)
{
    CHECK_FEATURE_RETURN(m_controllerExperimental, (void)0);
    m_boundsMode = boundsMode;
    CHECK_FAILURE(m_controllerExperimental->put_BoundsMode(boundsMode));
    ResizeWebView();
}
```

#### get_RasterizationScale

The rasterization scale for the WebView.

> public HRESULT [get_RasterizationScale](#get_rasterizationscale)(double * scale)

The rasterization scale is the combination of the monitor DPI scale and text scaling set by the user. This value should be updated when the DPI scale of the app's top level window changes (i.e. monitor DPI scale changes or window changes monitor) or when the text scale factor of the system changes.

```cpp
    case WM_DPICHANGED:
    {
        m_toolbar.UpdateDpiAndTextScale();
        if (auto view = GetComponent<ViewComponent>())
        {
            view->UpdateDpiAndTextScale();
        }

        RECT* const newWindowSize = reinterpret_cast<RECT*>(lParam);
        SetWindowPos(hWnd,
            nullptr,
            newWindowSize->left,
            newWindowSize->top,
            newWindowSize->right - newWindowSize->left,
            newWindowSize->bottom - newWindowSize->top,
            SWP_NOZORDER | SWP_NOACTIVATE);
        return true;
    }
    break;
```

```cpp
    if (winrt::try_get_activation_factory<winrt::Windows::UI::ViewManagement::UISettings>())
    {
        m_uiSettings = winrt::Windows::UI::ViewManagement::UISettings();
        m_uiSettings.TextScaleFactorChanged({ this, &AppWindow::OnTextScaleChanged });
    }
```

```cpp
void AppWindow::OnTextScaleChanged(
    winrt::Windows::UI::ViewManagement::UISettings const& settings,
    winrt::Windows::Foundation::IInspectable const& args)
{
    RunAsync([this] {
        m_toolbar.UpdateDpiAndTextScale();
        if (auto view = GetComponent<ViewComponent>())
        {
            view->UpdateDpiAndTextScale();
        }
    });
}
```
 Rasterization scale applies to the WebView content, as well as popups, context menus, scroll bars, etc. Normal app scaling scenarios should use the ZoomFactor property or SetBoundsAndZoomFactor API.

```cpp
void ViewComponent::SetRasterizationScale(float additionalScale)
{
    if (m_controllerExperimental)
    {
        CHECK_FAILURE(m_controllerExperimental->put_ShouldDetectMonitorScaleChanges(FALSE));
        m_webviewAdditionalRasterizationScale = additionalScale;
        double rasterizationScale =
            additionalScale * m_appWindow->GetDpiScale() * m_appWindow->GetTextScale();
        CHECK_FAILURE(m_controllerExperimental->put_RasterizationScale(rasterizationScale));
    }
}
```

#### get_ShouldDetectMonitorScaleChanges

ShouldDetectMonitorScaleChanges property determines whether the WebView attempts to track monitor DPI scale changes.

> public HRESULT [get_ShouldDetectMonitorScaleChanges](#get_shoulddetectmonitorscalechanges)(BOOL * value)

When true, the WebView will track monitor DPI scale changes, update the RasterizationScale property, and raises RasterizationScaleChanged event. When false, the WebView will not track monitor DPI scale changes, and the app must update the RasterizationScale property itself. RasterizationScaleChanged event will never raise when ShouldDetectMonitorScaleChanges is false.

#### put_BoundsMode

Set the BoundsMode property.

> public HRESULT [put_BoundsMode](#put_boundsmode)(COREWEBVIEW2_BOUNDS_MODE boundsMode)

#### put_RasterizationScale

Set the rasterization scale property.

> public HRESULT [put_RasterizationScale](#put_rasterizationscale)(double scale)

#### put_ShouldDetectMonitorScaleChanges

Set the ShouldDetectMonitorScaleChanges property.

> public HRESULT [put_ShouldDetectMonitorScaleChanges](#put_shoulddetectmonitorscalechanges)(BOOL value)

#### remove_RasterizationScaleChanged

Remove an event handler previously added with add_RasterizationScaleChanged.

> public HRESULT [remove_RasterizationScaleChanged](#remove_rasterizationscalechanged)(EventRegistrationToken token)

