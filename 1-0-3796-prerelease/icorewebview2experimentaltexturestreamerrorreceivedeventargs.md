---
description: The event args for the `ICoreWebViewTextureStream ErrorReceived` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTextureStreamErrorReceivedEventArgs
ms.date: 01/13/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTextureStreamErrorReceivedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalTextureStreamErrorReceivedEventArgs
- ICoreWebView2ExperimentalTextureStreamErrorReceivedEventArgs.get_Kind
- ICoreWebView2ExperimentalTextureStreamErrorReceivedEventArgs.get_Texture
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalTextureStreamErrorReceivedEventArgs

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalTextureStreamErrorReceivedEventArgs
  : public IUnknown
```

The event args for the `ICoreWebViewTextureStream ErrorReceived` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Kind](#get_kind) | The kind of error that has occurred.
[get_Texture](#get_texture) | The texture with which this error is associated.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### get_Kind

The kind of error that has occurred.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND * value)

#### get_Texture

The texture with which this error is associated.

> public HRESULT [get_Texture](#get_texture)([ICoreWebView2ExperimentalTexture](icorewebview2experimentaltexture.md#icorewebview2experimentaltexture) ** value)

For the `COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND` error kind, this property will be `nullptr`.

