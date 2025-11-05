---
description: This is a continuation of the ICoreWebView2AcceleratorKeyPressedEventArgs interface.
title: WebView2 Win32 C++ ICoreWebView2AcceleratorKeyPressedEventArgs2
ms.date: 10/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2AcceleratorKeyPressedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2AcceleratorKeyPressedEventArgs2
- ICoreWebView2AcceleratorKeyPressedEventArgs2.get_IsBrowserAcceleratorKeyEnabled
- ICoreWebView2AcceleratorKeyPressedEventArgs2.put_IsBrowserAcceleratorKeyEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2AcceleratorKeyPressedEventArgs2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2AcceleratorKeyPressedEventArgs2
  : public ICoreWebView2AcceleratorKeyPressedEventArgs
```

This is a continuation of the [ICoreWebView2AcceleratorKeyPressedEventArgs](icorewebview2acceleratorkeypressedeventargs.md#icorewebview2acceleratorkeypressedeventargs) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsBrowserAcceleratorKeyEnabled](#get_isbrowseracceleratorkeyenabled) | Gets the `IsBrowserAcceleratorKeyEnabled` property.
[put_IsBrowserAcceleratorKeyEnabled](#put_isbrowseracceleratorkeyenabled) | This property allows developers to enable or disable the browser from handling a specific browser accelerator key such as Ctrl+P or F3, etc.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### get_IsBrowserAcceleratorKeyEnabled

Gets the `IsBrowserAcceleratorKeyEnabled` property.

> public HRESULT [get_IsBrowserAcceleratorKeyEnabled](#get_isbrowseracceleratorkeyenabled)(BOOL * value)

#### put_IsBrowserAcceleratorKeyEnabled

This property allows developers to enable or disable the browser from handling a specific browser accelerator key such as Ctrl+P or F3, etc.

> public HRESULT [put_IsBrowserAcceleratorKeyEnabled](#put_isbrowseracceleratorkeyenabled)(BOOL value)

Browser accelerator keys are the keys/key combinations that access features specific to a web browser, including but not limited to:

* Ctrl-F and F3 for Find on Page

* Ctrl-P for Print

* Ctrl-R and F5 for Reload

* Ctrl-Plus and Ctrl-Minus for zooming

* Ctrl-Shift-C and F12 for DevTools

* Special keys for browser functions, such as Back, Forward, and Search

This property does not disable accelerator keys related to movement and text editing, such as:

* Home, End, Page Up, and Page Down

* Ctrl-X, Ctrl-C, Ctrl-V

* Ctrl-A for Select All

* Ctrl-Z for Undo

The `CoreWebView2Settings.AreBrowserAcceleratorKeysEnabled` API is a convenient setting for developers to disable all the browser accelerator keys together, and sets the default value for the `IsBrowserAcceleratorKeyEnabled` property. By default, `CoreWebView2Settings.AreBrowserAcceleratorKeysEnabled` is `TRUE` and `IsBrowserAcceleratorKeyEnabled` is `TRUE`. When developers change `CoreWebView2Settings.AreBrowserAcceleratorKeysEnabled` setting to `FALSE`, this will change default value for `IsBrowserAcceleratorKeyEnabled` to `FALSE`. If developers want specific keys to be handled by the browser after changing the `CoreWebView2Settings.AreBrowserAcceleratorKeysEnabled` setting to `FALSE`, they need to enable these keys by setting `IsBrowserAcceleratorKeyEnabled` to `TRUE`. This API will give the event arg higher priority over the `CoreWebView2Settings.AreBrowserAcceleratorKeysEnabled` setting when we handle the keys.

For browser accelerator keys, when an accelerator key is pressed, the propagation and processing order is:

1. A CoreWebView2Controller.AcceleratorKeyPressed event is raised

1. WebView2 browser feature accelerator key handling

1. Web Content Handling: If the key combination isn't reserved for browser actions, the key event propagates to the web content, where JavaScript event listeners can capture and respond to it.

[ICoreWebView2AcceleratorKeyPressedEventArgs](icorewebview2acceleratorkeypressedeventargs.md#icorewebview2acceleratorkeypressedeventargs) has a `Handled` property, that developers can use to mark a key as handled. When the key is marked as handled anywhere along the path, the event propagation stops, and web content will not receive the key. With `IsBrowserAcceleratorKeyEnabled` property, if developers mark `IsBrowserAcceleratorKeyEnabled` as `FALSE`, the browser will skip the WebView2 browser feature accelerator key handling process, but the event propagation continues, and web content will receive the key combination.

```cpp
    if (m_settings3)
    {
        // Register a handler for the AcceleratorKeyPressed event.
        CHECK_FAILURE(m_controller->add_AcceleratorKeyPressed(
            Callback<ICoreWebView2AcceleratorKeyPressedEventHandler>(
                [this](
                    ICoreWebView2Controller* sender,
                    ICoreWebView2AcceleratorKeyPressedEventArgs* args) -> HRESULT
                {
                    COREWEBVIEW2_KEY_EVENT_KIND kind;
                    CHECK_FAILURE(args->get_KeyEventKind(&kind));
                    // We only care about key down events.
                    if (kind == COREWEBVIEW2_KEY_EVENT_KIND_KEY_DOWN ||
                        kind == COREWEBVIEW2_KEY_EVENT_KIND_SYSTEM_KEY_DOWN)
                    {
                        UINT key;
                        CHECK_FAILURE(args->get_VirtualKey(&key));

                        wil::com_ptr<ICoreWebView2AcceleratorKeyPressedEventArgs2> args2;

                        args->QueryInterface(IID_PPV_ARGS(&args2));
                        if (args2)
                        {
                            if (key == 'P' && (GetKeyState(VK_CONTROL) < 0))
                            {
                                // tell the browser to skip the key
                                CHECK_FAILURE(args2->put_IsBrowserAcceleratorKeyEnabled(FALSE));
                            }
                            if (key == VK_F7)
                            {
                                // tell the browser to process the key
                                CHECK_FAILURE(args2->put_IsBrowserAcceleratorKeyEnabled(TRUE));
                            }
                        }
                    }
                    return S_OK;
                })
                .Get(),
            &m_acceleratorKeyPressedToken));
    }
```
 Gets the `IsBrowserAcceleratorKeyEnabled` property.

