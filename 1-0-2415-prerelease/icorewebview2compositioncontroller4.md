---
description: This Interface includes an API which enables non-client hit-testing support for WebView2.
title: WebView2 Win32 C++ ICoreWebView2CompositionController4
ms.date: 02/26/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CompositionController4
topic_type: 
- APIRef
api_name:
- ICoreWebView2CompositionController4
- ICoreWebView2CompositionController4.add_NonClientRegionChanged
- ICoreWebView2CompositionController4.GetNonClientRegionAtPoint
- ICoreWebView2CompositionController4.QueryNonClientRegion
- ICoreWebView2CompositionController4.remove_NonClientRegionChanged
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CompositionController4

```
interface ICoreWebView2CompositionController4
  : public ICoreWebView2CompositionController3
```

This Interface includes an API which enables non-client hit-testing support for WebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_NonClientRegionChanged](#add_nonclientregionchanged) | This method is used to add a listener for NonClientRegionChanged.
[GetNonClientRegionAtPoint](#getnonclientregionatpoint) | If you are hosting a WebView2 using CoreWebView2CompositionController, you can call this method in your Win32 WndProc to determine if the mouse is moving over or clicking on WebView2 web content that should be considered part of a non-client region.
[QueryNonClientRegion](#querynonclientregion) | This method is used to get the collection of rects that correspond to a particular COREWEBVIEW2_NON_CLIENT_REGION_KIND.
[remove_NonClientRegionChanged](#remove_nonclientregionchanged) | This method is used to remove an event handler previously added with add_NonClientRegionChanged.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### add_NonClientRegionChanged

This method is used to add a listener for NonClientRegionChanged.

> public HRESULT [add_NonClientRegionChanged](#add_nonclientregionchanged)([ICoreWebView2NonClientRegionChangedEventHandler](icorewebview2nonclientregionchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

The event is fired when regions which are marked as non-client in the app html have changed. So either when new regions have been marked, or unmarked, or the region(s) have been changed to a different kind.

```cpp
void ScenarioNonClientRegionSupport::AddChangeListener()
{
    if (m_compController4)
    {
        CHECK_FAILURE(m_compController4->add_NonClientRegionChanged(
            Callback<ICoreWebView2NonClientRegionChangedEventHandler>(
                [this](
                    ICoreWebView2CompositionController* sender,
                    ICoreWebView2NonClientRegionChangedEventArgs* args) -> HRESULT
                {
                    COREWEBVIEW2_NON_CLIENT_REGION_KIND region =
                        COREWEBVIEW2_NON_CLIENT_REGION_KIND_NOWHERE;
                    args->get_RegionKind(&region);
                    wil::com_ptr<ICoreWebView2RegionRectCollectionView> regionsCollection;
                    m_compController4->QueryNonClientRegion(region, &regionsCollection);
                    UINT32 count = 0;
                    regionsCollection->get_Count(&count);
                    RECT rect;
                    regionsCollection->GetValueAtIndex(0, &rect);
                    return S_OK;
                })
                .Get(),
            &m_nonClientRegionChanged));
    }
}
```

#### GetNonClientRegionAtPoint

If you are hosting a WebView2 using CoreWebView2CompositionController, you can call this method in your Win32 WndProc to determine if the mouse is moving over or clicking on WebView2 web content that should be considered part of a non-client region.

> public HRESULT [GetNonClientRegionAtPoint](#getnonclientregionatpoint)(POINT point, COREWEBVIEW2_NON_CLIENT_REGION_KIND * value)

The point parameter is expected to be in the client coordinate space of WebView2. The method sets the out parameter value as follows:

* COREWEBVIEW2_NON_CLIENT_REGION_KIND_CAPTION when point corresponds to a region (HTML element) within the WebView2 with `-webkit-app-region: drag` CSS style set.

* COREWEBVIEW2_NON_CLIENT_REGION_KIND_CLIENT when point corresponds to a region (HTML element) within the WebView2 without `-webkit-app-region: drag` CSS style set.

* COREWEBVIEW2_NON_CLIENT_REGION_KIND_NOWHERE when point is not within the WebView2.

NOTE: in order for WebView2 to properly handle the title bar system menu, the app needs to send WM_NCRBUTTONDOWN and WM_NCRBUTTONUP to SendMouseInput. See sample code below. 
```cpp
            || message == WM_NCRBUTTONDOWN || message == WM_NCRBUTTONUP
```

```cpp
    if (message == WM_NCHITTEST && compositionController4)
    {
        POINT point{GET_X_LPARAM(lParam), GET_Y_LPARAM(lParam)};
        ScreenToClient(hWnd, &point);
        if (PtInRect(&m_webViewBounds, point))
        {
            point.x -= m_webViewBounds.left;
            point.y -= m_webViewBounds.top;

            COREWEBVIEW2_NON_CLIENT_REGION_KIND region =
                COREWEBVIEW2_NON_CLIENT_REGION_KIND_NOWHERE;
            CHECK_FAILURE(compositionController4->GetNonClientRegionAtPoint(point, &region));
            *result = region;
            return true;
        }
    }
```

#### QueryNonClientRegion

This method is used to get the collection of rects that correspond to a particular COREWEBVIEW2_NON_CLIENT_REGION_KIND.

> public HRESULT [QueryNonClientRegion](#querynonclientregion)(COREWEBVIEW2_NON_CLIENT_REGION_KIND kind, [ICoreWebView2RegionRectCollectionView](icorewebview2regionrectcollectionview.md) ** rects)

This is to be used in the callback of add_NonClientRegionChanged whose event args object contains a region property of type COREWEBVIEW2_NON_CLIENT_REGION_KIND.

```cpp
void ScenarioNonClientRegionSupport::AddChangeListener()
{
    if (m_compController4)
    {
        CHECK_FAILURE(m_compController4->add_NonClientRegionChanged(
            Callback<ICoreWebView2NonClientRegionChangedEventHandler>(
                [this](
                    ICoreWebView2CompositionController* sender,
                    ICoreWebView2NonClientRegionChangedEventArgs* args) -> HRESULT
                {
                    COREWEBVIEW2_NON_CLIENT_REGION_KIND region =
                        COREWEBVIEW2_NON_CLIENT_REGION_KIND_NOWHERE;
                    args->get_RegionKind(&region);
                    wil::com_ptr<ICoreWebView2RegionRectCollectionView> regionsCollection;
                    m_compController4->QueryNonClientRegion(region, &regionsCollection);
                    UINT32 count = 0;
                    regionsCollection->get_Count(&count);
                    RECT rect;
                    regionsCollection->GetValueAtIndex(0, &rect);
                    return S_OK;
                })
                .Get(),
            &m_nonClientRegionChanged));
    }
}
```

#### remove_NonClientRegionChanged

This method is used to remove an event handler previously added with add_NonClientRegionChanged.

> public HRESULT [remove_NonClientRegionChanged](#remove_nonclientregionchanged)(EventRegistrationToken token)

