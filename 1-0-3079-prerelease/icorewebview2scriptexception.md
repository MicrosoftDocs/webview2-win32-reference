---
description: This interface represents a JavaScript exception.
title: WebView2 Win32 C++ ICoreWebView2ScriptException
ms.date: 01/16/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ScriptException
topic_type: 
- APIRef
api_name:
- ICoreWebView2ScriptException
- ICoreWebView2ScriptException.get_ColumnNumber
- ICoreWebView2ScriptException.get_LineNumber
- ICoreWebView2ScriptException.get_Message
- ICoreWebView2ScriptException.get_Name
- ICoreWebView2ScriptException.get_ToJson
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ScriptException

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ScriptException
  : public IUnknown
```

This interface represents a JavaScript exception.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ColumnNumber](#get_columnnumber) | The column number of the source where the exception occurred.
[get_LineNumber](#get_linenumber) | The line number of the source where the exception occurred.
[get_Message](#get_message) | The Message is the exception's message and potentially stack.
[get_Name](#get_name) | The Name is the exception's class name.
[get_ToJson](#get_tojson) | This will return all details of the exception as a JSON string.

If the CoreWebView2.ExecuteScriptWithResult result has Succeeded as false, you can use the result's Exception property to get the script exception.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2277.86
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### get_ColumnNumber

The column number of the source where the exception occurred.

> public HRESULT [get_ColumnNumber](#get_columnnumber)(UINT32 * value)

In the JSON it is `exceptionDetail.columnNumber`. Note that this position starts at 0.

#### get_LineNumber

The line number of the source where the exception occurred.

> public HRESULT [get_LineNumber](#get_linenumber)(UINT32 * value)

In the JSON it is `exceptionDetail.lineNumber`. Note that this position starts at 0.

#### get_Message

The Message is the exception's message and potentially stack.

> public HRESULT [get_Message](#get_message)(LPWSTR * value)

In the JSON it is exceptionDetail.exception.description. This is the empty string if the exception doesn't have a description. This can happen if the script throws a non-Error object such as throw "abc";.

#### get_Name

The Name is the exception's class name.

> public HRESULT [get_Name](#get_name)(LPWSTR * value)

In the JSON it is `exceptionDetail.exception.className`. This is the empty string if the exception doesn't have a class name. This can happen if the script throws a non-Error object such as `throw "abc";`

#### get_ToJson

This will return all details of the exception as a JSON string.

> public HRESULT [get_ToJson](#get_tojson)(LPWSTR * value)

In the case that script has thrown a non-Error object such as `throw "abc";` or any other non-Error object, you can get object specific properties.

