---
description: texture that the host writes to so that the Renderer will render on it.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTexture
ms.date: 02/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTexture
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalTexture
- ICoreWebView2ExperimentalTexture.get_Handle
- ICoreWebView2ExperimentalTexture.get_Resource
- ICoreWebView2ExperimentalTexture.get_Timestamp
- ICoreWebView2ExperimentalTexture.put_Timestamp
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalTexture

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalTexture
  : public IUnknown
```

texture that the host writes to so that the Renderer will render on it.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handle](#get_handle) | A handle to OS shared memory containing the texture.
[get_Resource](#get_resource) | Returns IUnknown type that could be query interface to IDXGIResource.
[get_Timestamp](#get_timestamp) | Gets timestamp of presenting texture.
[put_Timestamp](#put_timestamp) | Sets timestamp of presenting texture.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### get_Handle

A handle to OS shared memory containing the texture.

> public HRESULT [get_Handle](#get_handle)(HANDLE * value)

You can open it with `ID3D11Device1::OpenSharedResource1` and write your texture data to it. Do not close it yourself. The underlying texture will be closed by WebView2. Do not change the texture after calling `ICoreWebView2TextureStream::PresentTexture` before you can retrieve it again with `GetAvailableTexture`, or you the frame may not be rendered and the `ICoreWebView2TextureStream ErrorReceived` event will be raised.

#### get_Resource

Returns IUnknown type that could be query interface to IDXGIResource.

> public HRESULT [get_Resource](#get_resource)(IUnknown ** value)

The caller can write incoming texture to it.

#### get_Timestamp

Gets timestamp of presenting texture.

> public HRESULT [get_Timestamp](#get_timestamp)(UINT64 * value)

#### put_Timestamp

Sets timestamp of presenting texture.

> public HRESULT [put_Timestamp](#put_timestamp)(UINT64 value)

`value` is video capture time with microseconds units. The value does not have to be exact captured time, but it should be increasing order because renderer (composition) ignores incoming video frame (texture) if its timestamp is equal or prior to the current compositing video frame. It also will be exposed to the JS with `VideoFrame::timestamp`. (https://docs.w3cub.com/dom/videoframe/timestamp.html).

