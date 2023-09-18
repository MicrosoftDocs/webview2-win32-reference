---
description: 
title: WebView2 Win32 C++ ICoreWebView2_9
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_9
topic_type: 
- APIRef
api_name:
- ICoreWebView2_9
- ICoreWebView2_9.add_IsDefaultDownloadDialogOpenChanged
- ICoreWebView2_9.CloseDefaultDownloadDialog
- ICoreWebView2_9.get_DefaultDownloadDialogCornerAlignment
- ICoreWebView2_9.get_DefaultDownloadDialogMargin
- ICoreWebView2_9.get_IsDefaultDownloadDialogOpen
- ICoreWebView2_9.OpenDefaultDownloadDialog
- ICoreWebView2_9.put_DefaultDownloadDialogCornerAlignment
- ICoreWebView2_9.put_DefaultDownloadDialogMargin
- ICoreWebView2_9.remove_IsDefaultDownloadDialogOpenChanged
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_9

```
interface ICoreWebView2_9
  : public ICoreWebView2_8
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_IsDefaultDownloadDialogOpenChanged](#add_isdefaultdownloaddialogopenchanged) | Adds an event handler for the `IsDefaultDownloadDialogOpenChanged` event.
[CloseDefaultDownloadDialog](#closedefaultdownloaddialog) | 
[get_DefaultDownloadDialogCornerAlignment](#get_defaultdownloaddialogcorneralignment) | Gets the `DefaultDownloadDialogCornerAlignment` property.
[get_DefaultDownloadDialogMargin](#get_defaultdownloaddialogmargin) | Gets the `DefaultDownloadDialogMargin` property.
[get_IsDefaultDownloadDialogOpen](#get_isdefaultdownloaddialogopen) | Gets the `IsDefaultDownloadDialogOpen` property.
[OpenDefaultDownloadDialog](#opendefaultdownloaddialog) | 
[put_DefaultDownloadDialogCornerAlignment](#put_defaultdownloaddialogcorneralignment) | Sets the `DefaultDownloadDialogCornerAlignment` property.
[put_DefaultDownloadDialogMargin](#put_defaultdownloaddialogmargin) | Sets the `DefaultDownloadDialogMargin` property.
[remove_IsDefaultDownloadDialogOpenChanged](#remove_isdefaultdownloaddialogopenchanged) | Removes an event handler previously added with `add_IsDefaultDownloadDialogOpenChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1072.54
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### add_IsDefaultDownloadDialogOpenChanged

Adds an event handler for the `IsDefaultDownloadDialogOpenChanged` event.

> public HRESULT [add_IsDefaultDownloadDialogOpenChanged](#add_isdefaultdownloaddialogopenchanged)([ICoreWebView2IsDefaultDownloadDialogOpenChangedEventHandler](icorewebview2isdefaultdownloaddialogopenchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### CloseDefaultDownloadDialog

> public HRESULT [CloseDefaultDownloadDialog](#closedefaultdownloaddialog)()

#### get_DefaultDownloadDialogCornerAlignment

Gets the `DefaultDownloadDialogCornerAlignment` property.

> public HRESULT [get_DefaultDownloadDialogCornerAlignment](#get_defaultdownloaddialogcorneralignment)(COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT * value)

#### get_DefaultDownloadDialogMargin

Gets the `DefaultDownloadDialogMargin` property.

> public HRESULT [get_DefaultDownloadDialogMargin](#get_defaultdownloaddialogmargin)(POINT * value)

#### get_IsDefaultDownloadDialogOpen

Gets the `IsDefaultDownloadDialogOpen` property.

> public HRESULT [get_IsDefaultDownloadDialogOpen](#get_isdefaultdownloaddialogopen)(BOOL * value)

#### OpenDefaultDownloadDialog

> public HRESULT [OpenDefaultDownloadDialog](#opendefaultdownloaddialog)()

#### put_DefaultDownloadDialogCornerAlignment

Sets the `DefaultDownloadDialogCornerAlignment` property.

> public HRESULT [put_DefaultDownloadDialogCornerAlignment](#put_defaultdownloaddialogcorneralignment)(COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT value)

#### put_DefaultDownloadDialogMargin

Sets the `DefaultDownloadDialogMargin` property.

> public HRESULT [put_DefaultDownloadDialogMargin](#put_defaultdownloaddialogmargin)(POINT value)

#### remove_IsDefaultDownloadDialogOpenChanged

Removes an event handler previously added with `add_IsDefaultDownloadDialogOpenChanged`.

> public HRESULT [remove_IsDefaultDownloadDialogOpenChanged](#remove_isdefaultdownloaddialogopenchanged)(EventRegistrationToken token)

