---
description: This is the interface that handles texture streaming.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTextureStream
ms.date: 03/25/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTextureStream
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalTextureStream
- ICoreWebView2ExperimentalTextureStream.add_ErrorReceived
- ICoreWebView2ExperimentalTextureStream.add_StartRequested
- ICoreWebView2ExperimentalTextureStream.add_Stopped
- ICoreWebView2ExperimentalTextureStream.add_WebTextureReceived
- ICoreWebView2ExperimentalTextureStream.add_WebTextureStreamStopped
- ICoreWebView2ExperimentalTextureStream.AddAllowedOrigin
- ICoreWebView2ExperimentalTextureStream.CloseTexture
- ICoreWebView2ExperimentalTextureStream.CreateTexture
- ICoreWebView2ExperimentalTextureStream.get_Id
- ICoreWebView2ExperimentalTextureStream.GetAvailableTexture
- ICoreWebView2ExperimentalTextureStream.PresentTexture
- ICoreWebView2ExperimentalTextureStream.remove_ErrorReceived
- ICoreWebView2ExperimentalTextureStream.remove_StartRequested
- ICoreWebView2ExperimentalTextureStream.remove_Stopped
- ICoreWebView2ExperimentalTextureStream.remove_WebTextureReceived
- ICoreWebView2ExperimentalTextureStream.remove_WebTextureStreamStopped
- ICoreWebView2ExperimentalTextureStream.RemoveAllowedOrigin
- ICoreWebView2ExperimentalTextureStream.SetD3DDevice
- ICoreWebView2ExperimentalTextureStream.Stop
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalTextureStream

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalTextureStream
  : public IUnknown
