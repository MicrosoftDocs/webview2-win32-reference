---
description: This is ICoreWebView2ExperimentalEnvironment12 that returns the texture stream interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment12
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment12
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalEnvironment12
- ICoreWebView2ExperimentalEnvironment12.add_RenderAdapterLUIDChanged
- ICoreWebView2ExperimentalEnvironment12.CreateTextureStream
- ICoreWebView2ExperimentalEnvironment12.get_RenderAdapterLUID
- ICoreWebView2ExperimentalEnvironment12.remove_RenderAdapterLUIDChanged
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalEnvironment12

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment12
  : public IUnknown
```

This is ICoreWebView2ExperimentalEnvironment12 that returns the texture stream interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_RenderAdapterLUIDChanged](#add_renderadapterluidchanged) | Listens for change of graphics adapter LUID of the browser.
[CreateTextureStream](#createtexturestream) | Registers the stream id that the host can handle, providing a texture stream when requested from the WebView2's JavaScript code.
[get_RenderAdapterLUID](#get_renderadapterluid) | Get the graphics adapter LUID of the renderer.
[remove_RenderAdapterLUIDChanged](#remove_renderadapterluidchanged) | Remove listener for RenderAdapterLUIDChange event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### add_RenderAdapterLUIDChanged

Listens for change of graphics adapter LUID of the browser.

> public HRESULT [add_RenderAdapterLUIDChanged](#add_renderadapterluidchanged)([ICoreWebView2ExperimentalRenderAdapterLUIDChangedEventHandler](icorewebview2experimentalrenderadapterluidchangedeventhandler.md#icorewebview2experimentalrenderadapterluidchangedeventhandler) * eventHandler, EventRegistrationToken * token)

The host can get the updated LUID by RenderAdapterLUID. It is expected that the host updates texture's d3d Device with SetD3DDevice, removes existing textures and creates new texture.

#### CreateTextureStream

Registers the stream id that the host can handle, providing a texture stream when requested from the WebView2's JavaScript code.

> public HRESULT [CreateTextureStream](#createtexturestream)(LPCWSTR streamId, IUnknown * d3dDevice, [ICoreWebView2ExperimentalTextureStream](icorewebview2experimentaltexturestream.md#icorewebview2experimentaltexturestream) ** value)

The host can register multiple unique stream instances, each with a unique stream ID, enabling the host to stream from different sources concurrently. The host should call this only once for unique streamId. The second call of already created streamId without destroying [ICoreWebView2ExperimentalTextureStream](icorewebview2experimentaltexturestream.md#icorewebview2experimentaltexturestream) object will return an error. 'd3dDevice' is used for creating shared IDXGI resource and NT shared of it. The host should use Adapter of the LUID from the GetRenderAdapterLUID for creating the D3D Device.

#### get_RenderAdapterLUID

Get the graphics adapter LUID of the renderer.

> public HRESULT [get_RenderAdapterLUID](#get_renderadapterluid)(UINT64 * value)

The host should use this LUID adapter when creating D3D device to use with [CreateTextureStream()](#createtexturestream).

#### remove_RenderAdapterLUIDChanged

Remove listener for RenderAdapterLUIDChange event.

> public HRESULT [remove_RenderAdapterLUIDChanged](#remove_renderadapterluidchanged)(EventRegistrationToken token)

