---
description: This interface is an extension of ICoreWebView2_17 that manages navigation requests to URI schemes registered with the OS.
title: WebView2 Win32 C++ ICoreWebView2_18
ms.date: 06/12/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_18
topic_type: 
- APIRef
api_name:
- ICoreWebView2_18
- ICoreWebView2_18.add_LaunchingExternalUriScheme
- ICoreWebView2_18.remove_LaunchingExternalUriScheme
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_18

```
interface ICoreWebView2_18
  : public ICoreWebView2_17
```

This interface is an extension of [ICoreWebView2_17](icorewebview2_17.md#icorewebview2_17) that manages navigation requests to URI schemes registered with the OS.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_LaunchingExternalUriScheme](#add_launchingexternalurischeme) | Adds an event handler for the `LaunchingExternalUriScheme` event.
[remove_LaunchingExternalUriScheme](#remove_launchingexternalurischeme) | Removes an event handler previously added with `add_LaunchingExternalUriScheme`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    1.0.1905

## Members

#### add_LaunchingExternalUriScheme

Adds an event handler for the `LaunchingExternalUriScheme` event.

> public HRESULT [add_LaunchingExternalUriScheme](#add_launchingexternalurischeme)([ICoreWebView2LaunchingExternalUriSchemeEventHandler](icorewebview2launchingexternalurischemeeventhandler.md#icorewebview2launchingexternalurischemeeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `LaunchingExternalUriScheme` event. The `LaunchingExternalUriScheme` event is raised when a navigation request is made to a URI scheme that is registered with the OS. The `LaunchingExternalUriScheme` event handler may suppress the default dialog or replace the default dialog with a custom dialog.

If a deferral is not taken on the event args, the external URI scheme launch is blocked until the event handler returns. If a deferral is taken, the external URI scheme launch is blocked until the deferral is completed. The host also has the option to cancel the URI scheme launch.

The `NavigationStarting` and `NavigationCompleted` events will be raised, regardless of whether the `Cancel` property is set to `TRUE` or `FALSE`. The `NavigationCompleted` event will be raised with the `IsSuccess` property set to `FALSE` and the `WebErrorStatus` property set to `ConnectionAborted` regardless of whether the host sets the `Cancel` property on the [ICoreWebView2LaunchingExternalUriSchemeEventArgs](icorewebview2launchingexternalurischemeeventargs.md#icorewebview2launchingexternalurischemeeventargs). The `SourceChanged`, `ContentLoading`, and `HistoryChanged` events will not be raised for this navigation to the external URI scheme regardless of the `Cancel` property. The `LaunchingExternalUriScheme` event will be raised after the `NavigationStarting` event and before the `NavigationCompleted` event. The default `CoreWebView2Settings` will also be updated upon navigation to an external URI scheme. If a setting on the `CoreWebView2Settings` interface has been changed, navigating to an external URI scheme will trigger the `CoreWebView2Settings` to update.

The WebView2 may not display the default dialog based on user settings, browser settings, and whether the origin is determined as a [trustworthy origin](https://w3c.github.io/webappsec-secure-contexts#
potentially-trustworthy-origin); however, the event will still be raised.

If the request is initiated by a cross-origin frame without a user gesture, the request will be blocked and the `LaunchingExternalUriScheme` event will not be raised. 
```cpp
            m_launchingExternalUriScheme = !m_launchingExternalUriScheme;
            CHECK_FEATURE_RETURN(m_webView2_18);
            if (m_launchingExternalUriScheme)
            {
                CHECK_FAILURE(m_webView2_18->add_LaunchingExternalUriScheme(
                    Callback<ICoreWebView2LaunchingExternalUriSchemeEventHandler>(
                        [this](
                            ICoreWebView2* sender,
                            ICoreWebView2LaunchingExternalUriSchemeEventArgs* args)
                        {
                            auto showDialog = [this, args]
                            {
                                wil::unique_cotaskmem_string uri;
                                CHECK_FAILURE(args->get_Uri(&uri));
                                if (wcscmp(uri.get(), L"calculator://") == 0)
                                {
                                    // Set the event args to cancel the event and launch the
                                    // calculator app. This will always allow the external
                                    // URI scheme launch.
                                    args->put_Cancel(true);
                                    std::wstring schemeUrl = L"calculator://";
                                    SHELLEXECUTEINFO info = {sizeof(info)};
                                    info.fMask = SEE_MASK_NOASYNC;
                                    info.lpVerb = L"open";
                                    info.lpFile = schemeUrl.c_str();
                                    info.nShow = SW_SHOWNORMAL;
                                    ::ShellExecuteEx(&info);
                                }
                                else if (wcscmp(uri.get(), L"malicious://") == 0)
                                {
                                    // Always block the request in this case by cancelling
                                    // the event.
                                    args->put_Cancel(true);
                                }
                                else if (wcscmp(uri.get(), L"contoso://") == 0)
                                {
                                    // To display a custom dialog we cancel the launch,
                                    // display a custom dialog, and then manually launch the
                                    // external URI scheme depending on the user's
                                    // selection.
                                    args->put_Cancel(true);
                                    wil::unique_cotaskmem_string initiatingOrigin;
                                    CHECK_FAILURE(
                                        args->get_InitiatingOrigin(&initiatingOrigin));
                                    std::wstring message =
                                        L"Launching External URI Scheme request";
                                    std::wstring initiatingOriginString =
                                        initiatingOrigin.get();
                                    if (initiatingOriginString.empty())
                                    {
                                        message += L" from ";
                                        message += initiatingOriginString;
                                    }
                                    message += L" to ";
                                    message += uri.get();
                                    message += L"?\n\n";
                                    message += L"Do you want to grant permission?\n";
                                    int response = MessageBox(
                                        nullptr, message.c_str(),
                                        L"Launching External URI Scheme",
                                        MB_YESNO | MB_ICONWARNING);
                                    if (response == IDYES)
                                    {
                                        std::wstring schemeUrl = uri.get();
                                        SHELLEXECUTEINFO info = {sizeof(info)};
                                        info.fMask = SEE_MASK_NOASYNC;
                                        info.lpVerb = L"open";
                                        info.lpFile = schemeUrl.c_str();
                                        info.nShow = SW_SHOWNORMAL;
                                        ::ShellExecuteEx(&info);
                                    }
                                }
                                else
                                {
                                    // Do not cancel the event, allowing the request to use
                                    // the default dialog.
                                }
                                return S_OK;
                            };
                            showDialog();
                            return S_OK;
                            // A deferral may be taken for the event so that the
                            // CoreWebView2 doesn't examine the properties we set on the
                            // event args until after we call the Complete method
                            // asynchronously later. This will give the user more time to
                            // decide whether to launch the external URI scheme or not.
                            // A deferral doesn't need to be taken in this case, so taking
                            // a deferral is commented out here.
                            // wil::com_ptr<ICoreWebView2Deferral> deferral;
                            // CHECK_FAILURE(args->GetDeferral(&deferral));

                            // m_appWindow->RunAsync(
                            //     [deferral, showDialog]()
                            //     {
                            //         showDialog();
                            // CHECK_FAILURE(deferral->Complete());
                            //     });
                            // return S_OK;
                        })
                        .Get(),
                    &m_launchingExternalUriSchemeToken));
            }
            else
            {
                m_webView2_18->remove_LaunchingExternalUriScheme(
                    m_launchingExternalUriSchemeToken);
            }
            MessageBox(
                nullptr,
                (std::wstring(L"Launching External URI Scheme support has been ") +
                 (m_launchingExternalUriScheme ? L"enabled." : L"disabled."))
                    .c_str(),
                L"Launching External URI Scheme", MB_OK);
            return true;
```
 MSOWNERS: [mwinstanley@microsoft.com](mailto:mwinstanley@microsoft.com)

#### remove_LaunchingExternalUriScheme

Removes an event handler previously added with `add_LaunchingExternalUriScheme`.

> public HRESULT [remove_LaunchingExternalUriScheme](#remove_launchingexternalurischeme)(EventRegistrationToken token)