```

This is the interface that handles texture streaming.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ErrorReceived](#add_errorreceived) | The `ErrorReceived` event is raised when an error with this texture stream occurs asynchronously.
[add_StartRequested](#add_startrequested) | Listens for stream requests from the Javascript's getTextureStream call for this stream's id.
[add_Stopped](#add_stopped) | Listen to stop stream request once the stream started.
[add_WebTextureReceived](#add_webtexturereceived) | Event handler for receiving texture by Javascript.
[add_WebTextureStreamStopped](#add_webtexturestreamstopped) | The WebTextureStreamStopped event is raised when script unregisters its MediaStream from this texture stream.
[AddAllowedOrigin](#addallowedorigin) | Adds an allowed URI origin.
[CloseTexture](#closetexture) | Removes texture when the host removes the backed 2D texture.
[CreateTexture](#createtexture) | Creates texture that will be referenced by the host and the browser.
[get_Id](#get_id) | Get the stream ID of the object that is used when calling CreateTextureStream.
[GetAvailableTexture](#getavailabletexture) | Returns reuseable texture for video frame rendering.
[PresentTexture](#presenttexture) | Adds the provided `ICoreWebView2Texture` to the video stream as the next frame.
[remove_ErrorReceived](#remove_errorreceived) | Remove listener for ErrorReceived event.
[remove_StartRequested](#remove_startrequested) | Remove listener for StartRequest event.
[remove_Stopped](#remove_stopped) | Remove listener for Stopped event.
[remove_WebTextureReceived](#remove_webtexturereceived) | Remove listener for WebTextureReceived event.
[remove_WebTextureStreamStopped](#remove_webtexturestreamstopped) | Remove listener for WebTextureStreamStopped event.
[RemoveAllowedOrigin](#removeallowedorigin) | Remove added origin, which was added by AddAllowedOrigin.
[SetD3DDevice](#setd3ddevice) | Set the D3D device this texture stream should use for creating shared texture resources.
[Stop](#stop) | Stops this texture stream from streaming and moves it into the stopped state.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### add_ErrorReceived

The `ErrorReceived` event is raised when an error with this texture stream occurs asynchronously.

> public HRESULT [add_ErrorReceived](#add_errorreceived)([ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler](icorewebview2experimentaltexturestreamerrorreceivedeventhandler.md#icorewebview2experimentaltexturestreamerrorreceivedeventhandler) * eventHandler, EventRegistrationToken * token)

#### add_StartRequested

Listens for stream requests from the Javascript's getTextureStream call for this stream's id.

> public HRESULT [add_StartRequested](#add_startrequested)([ICoreWebView2ExperimentalTextureStreamStartRequestedEventHandler](icorewebview2experimentaltexturestreamstartrequestedeventhandler.md#icorewebview2experimentaltexturestreamstartrequestedeventhandler) * eventHandler, EventRegistrationToken * token)

It is called for the first request only, and will not be called with subsequent requests of same stream id from any pages in the middle of request handling or after it returns success. The request is regarded as success only when the host provides the stream, Present API call, within 10s after being requested. The texture stream becomes 'Started' state once it starts sending a texture until it calls Stop API or receives 'Stopped' event.

#### add_Stopped

Listen to stop stream request once the stream started.

> public HRESULT [add_Stopped](#add_stopped)([ICoreWebView2ExperimentalTextureStreamStoppedEventHandler](icorewebview2experimentaltexturestreamstoppedeventhandler.md#icorewebview2experimentaltexturestreamstoppedeventhandler) * eventHandler, EventRegistrationToken * token)

It is called when user stop all streaming requests from the renderers (Javascript) or the host calls the Stop API. The renderer can stream again by calling the streaming request API. The renderer cleared all registered Textures before sending the stop request event so that the callback of the next start request should register the textures again. The event is triggered when all requests for given stream id closed by the Javascript, or the host's Stop API call. texture related API calls after this event will return an error of HRESULT_FROM_WIN32(ERROR_INVALID_STATE).

#### add_WebTextureReceived

Event handler for receiving texture by Javascript.

> public HRESULT [add_WebTextureReceived](#add_webtexturereceived)([ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventHandler](icorewebview2experimentaltexturestreamwebtexturereceivedeventhandler.md#icorewebview2experimentaltexturestreamwebtexturereceivedeventhandler) * eventHandler, EventRegistrationToken * token)

The WebTextureReceived event is raised when script sends a video frame to this texture stream. Allowed script will call `chrome.webview. registerTextureStream` to register a MediaStream with a specified texture stream. Video frames added to that MediaStream will be raised in the WebTextureReceived event. See `registerTextureStream` for details. Script is allowed to call registerTextureStream if it is from an HTML document with an origin allowed via `ICoreWebView2TextureStream::AddAllowedOrigin` with the `allowWebTexture` parameter set. See `AddAllowedOrigin` for details.

#### add_WebTextureStreamStopped

The WebTextureStreamStopped event is raised when script unregisters its MediaStream from this texture stream.

> public HRESULT [add_WebTextureStreamStopped](#add_webtexturestreamstopped)([ICoreWebView2ExperimentalTextureStreamWebTextureStreamStoppedEventHandler](icorewebview2experimentaltexturestreamwebtexturestreamstoppedeventhandler.md#icorewebview2experimentaltexturestreamwebtexturestreamstoppedeventhandler) * eventHandler, EventRegistrationToken * token)

Script that has previously called `chrome.webview.registerTextureStream`, can call `chrome.webview. unregisterTextureStream` which will raise this event and then close associated ICoreWebView2WebTexture objects in the browser side. You should ensure that you release any references to associated ICoreWebView2WebTexture objects and their underlying resources. Once stopped, script may start again by calling `chrome.webview. registerTextureStream` and sending more frames. In this case the `ICoreWebView2TextureStream WebTextureReceived` event will be raised again.

#### AddAllowedOrigin

Adds an allowed URI origin.

> public HRESULT [AddAllowedOrigin](#addallowedorigin)(LPCWSTR origin, BOOL value)

The stream requests could be made from any frame, including iframes, but the origin of the page in the frames must be registered first in order for the request to succeed. The added origin will be persistent until ICoreWebView2ExperimentalTextureStream is destroyed or RemoveAllowedOrigin is called. The renderer does not support wildcard so it will compare literal string input to the requesting frame's page's origin after normalization. The page origin will be normalized so ASCII characters in the scheme and hostname will be lowercased, and non-ASCII characters in the hostname will be normalized to their punycode form. For example `HTTPS://WWW.???.COM` will be normalized to `https://www.xn--kfk.com` for comparison. So, the input string should have a scheme like `https://`. For example, `https://www.valid-host.com`, `http://www.valid-host.com` are valid origins but `www.valid-host.com`, or `https://*.valid-host.com.` are not valid origins. If invalid origin is provided, the API will return an error of E_INVALIDARG. getTextureStream() will fail unless the requesting frame's origin URI is added to the allowed origins. If `value` is TRUE, then the origin will also be added to WebTexture's allowed origin.

#### CloseTexture

Removes texture when the host removes the backed 2D texture.

