---
description: A continuation of the ICoreWebView2Environment interface for getting the crash dump folder path.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment
ms.date: 10/10/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment
---

# interface ICoreWebView2ExperimentalEnvironment

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment
  : public IUnknown
```

A continuation of the ICoreWebView2Environment interface for getting the crash dump folder path.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FailureReportFolderPath](#get_failurereportfolderpath) | `FailureReportFolderPath` returns the path of the folder where minidump files are written.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_FailureReportFolderPath

`FailureReportFolderPath` returns the path of the folder where minidump files are written.

> public HRESULT [get_FailureReportFolderPath](#get_failurereportfolderpath)(LPWSTR * value)

Whenever a WebView2 process crashes, a crash dump file will be created in the crash dump folder. The crash dump format is minidump files. Please see [Minidump Files documentation](/windows/win32/debug/minidump-files) for detailed information. Normally when a single child process fails, a minidump will be generated and written to disk, then the `ProcessFailed` event is raised. But for unexpected crashes, a minidump file might not be generated at all, despite whether `ProcessFailed` event is raised. If there are multiple process failures at once, multiple minidump files could be generated. Thus `FailureReportFolderPath` could contain old minidump files that are not associated with a specific `ProcessFailed` event. 
```cpp
        auto experimental_environment =
            m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment>();
        CHECK_FEATURE_RETURN(experimental_environment);
        wil::unique_cotaskmem_string failureReportFolder;
        experimental_environment->get_FailureReportFolderPath(&failureReportFolder);
        MessageBox(m_mainWindow, failureReportFolder.get(), L"Failure Report Folder", MB_OK);
```

