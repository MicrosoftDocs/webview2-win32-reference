---
description: This is the result for ExecuteScriptWithResult.
title: WebView2 Win32 C++ ICoreWebView2ExecuteScriptResult
ms.date: 10-29-2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExecuteScriptResult
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExecuteScriptResult
- ICoreWebView2ExecuteScriptResult.get_Exception
- ICoreWebView2ExecuteScriptResult.get_ResultAsJson
- ICoreWebView2ExecuteScriptResult.get_Succeeded
- ICoreWebView2ExecuteScriptResult.TryGetResultAsString
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExecuteScriptResult

```
interface ICoreWebView2ExecuteScriptResult
  : public IUnknown
```

This is the result for ExecuteScriptWithResult.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Exception](#get_exception) | If `Succeeded` is `FALSE`, you can use this property to get the unhandled exception thrown by script execution.
[get_ResultAsJson](#get_resultasjson) | A JSON encoded string that represents the result of running the provided JavaScript.
[get_Succeeded](#get_succeeded) | This property is true if ExecuteScriptWithResult successfully executed script with no unhandled exceptions and the result is available in the ResultAsJson property or via the TryGetResultAsString method.
[TryGetResultAsString](#trygetresultasstring) | If Succeeded is true and the result of script execution is a string, this method provides the value of the string result, and we will get the `FALSE` var value when the js result is not string type.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2277.86
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### get_Exception

If `Succeeded` is `FALSE`, you can use this property to get the unhandled exception thrown by script execution.

> public HRESULT [get_Exception](#get_exception)([ICoreWebView2ScriptException](icorewebview2scriptexception.md#icorewebview2scriptexception) ** exception)

If `Succeeded` is `TRUE`, getting this property fails with `E_INVALIDARG`.

#### get_ResultAsJson

A JSON encoded string that represents the result of running the provided JavaScript.

> public HRESULT [get_ResultAsJson](#get_resultasjson)(LPWSTR * jsonResult)

If the result is undefined, contains a reference cycle, or otherwise is not able to be encoded into JSON, then the result is considered to be null, which is encoded in JSON as the string "null". A function that has no explicit return value returns undefined. If the script that was run throws an unhandled exception, then the result is also "null". This method is applied asynchronously. If the method is run before `ContentLoading`, the script will not be executed and the string "null" will be returned. The return value description is as follows

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

1. E_POINTER: When the `stringResult` or `value` is nullptr. NOTE: If the `value` returns `FALSE`, the `stringResult` will be set to an empty string.

