---
description: Receives the result of the `GetSpellCheckSuggestions` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalGetSpellCheckSuggestionsCompletedHandler
ms.date: 10/28/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalGetSpellCheckSuggestionsCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalGetSpellCheckSuggestionsCompletedHandler
- ICoreWebView2ExperimentalGetSpellCheckSuggestionsCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalGetSpellCheckSuggestionsCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalGetSpellCheckSuggestionsCompletedHandler
  : public IUnknown
```

Receives the result of the `GetSpellCheckSuggestions` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalSpellCheckSuggestionCollectionView](icorewebview2experimentalspellchecksuggestioncollectionview.md#icorewebview2experimentalspellchecksuggestioncollectionview) * result)

