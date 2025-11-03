---
description: Extension of the ICoreWebView2 interface that provides sensitivity classification of a web page.
title: WebView2 Win32 C++ ICoreWebView2Experimental32
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental32
topic_type: 
- APIRef
api_name:
- ICoreWebView2Experimental32
- ICoreWebView2Experimental32.add_SensitivityInfoChanged
- ICoreWebView2Experimental32.get_SensitivityInfo
- ICoreWebView2Experimental32.remove_SensitivityInfoChanged
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Experimental32

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental32
  : public IUnknown
```

Extension of the [ICoreWebView2](icorewebview2.md#icorewebview2) interface that provides sensitivity classification of a web page.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_SensitivityInfoChanged](#add_sensitivityinfochanged) | Adds an event handler for the `SensitivityInfoChanged` event.
[get_SensitivityInfo](#get_sensitivityinfo) | Gets the current state of sensitivity label detection for the content loaded in the WebView2 control.
[remove_SensitivityInfoChanged](#remove_sensitivityinfochanged) | Removes an event handler previously added with `add_SensitivityInfoChanged`.

This interface enables applications to monitor and respond to changes in the sensitivity classification of web content loaded in the WebView2 control. When sensitivity labels are detected, updated, or removed from web pages, the `SensitivityInfoChanged` event is raised.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3590

## Members

#### add_SensitivityInfoChanged

Adds an event handler for the `SensitivityInfoChanged` event.

> public HRESULT [add_SensitivityInfoChanged](#add_sensitivityinfochanged)([ICoreWebView2ExperimentalSensitivityInfoChangedEventHandler](icorewebview2experimentalsensitivityinfochangedeventhandler.md#icorewebview2experimentalsensitivityinfochangedeventhandler) * eventHandler, EventRegistrationToken * token)

Event raised when the sensitivity label classification of web page changes. Web page may report sensitivity labels via [`Page Interaction Restriction Manager`](https://github.com/MicrosoftEdge/MSEdgeExplainers/blob/main/PageInteractionRestrictionManager/explainer.md). This event is triggered when the WebView2 control detects a change in the sensitivity labels associated with the currently loaded web page. Changes can occur when navigating to a new page in the main frame, when the existing page updates its sensitivity label information. On navigation to a new page `SensitivityInfoChanged` event is raised just after the `NavigationStarting` event. Applications can subscribe to this event to receive notifications about sensitivity changes. The event handler can then query the `SensitivityInfo` property to get the latest sensitivity label information and take appropriate actions based on the updated sensitivity classification.

```cpp
    CHECK_FAILURE(webView32->add_SensitivityInfoChanged(
        Callback<ICoreWebView2ExperimentalSensitivityInfoChangedEventHandler>(
            [this](ICoreWebView2* sender, IUnknown* args) -> HRESULT
            {
                auto webView32 = this->m_webView.try_query<ICoreWebView2Experimental32>();
                Microsoft::WRL::ComPtr<ICoreWebView2ExperimentalSensitivityInfo>
                    sensitivityInfo;
                webView32->get_SensitivityInfo(&sensitivityInfo);

                OnSensitivityChanged(sensitivityInfo.Get());

                return S_OK;
            })
            .Get(),
        &m_sensitivityInfoChangedToken));
```

#### get_SensitivityInfo

Gets the current state of sensitivity label detection for the content loaded in the WebView2 control.

> public HRESULT [get_SensitivityInfo](#get_sensitivityinfo)([ICoreWebView2ExperimentalSensitivityInfo](icorewebview2experimentalsensitivityinfo.md#icorewebview2experimentalsensitivityinfo) ** value)

See `ICoreWebView2SensitivityInfo` for more details.

```cpp
    COREWEBVIEW2_SENSITIVITY_LABELS_STATE sensitivityLabelsState;
    CHECK_FAILURE(sensitivityInfo->get_SensitivityLabelsState(&sensitivityLabelsState));
    Microsoft::WRL::ComPtr<ICoreWebView2ExperimentalSensitivityLabelCollectionView>
        sensitivityLabelsCollection;
    if (sensitivityLabelsState == COREWEBVIEW2_SENSITIVITY_LABELS_STATE_AVAILABLE)
    {
        CHECK_FAILURE(sensitivityInfo->get_SensitivityLabels(&sensitivityLabelsCollection));
    }
```

#### remove_SensitivityInfoChanged

Removes an event handler previously added with `add_SensitivityInfoChanged`.

> public HRESULT [remove_SensitivityInfoChanged](#remove_sensitivityinfochanged)(EventRegistrationToken token)

