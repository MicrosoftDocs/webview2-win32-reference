---
description: A continuation of the ICoreWebView2Settings interface that manages whether browser accelerator keys are enabled.
title: WebView2 Win32 C++ ICoreWebView2Settings3
ms.date: 06/23/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings3
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings3
- ICoreWebView2Settings3.get_AreBrowserAcceleratorKeysEnabled
- ICoreWebView2Settings3.put_AreBrowserAcceleratorKeysEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings3

```
interface ICoreWebView2Settings3
  : public ICoreWebView2Settings2
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md#icorewebview2settings) interface that manages whether browser accelerator keys are enabled.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AreBrowserAcceleratorKeysEnabled](#get_arebrowseracceleratorkeysenabled) | Gets the `AreBrowserAcceleratorKeysEnabled` property.
[put_AreBrowserAcceleratorKeysEnabled](#put_arebrowseracceleratorkeysenabled) | When this setting is set to FALSE, it disables all accelerator keys that access features specific to a web browser, including but not limited to:

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.864.35
WebView2 Win32 Prerelease |    1.0.865

## Members

#### get_AreBrowserAcceleratorKeysEnabled

Gets the `AreBrowserAcceleratorKeysEnabled` property.

> public HRESULT [get_AreBrowserAcceleratorKeysEnabled](#get_arebrowseracceleratorkeysenabled)(BOOL * value)

#### put_AreBrowserAcceleratorKeysEnabled

When this setting is set to FALSE, it disables all accelerator keys that access features specific to a web browser, including but not limited to:

> public HRESULT [put_AreBrowserAcceleratorKeysEnabled](#put_arebrowseracceleratorkeysenabled)(BOOL value)

* Ctrl-F and F3 for Find on Page

* Ctrl-P for Print

* Ctrl-R and F5 for Reload

* Ctrl-Plus and Ctrl-Minus for zooming

* Ctrl-Shift-C and F12 for DevTools

* Special keys for browser functions, such as Back, Forward, and Search

It does not disable accelerator keys related to movement and text editing, such as:

* Home, End, Page Up, and Page Down

* Ctrl-X, Ctrl-C, Ctrl-V

* Ctrl-A for Select All

* Ctrl-Z for Undo

Those accelerator keys will always be enabled unless they are handled in the `AcceleratorKeyPressed` event.

This setting has no effect on the `AcceleratorKeyPressed` event. The event will be fired for all accelerator keys, whether they are enabled or not.

The default value for `AreBrowserAcceleratorKeysEnabled` is TRUE.

```cpp
            CHECK_FEATURE_RETURN(m_settings3);

            BOOL enabled;
            CHECK_FAILURE(m_settings3->get_AreBrowserAcceleratorKeysEnabled(&enabled));
            if (enabled)
            {
                CHECK_FAILURE(m_settings3->put_AreBrowserAcceleratorKeysEnabled(FALSE));
                MessageBox(
                    nullptr,
                    L"Browser-specific accelerator keys will be disabled after the next "
                    L"navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings3->put_AreBrowserAcceleratorKeysEnabled(TRUE));
                MessageBox(
                    nullptr,
                    L"Browser-specific accelerator keys will be enabled after the next "
                    L"navigation.",
                    L"Settings change", MB_OK);
            }
```

