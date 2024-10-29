---
description: This is the ICoreWebView2_25 interface.
title: WebView2 Win32 C++ ICoreWebView2_25
ms.date: 10/29/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_25
topic_type: 
- APIRef
api_name:
- ICoreWebView2_25
- ICoreWebView2_25.add_SaveAsUIShowing
- ICoreWebView2_25.remove_SaveAsUIShowing
- ICoreWebView2_25.ShowSaveAsUI
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_25

```
interface ICoreWebView2_25
  : public ICoreWebView2_24
```

This is the ICoreWebView2_25 interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_SaveAsUIShowing](#add_saveasuishowing) | Adds an event handler for the `SaveAsUIShowing` event.
[remove_SaveAsUIShowing](#remove_saveasuishowing) | Removes an event handler previously added with `add_SaveAsUIShowing`.
[ShowSaveAsUI](#showsaveasui) | Programmatically trigger a Save As action for the currently loaded document.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2739.15
WebView2 Win32 Prerelease |    1.0.2730

## Members

#### add_SaveAsUIShowing

Adds an event handler for the `SaveAsUIShowing` event.

> public HRESULT [add_SaveAsUIShowing](#add_saveasuishowing)([ICoreWebView2SaveAsUIShowingEventHandler](icorewebview2saveasuishowingeventhandler.md#icorewebview2saveasuishowingeventhandler) * eventHandler, EventRegistrationToken * token)

This event is raised when save as is triggered, programmatically or manually.

```cpp
// Turn on/off Silent SaveAs, which won't show the system default save as dialog.
// This example hides the default save as dialog and shows a customized dialog.
bool ScenarioSaveAs::ToggleSilent()
{
    if (!m_webView2_25)
        return false;
    m_silentSaveAs = !m_silentSaveAs;
    if (m_silentSaveAs && m_saveAsUIShowingToken.value == 0)
    {
        // Register a handler for the `SaveAsUIShowing` event.
        m_webView2_25->add_SaveAsUIShowing(
            Callback<ICoreWebView2SaveAsUIShowingEventHandler>(
                [this](ICoreWebView2* sender, ICoreWebView2SaveAsUIShowingEventArgs* args)
                    -> HRESULT
                {
                    // Hide the system default save as dialog.
                    CHECK_FAILURE(args->put_SuppressDefaultDialog(TRUE));

                    auto showCustomizedDialog = [this, args = wil::make_com_ptr(args)]
                    {
                        // Preview the content mime type, optional.
                        wil::unique_cotaskmem_string mimeType;
                        CHECK_FAILURE(args->get_ContentMimeType(&mimeType));

                        SaveAsDialog dialog(m_appWindow->GetMainWindow(), saveAsKind);
                        if (dialog.confirmed)
                        {
                            // Set the SaveAsFilePath, Kind, AllowReplace for the event
                            // args from this customized dialog inputs, optional. If nothing
                            // needs to input, the event args will provide default values.
                            CHECK_FAILURE(args->put_SaveAsFilePath(dialog.path.c_str()));
                            CHECK_FAILURE(args->put_Kind(dialog.selectedKind));
                            CHECK_FAILURE(args->put_AllowReplace(dialog.allowReplace));

                            BOOL allowReplace;
                            CHECK_FAILURE(args->get_AllowReplace(&allowReplace));
                            wil::unique_cotaskmem_string path;
                            CHECK_FAILURE(args->get_SaveAsFilePath(&path));
                            COREWEBVIEW2_SAVE_AS_KIND selectedKind;
                            CHECK_FAILURE(args->get_Kind(&selectedKind));

                            // Preview silent save as event args inputs, optional.
                            MessageBox(
                                m_appWindow->GetMainWindow(),
                                (std::wstring(L"Content Mime Type: ") + mimeType.get() + L"\n" +
                                 L"Fullpath: " + path.get() + L"\n" + L"Allow Replace: " +
                                 (allowReplace ? L"true" : L"false") + L"\n" +
                                 L"Selected Save As Kind: " + saveAsKindString[selectedKind])
                                    .c_str(),
                                L"Silent Save As Parameters Preview", MB_OK);
                        }
                        else
                        {
                            // Save As cancelled from this customized dialog.
                            CHECK_FAILURE(args->put_Cancel(TRUE));
                        }
                    };

                    wil::com_ptr<ICoreWebView2Deferral> deferral;
                    CHECK_FAILURE(args->GetDeferral(&deferral));

                    m_appWindow->RunAsync(
                        [deferral, showCustomizedDialog]()
                        {
                            showCustomizedDialog();
                            CHECK_FAILURE(deferral->Complete());
                        });
                    return S_OK;
                })
                .Get(),
            &m_saveAsUIShowingToken);
    }
    else
    {
        // Unregister the handler for the `SaveAsUIShowing` event.
        m_webView2_25->remove_SaveAsUIShowing(m_saveAsUIShowingToken);
        m_saveAsUIShowingToken.value = 0;
    }
    MessageBox(
        m_appWindow->GetMainWindow(),
        (m_silentSaveAs ? L"Silent Save As Enabled" : L"Silent Save As Disabled"), L"Info",
        MB_OK);
    return true;
}
```

#### remove_SaveAsUIShowing

Removes an event handler previously added with `add_SaveAsUIShowing`.

> public HRESULT [remove_SaveAsUIShowing](#remove_saveasuishowing)(EventRegistrationToken token)

#### ShowSaveAsUI

Programmatically trigger a Save As action for the currently loaded document.

> public HRESULT [ShowSaveAsUI](#showsaveasui)([ICoreWebView2ShowSaveAsUICompletedHandler](icorewebview2showsaveasuicompletedhandler.md#icorewebview2showsaveasuicompletedhandler) * handler)

The `SaveAsUIShowing` event is raised.

Opens a system modal dialog by default. If the `SuppressDefaultDialog` property is `TRUE`, the system dialog is not opened.

This method returns `COREWEBVIEW2_SAVE_AS_UI_RESULT`. See `COREWEBVIEW2_SAVE_AS_UI_RESULT` for details.

```cpp
// Call ShowSaveAsUI method to trigger the programmatic save as.
bool ScenarioSaveAs::ProgrammaticSaveAs()
{
    if (!m_webView2_25)
        return false;
    m_webView2_25->ShowSaveAsUI(
        Callback<ICoreWebView2ShowSaveAsUICompletedHandler>(
            [this](HRESULT errorCode, COREWEBVIEW2_SAVE_AS_UI_RESULT result) -> HRESULT
            {
                // Show ShowSaveAsUI returned result, optional.
                MessageBox(
                    m_appWindow->GetMainWindow(),
                    (L"ShowSaveAsUI " + saveAsUIResultString[result]).c_str(), L"Info", MB_OK);
                return S_OK;
            })
            .Get());
    return true;
}
```

