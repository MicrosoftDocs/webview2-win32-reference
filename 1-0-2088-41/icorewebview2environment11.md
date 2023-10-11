---
description: A continuation of the ICoreWebView2Environment interface for getting the crash dump folder path.
title: WebView2 Win32 C++ ICoreWebView2Environment11
ms.date: 10/16/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment11
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment11
- ICoreWebView2Environment11.get_FailureReportFolderPath
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment11

```
interface ICoreWebView2Environment11
  : public ICoreWebView2Environment10
```

A continuation of the [ICoreWebView2Environment](icorewebview2environment.md) interface for getting the crash dump folder path.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FailureReportFolderPath](#get_failurereportfolderpath) | `FailureReportFolderPath` returns the path of the folder where minidump files are written.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1518.46
WebView2 Win32 Prerelease |    1.0.1549

## Members

#### get_FailureReportFolderPath

`FailureReportFolderPath` returns the path of the folder where minidump files are written.

> public HRESULT [get_FailureReportFolderPath](#get_failurereportfolderpath)(LPWSTR * value)

Whenever a WebView2 process crashes, a crash dump file will be created in the crash dump folder. The crash dump format is minidump files. Please see [Minidump Files documentation](/windows/win32/debug/minidump-files) for detailed information. Normally when a single child process fails, a minidump will be generated and written to disk, then the `ProcessFailed` event is raised. But for unexpected crashes, a minidump file might not be generated at all, despite whether `ProcessFailed` event is raised. If there are multiple process failures at once, multiple minidump files could be generated. Thus `FailureReportFolderPath` could contain old minidump files that are not associated with a specific `ProcessFailed` event. 
```cpp
        auto environment11 = m_webViewEnvironment.try_query<ICoreWebView2Environment11>();
        CHECK_FEATURE_RETURN(environment11);
        wil::unique_cotaskmem_string failureReportFolder;
        environment11->get_FailureReportFolderPath(&failureReportFolder);
        MessageBox(m_mainWindow, failureReportFolder.get(), L"Failure Report Folder", MB_OK);
```

