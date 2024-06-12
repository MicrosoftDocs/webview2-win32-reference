---
description: Event args for the `NotificationReceived` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalNotificationReceivedEventArgs
ms.date: 06/12/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalNotificationReceivedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalNotificationReceivedEventArgs
- ICoreWebView2ExperimentalNotificationReceivedEventArgs.get_Handled
- ICoreWebView2ExperimentalNotificationReceivedEventArgs.get_Notification
- ICoreWebView2ExperimentalNotificationReceivedEventArgs.get_SenderOrigin
- ICoreWebView2ExperimentalNotificationReceivedEventArgs.GetDeferral
- ICoreWebView2ExperimentalNotificationReceivedEventArgs.put_Handled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalNotificationReceivedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalNotificationReceivedEventArgs
  : public IUnknown
```

Event args for the `NotificationReceived` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Gets whether the `NotificationReceived` event is handled by host.
[get_Notification](#get_notification) | The notification that was received.
[get_SenderOrigin](#get_senderorigin) | The origin of the web content that sends the notification, such as `https://example.com/` or `https://www.example.com/`.
[GetDeferral](#getdeferral) | Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.
[put_Handled](#put_handled) | Sets whether the `NotificationReceived` event is handled by the host after the event handler completes or if there is a deferral then after the deferral is completed.

```cpp
    // Register a handler for the NotificationReceived event.
    CHECK_FAILURE(m_webView2Experimental22->add_NotificationReceived(
        Callback<ICoreWebView2ExperimentalNotificationReceivedEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2ExperimentalNotificationReceivedEventArgs* args) -> HRESULT
            {
                // Block notifications from specific URIs and set Handled to
                // true so the the default notification UI will not be
                // shown by WebView2 either.
                CHECK_FAILURE(args->put_Handled(TRUE));

                Microsoft::WRL::ComPtr<ICoreWebView2Deferral> deferral;
                CHECK_FAILURE(args->GetDeferral(&deferral));
                wil::unique_cotaskmem_string origin;
                CHECK_FAILURE(args->get_SenderOrigin(&origin));
                std::wstring originString = origin.get();
                Microsoft::WRL::ComPtr<ICoreWebView2ExperimentalNotification> notification;
                CHECK_FAILURE(args->get_Notification(&notification));

                notification->add_CloseRequested(
                    Callback<ICoreWebView2ExperimentalNotificationCloseRequestedEventHandler>(
                        [this, &sender](
                            ICoreWebView2ExperimentalNotification* notification,
                            IUnknown* args) -> HRESULT
                        {
                            // Remove the notification from the list of active
                            // notifications.
                            RemoveNotification(notification);
                            return S_OK;
                        })
                        .Get(),
                    &m_notificationCloseRequestedToken);

                m_appWindow->RunAsync(
                    [this,
                     notificationCom = wil::make_com_ptr<ICoreWebView2ExperimentalNotification>(
                         notification.Get()),
                     deferral, originString]()
                    {
                        ShowNotification(notificationCom.get(), originString);
                        deferral->Complete();
                    });

                return S_OK;
            })
            .Get(),
        &m_notificationReceivedToken));
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### get_Handled

Gets whether the `NotificationReceived` event is handled by host.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_Notification

The notification that was received.

> public HRESULT [get_Notification](#get_notification)([ICoreWebView2ExperimentalNotification](icorewebview2experimentalnotification.md#icorewebview2experimentalnotification) ** value)

You can access the properties on the Notification object to show your own notification.

#### get_SenderOrigin

The origin of the web content that sends the notification, such as `https://example.com/` or `https://www.example.com/`.

> public HRESULT [get_SenderOrigin](#get_senderorigin)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetDeferral

Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) ** deferral)

Use this operation to complete the event at a later time.

#### put_Handled

Sets whether the `NotificationReceived` event is handled by the host after the event handler completes or if there is a deferral then after the deferral is completed.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

If `Handled` is set to TRUE then WebView will not display the notification with the default UI, and the host will be responsible for handling the notification and for letting the web content know that the notification has been displayed, clicked, or closed. You must set `Handled` to `TRUE` before you call `ReportShown`, `ReportClicked`, `ReportClickedWithActionIndex` and `ReportClosed`, otherwise they will fail with `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)`. If after the event handler or deferral completes `Handled` is set to FALSE then WebView will display the default notification UI. Note that you cannot un-handle this event once you have set `Handled` to be `TRUE`. The initial value is FALSE.

