---
description: A continuation of the ICoreWebView2ProcessFailedEventArgs2 interface fot getting blocked file for code integrity process failures.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProcessFailedEventArgs
ms.date: 01/29/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProcessFailedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProcessFailedEventArgs
- ICoreWebView2ExperimentalProcessFailedEventArgs.get_FailureSourceModulePath
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProcessFailedEventArgs

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProcessFailedEventArgs
  : public IUnknown
```

A continuation of the [ICoreWebView2ProcessFailedEventArgs2](icorewebview2processfailedeventargs2.md) interface fot getting blocked file for code integrity process failures.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FailureSourceModulePath](#get_failuresourcemodulepath) | This property is the full path of the module that caused the crash in cases of Windows Code Integrity failures.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2164

## Members

#### get_FailureSourceModulePath

This property is the full path of the module that caused the crash in cases of Windows Code Integrity failures.

> public HRESULT [get_FailureSourceModulePath](#get_failuresourcemodulepath)(LPWSTR * modulePath)

[Windows Code Integrity](/mem/intune/user-help/you-need-to-enable-code-integrity) is a feature that verifies the integrity and authenticity of dynamic-link libraries (DLLs) on Windows systems. It ensures that only trusted code can run on the system and prevents unauthorized or malicious modifications. When ProcessFailed occurred due to a failed Code Integrity check, this property returns the full path of the file that was prevented from loading on the system. The webview2 process which tried to load the DLL will fail with exit code STATUS_INVALID_IMAGE_HASH(-1073740760). A file can fail integrity check for various reasons, such as:

* It has an invalid or missing signature that does not match the publisher or signer of the file.

* It has been tampered with or corrupted by malware or other software.

* It has been blocked by an administrator or a security policy. This property always will be the empty string if failure is not caused by STATUS_INVALID_IMAGE_HASH.

