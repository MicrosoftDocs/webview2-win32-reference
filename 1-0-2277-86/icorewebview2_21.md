---
description: This is the interface for getting string and exception with ExecuteScriptWithResult.
title: WebView2 Win32 C++ ICoreWebView2_21
ms.date: 02/26/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_21
topic_type: 
- APIRef
api_name:
- ICoreWebView2_21
- ICoreWebView2_21.ExecuteScriptWithResult
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_21

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2_21
  : public ICoreWebView2_20
```

This is the interface for getting string and exception with ExecuteScriptWithResult.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[ExecuteScriptWithResult](#executescriptwithresult) | Run JavaScript code from the JavaScript parameter in the current top-level document rendered in the WebView.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2277.86
WebView2 Win32 Prerelease |    

## Members

#### ExecuteScriptWithResult

Run JavaScript code from the JavaScript parameter in the current top-level document rendered in the WebView.

> public HRESULT [ExecuteScriptWithResult](#executescriptwithresult)(LPCWSTR javaScript, [ICoreWebView2ExecuteScriptWithResultCompletedHandler](icorewebview2executescriptwithresultcompletedhandler.md) * handler)

The result of the execution is returned asynchronously in the CoreWebView2ExecuteScriptResult object which has methods and properties to obtain the successful result of script execution as well as any unhandled JavaScript exceptions. If this method is run after the NavigationStarting event during a navigation, the script runs in the new document when loading it, around the time ContentLoading is run. This operation executes the script even if ICoreWebView2Settings::IsScriptEnabled is set to FALSE.

```cpp
void ScriptComponent::ExecuteScriptWithResult()
{
    TextInputDialog dialog(
        m_appWindow->GetMainWindow(), L"Execute Script With Result", L"Enter script code:",
        L"Enter the JavaScript code to run in the webview.", L"");
    if (dialog.confirmed)
    {
        wil::com_ptr<ICoreWebView2_21> webView = m_webView.try_query<ICoreWebView2_21>();

        if (!webView)
        {
            MessageBox(
                nullptr, L"Get webview2 failed!", L"ExecuteScriptWithResult Result", MB_OK);
            return;
        }

        // The main interface for excute script, the first param is the string
        // which user want to execute, the second param is the callback to process
        // the result, here use a lamada to the param.
        webView->ExecuteScriptWithResult(
            dialog.input.c_str(),
            // The callback function has two param, the first one is the status of call.s
            // it will always be the S_OK for now, and the second is the result struct.
            Callback<ICoreWebView2ExecuteScriptWithResultCompletedHandler>(
                [this](HRESULT errorCode, ICoreWebView2ExecuteScriptResult* result) -> HRESULT
                {
                    if (errorCode != S_OK || result == nullptr)
                    {
                        MessageBox(
                            nullptr, L"Call interface failed!",
                            L"ExecuteScriptWithResult Result", MB_OK);
                        return S_OK;
                    }
                    else
                    {
                        wil::com_ptr<ICoreWebView2ScriptException> exception;
                        BOOL isSuccess;

                        // User should always invoke the get_Success firstly to get if execute
                        // success.
                        if (result->get_Succeeded(&isSuccess) != S_OK)
                        {
                            MessageBox(
                                nullptr, L"Get execute status failed!",
                                L"ExecuteScriptWithResult Result", MB_OK);
                            return S_OK;
                        }

                        // If execute success, then we can get the raw json data, and try to get
                        // the string.
                        if (isSuccess)
                        {
                            wil::unique_cotaskmem_string rawJsonData;
                            // Get the raw json.
                            if (result->get_ResultAsJson(&rawJsonData) == S_OK)
                            {
                                MessageBox(
                                    nullptr, rawJsonData.get(),
                                    L"ExecuteScriptWithResult Json Result", MB_OK);
                            }
                            else
                            {
                                MessageBox(
                                    nullptr, L"Get raw json data failed",
                                    L"ExecuteScriptWithResult Json Result", MB_OK);
                            }

                            // Get the string, and if the result is not the string type,
                            // it will return the E_INVALIDARG.
                            wil::unique_cotaskmem_string stringData;
                            BOOL isString = FALSE;
                            if (result->TryGetResultAsString(&stringData, &isString) == S_OK &&
                                isString)
                            {
                                MessageBox(
                                    nullptr, stringData.get(),
                                    L"ExecuteScriptWithResult String Result", MB_OK);
                            }
                            else
                            {
                                MessageBox(
                                    nullptr, L"Get string failed",
                                    L"ExecuteScriptWithResult String Result", MB_OK);
                            }
                        }
                        else // If execute failed, then we can get the exception struct to get
                             // the reason of failed.
                        {
                            if (result->get_Exception(&exception) == S_OK)
                            {
                                // Get the exception name, this could return the empty string,
                                // such as `throw 1`.
                                wil::unique_cotaskmem_string exceptionName;
                                if (exception && exception->get_Name(&exceptionName) == S_OK)
                                {
                                    MessageBox(
                                        nullptr, exceptionName.get(),
                                        L"ExecuteScriptWithResult Exception Name", MB_OK);
                                }

                                // Get the exception message, this could return the empty
                                // string, such as `throw 1`.
                                wil::unique_cotaskmem_string exceptionMessage;
                                if (exception &&
                                    exception->get_Message(&exceptionMessage) == S_OK)
                                {
                                    MessageBox(
                                        nullptr, exceptionMessage.get(),
                                        L"ExecuteScriptWithResult Exception Message", MB_OK);
                                }

                                // Get the exception detail, it's a json struct data with all
                                // exception infomation , we can parse it and get the detail
                                // what we need.
                                wil::unique_cotaskmem_string exceptionDetail;
                                if (exception &&
                                    exception->get_ToJson(&exceptionDetail) == S_OK)
                                {
                                    MessageBox(
                                        nullptr, exceptionDetail.get(),
                                        L"ExecuteScriptWithResult Exception Detail", MB_OK);
                                }

                                uint32_t lineNumber = 0;
                                uint32_t columnNumber = 0;
                                if (exception &&
                                    exception->get_LineNumber(&lineNumber) == S_OK &&
                                    exception->get_ColumnNumber(&columnNumber) == S_OK)
                                {
                                    auto exceptionLocationInfo =
                                        L"LineNumber:" + std::to_wstring(lineNumber) +
                                        L", ColumnNumber:" + std::to_wstring(columnNumber);
                                    MessageBox(
                                        nullptr, exceptionLocationInfo.c_str(),
                                        L"ExecuteScriptWithResult Exception Location", MB_OK);
                                }
                            }
                            else
                            {
                                MessageBox(
                                    nullptr, L"Get exception failed",
                                    L"ExecuteScriptWithResult Result", MB_OK);
                            }
                        }
                    }
                    return S_OK;
                })
                .Get());
    }
}
```

