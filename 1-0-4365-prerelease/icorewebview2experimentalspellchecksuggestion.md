---
description: Represents a spelling correction that can be applied through ICoreWebView2ContextMenuRequestedEventArgs::put_SelectedCommandId.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSpellCheckSuggestion
ms.date: 10/28/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSpellCheckSuggestion
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSpellCheckSuggestion
- ICoreWebView2ExperimentalSpellCheckSuggestion.get_CommandId
- ICoreWebView2ExperimentalSpellCheckSuggestion.get_SuggestionText
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSpellCheckSuggestion

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSpellCheckSuggestion
  : public IUnknown
```

Represents a spelling correction that can be applied through [ICoreWebView2ContextMenuRequestedEventArgs::put_SelectedCommandId](icorewebview2contextmenurequestedeventargs.md#put_selectedcommandid).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_CommandId](#get_commandid) | Gets the opaque command ID used to apply this correction.
[get_SuggestionText](#get_suggestiontext) | Gets the browser-generated spelling correction text.

The object remains readable while retained. Its `CommandId` is valid only for the originating context menu request and must be assigned before that request's deferral is completed.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_CommandId

Gets the opaque command ID used to apply this correction.

> public HRESULT [get_CommandId](#get_commandid)(INT32 * value)

Assign this value to [ICoreWebView2ContextMenuRequestedEventArgs::put_SelectedCommandId](icorewebview2contextmenurequestedeventargs.md#put_selectedcommandid) before completing the context menu deferral. Do not invent, modify, or retain this value for a later context menu request. Suggestion and context menu item command IDs share the originating request's command namespace. Equal IDs identify the same command, so do not assume this value differs from every [ICoreWebView2ContextMenuItem::get_CommandId](icorewebview2contextmenuitem.md#get_commandid) in that request.

#### get_SuggestionText

Gets the browser-generated spelling correction text.

> public HRESULT [get_SuggestionText](#get_suggestiontext)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

