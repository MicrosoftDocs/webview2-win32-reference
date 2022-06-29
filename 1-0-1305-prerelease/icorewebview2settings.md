---
description: Defines properties that enable, disable, or modify WebView features.
title: WebView2 Win32 C++ ICoreWebView2Settings
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings
---

# interface ICoreWebView2Settings

```
interface ICoreWebView2Settings
  : public IUnknown
```

Defines properties that enable, disable, or modify WebView features.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AreDefaultContextMenusEnabled](#get_aredefaultcontextmenusenabled) | The `AreDefaultContextMenusEnabled` property is used to prevent default context menus from being shown to user in WebView.
[get_AreDefaultScriptDialogsEnabled](#get_aredefaultscriptdialogsenabled) | `AreDefaultScriptDialogsEnabled` is used when loading a new HTML document.
[get_AreDevToolsEnabled](#get_aredevtoolsenabled) | `AreDevToolsEnabled` controls whether the user is able to use the context menu or keyboard shortcuts to open the DevTools window.
[get_AreHostObjectsAllowed](#get_arehostobjectsallowed) | The `AreHostObjectsAllowed` property is used to control whether host objects are accessible from the page in WebView.
[get_IsBuiltInErrorPageEnabled](#get_isbuiltinerrorpageenabled) | The `IsBuiltInErrorPageEnabled` property is used to disable built in error page for navigation failure and render process failure.
[get_IsScriptEnabled](#get_isscriptenabled) | Controls if running JavaScript is enabled in all future navigations in the WebView.
[get_IsStatusBarEnabled](#get_isstatusbarenabled) | `IsStatusBarEnabled` controls whether the status bar is displayed.
[get_IsWebMessageEnabled](#get_iswebmessageenabled) | The `IsWebMessageEnabled` property is used when loading a new HTML document.
[get_IsZoomControlEnabled](#get_iszoomcontrolenabled) | The `IsZoomControlEnabled` property is used to prevent the user from impacting the zoom of the WebView.
[put_AreDefaultContextMenusEnabled](#put_aredefaultcontextmenusenabled) | Sets the `AreDefaultContextMenusEnabled` property.
[put_AreDefaultScriptDialogsEnabled](#put_aredefaultscriptdialogsenabled) | Sets the `AreDefaultScriptDialogsEnabled` property.
[put_AreDevToolsEnabled](#put_aredevtoolsenabled) | Sets the `AreDevToolsEnabled` property.
[put_AreHostObjectsAllowed](#put_arehostobjectsallowed) | Sets the `AreHostObjectsAllowed` property.
[put_IsBuiltInErrorPageEnabled](#put_isbuiltinerrorpageenabled) | Sets the `IsBuiltInErrorPageEnabled` property.
[put_IsScriptEnabled](#put_isscriptenabled) | Sets the `IsScriptEnabled` property.
[put_IsStatusBarEnabled](#put_isstatusbarenabled) | Sets the `IsStatusBarEnabled` property.
[put_IsWebMessageEnabled](#put_iswebmessageenabled) | Sets the `IsWebMessageEnabled` property.
[put_IsZoomControlEnabled](#put_iszoomcontrolenabled) | Sets the `IsZoomControlEnabled` property.

Changes to `IsGeneralAutofillEnabled` and `IsPasswordAutosaveEnabled` apply immediately, while other setting changes made after `NavigationStarting` event do not apply until the next top-level navigation.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_AreDefaultContextMenusEnabled

The `AreDefaultContextMenusEnabled` property is used to prevent default context menus from being shown to user in WebView.

> public HRESULT [get_AreDefaultContextMenusEnabled](#get_aredefaultcontextmenusenabled)(BOOL * enabled)

The default value is `TRUE`.

```cpp
            BOOL allowContextMenus;
            CHECK_FAILURE(m_settings->get_AreDefaultContextMenusEnabled(&allowContextMenus));
            if (allowContextMenus)
            {
                CHECK_FAILURE(m_settings->put_AreDefaultContextMenusEnabled(FALSE));
                MessageBox(
                    nullptr, L"Context menus will be disabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings->put_AreDefaultContextMenusEnabled(TRUE));
                MessageBox(
                    nullptr, L"Context menus will be enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### get_AreDefaultScriptDialogsEnabled

`AreDefaultScriptDialogsEnabled` is used when loading a new HTML document.

> public HRESULT [get_AreDefaultScriptDialogsEnabled](#get_aredefaultscriptdialogsenabled)(BOOL * areDefaultScriptDialogsEnabled)

If set to `FALSE`, WebView2 does not render the default JavaScript dialog box (Specifically those displayed by the JavaScript alert, confirm, prompt functions and `beforeunload` event). Instead, if an event handler is set using `add_ScriptDialogOpening`, WebView sends an event that contains all of the information for the dialog and allow the host app to show a custom UI. The default value is `TRUE`.

#### get_AreDevToolsEnabled

`AreDevToolsEnabled` controls whether the user is able to use the context menu or keyboard shortcuts to open the DevTools window.

> public HRESULT [get_AreDevToolsEnabled](#get_aredevtoolsenabled)(BOOL * areDevToolsEnabled)

The default value is `TRUE`.

#### get_AreHostObjectsAllowed

The `AreHostObjectsAllowed` property is used to control whether host objects are accessible from the page in WebView.

> public HRESULT [get_AreHostObjectsAllowed](#get_arehostobjectsallowed)(BOOL * allowed)

The default value is `TRUE`.

```cpp
            BOOL allowHostObjects;
            CHECK_FAILURE(m_settings->get_AreHostObjectsAllowed(&allowHostObjects));
            if (allowHostObjects)
            {
                CHECK_FAILURE(m_settings->put_AreHostObjectsAllowed(FALSE));
                MessageBox(
                    nullptr,
                    L"Access to host objects will be denied after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings->put_AreHostObjectsAllowed(TRUE));
                MessageBox(
                    nullptr,
                    L"Access to host objects will be allowed after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### get_IsBuiltInErrorPageEnabled

The `IsBuiltInErrorPageEnabled` property is used to disable built in error page for navigation failure and render process failure.

> public HRESULT [get_IsBuiltInErrorPageEnabled](#get_isbuiltinerrorpageenabled)(BOOL * enabled)

When disabled, a blank page is displayed when the related error happens. The default value is `TRUE`.

```cpp
            BOOL enabled;
            CHECK_FAILURE(m_settings->get_IsBuiltInErrorPageEnabled(&enabled));
            if (enabled)
            {
                CHECK_FAILURE(m_settings->put_IsBuiltInErrorPageEnabled(FALSE));
                MessageBox(
                    nullptr, L"Built-in error page will be disabled for future navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings->put_IsBuiltInErrorPageEnabled(TRUE));
                MessageBox(
                    nullptr, L"Built-in error page will be enabled for future navigation.",
                    L"Settings change", MB_OK);
            }
```

#### get_IsScriptEnabled

Controls if running JavaScript is enabled in all future navigations in the WebView.

> public HRESULT [get_IsScriptEnabled](#get_isscriptenabled)(BOOL * isScriptEnabled)

This only affects scripts in the document. Scripts injected with `ExecuteScript` runs even if script is disabled. The default value is `TRUE`.

```cpp
                // Changes to settings will apply at the next navigation, which includes the
                // navigation after a NavigationStarting event.  We can use this to change
                // settings according to what site we're visiting.
                if (ShouldBlockScriptForUri(uri.get()))
                {
                    m_settings->put_IsScriptEnabled(FALSE);
                }
                else
                {
                    m_settings->put_IsScriptEnabled(m_isScriptEnabled);
                }
```

#### get_IsStatusBarEnabled

`IsStatusBarEnabled` controls whether the status bar is displayed.

> public HRESULT [get_IsStatusBarEnabled](#get_isstatusbarenabled)(BOOL * isStatusBarEnabled)

The status bar is usually displayed in the lower left of the WebView and shows things such as the URI of a link when the user hovers over it and other information. The default value is `TRUE`. The status bar UI can be altered by web content and should not be considered secure.

#### get_IsWebMessageEnabled

The `IsWebMessageEnabled` property is used when loading a new HTML document.

> public HRESULT [get_IsWebMessageEnabled](#get_iswebmessageenabled)(BOOL * isWebMessageEnabled)

If set to `TRUE`, communication from the host to the top-level HTML document of the WebView is allowed using `PostWebMessageAsJson`, `PostWebMessageAsString`, and message event of `window.chrome.webview`. For more information, navigate to PostWebMessageAsJson. Communication from the top-level HTML document of the WebView to the host is allowed using the postMessage function of `window.chrome.webview` and `add_WebMessageReceived` method. For more information, navigate to [add_WebMessageReceived](/microsoft-edge/webview2/reference/win32/icorewebview2#add_webmessagereceived). If set to false, then communication is disallowed. `PostWebMessageAsJson` and `PostWebMessageAsString` fails with `E_ACCESSDENIED` and `window.chrome.webview.postMessage` fails by throwing an instance of an `Error` object. The default value is `TRUE`.

```cpp
    ComPtr<ICoreWebView2Settings> settings;
    CHECK_FAILURE(m_webView->get_Settings(&settings));

    CHECK_FAILURE(settings->put_IsWebMessageEnabled(TRUE));
```

#### get_IsZoomControlEnabled

The `IsZoomControlEnabled` property is used to prevent the user from impacting the zoom of the WebView.

> public HRESULT [get_IsZoomControlEnabled](#get_iszoomcontrolenabled)(BOOL * enabled)

When disabled, the user is not able to zoom using Ctrl++, Ctrl+-, or Ctrl+mouse wheel, but the zoom is set using `ZoomFactor` API. The default value is `TRUE`.

```cpp
            BOOL zoomControlEnabled;
            CHECK_FAILURE(m_settings->get_IsZoomControlEnabled(&zoomControlEnabled));
            if (zoomControlEnabled)
            {
                CHECK_FAILURE(m_settings->put_IsZoomControlEnabled(FALSE));
                MessageBox(
                    nullptr, L"Zoom control will be disabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings->put_IsZoomControlEnabled(TRUE));
                MessageBox(
                    nullptr, L"Zoom control will be enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_AreDefaultContextMenusEnabled

Sets the `AreDefaultContextMenusEnabled` property.

> public HRESULT [put_AreDefaultContextMenusEnabled](#put_aredefaultcontextmenusenabled)(BOOL enabled)

#### put_AreDefaultScriptDialogsEnabled

Sets the `AreDefaultScriptDialogsEnabled` property.

> public HRESULT [put_AreDefaultScriptDialogsEnabled](#put_aredefaultscriptdialogsenabled)(BOOL areDefaultScriptDialogsEnabled)

#### put_AreDevToolsEnabled

Sets the `AreDevToolsEnabled` property.

> public HRESULT [put_AreDevToolsEnabled](#put_aredevtoolsenabled)(BOOL areDevToolsEnabled)

#### put_AreHostObjectsAllowed

Sets the `AreHostObjectsAllowed` property.

> public HRESULT [put_AreHostObjectsAllowed](#put_arehostobjectsallowed)(BOOL allowed)

#### put_IsBuiltInErrorPageEnabled

Sets the `IsBuiltInErrorPageEnabled` property.

> public HRESULT [put_IsBuiltInErrorPageEnabled](#put_isbuiltinerrorpageenabled)(BOOL enabled)

#### put_IsScriptEnabled

Sets the `IsScriptEnabled` property.

> public HRESULT [put_IsScriptEnabled](#put_isscriptenabled)(BOOL isScriptEnabled)

#### put_IsStatusBarEnabled

Sets the `IsStatusBarEnabled` property.

> public HRESULT [put_IsStatusBarEnabled](#put_isstatusbarenabled)(BOOL isStatusBarEnabled)

#### put_IsWebMessageEnabled

Sets the `IsWebMessageEnabled` property.

> public HRESULT [put_IsWebMessageEnabled](#put_iswebmessageenabled)(BOOL isWebMessageEnabled)

#### put_IsZoomControlEnabled

Sets the `IsZoomControlEnabled` property.

> public HRESULT [put_IsZoomControlEnabled](#put_iszoomcontrolenabled)(BOOL enabled)

