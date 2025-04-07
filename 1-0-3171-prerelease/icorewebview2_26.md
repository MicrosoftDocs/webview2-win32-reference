---
description: This is the ICoreWebView2_26 interface.
title: WebView2 Win32 C++ ICoreWebView2_26
ms.date: 03/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_26
topic_type: 
- APIRef
api_name:
- ICoreWebView2_26
- ICoreWebView2_26.add_SaveFileSecurityCheckStarting
- ICoreWebView2_26.remove_SaveFileSecurityCheckStarting
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_26

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2_26
  : public ICoreWebView2_25
```

This is the ICoreWebView2_26 interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_SaveFileSecurityCheckStarting](#add_savefilesecuritycheckstarting) | Adds an event handler for the `SaveFileSecurityCheckStarting` event.
[remove_SaveFileSecurityCheckStarting](#remove_savefilesecuritycheckstarting) | Removes an event handler previously added with `add_SaveFileSecurityCheckStarting`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2849.39
WebView2 Win32 Prerelease |    1.0.2895

## Members

#### add_SaveFileSecurityCheckStarting

Adds an event handler for the `SaveFileSecurityCheckStarting` event.

> public HRESULT [add_SaveFileSecurityCheckStarting](#add_savefilesecuritycheckstarting)([ICoreWebView2SaveFileSecurityCheckStartingEventHandler](icorewebview2savefilesecuritycheckstartingeventhandler.md#icorewebview2savefilesecuritycheckstartingeventhandler) * eventHandler, EventRegistrationToken * token)

This event will be raised during system FileTypePolicy checking the dangerous file extension list.

Developers can specify their own logic for determining whether to allow a particular type of file to be saved from the document origin URI. Developers can also determine the save decision based on other criteria.

Here are two properties in [ICoreWebView2SaveFileSecurityCheckStartingEventArgs](icorewebview2savefilesecuritycheckstartingeventargs.md#icorewebview2savefilesecuritycheckstartingeventargs) to manage the decision: `CancelSave` and `SuppressDefaultPolicy`. Table of Properties' value and result:

CancelSave   |SuppressDefaultPolicy   |Result
--------- | --------- | ---------
False   |False   |Perform the default policy check. It may show the
||security warning UI if the file extension is
||dangerous.
-------&mdash;|---&mdash;|------------------&mdash;
False   |True   |Skip the default policy check and the possible
||security warning. Start saving or downloading.
-------&mdash;|---&mdash;|------------------&mdash;
True   |Any   |Skip the default policy check and the possible
||security warning. Abort save or download.

```cpp
// This example will register the event with two custom rules.
// 1. Suppressing file type policy, security dialog, and allows saving ".eml" files
// directly; when the URI is trusted.
// 2. Showing customized warning UI when saving ".iso" files. It allows to block
// the saving directly.
bool ScenarioFileTypePolicy::SuppressPolicyForExtension()
{
    m_webView2_26 = m_webView2.try_query<ICoreWebView2_26>();
    if (!m_webView2_26)
        return false;
    m_webView2_26->add_SaveFileSecurityCheckStarting(
        Callback<ICoreWebView2SaveFileSecurityCheckStartingEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2SaveFileSecurityCheckStartingEventArgs* args) -> HRESULT
            {
                // Get the file extension for file to be saved.
                // And convert the extension to lower case for a
                // case-insensitive comparasion.
                wil::unique_cotaskmem_string extension;
                CHECK_FAILURE(args->get_FileExtension(&extension));
                std::wstring extension_lower = extension.get();
                std::transform(
                    extension_lower.begin(), extension_lower.end(), extension_lower.begin(),
                    ::towlower);

                // Suppress default policy for ".eml" file.
                if (wcscmp(extension_lower.c_str(), L".eml") == 0)
                {
                    CHECK_FAILURE(args->put_SuppressDefaultPolicy(TRUE));
                }

                // Cancel save/download for ".iso" file.
                if (wcscmp(extension_lower.c_str(), L".iso") == 0)
                {
                    wil::com_ptr<ICoreWebView2Deferral> deferral;
                    CHECK_FAILURE(args->GetDeferral(&deferral));

                    m_appWindow->RunAsync(
                        [this, args = wil::make_com_ptr(args), deferral]()
                        {
                            // With the deferral, the cancel decision and
                            // message box can be replaced with a customized UI.
                            CHECK_FAILURE(args->put_CancelSave(TRUE));
                            MessageBox(
                                m_appWindow->GetMainWindow(), L"The saving has been blocked",
                                L"Info", MB_OK);
                            CHECK_FAILURE(deferral->Complete());
                        });
                }
                if (wcscmp(extension_lower.c_str(), L"exe") == 0)
                {
                    if (is_exe_blocked.has_value())
                    {
                        if (is_exe_blocked)
                        {
                            args->put_CancelSave(true);
                        }
                        else
                        {
                            args->put_SuppressDefaultPolicy(true);
                        }
                    }
                }
                return S_OK;
            })
            .Get(),
        &m_saveFileSecurityCheckStartingToken);

    MessageBox(
        m_appWindow->GetMainWindow(),
        (L"Example rules of Dangerous File Security Policy has been applied in this demo page"),
        L"Info", MB_OK);
    return true;
}
```

#### remove_SaveFileSecurityCheckStarting

Removes an event handler previously added with `add_SaveFileSecurityCheckStarting`.

> public HRESULT [remove_SaveFileSecurityCheckStarting](#remove_savefilesecuritycheckstarting)(EventRegistrationToken token)

