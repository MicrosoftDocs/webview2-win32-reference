---
description: Profile2 interface.
title: WebView2 Win32 C++ ICoreWebView2Profile2
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile2
---

# interface ICoreWebView2Profile2

```
interface ICoreWebView2Profile2
  : public ICoreWebView2Profile
```

Profile2 interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[ClearBrowsingData](#clearbrowsingdata) | Clear browsing data based on a data type.
[ClearBrowsingDataAll](#clearbrowsingdataall) | ClearBrowsingDataAll behaves like ClearBrowsingData except that it clears the entirety of the data associated with the profile it is called on.
[ClearBrowsingDataInTimeRange](#clearbrowsingdataintimerange) | ClearBrowsingDataInTimeRange behaves like ClearBrowsingData except that it takes in two additional parameters for the start and end time for which it should clear the data between.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### ClearBrowsingData

Clear browsing data based on a data type.

> public HRESULT [ClearBrowsingData](#clearbrowsingdata)(COREWEBVIEW2_BROWSING_DATA_KINDS dataKinds, ICoreWebView2ClearBrowsingDataCompletedHandler * handler)

This method takes two parameters, the first being a mask of one or more `COREWEBVIEW2_BROWSING_DATA_KINDS`. OR operation(s) can be applied to multiple `COREWEBVIEW2_BROWSING_DATA_KINDS` to create a mask representing those data types. The browsing data kinds that are supported are listed below. These data kinds follow a hierarchical structure in which nested bullet points are included in their parent bullet point's data kind. Ex: All DOM storage is encompassed in all site data which is encompassed in all profile data.

* All Profile

* All Site Data

* All DOM Storage: File Systems, Indexed DB, Local Storage, Web SQL, Cache Storage

* Cookies

* Disk Cache

* Download History

* General Autofill

* Password Autosave

* Browsing History

* Settings The completed handler will be invoked when the browsing data has been cleared and will indicate if the specified data was properly cleared. In the case in which the operation is interrupted and the corresponding data is not fully cleared the handler will return `E_ABORT` and otherwise will return `S_OK`. Because this is an asynchronous operation, code that is dependent on the cleared data must be placed in the callback of this operation. If the WebView object is closed before the clear browsing data operation has completed, the handler will be released, but not invoked. In this case the clear browsing data operation may or may not be completed. ClearBrowsingData clears the `dataKinds` regardless of timestamp.

#### ClearBrowsingDataAll

ClearBrowsingDataAll behaves like ClearBrowsingData except that it clears the entirety of the data associated with the profile it is called on.

> public HRESULT [ClearBrowsingDataAll](#clearbrowsingdataall)([ICoreWebView2ClearBrowsingDataCompletedHandler](icorewebview2clearbrowsingdatacompletedhandler.md) * handler)

It clears the data regardless of timestamp.

```cpp
bool AppWindow::ClearBrowsingData(COREWEBVIEW2_BROWSING_DATA_KINDS dataKinds)
{
    auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
    CHECK_FEATURE_RETURN(webView2_13);
    wil::com_ptr<ICoreWebView2Profile> webView2Profile;
    CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
    CHECK_FEATURE_RETURN(webView2Profile);
    auto webView2Profile2 = webView2Profile.try_query<ICoreWebView2Profile2>();
    CHECK_FEATURE_RETURN(webView2Profile2);
    // Clear the browsing data from the last hour.
    double endTime = (double)std::time(nullptr);
    double startTime = endTime - 3600.0;
    CHECK_FAILURE(webView2Profile2->ClearBrowsingDataInTimeRange(
        dataKinds, startTime, endTime,
        Callback<ICoreWebView2ClearBrowsingDataCompletedHandler>(
            [this](HRESULT error) -> HRESULT {
                AsyncMessageBox(L"Completed", L"Clear Browsing Data");
                return S_OK;
            })
            .Get()));
    return true;
}
```

#### ClearBrowsingDataInTimeRange

ClearBrowsingDataInTimeRange behaves like ClearBrowsingData except that it takes in two additional parameters for the start and end time for which it should clear the data between.

> public HRESULT [ClearBrowsingDataInTimeRange](#clearbrowsingdataintimerange)(COREWEBVIEW2_BROWSING_DATA_KINDS dataKinds, double startTime, double endTime, [ICoreWebView2ClearBrowsingDataCompletedHandler](icorewebview2clearbrowsingdatacompletedhandler.md) * handler)

The `startTime` and `endTime` parameters correspond to the number of seconds since the UNIX epoch. `startTime` is inclusive while `endTime` is exclusive, therefore the data will be cleared between [startTime, endTime).

