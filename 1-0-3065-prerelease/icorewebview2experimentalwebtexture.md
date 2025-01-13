---
description: Received texture that the renderer writes to so that the host will read on it.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalWebTexture
ms.date: 01/13/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalWebTexture
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalWebTexture
- ICoreWebView2ExperimentalWebTexture.get_Handle
- ICoreWebView2ExperimentalWebTexture.get_Resource
- ICoreWebView2ExperimentalWebTexture.get_Timestamp
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalWebTexture

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalWebTexture
  : public IUnknown
```

Received texture that the renderer writes to so that the host will read on it.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handle](#get_handle) | texture handle.
[get_Resource](#get_resource) | Direct2D texture resource.
[get_Timestamp](#get_timestamp) | The timestamp of the web texture.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### get_Handle

texture handle.

> public HRESULT [get_Handle](#get_handle)(HANDLE * value)

The handle's lifetime is owned by the ICoreWebView2TextureStream object so the host must not close it. The same handle value will be used for same texture so the host can use handle value as a unique texture key. If the host opens its own resources by handle, then it is suggested that the host removes those resources when the handle's texture size is changed because the browser also removed previously allocated different sized textures when image size is changed.

#### get_Resource

Direct2D texture resource.

> public HRESULT [get_Resource](#get_resource)(IUnknown ** value)

The same resource value will be used for same texture so the host can use resource value as a unique texture key. [ICoreWebView2ExperimentalTextureStream](icorewebview2experimentaltexturestream.md#icorewebview2experimentaltexturestream) object has a reference of the resource so ICoreWebView2ExperimentalWebTexture holds same resource object for the same texture.

#### get_Timestamp

The timestamp of the web texture.

> public HRESULT [get_Timestamp](#get_timestamp)(UINT64 * value)

Javascript can set this value with any value, but it is suggested to use same value of its original video frame that is a value of PresentTexture so that the host is able to tell the receiving texture delta.

