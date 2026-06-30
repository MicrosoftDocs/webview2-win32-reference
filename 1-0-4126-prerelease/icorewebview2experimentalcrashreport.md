---
description: Provides crash signature data captured at the moment of process failure.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCrashReport
ms.date: 06/30/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCrashReport
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalCrashReport
- ICoreWebView2ExperimentalCrashReport.get_BucketId
- ICoreWebView2ExperimentalCrashReport.get_CrashReportId
- ICoreWebView2ExperimentalCrashReport.get_ExceptionCode
- ICoreWebView2ExperimentalCrashReport.get_FaultingModuleName
- ICoreWebView2ExperimentalCrashReport.get_FaultingModuleVersion
- ICoreWebView2ExperimentalCrashReport.get_FaultOffset
- ICoreWebView2ExperimentalCrashReport.get_ReportTime
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalCrashReport

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalCrashReport
  : public IUnknown
```

Provides crash signature data captured at the moment of process failure.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_BucketId](#get_bucketid) | Crash bucket identifier assigned by Microsoft's crash telemetry service.
[get_CrashReportId](#get_crashreportid) | The unique identifier (UUID) for this crash report.
[get_ExceptionCode](#get_exceptioncode) | The Windows exception code for the failure, e.g.
[get_FaultingModuleName](#get_faultingmodulename) | Basename of the module containing the faulting instruction, e.g.
[get_FaultingModuleVersion](#get_faultingmoduleversion) | Version of the faulting module, e.g.
[get_FaultOffset](#get_faultoffset) | Relative virtual address (RVA) of the faulting instruction within `FaultingModuleName`.
[get_ReportTime](#get_reporttime) | Time the crash report was recorded, as a Windows FILETIME value (100-nanosecond intervals since Jan 1 1601 UTC).

CrashReport is null when the failure did not produce a crash report (normal exit, external kill, launch failure, hang). CrashReport may be null for certain crash-type failures where no crash report was produced; host apps should always check for null before accessing properties.

```cpp
                    // Query for the crash report (available when Crashpad handled
                    // the crash; nullptr for __fastfail / WER-only crashes).
                    auto experimentalArgs2 =
                        args.try_query<ICoreWebView2ExperimentalProcessFailedEventArgs2>();
                    if (experimentalArgs2)
                    {
                        wil::com_ptr<ICoreWebView2ExperimentalCrashReport> crashReport;
                        CHECK_FAILURE(experimentalArgs2->get_CrashReport(&crashReport));
                        if (crashReport)
                        {
                            wil::unique_cotaskmem_string crashReportId;
                            if (SUCCEEDED(crashReport->get_CrashReportId(&crashReportId)) &&
                                crashReportId)
                            {
                                message << L"\nCrash Report ID: " << crashReportId.get();
                            }

                            UINT32 exceptionCode;
                            if (SUCCEEDED(crashReport->get_ExceptionCode(&exceptionCode)))
                            {
                                message << L"\nException Code: 0x" << std::hex << exceptionCode
                                        << std::dec;
                            }

                            wil::unique_cotaskmem_string faultingModuleName;
                            if (SUCCEEDED(
                                    crashReport->get_FaultingModuleName(&faultingModuleName)) &&
                                faultingModuleName)
                            {
                                message << L"\nFaulting Module: " << faultingModuleName.get();
                            }

                            wil::unique_cotaskmem_string faultingModuleVersion;
                            if (SUCCEEDED(crashReport->get_FaultingModuleVersion(
                                    &faultingModuleVersion)) &&
                                faultingModuleVersion)
                            {
                                message << L"\nModule Version: " << faultingModuleVersion.get();
                            }

                            UINT64 faultOffset;
                            if (SUCCEEDED(crashReport->get_FaultOffset(&faultOffset)))
                            {
                                message << L"\nFault Offset: 0x" << std::hex << faultOffset
                                        << std::dec;
                            }

                            wil::unique_cotaskmem_string bucketId;
                            if (SUCCEEDED(crashReport->get_BucketId(&bucketId)) && bucketId)
                            {
                                message << L"\nCrash Bucket: " << bucketId.get();
                            }

                            UINT64 reportTime;
                            if (SUCCEEDED(crashReport->get_ReportTime(&reportTime)))
                            {
                                message << L"\nReport Time: " << reportTime;
                            }
                        }
                    }
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_BucketId

Crash bucket identifier assigned by Microsoft's crash telemetry service.

> public HRESULT [get_BucketId](#get_bucketid)(LPWSTR * value)

Returned as a 32-character hex string. Empty when no bucket was assigned: crash data was not uploaded to Microsoft's telemetry service (custom crash reporting enabled), or no response was received from the telemetry service (network throttled or unavailable).

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_CrashReportId

The unique identifier (UUID) for this crash report.

> public HRESULT [get_CrashReportId](#get_crashreportid)(LPWSTR * value)

Use this to locate the corresponding dump file in `FailureReportFolderPath`.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_ExceptionCode

The Windows exception code for the failure, e.g.

> public HRESULT [get_ExceptionCode](#get_exceptioncode)(UINT32 * value)

`0xC0000005` for `STATUS_ACCESS_VIOLATION`. `0` if not available.

#### get_FaultingModuleName

Basename of the module containing the faulting instruction, e.g.

> public HRESULT [get_FaultingModuleName](#get_faultingmodulename)(LPWSTR * value)

`renderer.dll`.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_FaultingModuleVersion

Version of the faulting module, e.g.

> public HRESULT [get_FaultingModuleVersion](#get_faultingmoduleversion)(LPWSTR * value)

`128.0.2739.42`.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_FaultOffset

Relative virtual address (RVA) of the faulting instruction within `FaultingModuleName`.

> public HRESULT [get_FaultOffset](#get_faultoffset)(UINT64 * value)

`0` if not available.

#### get_ReportTime

Time the crash report was recorded, as a Windows FILETIME value (100-nanosecond intervals since Jan 1 1601 UTC).

> public HRESULT [get_ReportTime](#get_reporttime)(UINT64 * value)

`0` if unavailable.

