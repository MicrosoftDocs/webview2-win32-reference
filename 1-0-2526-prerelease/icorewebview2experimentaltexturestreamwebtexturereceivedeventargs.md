---
description: The event args for the `ICoreWebView2TextureStream WebTextureReceived` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventArgs
ms.date: 06/19/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventArgs
- ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventArgs.get_WebTexture
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventArgs

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventArgs
  : public IUnknown
```

The event args for the `ICoreWebView2TextureStream WebTextureReceived` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_WebTexture](#get_webtexture) | Return [ICoreWebView2ExperimentalWebTexture](icorewebview2experimentalwebtexture.md#icorewebview2experimentalwebtexture) object.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### get_WebTexture

Return [ICoreWebView2ExperimentalWebTexture](icorewebview2experimentalwebtexture.md#icorewebview2experimentalwebtexture) object.

> public HRESULT [get_WebTexture](#get_webtexture)([ICoreWebView2ExperimentalWebTexture](icorewebview2experimentalwebtexture.md#icorewebview2experimentalwebtexture) ** value)

