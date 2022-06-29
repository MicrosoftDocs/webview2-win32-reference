---
description: Collection of `FrameInfo`s (name and source).
title: WebView2 Win32 C++ ICoreWebView2FrameInfoCollection
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameInfoCollection
---

# interface ICoreWebView2FrameInfoCollection

```
interface ICoreWebView2FrameInfoCollection
  : public IUnknown
```

Collection of `FrameInfo`s (name and source).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetIterator](#getiterator) | Gets an iterator over the collection of `FrameInfo`s.

Used to list the affected frames' info when a frame-only render process failure occurs in the ICoreWebView2.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.818.41
WebView2 Win32 Prerelease |    1.0.824

## Members

#### GetIterator

Gets an iterator over the collection of `FrameInfo`s.

> public HRESULT [GetIterator](#getiterator)(ICoreWebView2FrameInfoCollectionIterator ** iterator)