> public HRESULT [CloseTexture](#closetexture)([ICoreWebView2ExperimentalTexture](icorewebview2experimentaltexture.md#icorewebview2experimentaltexture) * texture)

The host can save the resources by deleting 2D textures when it changes the frame sizes. The API will send a message to the browser where it will remove texture.

#### CreateTexture

Creates texture that will be referenced by the host and the browser.

> public HRESULT [CreateTexture](#createtexture)(UINT32 widthInTexels, UINT32 heightInTexels, [ICoreWebView2ExperimentalTexture](icorewebview2experimentaltexture.md#icorewebview2experimentaltexture) ** texture)

By using the texture mechanism, the host does not have to send respective texture to the renderer, instead it notifies it with internal texture id, which is the identity of the texture. The texture is 2D texture, IDXGIResource, format and will be exposed through shared HANDLE or IUnknown type through [ICoreWebView2ExperimentalTexture](icorewebview2experimentaltexture.md#icorewebview2experimentaltexture). Whenever the host has new texture to write, it should ask reusable [ICoreWebView2ExperimentalTexture](icorewebview2experimentaltexture.md#icorewebview2experimentaltexture) from the GetAvailableTexture, which returns [ICoreWebView2ExperimentalTexture](icorewebview2experimentaltexture.md#icorewebview2experimentaltexture). If the GetAvailableTexture returns an error, then the host calls the CreateTexture to allocate new texture. The API also registers created shared handle to the browser once it created the resource.

Unit for width and height is texture unit (in texels) [D3D11_TEXTURE2D_DESC](/windows/win32/api/d3d11/ns-d3d11-d3d11_texture2d_desc).

#### get_Id

Get the stream ID of the object that is used when calling CreateTextureStream.

> public HRESULT [get_Id](#get_id)(LPWSTR * value)

The caller must free the returned string with CoTaskMemFree. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings). MSOWNERS: TBD ([wv2core@microsoft.com](mailto:wv2core@microsoft.com))

#### GetAvailableTexture

Returns reuseable texture for video frame rendering.

> public HRESULT [GetAvailableTexture](#getavailabletexture)([ICoreWebView2ExperimentalTexture](icorewebview2experimentaltexture.md#icorewebview2experimentaltexture) ** texture)

Once the renderer finishes rendering of texture's video frame, which was requested by Present, the renderer informs the host so that it can be reused. The host has to create new texture with CreateTexture if the API return an error HRESULT_FROM_WIN32(ERROR_NO_MORE_ITEMS).

#### PresentTexture

Adds the provided `ICoreWebView2Texture` to the video stream as the next frame.

> public HRESULT [PresentTexture](#presenttexture)([ICoreWebView2ExperimentalTexture](icorewebview2experimentaltexture.md#icorewebview2experimentaltexture) * texture)

The `ICoreWebView2Texture` must not be closed. The `ICoreWebView2Texture` must have been obtained via a call to `ICoreWebView2TextureStream::GetAvailableTexture` or ` ICoreWebView2TextureStream::CreateTexture` from this `ICoreWebView2TextureStream`. If the `ICoreWebView2Texture` is closed or was created from a different `ICoreWebView2TextureStream` this method will return `E_INVALIDARG`. You should write your video frame data to the `ICoreWebView2Texture` before calling this method. After this method completes WebView2 will take some time asynchronously to send the texture to the WebView2 processes to be added to the video stream. Do not close or otherwise change the provided `ICoreWebView2Texture` after calling this method. Doing so may result in the texture not being added to the texture stream and the `ErrorReceived` event may be raised.

#### remove_ErrorReceived

Remove listener for ErrorReceived event.

> public HRESULT [remove_ErrorReceived](#remove_errorreceived)(EventRegistrationToken token)

#### remove_StartRequested

Remove listener for StartRequest event.

> public HRESULT [remove_StartRequested](#remove_startrequested)(EventRegistrationToken token)

#### remove_Stopped

Remove listener for Stopped event.

> public HRESULT [remove_Stopped](#remove_stopped)(EventRegistrationToken token)

#### remove_WebTextureReceived

Remove listener for WebTextureReceived event.

> public HRESULT [remove_WebTextureReceived](#remove_webtexturereceived)(EventRegistrationToken token)

#### remove_WebTextureStreamStopped

Remove listener for WebTextureStreamStopped event.

> public HRESULT [remove_WebTextureStreamStopped](#remove_webtexturestreamstopped)(EventRegistrationToken token)

#### RemoveAllowedOrigin

Remove added origin, which was added by AddAllowedOrigin.

> public HRESULT [RemoveAllowedOrigin](#removeallowedorigin)(LPCWSTR origin)

The allowed or disallowed origins will take effect only when Javascript request a streaming. So, once the streaming started, it does not stop streaming.

#### SetD3DDevice

Set the D3D device this texture stream should use for creating shared texture resources.

> public HRESULT [SetD3DDevice](#setd3ddevice)(IUnknown * d3dDevice)

When the RenderAdapterLUIDChanged event is raised you should create a new D3D device using the RenderAdapterLUID property and call SetD3DDevice with the new D3D device. See the `CreateTextureStream``d3dDevice` parameter for more details.

#### Stop

Stops this texture stream from streaming and moves it into the stopped state.

> public HRESULT [Stop](#stop)()

When moving to the stopped state the `ICoreWebView2TextureStream Stopped` event will be raised and in script the `MediaStreamTrack ended` event will be raised. Once stopped, script may again call `Webview.getTextureStream` moving the texture stream back to the start requested state. See the `StartRequested` event for details. Once stopped, calls to CreateTexture, GetAvailableTexture, PresentTexture, and CloseTexture will fail with HRESULT_FROM_WIN32(ERROR_INVALID_STATE). The `Stop` method is implicitly called when the texture stream object is destroyed.

