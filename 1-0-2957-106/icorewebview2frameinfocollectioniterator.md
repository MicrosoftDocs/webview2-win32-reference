---
description: Iterator for a collection of `FrameInfo`s.
title: WebView2 Win32 C++ ICoreWebView2FrameInfoCollectionIterator
ms.date: 01/13/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameInfoCollectionIterator
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameInfoCollectionIterator
- ICoreWebView2FrameInfoCollectionIterator.get_HasCurrent
- ICoreWebView2FrameInfoCollectionIterator.GetCurrent
- ICoreWebView2FrameInfoCollectionIterator.MoveNext
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameInfoCollectionIterator

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2FrameInfoCollectionIterator
  : public IUnknown
```

Iterator for a collection of `FrameInfo`s.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HasCurrent](#get_hascurrent) | `TRUE` when the iterator has not run out of `FrameInfo`s.
[GetCurrent](#getcurrent) | Get the current [ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) of the iterator.
[MoveNext](#movenext) | Move the iterator to the next `FrameInfo` in the collection.

For more info, see [ICoreWebView2ProcessFailedEventArgs2](icorewebview2processfailedeventargs2.md#icorewebview2processfailedeventargs2) and [ICoreWebView2FrameInfoCollection](icorewebview2frameinfocollection.md#icorewebview2frameinfocollection).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.818.41
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_HasCurrent

`TRUE` when the iterator has not run out of `FrameInfo`s.

> public HRESULT [get_HasCurrent](#get_hascurrent)(BOOL * value)

If the collection over which the iterator is iterating is empty or if the iterator has gone past the end of the collection, then this is `FALSE`.

#### GetCurrent

Get the current [ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) of the iterator.

> public HRESULT [GetCurrent](#getcurrent)([ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) ** value)

Returns `HRESULT_FROM_WIN32(ERROR_INVALID_INDEX)` if HasCurrent is `FALSE`.

#### MoveNext

Move the iterator to the next `FrameInfo` in the collection.

> public HRESULT [MoveNext](#movenext)(BOOL * value)

