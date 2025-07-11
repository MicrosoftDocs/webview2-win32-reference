---
description: Contains the information packed into the `LPARAM` sent to a Win32 key event.
title: WebView2 Win32 C++ COREWEBVIEW2_PHYSICAL_KEY_STATUS
ms.date: 05/27/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, COREWEBVIEW2_PHYSICAL_KEY_STATUS
topic_type: 
- APIRef
api_name:
- COREWEBVIEW2_PHYSICAL_KEY_STATUS
- COREWEBVIEW2_PHYSICAL_KEY_STATUS.IsExtendedKey
- COREWEBVIEW2_PHYSICAL_KEY_STATUS.IsKeyReleased
- COREWEBVIEW2_PHYSICAL_KEY_STATUS.IsMenuKeyDown
- COREWEBVIEW2_PHYSICAL_KEY_STATUS.RepeatCount
- COREWEBVIEW2_PHYSICAL_KEY_STATUS.ScanCode
- COREWEBVIEW2_PHYSICAL_KEY_STATUS.WasKeyDown
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# struct COREWEBVIEW2_PHYSICAL_KEY_STATUS

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

Contains the information packed into the `LPARAM` sent to a Win32 key event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[IsExtendedKey](#isextendedkey) | Indicates that the key is an extended key.
[IsKeyReleased](#iskeyreleased) | Indicates that the key was released.
[IsMenuKeyDown](#ismenukeydown) | Indicates that a menu key is held down (context code).
[RepeatCount](#repeatcount) | Specifies the repeat count for the current message.
[ScanCode](#scancode) | Specifies the scan code.
[WasKeyDown](#waskeydown) | Indicates that the key was held down.

For more information about `WM_KEYDOWN`, navigate to [WM_KEYDOWN message](/windows/win32/inputdev/wm-keydown).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### IsExtendedKey

Indicates that the key is an extended key.

> public BOOL [IsExtendedKey](#isextendedkey)

#### IsKeyReleased

Indicates that the key was released.

> public BOOL [IsKeyReleased](#iskeyreleased)

#### IsMenuKeyDown

Indicates that a menu key is held down (context code).

> public BOOL [IsMenuKeyDown](#ismenukeydown)

#### RepeatCount

Specifies the repeat count for the current message.

> public UINT32 [RepeatCount](#repeatcount)

#### ScanCode

Specifies the scan code.

> public UINT32 [ScanCode](#scancode)

#### WasKeyDown

Indicates that the key was held down.

> public BOOL [WasKeyDown](#waskeydown)

