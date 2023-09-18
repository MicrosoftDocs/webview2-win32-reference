---
description: 
title: WebView2 Win32 C++ ICoreWebView2AcceleratorKeyPressedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2AcceleratorKeyPressedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2AcceleratorKeyPressedEventArgs
- ICoreWebView2AcceleratorKeyPressedEventArgs.get_Handled
- ICoreWebView2AcceleratorKeyPressedEventArgs.get_KeyEventKind
- ICoreWebView2AcceleratorKeyPressedEventArgs.get_KeyEventLParam
- ICoreWebView2AcceleratorKeyPressedEventArgs.get_PhysicalKeyStatus
- ICoreWebView2AcceleratorKeyPressedEventArgs.get_VirtualKey
- ICoreWebView2AcceleratorKeyPressedEventArgs.put_Handled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2AcceleratorKeyPressedEventArgs

```
interface ICoreWebView2AcceleratorKeyPressedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Gets the `Handled` property.
[get_KeyEventKind](#get_keyeventkind) | Gets the `KeyEventKind` property.
[get_KeyEventLParam](#get_keyeventlparam) | Gets the `KeyEventLParam` property.
[get_PhysicalKeyStatus](#get_physicalkeystatus) | Gets the `PhysicalKeyStatus` property.
[get_VirtualKey](#get_virtualkey) | Gets the `VirtualKey` property.
[put_Handled](#put_handled) | Sets the `Handled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_KeyEventKind

Gets the `KeyEventKind` property.

> public HRESULT [get_KeyEventKind](#get_keyeventkind)(COREWEBVIEW2_KEY_EVENT_KIND * value)

#### get_KeyEventLParam

Gets the `KeyEventLParam` property.

> public HRESULT [get_KeyEventLParam](#get_keyeventlparam)(INT32 * value)

#### get_PhysicalKeyStatus

Gets the `PhysicalKeyStatus` property.

> public HRESULT [get_PhysicalKeyStatus](#get_physicalkeystatus)([COREWEBVIEW2_PHYSICAL_KEY_STATUS](corewebview2_physical_key_status.md) * value)

#### get_VirtualKey

Gets the `VirtualKey` property.

> public HRESULT [get_VirtualKey](#get_virtualkey)(UINT32 * value)

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

