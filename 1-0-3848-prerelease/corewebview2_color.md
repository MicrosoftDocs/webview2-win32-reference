---
description: A value representing RGBA color (Red, Green, Blue, Alpha) for WebView2.
title: WebView2 Win32 C++ COREWEBVIEW2_COLOR
ms.date: 02/09/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, COREWEBVIEW2_COLOR
topic_type: 
- APIRef
api_name:
- COREWEBVIEW2_COLOR
- COREWEBVIEW2_COLOR.A
- COREWEBVIEW2_COLOR.B
- COREWEBVIEW2_COLOR.G
- COREWEBVIEW2_COLOR.R
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# struct COREWEBVIEW2_COLOR

A value representing RGBA color (Red, Green, Blue, Alpha) for WebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[A](#a) | Specifies the intensity of the Alpha ie.
[B](#b) | Specifies the intensity of the Blue color.
[G](#g) | Specifies the intensity of the Green color.
[R](#r) | Specifies the intensity of the Red color.

Each component takes a value from 0 to 255, with 0 being no intensity and 255 being the highest intensity.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### A

Specifies the intensity of the Alpha ie.

> public BYTE [A](#a)

opacity value. 0 is transparent, 255 is opaque.

#### B

Specifies the intensity of the Blue color.

> public BYTE [B](#b)

#### G

Specifies the intensity of the Green color.

> public BYTE [G](#g)

#### R

Specifies the intensity of the Red color.

> public BYTE [R](#r)

