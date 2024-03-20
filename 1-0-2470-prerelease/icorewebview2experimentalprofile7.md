---
description: This is the ICoreWebView2 experimental profile interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile7
ms.date: 03/25/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile7
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfile7
- ICoreWebView2ExperimentalProfile7.ClearCustomDataPartition
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfile7

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile7
  : public IUnknown
```

This is the [ICoreWebView2](icorewebview2.md#icorewebview2) experimental profile interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[ClearCustomDataPartition](#clearcustomdatapartition) | Clears all DOM storage and cookies in the custom data partition identified by the `customDataPartitionId`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### ClearCustomDataPartition

Clears all DOM storage and cookies in the custom data partition identified by the `customDataPartitionId`.

> public HRESULT [ClearCustomDataPartition](#clearcustomdatapartition)(LPCWSTR customDataPartitionId, [ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler](icorewebview2experimentalclearcustomdatapartitioncompletedhandler.md#icorewebview2experimentalclearcustomdatapartitioncompletedhandler) * handler)

If `customDataPartitionId` is nullptr or empty string, the API will fail with E_INVALIDARG. If no partition is found for the specified `customDataPartitionId`, the API succeeds without doing anything. As DOM storage and cookies in the custom data partition is also browsing data, they will also be cleared when `ClearBrowsingData`, `ClearBrowsingDataInTimeRange` or `ClearBrowsingDataAll` is called and the clearing condition is met.

```cpp
bool AppWindow::ClearCustomDataPartition()
{
    auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
    CHECK_FEATURE_RETURN(webView2_13);
    wil::com_ptr<ICoreWebView2Profile> webView2Profile;
    CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
    CHECK_FEATURE_RETURN(webView2Profile);
    auto webView2Profile7 = webView2Profile.try_query<ICoreWebView2ExperimentalProfile7>();
    CHECK_FEATURE_RETURN(webView2Profile7);
    std::wstring partitionToClearData;
    wil::com_ptr<ICoreWebView2Experimental20> webViewStaging20;
    webViewStaging20 = m_webView.try_query<ICoreWebView2Experimental20>();
    wil::unique_cotaskmem_string partitionId;
    CHECK_FAILURE(webViewStaging20->get_CustomDataPartitionId(&partitionId));
    if (!partitionId.get() || !*partitionId.get())
    {
        TextInputDialog dialog(
            GetMainWindow(), L"Custom Data Partition Id", L"Custom Data Partition Id:",
            L"Enter custom data partition id");
        if (dialog.confirmed)
        {
            partitionToClearData = dialog.input.c_str();
        }
    }
    else
    {
        // Use partition id from the WebView.
        partitionToClearData = partitionId.get();
    }
    if (!partitionToClearData.empty())
    {
        CHECK_FAILURE(webView2Profile7->ClearCustomDataPartition(
            partitionToClearData.c_str(),
            Callback<ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler>(
                [this](HRESULT result) -> HRESULT
                {
                    if (SUCCEEDED(result))
                    {
                        AsyncMessageBox(L"Completed", L"Clear Custom Data Partition");
                    }
                    else
                    {
                        std::wstringstream message;
                        message << L"Failed: " << std::to_wstring(result) << L"(0x" << std::hex
                                << result << L")" << std::endl;
                        AsyncMessageBox(message.str(), L"Clear Custom Data Partition");
                    }
                    return S_OK;
                })
                .Get()));
    }
    return true;
}
```

