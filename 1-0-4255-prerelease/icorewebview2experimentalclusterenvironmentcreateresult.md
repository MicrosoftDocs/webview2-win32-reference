---
description: The result of `CreateOrJoinCoreWebView2ClusterEnvironment`, carrying the `Status` and, on success, the shared `Environment`.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalClusterEnvironmentCreateResult
ms.date: 09/03/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalClusterEnvironmentCreateResult
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalClusterEnvironmentCreateResult
- ICoreWebView2ExperimentalClusterEnvironmentCreateResult.get_Environment
- ICoreWebView2ExperimentalClusterEnvironmentCreateResult.get_Status
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalClusterEnvironmentCreateResult

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalClusterEnvironmentCreateResult
  : public IUnknown
```

The result of `CreateOrJoinCoreWebView2ClusterEnvironment`, carrying the `Status` and, on success, the shared `Environment`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Environment](#get_environment) | The shared cluster environment.
[get_Status](#get_status) | The outcome of the operation.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_Environment

The shared cluster environment.

> public HRESULT [get_Environment](#get_environment)([ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) ** value)

Non-null only when `Status` is `COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS_SUCCEEDED`.

#### get_Status

The outcome of the operation.

> public HRESULT [get_Status](#get_status)(COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS * value)

