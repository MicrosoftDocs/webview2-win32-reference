---
description: This is the ICoreWebView2Environment Experimental interface for creating a diagnostic monitor.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment16
ms.date: 09/03/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment16
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalEnvironment16
- ICoreWebView2ExperimentalEnvironment16.CreateDiagnosticMonitor
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalEnvironment16

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment16
  : public IUnknown
```

This is the [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) Experimental interface for creating a diagnostic monitor.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateDiagnosticMonitor](#creatediagnosticmonitor) | Creates a new diagnostic monitor.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.4181

## Members

#### CreateDiagnosticMonitor

Creates a new diagnostic monitor.

> public HRESULT [CreateDiagnosticMonitor](#creatediagnosticmonitor)([ICoreWebView2ExperimentalDiagnosticMonitor](icorewebview2experimentaldiagnosticmonitor.md#icorewebview2experimentaldiagnosticmonitor) ** value)

The monitor receives diagnostic signals from all layers - WebView, Profile, and Environment - that match its filters.

Multiple monitors can coexist, each with its own filters and event handlers. This enables independent consumers such as a telemetry pipeline and a debug panel to operate without interfering with each other.

The monitor is active immediately, but no events fire until a filter is set via `SetDiagnosticFilter`.

Release the monitor to stop receiving events and free resources.

```cpp
    // Create the monitor.
    wil::com_ptr<ICoreWebView2ExperimentalDiagnosticMonitor> monitor;
    HRESULT hr = m_environment16->CreateDiagnosticMonitor(&monitor);
    if (FAILED(hr))
    {
        std::wstringstream ss;
        ss << L"CreateDiagnosticMonitor failed: 0x" << std::hex << hr;
        MessageBox(
            m_appWindow->GetMainWindow(), ss.str().c_str(), L"Diagnostic Monitor",
            MB_OK | MB_ICONERROR);
        return;
    }

    // Set filter for NETWORK_REQUEST category.
    hr = monitor->SetDiagnosticFilter(
        COREWEBVIEW2_DIAGNOSTIC_CATEGORY_NETWORK_REQUEST,
        jsonFilter.empty() ? L"" : jsonFilter.c_str());
    if (FAILED(hr))
    {
        std::wstringstream ss;
        ss << L"SetDiagnosticFilter failed: 0x" << std::hex << hr;
        MessageBox(
            m_appWindow->GetMainWindow(), ss.str().c_str(), L"Diagnostic Monitor",
            MB_OK | MB_ICONERROR);
        return;
    }

    // Register the event handler. Capture the monitor name for logging.
    std::wstring capturedName = monitorName;
    EventRegistrationToken token;
    CHECK_FAILURE(monitor->add_DiagnosticReceived(
        Callback<ICoreWebView2ExperimentalDiagnosticReceivedEventHandler>(
            [this, capturedName](
                ICoreWebView2ExperimentalDiagnosticMonitor* sender,
                ICoreWebView2ExperimentalDiagnosticReceivedEventArgs* args) -> HRESULT
            {
                COREWEBVIEW2_DIAGNOSTIC_CATEGORY category;
                CHECK_FAILURE(args->get_Category(&category));

                COREWEBVIEW2_DIAGNOSTIC_SCOPE scope;
                CHECK_FAILURE(args->get_Scope(&scope));

                INT64 timestamp = 0;
                CHECK_FAILURE(args->get_Timestamp(&timestamp));

                wil::unique_cotaskmem_string detailsJson;
                CHECK_FAILURE(args->get_DetailsAsJson(&detailsJson));

                m_totalEventCount++;

                // Pretty-print the JSON details for readability.
                std::wstring json = detailsJson.get();
                std::wstringstream pretty;
                int indent = 0;
                bool inString = false;
                wchar_t prevCh = 0;
                for (wchar_t ch : json)
                {
                    if (ch == L'"' && prevCh != L'\\')
                        inString = !inString;
                    if (inString)
                    {
                        pretty << ch;
                        prevCh = ch;
                        continue;
                    }
                    if (ch == L'{' || ch == L'[')
                    {
                        pretty << ch << L"\r\n";
                        indent += 2;
                        for (int i = 0; i < indent; ++i)
                            pretty << L' ';
                    }
                    else if (ch == L'}' || ch == L']')
                    {
                        pretty << L"\r\n";
                        indent -= 2;
                        for (int i = 0; i < indent; ++i)
                            pretty << L' ';
                        pretty << ch;
                    }
                    else if (ch == L',')
                    {
                        pretty << ch << L"\r\n";
                        for (int i = 0; i < indent; ++i)
                            pretty << L' ';
                    }
                    else
                    {
                        pretty << ch;
                    }
                    prevCh = ch;
                }

                std::wstringstream ss;
                ss << L"Event #" << m_totalEventCount << L"\r\n"
                   << L"Category: " << static_cast<int>(category) << L"  Scope: "
                   << static_cast<int>(scope) << L"  Timestamp (ms since UNIX epoch): "
                   << timestamp << L"\r\n\r\n"
                   << L"Details:\r\n"
                   << pretty.str();

                MessageBox(
                    m_appWindow->GetMainWindow(), ss.str().c_str(), capturedName.c_str(),
                    MB_OK | MB_ICONINFORMATION);

                return S_OK;
            })
            .Get(),
        &token));
```

