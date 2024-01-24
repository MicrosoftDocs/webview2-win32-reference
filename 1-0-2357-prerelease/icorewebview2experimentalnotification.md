---
description: This is the ICoreWebView2ExperimentalNotification that represents a HTML Notification object.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalNotification
ms.date: 01/29/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalNotification
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalNotification
- ICoreWebView2ExperimentalNotification.add_CloseRequested
- ICoreWebView2ExperimentalNotification.get_BadgeUri
- ICoreWebView2ExperimentalNotification.get_Body
- ICoreWebView2ExperimentalNotification.get_BodyImageUri
- ICoreWebView2ExperimentalNotification.get_Direction
- ICoreWebView2ExperimentalNotification.get_IconUri
- ICoreWebView2ExperimentalNotification.get_IsSilent
- ICoreWebView2ExperimentalNotification.get_Language
- ICoreWebView2ExperimentalNotification.get_RequiresInteraction
- ICoreWebView2ExperimentalNotification.get_ShouldRenotify
- ICoreWebView2ExperimentalNotification.get_Tag
- ICoreWebView2ExperimentalNotification.get_Timestamp
- ICoreWebView2ExperimentalNotification.get_Title
- ICoreWebView2ExperimentalNotification.GetVibrationPattern
- ICoreWebView2ExperimentalNotification.remove_CloseRequested
- ICoreWebView2ExperimentalNotification.ReportClicked
- ICoreWebView2ExperimentalNotification.ReportClosed
- ICoreWebView2ExperimentalNotification.ReportShown
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalNotification

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalNotification
  : public IUnknown
