---
description: Implements the interface to receive `IsDocumentPlayingAudioChanged` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalIsDocumentPlayingAudioChangedEventHandler
ms.date: 11/29/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalIsDocumentPlayingAudioChangedEventHandler
---

# interface ICoreWebView2ExperimentalIsDocumentPlayingAudioChangedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalIsDocumentPlayingAudioChangedEventHandler
  : public IUnknown
```

Implements the interface to receive `IsDocumentPlayingAudioChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

Use the IsDocumentPlayingAudio property to get the audio playing state.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1018

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

