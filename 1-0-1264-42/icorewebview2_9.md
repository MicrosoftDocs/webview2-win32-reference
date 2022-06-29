---
description: This interface is an extension of ICoreWebView2_8 that default download dialog positioning and anchoring.
title: WebView2 Win32 C++ ICoreWebView2_9
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_9
---

# interface ICoreWebView2_9

```
interface ICoreWebView2_9
  : public ICoreWebView2_8
```

This interface is an extension of [ICoreWebView2_8](icorewebview2_8.md) that default download dialog positioning and anchoring.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_IsDefaultDownloadDialogOpenChanged](#add_isdefaultdownloaddialogopenchanged) | Raised when the `IsDefaultDownloadDialogOpen` property changes.
[CloseDefaultDownloadDialog](#closedefaultdownloaddialog) | Close the default download dialog.
[get_DefaultDownloadDialogCornerAlignment](#get_defaultdownloaddialogcorneralignment) | Get the default download dialog corner alignment.
[get_DefaultDownloadDialogMargin](#get_defaultdownloaddialogmargin) | Get the default download dialog margin.
[get_IsDefaultDownloadDialogOpen](#get_isdefaultdownloaddialogopen) | `TRUE` if the default download dialog is currently open.
[OpenDefaultDownloadDialog](#opendefaultdownloaddialog) | Open the default download dialog.
[put_DefaultDownloadDialogCornerAlignment](#put_defaultdownloaddialogcorneralignment) | Set the default download dialog corner alignment.
[put_DefaultDownloadDialogMargin](#put_defaultdownloaddialogmargin) | Set the default download dialog margin relative to the WebView corner specified by `DefaultDownloadDialogCornerAlignment`.
[remove_IsDefaultDownloadDialogOpenChanged](#remove_isdefaultdownloaddialogopenchanged) | Remove an event handler previously added with `add_IsDefaultDownloadDialogOpenChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1072.54
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### add_IsDefaultDownloadDialogOpenChanged

Raised when the `IsDefaultDownloadDialogOpen` property changes.

> public HRESULT [add_IsDefaultDownloadDialogOpenChanged](#add_isdefaultdownloaddialogopenchanged)([ICoreWebView2IsDefaultDownloadDialogOpenChangedEventHandler](icorewebview2isdefaultdownloaddialogopenchangedeventhandler.md) * handler, EventRegistrationToken * token)

This event comes after the `DownloadStarting` event. Setting the `Handled` property on the `DownloadStartingEventArgs` disables the default download dialog and ensures that this event is never raised.

#### CloseDefaultDownloadDialog

Close the default download dialog.

> public HRESULT [CloseDefaultDownloadDialog](#closedefaultdownloaddialog)()

Calling this method raises the `IsDefaultDownloadDialogOpenChanged` event if the dialog was open. No effect if the dialog is already closed.

#### get_DefaultDownloadDialogCornerAlignment

Get the default download dialog corner alignment.

> public HRESULT [get_DefaultDownloadDialogCornerAlignment](#get_defaultdownloaddialogcorneralignment)([COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT](icorewebview2.md) * value)

#### get_DefaultDownloadDialogMargin

Get the default download dialog margin.

> public HRESULT [get_DefaultDownloadDialogMargin](#get_defaultdownloaddialogmargin)(POINT * value)

#### get_IsDefaultDownloadDialogOpen

`TRUE` if the default download dialog is currently open.

> public HRESULT [get_IsDefaultDownloadDialogOpen](#get_isdefaultdownloaddialogopen)(BOOL * value)

The value of this property changes only when the default download dialog is explicitly opened or closed. Hiding the WebView implicitly hides the dialog, but does not change the value of this property.

#### OpenDefaultDownloadDialog

Open the default download dialog.

> public HRESULT [OpenDefaultDownloadDialog](#opendefaultdownloaddialog)()

If the dialog is opened before there are recent downloads, the dialog shows all past downloads for the current profile. Otherwise, the dialog shows only the recent downloads with a "See more" button for past downloads. Calling this method raises the `IsDefaultDownloadDialogOpenChanged` event if the dialog was closed. No effect if the dialog is already open.

```cpp
void ViewComponent::ToggleDefaultDownloadDialog()
{
    if (m_webView2_9)
    {
        BOOL isOpen;
        m_webView2_9->get_IsDefaultDownloadDialogOpen(&isOpen);
        if (isOpen)
        {
            m_webView2_9->CloseDefaultDownloadDialog();
        }
        else
        {
            m_webView2_9->OpenDefaultDownloadDialog();
        }
    }
}
```

#### put_DefaultDownloadDialogCornerAlignment

Set the default download dialog corner alignment.

> public HRESULT [put_DefaultDownloadDialogCornerAlignment](#put_defaultdownloaddialogcorneralignment)([COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT](icorewebview2.md) value)

The dialog can be aligned to any of the WebView corners (see COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT). When the WebView or dialog changes size, the dialog keeps its position relative to the corner. The dialog may become partially or completely outside of the WebView bounds if the WebView is small enough. Set the margin relative to the corner with the `DefaultDownloadDialogMargin` property.

```cpp
void ViewComponent::SetDefaultDownloadDialogPosition()
{
    COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT cornerAlignment =
        COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT_TOP_LEFT;
    POINT margin = {m_downloadsButtonMargin,
        (m_downloadsButtonMargin + m_downloadsButtonHeight)};
    CHECK_FAILURE(
        m_webView2_9->put_DefaultDownloadDialogCornerAlignment(
        cornerAlignment));
    CHECK_FAILURE(
        m_webView2_9->put_DefaultDownloadDialogMargin(margin));
}
```

#### put_DefaultDownloadDialogMargin

Set the default download dialog margin relative to the WebView corner specified by `DefaultDownloadDialogCornerAlignment`.

> public HRESULT [put_DefaultDownloadDialogMargin](#put_defaultdownloaddialogmargin)(POINT value)

The margin is a point that describes the vertical and horizontal distances between the chosen WebView corner and the default download dialog corner nearest to it. Positive values move the dialog towards the center of the WebView from the chosen WebView corner, and negative values move the dialog away from it. Use (0, 0) to align the dialog to the WebView corner with no margin.

#### remove_IsDefaultDownloadDialogOpenChanged

Remove an event handler previously added with `add_IsDefaultDownloadDialogOpenChanged`.

> public HRESULT [remove_IsDefaultDownloadDialogOpenChanged](#remove_isdefaultdownloaddialogopenchanged)(EventRegistrationToken token)