```

This is the ICoreWebView2ExperimentalNotification that represents a [HTML Notification object](https://developer.mozilla.org/docs/Web/API/Notification).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_CloseRequested](#add_closerequested) | Add an event handler for the `CloseRequested` event.
[get_BadgeUri](#get_badgeuri) | A string containing the URI of the image used to represent the notification when there isn't enough space to display the notification itself.
[get_Body](#get_body) | A string representing the body text of the notification.
[get_BodyImageUri](#get_bodyimageuri) | A string containing the URI of an image to be displayed in the notification.
[get_Direction](#get_direction) | The text direction in which to display the notification.
[get_IconUri](#get_iconuri) | A string containing the URI of an icon to be displayed in the notification.
[get_IsSilent](#get_issilent) | Indicates whether the notification should be silent &ndash; i.e., no sounds or vibrations should be issued, regardless of the device settings.
[get_Language](#get_language) | The notification's language, as intended to be specified using a string representing a language tag (such as `en-US`) according to [BCP47](https://datatracker.ietf.org/doc/html/rfc5646).
[get_RequiresInteraction](#get_requiresinteraction) | A boolean value indicating that a notification should remain active until the user clicks or dismisses it, rather than closing automatically.
[get_ShouldRenotify](#get_shouldrenotify) | Indicates whether the user should be notified after a new notification replaces an old one.
[get_Tag](#get_tag) | A string representing an identifying tag for the notification.
[get_Timestamp](#get_timestamp) | Indicates the time at which a notification is created or applicable (past, present, or future) as the number of milliseconds since the UNIX epoch.
[get_Title](#get_title) | The title of the notification.
[GetVibrationPattern](#getvibrationpattern) | Gets the vibration pattern for devices with vibration hardware to emit.
[remove_CloseRequested](#remove_closerequested) | Remove an event handler previously added with `add_CloseRequested`.
[ReportClicked](#reportclicked) | The host may run this to report the notification has been clicked, and it will cause the [click](https://developer.mozilla.org/docs/Web/API/Notification/click_event) event to be raised for non-persistent notifications and the [notificationclick](https://developer.mozilla.org/docs/Web/API/ServiceWorkerGlobalScope/notificationclick_event) event for persistent notifications.
[ReportClosed](#reportclosed) | The host may run this to report the notification was dismissed, and it will cause the [close](https://developer.mozilla.org/docs/Web/API/Notification/close_event) event to be raised for non-persistent notifications and the [notificationclose](https://developer.mozilla.org/docs/Web/API/ServiceWorkerGlobalScope/notificationclose_event) event for persistent notifications.
[ReportShown](#reportshown) | The host may run this to report the notification has been displayed and it will cause the [show](https://developer.mozilla.org/docs/Web/API/Notification/show_event) event to be raised for non-persistent notifications.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### add_CloseRequested

Add an event handler for the `CloseRequested` event.

> public HRESULT [add_CloseRequested](#add_closerequested)(ICoreWebView2ExperimentalNotificationCloseRequestedEventHandler * eventHandler, EventRegistrationToken * token)

This event is raised when the notification is closed by the web code, such as through `notification.close()`. You don't need to call `ReportClosed` since this is coming from the web code.

#### get_BadgeUri

A string containing the URI of the image used to represent the notification when there isn't enough space to display the notification itself.

> public HRESULT [get_BadgeUri](#get_badgeuri)(LPWSTR * value)

The default value is an empty string.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Body

A string representing the body text of the notification.

> public HRESULT [get_Body](#get_body)(LPWSTR * value)

The default value is an empty string.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_BodyImageUri

A string containing the URI of an image to be displayed in the notification.

> public HRESULT [get_BodyImageUri](#get_bodyimageuri)(LPWSTR * value)

The default value is an empty string.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Direction

The text direction in which to display the notification.

> public HRESULT [get_Direction](#get_direction)(COREWEBVIEW2_TEXT_DIRECTION_KIND * value)

This corresponds to [Notification.dir](https://developer.mozilla.org/docs/Web/API/Notification/dir) DOM API. The default value is `COREWEBVIEW2_TEXT_DIRECTION_KIND_DEFAULT`.

#### get_IconUri

A string containing the URI of an icon to be displayed in the notification.

> public HRESULT [get_IconUri](#get_iconuri)(LPWSTR * value)

The default value is an empty string.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_IsSilent

Indicates whether the notification should be silent &ndash; i.e., no sounds or vibrations should be issued, regardless of the device settings.

> public HRESULT [get_IsSilent](#get_issilent)(BOOL * value)

This corresponds to [Notification.silent](https://developer.mozilla.org/docs/Web/API/Notification/silent) DOM API. The default value is `FALSE`.

#### get_Language

The notification's language, as intended to be specified using a string representing a language tag (such as `en-US`) according to [BCP47](https://datatracker.ietf.org/doc/html/rfc5646).

> public HRESULT [get_Language](#get_language)(LPWSTR * value)

Note that no validation is performed on this property and it can be any string the notification sender specifies. This corresponds to [Notification.lang](https://developer.mozilla.org/docs/Web/API/Notification/lang) DOM API. The default value is an empty string.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_RequiresInteraction

A boolean value indicating that a notification should remain active until the user clicks or dismisses it, rather than closing automatically.

> public HRESULT [get_RequiresInteraction](#get_requiresinteraction)(BOOL * value)

This corresponds to [Notification.requireInteraction](https://developer.mozilla.org/docs/Web/API/Notification/requireInteraction) DOM API. Note that you may not be able to necessarily implement this due to native API limitations. The default value is `FALSE`.

#### get_ShouldRenotify

Indicates whether the user should be notified after a new notification replaces an old one.

> public HRESULT [get_ShouldRenotify](#get_shouldrenotify)(BOOL * value)

This corresponds to [Notification.renotify](https://developer.mozilla.org/docs/Web/API/Notification/renotify) DOM API. The default value is `FALSE`.

#### get_Tag

A string representing an identifying tag for the notification.

> public HRESULT [get_Tag](#get_tag)(LPWSTR * value)

This corresponds to [Notification.tag](https://developer.mozilla.org/docs/Web/API/Notification/tag) DOM API. The default value is an empty string.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Timestamp

Indicates the time at which a notification is created or applicable (past, present, or future) as the number of milliseconds since the UNIX epoch.

> public HRESULT [get_Timestamp](#get_timestamp)(double * value)

#### get_Title

The title of the notification.

> public HRESULT [get_Title](#get_title)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetVibrationPattern

Gets the vibration pattern for devices with vibration hardware to emit.

> public HRESULT [GetVibrationPattern](#getvibrationpattern)(UINT32 * count, UINT64 ** vibrationPattern)

The vibration pattern can be represented by an array of 64-bit unsigned integers describing a pattern of vibrations and pauses. See [Vibration API](https://developer.mozilla.org/docs/Web/API/Vibration_API) for more information. This corresponds to [Notification.vibrate](https://developer.mozilla.org/docs/Web/API/Notification/vibrate) DOM API. An empty array is returned if no vibration patterns are specified.

#### remove_CloseRequested

Remove an event handler previously added with `add_CloseRequested`.

> public HRESULT [remove_CloseRequested](#remove_closerequested)(EventRegistrationToken token)

#### ReportClicked

The host may run this to report the notification has been clicked, and it will cause the [click](https://developer.mozilla.org/docs/Web/API/Notification/click_event) event to be raised for non-persistent notifications and the [notificationclick](https://developer.mozilla.org/docs/Web/API/ServiceWorkerGlobalScope/notificationclick_event) event for persistent notifications.

> public HRESULT [ReportClicked](#reportclicked)()

Use `ReportClickedWithActionIndex` to specify an action to activate a persistent notification. You must not run this unless you are handling the `NotificationReceived` event. Returns `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)` if `Handled` is `FALSE` or `ReportShown` has not been run when this is called.

#### ReportClosed

The host may run this to report the notification was dismissed, and it will cause the [close](https://developer.mozilla.org/docs/Web/API/Notification/close_event) event to be raised for non-persistent notifications and the [notificationclose](https://developer.mozilla.org/docs/Web/API/ServiceWorkerGlobalScope/notificationclose_event) event for persistent notifications.

> public HRESULT [ReportClosed](#reportclosed)()

You must not run this unless you are handling the `NotificationReceived` event. Returns `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)` if `Handled` is `FALSE` or `ReportShown` has not been run when this is called.

#### ReportShown

The host may run this to report the notification has been displayed and it will cause the [show](https://developer.mozilla.org/docs/Web/API/Notification/show_event) event to be raised for non-persistent notifications.

> public HRESULT [ReportShown](#reportshown)()

You must not run this unless you are handling the `NotificationReceived` event. Returns `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)` if `Handled` is `FALSE` when this is called.

