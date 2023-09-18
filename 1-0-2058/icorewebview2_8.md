---
description: 
title: WebView2 Win32 C++ ICoreWebView2_8
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_8
topic_type: 
- APIRef
api_name:
- ICoreWebView2_8
- ICoreWebView2_8.add_IsDocumentPlayingAudioChanged
- ICoreWebView2_8.add_IsMutedChanged
- ICoreWebView2_8.get_IsDocumentPlayingAudio
- ICoreWebView2_8.get_IsMuted
- ICoreWebView2_8.put_IsMuted
- ICoreWebView2_8.remove_IsDocumentPlayingAudioChanged
- ICoreWebView2_8.remove_IsMutedChanged
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_8

```
interface ICoreWebView2_8
  : public ICoreWebView2_7
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_IsDocumentPlayingAudioChanged](#add_isdocumentplayingaudiochanged) | Adds an event handler for the `IsDocumentPlayingAudioChanged` event.
[add_IsMutedChanged](#add_ismutedchanged) | Adds an event handler for the `IsMutedChanged` event.
[get_IsDocumentPlayingAudio](#get_isdocumentplayingaudio) | Gets the `IsDocumentPlayingAudio` property.
[get_IsMuted](#get_ismuted) | Gets the `IsMuted` property.
[put_IsMuted](#put_ismuted) | Sets the `IsMuted` property.
[remove_IsDocumentPlayingAudioChanged](#remove_isdocumentplayingaudiochanged) | Removes an event handler previously added with `add_IsDocumentPlayingAudioChanged`.
[remove_IsMutedChanged](#remove_ismutedchanged) | Removes an event handler previously added with `add_IsMutedChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1072.54
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### add_IsDocumentPlayingAudioChanged

Adds an event handler for the `IsDocumentPlayingAudioChanged` event.

> public HRESULT [add_IsDocumentPlayingAudioChanged](#add_isdocumentplayingaudiochanged)([ICoreWebView2IsDocumentPlayingAudioChangedEventHandler](icorewebview2isdocumentplayingaudiochangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_IsMutedChanged

Adds an event handler for the `IsMutedChanged` event.

> public HRESULT [add_IsMutedChanged](#add_ismutedchanged)([ICoreWebView2IsMutedChangedEventHandler](icorewebview2ismutedchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### get_IsDocumentPlayingAudio

Gets the `IsDocumentPlayingAudio` property.

> public HRESULT [get_IsDocumentPlayingAudio](#get_isdocumentplayingaudio)(BOOL * value)

#### get_IsMuted

Gets the `IsMuted` property.

> public HRESULT [get_IsMuted](#get_ismuted)(BOOL * value)

#### put_IsMuted

Sets the `IsMuted` property.

> public HRESULT [put_IsMuted](#put_ismuted)(BOOL value)

#### remove_IsDocumentPlayingAudioChanged

Removes an event handler previously added with `add_IsDocumentPlayingAudioChanged`.

> public HRESULT [remove_IsDocumentPlayingAudioChanged](#remove_isdocumentplayingaudiochanged)(EventRegistrationToken token)

#### remove_IsMutedChanged

Removes an event handler previously added with `add_IsMutedChanged`.

> public HRESULT [remove_IsMutedChanged](#remove_ismutedchanged)(EventRegistrationToken token)

