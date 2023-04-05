---
description: This is the result for ExecuteScriptWithResult.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalExecuteScriptResult
ms.date: 04/05/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalExecuteScriptResult
---

# interface ICoreWebView2ExperimentalExecuteScriptResult

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalExecuteScriptResult
  : public IUnknown
```

This is the result for ExecuteScriptWithResult.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Exception](#get_exception) | If Succeeded is false, you can use this property to get the unhandled exception thrown by script execution Note that due to the compatibility of the WinRT/.NET interface, S_OK will be returned even if the acquisition fails.
[get_ResultAsJson](#get_resultasjson) | A function that has no explicit return value returns undefined.
[get_Succeeded](#get_succeeded) | This property is true if ExecuteScriptWithResult successfully executed script with no unhandled exceptions and the result is available in the ResultAsJson property or via the TryGetResultAsString method.
[TryGetResultAsString](#trygetresultasstring) | If Succeeded is true and the result of script execution is a string, this method provides the value of the string result, and we will get the `FALSE` var value when the js result is not string type.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1466

## Members

#### get_Exception

If Succeeded is false, you can use this property to get the unhandled exception thrown by script execution Note that due to the compatibility of the WinRT/.NET interface, S_OK will be returned even if the acquisition fails.

> public HRESULT [get_Exception](#get_exception)([ICoreWebView2ExperimentalScriptException](icorewebview2experimentalscriptexception.md) ** exception)

We can determine whether the acquisition is successful by judging whether the `exception` is nullptr.

#### get_ResultAsJson

A function that has no explicit return value returns undefined.

> public HRESULT [get_ResultAsJson](#get_resultasjson)(LPWSTR * jsonResult)

If the script that was run throws an unhandled exception, then the result is also "null". This method is applied asynchronously. If the method is run before `ContentLoading`, the script will not be executed and the string "null" will be returned. The return value description is as follows

1. S_OK: Execution succeeds.

1. E_POINTER: When the `jsonResult` is nullptr.

#### get_Succeeded

This property is true if ExecuteScriptWithResult successfully executed script with no unhandled exceptions and the result is available in the ResultAsJson property or via the TryGetResultAsString method.

> public HRESULT [get_Succeeded](#get_succeeded)(BOOL * value)

If it is false then the script execution had an unhandled exception which you can get via the Exception property.

#### TryGetResultAsString

If Succeeded is true and the result of script execution is a string, this method provides the value of the string result, and we will get the `FALSE` var value when the js result is not string type.

> public HRESULT [TryGetResultAsString](#trygetresultasstring)(LPWSTR * stringResult, BOOL * value)

The return value description is as follows

1. S_OK: Execution succeeds.

1. E_POINTER: When the `stringResult` or `value` is nullptr. NOTE: If the `value` returns `FALSE`, the `stringResult` will be set to a empty string.

