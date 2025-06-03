---
description: WebView2 Win32 Globals
title: Globals
ms.date: 04/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
topic_type: 
- APIRef
api_name:
- CompareBrowserVersions
- CreateCoreWebView2Environment
- CreateCoreWebView2EnvironmentWithOptions
- CreateWebViewEnvironmentWithOptionsInternal
- GetAvailableCoreWebView2BrowserVersionString
- GetAvailableCoreWebView2BrowserVersionStringWithOptions
api_type:
- DllExport
api_location:
- WebView2Loader.dll
---

# Globals

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[COREWEBVIEW2_BOUNDS_MODE](#corewebview2_bounds_mode) | Mode for how the Bounds property is interpreted in relation to the RasterizationScale property.
[COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND](#corewebview2_browser_process_exit_kind) | Specifies the browser process exit type used in the [ICoreWebView2BrowserProcessExitedEventArgs](icorewebview2browserprocessexitedeventargs.md#icorewebview2browserprocessexitedeventargs) interface.
[COREWEBVIEW2_BROWSING_DATA_KINDS](#corewebview2_browsing_data_kinds) | Specifies the datatype for the [ICoreWebView2Profile2::ClearBrowsingData](icorewebview2profile2.md#clearbrowsingdata) method.
[COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT](#corewebview2_capture_preview_image_format) | Specifies the image format for the [ICoreWebView2::CapturePreview](icorewebview2.md#capturepreview) method.
[COREWEBVIEW2_CHANNEL_SEARCH_KIND](#corewebview2_channel_search_kind) | The channel search kind determines the order that release channels are searched for during environment creation.
[COREWEBVIEW2_CLIENT_CERTIFICATE_KIND](#corewebview2_client_certificate_kind) | Specifies the client certificate kind.
[COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND](#corewebview2_context_menu_item_kind) | Specifies the menu item kind for the [ICoreWebView2ContextMenuItem::get_Kind](icorewebview2contextmenuitem.md#get_kind) method.
[COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND](#corewebview2_context_menu_target_kind) | Indicates the kind of context for which the context menu was created for the [ICoreWebView2ContextMenuTarget::get_Kind](icorewebview2contextmenutarget.md#get_kind) method.
[COREWEBVIEW2_COOKIE_SAME_SITE_KIND](#corewebview2_cookie_same_site_kind) | Kind of cookie SameSite status used in the [ICoreWebView2Cookie](icorewebview2cookie.md#icorewebview2cookie) interface.
[COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT](#corewebview2_default_download_dialog_corner_alignment) | The default download dialog can be aligned to any of the WebView corners by setting the `DefaultDownloadDialogCornerAlignment` property.
[COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON](#corewebview2_download_interrupt_reason) | Reason why a download was interrupted.
[COREWEBVIEW2_DOWNLOAD_STATE](#corewebview2_download_state) | State of the download operation.
[COREWEBVIEW2_FAVICON_IMAGE_FORMAT](#corewebview2_favicon_image_format) | Specifies the image format to use for favicon.
[COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND](#corewebview2_file_system_handle_kind) | Kind of CoreWebView2FileSystemHandle as described in [FileSystemHandle.kind](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/kind).
[COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION](#corewebview2_file_system_handle_permission) | Allowed permissions of a CoreWebView2FileSystemHandle as described in [FileSystemHandle.requestPermission()](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/requestPermission).
[COREWEBVIEW2_FRAME_KIND](#corewebview2_frame_kind) | Indicates the frame type used in the [ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) interface.
[COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND](#corewebview2_host_resource_access_kind) | Kind of cross origin resource access allowed for host resources during download.
[COREWEBVIEW2_KEY_EVENT_KIND](#corewebview2_key_event_kind) | Specifies the key event type that triggered an `AcceleratorKeyPressed` event.
[COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL](#corewebview2_memory_usage_target_level) | Specifies memory usage target level of WebView.
[COREWEBVIEW2_MOUSE_EVENT_KIND](#corewebview2_mouse_event_kind) | Mouse event type used by SendMouseInput to convey the type of mouse event being sent to WebView.
[COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS](#corewebview2_mouse_event_virtual_keys) | Mouse event virtual keys associated with a COREWEBVIEW2_MOUSE_EVENT_KIND for SendMouseInput.
[COREWEBVIEW2_MOVE_FOCUS_REASON](#corewebview2_move_focus_reason) | Specifies the reason for moving focus.
[COREWEBVIEW2_NAVIGATION_KIND](#corewebview2_navigation_kind) | Specifies the navigation kind of each navigation.
[COREWEBVIEW2_NON_CLIENT_REGION_KIND](#corewebview2_non_client_region_kind) | This enum contains values representing possible regions a given point lies within.
[COREWEBVIEW2_PDF_TOOLBAR_ITEMS](#corewebview2_pdf_toolbar_items) | Specifies the PDF toolbar item types used for the `ICoreWebView2Settings::put_HiddenPdfToolbarItems` method.
[COREWEBVIEW2_PERMISSION_KIND](#corewebview2_permission_kind) | Indicates the type of a permission request.
[COREWEBVIEW2_PERMISSION_STATE](#corewebview2_permission_state) | Specifies the response to a permission request.
[COREWEBVIEW2_POINTER_EVENT_KIND](#corewebview2_pointer_event_kind) | Pointer event type used by SendPointerInput to convey the type of pointer event being sent to WebView.
[COREWEBVIEW2_PREFERRED_COLOR_SCHEME](#corewebview2_preferred_color_scheme) | An enum to represent the options for WebView2 color scheme: auto, light, or dark.
[COREWEBVIEW2_PRINT_COLLATION](#corewebview2_print_collation) | Specifies the collation for a print.
[COREWEBVIEW2_PRINT_COLOR_MODE](#corewebview2_print_color_mode) | Specifies the color mode for a print.
[COREWEBVIEW2_PRINT_DIALOG_KIND](#corewebview2_print_dialog_kind) | Specifies the print dialog kind.
[COREWEBVIEW2_PRINT_DUPLEX](#corewebview2_print_duplex) | Specifies the duplex option for a print.
[COREWEBVIEW2_PRINT_MEDIA_SIZE](#corewebview2_print_media_size) | Specifies the media size for a print.
[COREWEBVIEW2_PRINT_ORIENTATION](#corewebview2_print_orientation) | The orientation for printing, used by the `Orientation` property on [ICoreWebView2PrintSettings](icorewebview2printsettings.md#icorewebview2printsettings).
[COREWEBVIEW2_PRINT_STATUS](#corewebview2_print_status) | Indicates the status for printing.
[COREWEBVIEW2_PROCESS_FAILED_KIND](#corewebview2_process_failed_kind) | Specifies the process failure type used in the [ICoreWebView2ProcessFailedEventArgs](icorewebview2processfailedeventargs.md#icorewebview2processfailedeventargs) interface.
[COREWEBVIEW2_PROCESS_FAILED_REASON](#corewebview2_process_failed_reason) | Specifies the process failure reason used in the [ICoreWebView2ProcessFailedEventArgs](icorewebview2processfailedeventargs.md#icorewebview2processfailedeventargs) interface.
[COREWEBVIEW2_PROCESS_KIND](#corewebview2_process_kind) | Indicates the process type used in the [ICoreWebView2ProcessInfo](icorewebview2processinfo.md#icorewebview2processinfo) interface.
[COREWEBVIEW2_RELEASE_CHANNELS](#corewebview2_release_channels) | The WebView2 release channels.
[COREWEBVIEW2_SAVE_AS_KIND](#corewebview2_save_as_kind) | Specifies Save As kind selection options for [ICoreWebView2SaveAsUIShowingEventArgs](icorewebview2saveasuishowingeventargs.md#icorewebview2saveasuishowingeventargs).
[COREWEBVIEW2_SAVE_AS_UI_RESULT](#corewebview2_save_as_ui_result) | Status of a programmatic Save As call.
[COREWEBVIEW2_SCRIPT_DIALOG_KIND](#corewebview2_script_dialog_kind) | Specifies the JavaScript dialog type used in the [ICoreWebView2ScriptDialogOpeningEventHandler](icorewebview2scriptdialogopeningeventhandler.md#icorewebview2scriptdialogopeningeventhandler) interface.
[COREWEBVIEW2_SCROLLBAR_STYLE](#corewebview2_scrollbar_style) | Set ScrollBar style on [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) during environment creation.
[COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION](#corewebview2_server_certificate_error_action) | Specifies the action type when server certificate error is detected to be used in the [ICoreWebView2ServerCertificateErrorDetectedEventArgs](icorewebview2servercertificateerrordetectedeventargs.md#icorewebview2servercertificateerrordetectedeventargs) interface.
[COREWEBVIEW2_SHARED_BUFFER_ACCESS](#corewebview2_shared_buffer_access) | Specifies the desired access from script to `CoreWebView2SharedBuffer`.
[COREWEBVIEW2_TEXT_DIRECTION_KIND](#corewebview2_text_direction_kind) | Indicates the text direction of the notification.
[COREWEBVIEW2_TRACKING_PREVENTION_LEVEL](#corewebview2_tracking_prevention_level) | Tracking prevention levels.
[COREWEBVIEW2_WEB_ERROR_STATUS](#corewebview2_web_error_status) | Indicates the error status values for web navigations.
[COREWEBVIEW2_WEB_RESOURCE_CONTEXT](#corewebview2_web_resource_context) | Specifies the web resource request contexts.
[COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS](#corewebview2_web_resource_request_source_kinds) | Specifies the source of `WebResourceRequested` event.
[CompareBrowserVersions](#comparebrowserversions) | This method is for anyone want to compare version correctly to determine which version is newer, older or same.
[CreateCoreWebView2Environment](#createcorewebview2environment) | Creates an evergreen WebView2 Environment using the installed WebView2 Runtime version.
[CreateCoreWebView2EnvironmentWithOptions](#createcorewebview2environmentwithoptions) | DLL export to create a WebView2 environment with a custom version of WebView2 Runtime, user data folder, and with or without additional options.
[CreateWebViewEnvironmentWithOptionsInternal](#createwebviewenvironmentwithoptionsinternal) | This is a DLL export out of `EmbeddedBrowserWebView.dll` which can be found in the installation folder of the WebView2 Runtime you wish to use.
[GetAvailableCoreWebView2BrowserVersionString](#getavailablecorewebview2browserversionstring) | Get the browser version info including channel name if it is not the WebView2 Runtime.
[GetAvailableCoreWebView2BrowserVersionStringWithOptions](#getavailablecorewebview2browserversionstringwithoptions) | This function will tell you the browser version info of the release channel used when creating an environment with the same options.

## Members

#### COREWEBVIEW2_BOUNDS_MODE

> enum [COREWEBVIEW2_BOUNDS_MODE](#corewebview2_bounds_mode)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_BOUNDS_MODE_USE_RAW_PIXELS            | Bounds property represents raw pixels. Physical size of Webview is not impacted by RasterizationScale.
COREWEBVIEW2_BOUNDS_MODE_USE_RASTERIZATION_SCALE            | Bounds property represents logical pixels and the RasterizationScale property is used to get the physical size of the WebView.

Mode for how the Bounds property is interpreted in relation to the RasterizationScale property.

#### COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND

> enum [COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND](#corewebview2_browser_process_exit_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_NORMAL            | Indicates that the browser process ended normally.
COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_FAILED            | Indicates that the browser process ended unexpectedly.

Specifies the browser process exit type used in the [ICoreWebView2BrowserProcessExitedEventArgs](icorewebview2browserprocessexitedeventargs.md#icorewebview2browserprocessexitedeventargs) interface.

#### COREWEBVIEW2_BROWSING_DATA_KINDS

> enum [COREWEBVIEW2_BROWSING_DATA_KINDS](#corewebview2_browsing_data_kinds)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_BROWSING_DATA_KINDS_FILE_SYSTEMS            | Specifies file systems data.
COREWEBVIEW2_BROWSING_DATA_KINDS_INDEXED_DB            | Specifies data stored by the IndexedDB DOM feature.
COREWEBVIEW2_BROWSING_DATA_KINDS_LOCAL_STORAGE            | Specifies data stored by the localStorage DOM API.
COREWEBVIEW2_BROWSING_DATA_KINDS_WEB_SQL            | Specifies data stored by the Web SQL database DOM API.
COREWEBVIEW2_BROWSING_DATA_KINDS_CACHE_STORAGE            | Specifies data stored by the CacheStorage DOM API.
COREWEBVIEW2_BROWSING_DATA_KINDS_ALL_DOM_STORAGE            | Specifies DOM storage data, now and future.
COREWEBVIEW2_BROWSING_DATA_KINDS_COOKIES            | Specifies HTTP cookies data.
COREWEBVIEW2_BROWSING_DATA_KINDS_ALL_SITE            | Specifies all site data, now and future.
COREWEBVIEW2_BROWSING_DATA_KINDS_DISK_CACHE            | Specifies disk cache.
COREWEBVIEW2_BROWSING_DATA_KINDS_DOWNLOAD_HISTORY            | Specifies download history data.
COREWEBVIEW2_BROWSING_DATA_KINDS_GENERAL_AUTOFILL            | Specifies general autofill form data.
COREWEBVIEW2_BROWSING_DATA_KINDS_PASSWORD_AUTOSAVE            | Specifies password autosave data.
COREWEBVIEW2_BROWSING_DATA_KINDS_BROWSING_HISTORY            | Specifies browsing history data.
COREWEBVIEW2_BROWSING_DATA_KINDS_SETTINGS            | Specifies settings data.
COREWEBVIEW2_BROWSING_DATA_KINDS_ALL_PROFILE            | Specifies profile data that should be wiped to make it look like a new profile.
COREWEBVIEW2_BROWSING_DATA_KINDS_SERVICE_WORKERS            | Specifies service workers registered for an origin, and clear will result in termination and deregistration of them.

Specifies the datatype for the [ICoreWebView2Profile2::ClearBrowsingData](icorewebview2profile2.md#clearbrowsingdata) method.

#### COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT

> enum [COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT](#corewebview2_capture_preview_image_format)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT_PNG            | Indicates that the PNG image format is used.
COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT_JPEG            | Indicates the JPEG image format is used.

Specifies the image format for the [ICoreWebView2::CapturePreview](icorewebview2.md#capturepreview) method.

#### COREWEBVIEW2_CHANNEL_SEARCH_KIND

> enum [COREWEBVIEW2_CHANNEL_SEARCH_KIND](#corewebview2_channel_search_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CHANNEL_SEARCH_KIND_MOST_STABLE            | Search for a release channel from most to least stable: WebView2 Runtime -> Beta -> Dev -> Canary.
COREWEBVIEW2_CHANNEL_SEARCH_KIND_LEAST_STABLE            | Search for a release channel from least to most stable: Canary -> Dev -> Beta -> WebView2 Runtime.

The channel search kind determines the order that release channels are searched for during environment creation.

The default behavior is to search for and use the most stable channel found on the device. The order from most to least stable is: WebView2 Runtime -> Beta -> Dev -> Canary. Switch the order to prefer the least stable channel in order to perform pre-release testing. See `COREWEBVIEW2_RELEASE_CHANNELS` for descriptions of channels.

#### COREWEBVIEW2_CLIENT_CERTIFICATE_KIND

> enum [COREWEBVIEW2_CLIENT_CERTIFICATE_KIND](#corewebview2_client_certificate_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CLIENT_CERTIFICATE_KIND_SMART_CARD            | Specifies smart card certificate.
COREWEBVIEW2_CLIENT_CERTIFICATE_KIND_PIN            | Specifies PIN certificate.
COREWEBVIEW2_CLIENT_CERTIFICATE_KIND_OTHER            | Specifies other certificate.

Specifies the client certificate kind.

#### COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND

> enum [COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND](#corewebview2_context_menu_item_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_COMMAND            | Specifies a command menu item kind.
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_CHECK_BOX            | Specifies a check box menu item kind.
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_RADIO            | Specifies a radio button menu item kind.
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SEPARATOR            | Specifies a separator menu item kind.
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SUBMENU            | Specifies a submenu menu item kind.

Specifies the menu item kind for the [ICoreWebView2ContextMenuItem::get_Kind](icorewebview2contextmenuitem.md#get_kind) method.

#### COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND

> enum [COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND](#corewebview2_context_menu_target_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_PAGE            | Indicates that the context menu was created for the page without any additional content.
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_IMAGE            | Indicates that the context menu was created for an image element.
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_SELECTED_TEXT            | Indicates that the context menu was created for selected text.
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_AUDIO            | Indicates that the context menu was created for an audio element.
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_VIDEO            | Indicates that the context menu was created for a video element.

Indicates the kind of context for which the context menu was created for the [ICoreWebView2ContextMenuTarget::get_Kind](icorewebview2contextmenutarget.md#get_kind) method.

This enum will always represent the active element that caused the context menu request. If there is a selection with multiple images, audio and text, for example, the element that the end user right clicks on within this selection will be the option represented by this enum.

#### COREWEBVIEW2_COOKIE_SAME_SITE_KIND

> enum [COREWEBVIEW2_COOKIE_SAME_SITE_KIND](#corewebview2_cookie_same_site_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_COOKIE_SAME_SITE_KIND_NONE            | None SameSite type. No restrictions on cross-site requests.
COREWEBVIEW2_COOKIE_SAME_SITE_KIND_LAX            | Lax SameSite type. The cookie will be sent with "same-site" requests, and with "cross-site" top level navigation.
COREWEBVIEW2_COOKIE_SAME_SITE_KIND_STRICT            | Strict SameSite type. The cookie will only be sent along with "same-site" requests.

Kind of cookie SameSite status used in the [ICoreWebView2Cookie](icorewebview2cookie.md#icorewebview2cookie) interface.

These fields match those as specified in https://developer.mozilla.org/docs/Web/HTTP/Cookies#. Learn more about SameSite cookies here: https://tools.ietf.org/html/draft-west-first-party-cookies-07

#### COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT

> enum [COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT](#corewebview2_default_download_dialog_corner_alignment)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT_TOP_LEFT            | Top-left corner of the WebView.
COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT_TOP_RIGHT            | Top-right corner of the WebView.
COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT_BOTTOM_LEFT            | Bottom-left corner of the WebView.
COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT_BOTTOM_RIGHT            | Bottom-right corner of the WebView.

The default download dialog can be aligned to any of the WebView corners by setting the `DefaultDownloadDialogCornerAlignment` property.

The default position is top-right corner.

#### COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON

> enum [COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON](#corewebview2_download_interrupt_reason)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NONE            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_FAILED            | Generic file error.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_ACCESS_DENIED            | Access denied due to security restrictions.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_NO_SPACE            | Disk full.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_NAME_TOO_LONG            | Result file path with file name is too long.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_TOO_LARGE            | File is too large for file system.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_MALICIOUS            | Microsoft Defender Smartscreen detected a virus in the file.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_TRANSIENT_ERROR            | File was in use, too many files opened, or out of memory.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_BLOCKED_BY_POLICY            | File blocked by local policy.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_SECURITY_CHECK_FAILED            | Security check failed unexpectedly.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_TOO_SHORT            | Seeking past the end of a file in opening a file, as part of resuming an interrupted download.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_HASH_MISMATCH            | Partial file did not match the expected hash and was deleted.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_FAILED            | Generic network error. User can retry the download manually.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_TIMEOUT            | Network operation timed out.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_DISCONNECTED            | Network connection lost. User can retry the download manually.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_SERVER_DOWN            | Server has gone down. User can retry the download manually.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_INVALID_REQUEST            | Network request invalid because original or redirected URI is invalid, has an unsupported scheme, or is disallowed by network policy.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_FAILED            | Generic server error. User can retry the download manually.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_NO_RANGE            | Server does not support range requests.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_BAD_CONTENT            | Server does not have the requested data.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_UNAUTHORIZED            | Server did not authorize access to resource.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_CERTIFICATE_PROBLEM            | Server certificate problem.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_FORBIDDEN            | Server access forbidden.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_UNEXPECTED_RESPONSE            | Unexpected server response.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_CONTENT_LENGTH_MISMATCH            | Server sent fewer bytes than the Content-Length header.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_CROSS_ORIGIN_REDIRECT            | Unexpected cross-origin redirect.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_USER_CANCELED            | User canceled the download.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_USER_SHUTDOWN            | User shut down the WebView.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_USER_PAUSED            | User paused the download.
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_DOWNLOAD_PROCESS_CRASHED            | WebView crashed.

Reason why a download was interrupted.

#### COREWEBVIEW2_DOWNLOAD_STATE

> enum [COREWEBVIEW2_DOWNLOAD_STATE](#corewebview2_download_state)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_DOWNLOAD_STATE_IN_PROGRESS            | The download is in progress.
COREWEBVIEW2_DOWNLOAD_STATE_INTERRUPTED            | The connection with the file host was broken.
COREWEBVIEW2_DOWNLOAD_STATE_COMPLETED            | The download completed successfully.

State of the download operation.

#### COREWEBVIEW2_FAVICON_IMAGE_FORMAT

> enum [COREWEBVIEW2_FAVICON_IMAGE_FORMAT](#corewebview2_favicon_image_format)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_FAVICON_IMAGE_FORMAT_PNG            | Indicates that the PNG image format is used.
COREWEBVIEW2_FAVICON_IMAGE_FORMAT_JPEG            | Indicates the JPEG image format is used.

Specifies the image format to use for favicon.

#### COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND

> enum [COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND](#corewebview2_file_system_handle_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND_FILE            | FileSystemHandle is for a file [FileSystemFileHandle](https://developer.mozilla.org/docs/Web/API/FileSystemFileHandle).
COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND_DIRECTORY            | FileSystemHandle is for a directory [FileSystemDirectoryHandle](https://developer.mozilla.org/docs/Web/API/FileSystemDirectoryHandle).

Kind of CoreWebView2FileSystemHandle as described in [FileSystemHandle.kind](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/kind).

#### COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION

> enum [COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION](#corewebview2_file_system_handle_permission)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION_READ_ONLY            | Read-only permission for FileSystemHandle.
COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION_READ_WRITE            | Read and write permissions for FileSystemHandle.

Allowed permissions of a CoreWebView2FileSystemHandle as described in [FileSystemHandle.requestPermission()](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/requestPermission).

#### COREWEBVIEW2_FRAME_KIND

> enum [COREWEBVIEW2_FRAME_KIND](#corewebview2_frame_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_FRAME_KIND_UNKNOWN            | Indicates that the frame is an unknown type frame.
COREWEBVIEW2_FRAME_KIND_MAIN_FRAME            | Indicates that the frame is a primary main frame(webview).
COREWEBVIEW2_FRAME_KIND_IFRAME            | Indicates that the frame is an iframe.
COREWEBVIEW2_FRAME_KIND_EMBED            | Indicates that the frame is an embed element.
COREWEBVIEW2_FRAME_KIND_OBJECT            | Indicates that the frame is an object element.

Indicates the frame type used in the [ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) interface.

#### COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND

> enum [COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND](#corewebview2_host_resource_access_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY            | All cross origin resource access is denied, including normal sub resource access as src of a script or image element.
COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_ALLOW            | All cross origin resource access is allowed, including accesses that are subject to Cross-Origin Resource Sharing(CORS) check.
COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY_CORS            | Cross origin resource access is allowed for normal sub resource access like as src of a script or image element, while any access that subjects to CORS check will be denied.

Kind of cross origin resource access allowed for host resources during download.

Note that other normal access checks like same origin DOM access check and [Content Security Policy](https://developer.mozilla.org/docs/Web/HTTP/CSP) still apply.

The following table illustrates the host resource cross origin access according to access context and `COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND`.

Cross Origin Access Context   |DENY   |ALLOW   |DENY_CORS
--------- | --------- | --------- | ---------
From DOM like src of img, script or iframe element   |Deny   |Allow   |Allow
From Script like Fetch or XMLHttpRequest   |Deny   |Allow   |Deny

#### COREWEBVIEW2_KEY_EVENT_KIND

> enum [COREWEBVIEW2_KEY_EVENT_KIND](#corewebview2_key_event_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_KEY_EVENT_KIND_KEY_DOWN            | Specifies that the key event type corresponds to window message `WM_KEYDOWN`.
COREWEBVIEW2_KEY_EVENT_KIND_KEY_UP            | Specifies that the key event type corresponds to window message `WM_KEYUP`.
COREWEBVIEW2_KEY_EVENT_KIND_SYSTEM_KEY_DOWN            | Specifies that the key event type corresponds to window message `WM_SYSKEYDOWN`.
COREWEBVIEW2_KEY_EVENT_KIND_SYSTEM_KEY_UP            | Specifies that the key event type corresponds to window message `WM_SYSKEYUP`.

Specifies the key event type that triggered an `AcceleratorKeyPressed` event.

#### COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL

> enum [COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL](#corewebview2_memory_usage_target_level)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_NORMAL            | Specifies normal memory usage target level.
COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_LOW            | Specifies low memory usage target level.

Specifies memory usage target level of WebView.

#### COREWEBVIEW2_MOUSE_EVENT_KIND

> enum [COREWEBVIEW2_MOUSE_EVENT_KIND](#corewebview2_mouse_event_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MOUSE_EVENT_KIND_HORIZONTAL_WHEEL            | Mouse horizontal wheel scroll event, WM_MOUSEHWHEEL.
COREWEBVIEW2_MOUSE_EVENT_KIND_LEFT_BUTTON_DOUBLE_CLICK            | Left button double click mouse event, WM_LBUTTONDBLCLK.
COREWEBVIEW2_MOUSE_EVENT_KIND_LEFT_BUTTON_DOWN            | Left button down mouse event, WM_LBUTTONDOWN.
COREWEBVIEW2_MOUSE_EVENT_KIND_LEFT_BUTTON_UP            | Left button up mouse event, WM_LBUTTONUP.
COREWEBVIEW2_MOUSE_EVENT_KIND_LEAVE            | Mouse leave event, WM_MOUSELEAVE.
COREWEBVIEW2_MOUSE_EVENT_KIND_MIDDLE_BUTTON_DOUBLE_CLICK            | Middle button double click mouse event, WM_MBUTTONDBLCLK.
COREWEBVIEW2_MOUSE_EVENT_KIND_MIDDLE_BUTTON_DOWN            | Middle button down mouse event, WM_MBUTTONDOWN.
COREWEBVIEW2_MOUSE_EVENT_KIND_MIDDLE_BUTTON_UP            | Middle button up mouse event, WM_MBUTTONUP.
COREWEBVIEW2_MOUSE_EVENT_KIND_MOVE            | Mouse move event, WM_MOUSEMOVE.
COREWEBVIEW2_MOUSE_EVENT_KIND_RIGHT_BUTTON_DOUBLE_CLICK            | Right button double click mouse event, WM_RBUTTONDBLCLK.
COREWEBVIEW2_MOUSE_EVENT_KIND_RIGHT_BUTTON_DOWN            | Right button down mouse event, WM_RBUTTONDOWN.
COREWEBVIEW2_MOUSE_EVENT_KIND_RIGHT_BUTTON_UP            | Right button up mouse event, WM_RBUTTONUP.
COREWEBVIEW2_MOUSE_EVENT_KIND_WHEEL            | Mouse wheel scroll event, WM_MOUSEWHEEL.
COREWEBVIEW2_MOUSE_EVENT_KIND_X_BUTTON_DOUBLE_CLICK            | First or second X button double click mouse event, WM_XBUTTONDBLCLK.
COREWEBVIEW2_MOUSE_EVENT_KIND_X_BUTTON_DOWN            | First or second X button down mouse event, WM_XBUTTONDOWN.
COREWEBVIEW2_MOUSE_EVENT_KIND_X_BUTTON_UP            | First or second X button up mouse event, WM_XBUTTONUP.
COREWEBVIEW2_MOUSE_EVENT_KIND_NON_CLIENT_RIGHT_BUTTON_DOWN            | Mouse Right Button Down event over a nonclient area, WM_NCRBUTTONDOWN.
COREWEBVIEW2_MOUSE_EVENT_KIND_NON_CLIENT_RIGHT_BUTTON_UP            | Mouse Right Button up event over a nonclient area, WM_NCRBUTTONUP.

Mouse event type used by SendMouseInput to convey the type of mouse event being sent to WebView.

The values of this enum align with the matching WM_* window messages.

#### COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS

> enum [COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS](#corewebview2_mouse_event_virtual_keys)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_NONE            | No additional keys pressed.
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_LEFT_BUTTON            | Left mouse button is down, MK_LBUTTON.
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_RIGHT_BUTTON            | Right mouse button is down, MK_RBUTTON.
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_SHIFT            | SHIFT key is down, MK_SHIFT.
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_CONTROL            | CTRL key is down, MK_CONTROL.
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_MIDDLE_BUTTON            | Middle mouse button is down, MK_MBUTTON.
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_X_BUTTON1            | First X button is down, MK_XBUTTON1.
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_X_BUTTON2            | Second X button is down, MK_XBUTTON2.

Mouse event virtual keys associated with a COREWEBVIEW2_MOUSE_EVENT_KIND for SendMouseInput.

These values can be combined into a bit flag if more than one virtual key is pressed for the event. The values of this enum align with the matching MK_* mouse keys.

#### COREWEBVIEW2_MOVE_FOCUS_REASON

> enum [COREWEBVIEW2_MOVE_FOCUS_REASON](#corewebview2_move_focus_reason)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MOVE_FOCUS_REASON_PROGRAMMATIC            | Specifies that the code is setting focus into WebView.
COREWEBVIEW2_MOVE_FOCUS_REASON_NEXT            | Specifies that the focus is moving due to Tab traversal forward.
COREWEBVIEW2_MOVE_FOCUS_REASON_PREVIOUS            | Specifies that the focus is moving due to Tab traversal backward.

Specifies the reason for moving focus.

#### COREWEBVIEW2_NAVIGATION_KIND

> enum [COREWEBVIEW2_NAVIGATION_KIND](#corewebview2_navigation_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_NAVIGATION_KIND_RELOAD            | A navigation caused by `CoreWebView2.Reload()`, `location.reload()`, the end user using F5 or other UX, or other reload mechanisms to reload the current document without modifying the navigation history.
COREWEBVIEW2_NAVIGATION_KIND_BACK_OR_FORWARD            | A navigation back or forward to a different entry in the session navigation history, like via `CoreWebView2.Back()`, `location.back()`, the end user pressing Alt+Left or other UX, or other mechanisms to navigate back or forward in the current session navigation history.
COREWEBVIEW2_NAVIGATION_KIND_NEW_DOCUMENT            | A navigation to another document, which can be caused by `CoreWebView2.Navigate()`, `window.location.href = ...`, or other WebView2 or DOM APIs that navigate to a new URI.

Specifies the navigation kind of each navigation.

#### COREWEBVIEW2_NON_CLIENT_REGION_KIND

> enum [COREWEBVIEW2_NON_CLIENT_REGION_KIND](#corewebview2_non_client_region_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_NON_CLIENT_REGION_KIND_NOWHERE            | A hit test region out of bounds of the WebView2.
COREWEBVIEW2_NON_CLIENT_REGION_KIND_CLIENT            | A hit test region in the WebView2 which does not have the CSS style `-webkit-app-region: drag` set.
COREWEBVIEW2_NON_CLIENT_REGION_KIND_CAPTION            | A hit test region in the WebView2 which has the CSS style `-webkit-app-region: drag` set.
COREWEBVIEW2_NON_CLIENT_REGION_KIND_MINIMIZE            | A hit test region in the Webview2 which corresponds to the minimize window control button.
COREWEBVIEW2_NON_CLIENT_REGION_KIND_MAXIMIZE            | A hit test region in the Webview2 which corresponds to the maximize window control button.
COREWEBVIEW2_NON_CLIENT_REGION_KIND_CLOSE            | A hit test region in the Webview2 which corresponds to the close window control button.

This enum contains values representing possible regions a given point lies within.

The values of this enum align with the matching WM_NCHITTEST* window message return values.

#### COREWEBVIEW2_PDF_TOOLBAR_ITEMS

> enum [COREWEBVIEW2_PDF_TOOLBAR_ITEMS](#corewebview2_pdf_toolbar_items)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_NONE            | No item.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SAVE            | The save button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PRINT            | The print button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SAVE_AS            | The save as button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_ZOOM_IN            | The zoom in button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_ZOOM_OUT            | The zoom out button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_ROTATE            | The rotate button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_FIT_PAGE            | The fit page button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PAGE_LAYOUT            | The page layout button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_BOOKMARKS            | The bookmarks button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PAGE_SELECTOR            | The page select button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SEARCH            | The search button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_FULL_SCREEN            | The full screen button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_MORE_SETTINGS            | The more settings button.

Specifies the PDF toolbar item types used for the `ICoreWebView2Settings::put_HiddenPdfToolbarItems` method.

#### COREWEBVIEW2_PERMISSION_KIND

> enum [COREWEBVIEW2_PERMISSION_KIND](#corewebview2_permission_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PERMISSION_KIND_UNKNOWN_PERMISSION            | Indicates an unknown permission.
COREWEBVIEW2_PERMISSION_KIND_MICROPHONE            | Indicates permission to capture audio.
COREWEBVIEW2_PERMISSION_KIND_CAMERA            | Indicates permission to capture video.
COREWEBVIEW2_PERMISSION_KIND_GEOLOCATION            | Indicates permission to access geolocation.
COREWEBVIEW2_PERMISSION_KIND_NOTIFICATIONS            | Indicates permission to send web notifications.
COREWEBVIEW2_PERMISSION_KIND_OTHER_SENSORS            | Indicates permission to access generic sensor.
COREWEBVIEW2_PERMISSION_KIND_CLIPBOARD_READ            | Indicates permission to read the system clipboard without a user gesture.
COREWEBVIEW2_PERMISSION_KIND_MULTIPLE_AUTOMATIC_DOWNLOADS            | Indicates permission to automatically download multiple files.
COREWEBVIEW2_PERMISSION_KIND_FILE_READ_WRITE            | Indicates permission to read and write to files or folders on the device.
COREWEBVIEW2_PERMISSION_KIND_AUTOPLAY            | Indicates permission to play audio and video automatically on sites.
COREWEBVIEW2_PERMISSION_KIND_LOCAL_FONTS            | Indicates permission to use fonts on the device.
COREWEBVIEW2_PERMISSION_KIND_MIDI_SYSTEM_EXCLUSIVE_MESSAGES            | Indicates permission to send and receive system exclusive messages to/from MIDI (Musical Instrument Digital Interface) devices.
COREWEBVIEW2_PERMISSION_KIND_WINDOW_MANAGEMENT            | Indicates permission to open and place windows on the screen.

Indicates the type of a permission request.

#### COREWEBVIEW2_PERMISSION_STATE

> enum [COREWEBVIEW2_PERMISSION_STATE](#corewebview2_permission_state)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PERMISSION_STATE_DEFAULT            | Specifies that the default browser behavior is used, which normally prompt users for decision.
COREWEBVIEW2_PERMISSION_STATE_ALLOW            | Specifies that the permission request is granted.
COREWEBVIEW2_PERMISSION_STATE_DENY            | Specifies that the permission request is denied.

Specifies the response to a permission request.

#### COREWEBVIEW2_POINTER_EVENT_KIND

> enum [COREWEBVIEW2_POINTER_EVENT_KIND](#corewebview2_pointer_event_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_POINTER_EVENT_KIND_ACTIVATE            | Corresponds to WM_POINTERACTIVATE.
COREWEBVIEW2_POINTER_EVENT_KIND_DOWN            | Corresponds to WM_POINTERDOWN.
COREWEBVIEW2_POINTER_EVENT_KIND_ENTER            | Corresponds to WM_POINTERENTER.
COREWEBVIEW2_POINTER_EVENT_KIND_LEAVE            | Corresponds to WM_POINTERLEAVE.
COREWEBVIEW2_POINTER_EVENT_KIND_UP            | Corresponds to WM_POINTERUP.
COREWEBVIEW2_POINTER_EVENT_KIND_UPDATE            | Corresponds to WM_POINTERUPDATE.

Pointer event type used by SendPointerInput to convey the type of pointer event being sent to WebView.

The values of this enum align with the matching WM_POINTER* window messages.

#### COREWEBVIEW2_PREFERRED_COLOR_SCHEME

> enum [COREWEBVIEW2_PREFERRED_COLOR_SCHEME](#corewebview2_preferred_color_scheme)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PREFERRED_COLOR_SCHEME_AUTO            | Auto color scheme.
COREWEBVIEW2_PREFERRED_COLOR_SCHEME_LIGHT            | Light color scheme.
COREWEBVIEW2_PREFERRED_COLOR_SCHEME_DARK            | Dark color scheme.

An enum to represent the options for WebView2 color scheme: auto, light, or dark.

#### COREWEBVIEW2_PRINT_COLLATION

> enum [COREWEBVIEW2_PRINT_COLLATION](#corewebview2_print_collation)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_COLLATION_DEFAULT            | The default collation for a printer.
COREWEBVIEW2_PRINT_COLLATION_COLLATED            | Indicate that the collation has been selected for the printed output.
COREWEBVIEW2_PRINT_COLLATION_UNCOLLATED            | Indicate that the collation has not been selected for the printed output.

Specifies the collation for a print.

#### COREWEBVIEW2_PRINT_COLOR_MODE

> enum [COREWEBVIEW2_PRINT_COLOR_MODE](#corewebview2_print_color_mode)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_COLOR_MODE_DEFAULT            | The default color mode for a printer.
COREWEBVIEW2_PRINT_COLOR_MODE_COLOR            | Indicate that the printed output will be in color.
COREWEBVIEW2_PRINT_COLOR_MODE_GRAYSCALE            | Indicate that the printed output will be in shades of gray.

Specifies the color mode for a print.

#### COREWEBVIEW2_PRINT_DIALOG_KIND

> enum [COREWEBVIEW2_PRINT_DIALOG_KIND](#corewebview2_print_dialog_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_DIALOG_KIND_BROWSER            | Opens the browser print preview dialog.
COREWEBVIEW2_PRINT_DIALOG_KIND_SYSTEM            | Opens the system print dialog.

Specifies the print dialog kind.

#### COREWEBVIEW2_PRINT_DUPLEX

> enum [COREWEBVIEW2_PRINT_DUPLEX](#corewebview2_print_duplex)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_DUPLEX_DEFAULT            | The default duplex for a printer.
COREWEBVIEW2_PRINT_DUPLEX_ONE_SIDED            | Print on only one side of the sheet.
COREWEBVIEW2_PRINT_DUPLEX_TWO_SIDED_LONG_EDGE            | Print on both sides of the sheet, flipped along the long edge.
COREWEBVIEW2_PRINT_DUPLEX_TWO_SIDED_SHORT_EDGE            | Print on both sides of the sheet, flipped along the short edge.

Specifies the duplex option for a print.

#### COREWEBVIEW2_PRINT_MEDIA_SIZE

> enum [COREWEBVIEW2_PRINT_MEDIA_SIZE](#corewebview2_print_media_size)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_MEDIA_SIZE_DEFAULT            | The default media size for a printer.
COREWEBVIEW2_PRINT_MEDIA_SIZE_CUSTOM            | Indicate custom media size that is specific to the printer.

Specifies the media size for a print.

#### COREWEBVIEW2_PRINT_ORIENTATION

> enum [COREWEBVIEW2_PRINT_ORIENTATION](#corewebview2_print_orientation)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_ORIENTATION_PORTRAIT            | Print the page(s) in portrait orientation.
COREWEBVIEW2_PRINT_ORIENTATION_LANDSCAPE            | Print the page(s) in landscape orientation.

The orientation for printing, used by the `Orientation` property on [ICoreWebView2PrintSettings](icorewebview2printsettings.md#icorewebview2printsettings).

#### COREWEBVIEW2_PRINT_STATUS

> enum [COREWEBVIEW2_PRINT_STATUS](#corewebview2_print_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_STATUS_SUCCEEDED            | Indicates that the print operation is succeeded.
COREWEBVIEW2_PRINT_STATUS_PRINTER_UNAVAILABLE            | Indicates that the printer is not available.
COREWEBVIEW2_PRINT_STATUS_OTHER_ERROR            | Indicates that the print operation is failed.

Indicates the status for printing.

#### COREWEBVIEW2_PROCESS_FAILED_KIND

> enum [COREWEBVIEW2_PROCESS_FAILED_KIND](#corewebview2_process_failed_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PROCESS_FAILED_KIND_BROWSER_PROCESS_EXITED            | Indicates that the browser process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_EXITED            | Indicates that the main frame's render process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_UNRESPONSIVE            | Indicates that the main frame's render process is unresponsive.
COREWEBVIEW2_PROCESS_FAILED_KIND_FRAME_RENDER_PROCESS_EXITED            | Indicates that a frame-only render process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_UTILITY_PROCESS_EXITED            | Indicates that a utility process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_SANDBOX_HELPER_PROCESS_EXITED            | Indicates that a sandbox helper process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_GPU_PROCESS_EXITED            | Indicates that the GPU process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_PPAPI_PLUGIN_PROCESS_EXITED            | Indicates that a PPAPI plugin process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_PPAPI_BROKER_PROCESS_EXITED            | Indicates that a PPAPI plugin broker process ended unexpectedly.
COREWEBVIEW2_PROCESS_FAILED_KIND_UNKNOWN_PROCESS_EXITED            | Indicates that a process of unspecified kind ended unexpectedly.

Specifies the process failure type used in the [ICoreWebView2ProcessFailedEventArgs](icorewebview2processfailedeventargs.md#icorewebview2processfailedeventargs) interface.

The values in this enum make reference to the process kinds in the Chromium architecture. For more information about what these processes are and what they do, see [Browser Architecture - Inside look at modern web browser](https://developers.google.com/web/updates/2018/09/inside-browser-part1).

#### COREWEBVIEW2_PROCESS_FAILED_REASON

> enum [COREWEBVIEW2_PROCESS_FAILED_REASON](#corewebview2_process_failed_reason)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PROCESS_FAILED_REASON_UNEXPECTED            | An unexpected process failure occurred.
COREWEBVIEW2_PROCESS_FAILED_REASON_UNRESPONSIVE            | The process became unresponsive.
COREWEBVIEW2_PROCESS_FAILED_REASON_TERMINATED            | The process was terminated. For example, from Task Manager.
COREWEBVIEW2_PROCESS_FAILED_REASON_CRASHED            | The process crashed.
COREWEBVIEW2_PROCESS_FAILED_REASON_LAUNCH_FAILED            | The process failed to launch.
COREWEBVIEW2_PROCESS_FAILED_REASON_OUT_OF_MEMORY            | The process terminated due to running out of memory.
COREWEBVIEW2_PROCESS_FAILED_REASON_PROFILE_DELETED            | Deprecated. This value is unused.

Specifies the process failure reason used in the [ICoreWebView2ProcessFailedEventArgs](icorewebview2processfailedeventargs.md#icorewebview2processfailedeventargs) interface.

For process failures where a process has exited, it indicates the type of issue that produced the process exit.

#### COREWEBVIEW2_PROCESS_KIND

> enum [COREWEBVIEW2_PROCESS_KIND](#corewebview2_process_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PROCESS_KIND_BROWSER            | Indicates the browser process kind.
COREWEBVIEW2_PROCESS_KIND_RENDERER            | Indicates the render process kind.
COREWEBVIEW2_PROCESS_KIND_UTILITY            | Indicates the utility process kind.
COREWEBVIEW2_PROCESS_KIND_SANDBOX_HELPER            | Indicates the sandbox helper process kind.
COREWEBVIEW2_PROCESS_KIND_GPU            | Indicates the GPU process kind.
COREWEBVIEW2_PROCESS_KIND_PPAPI_PLUGIN            | Indicates the PPAPI plugin process kind.
COREWEBVIEW2_PROCESS_KIND_PPAPI_BROKER            | Indicates the PPAPI plugin broker process kind.

Indicates the process type used in the [ICoreWebView2ProcessInfo](icorewebview2processinfo.md#icorewebview2processinfo) interface.

#### COREWEBVIEW2_RELEASE_CHANNELS

> enum [COREWEBVIEW2_RELEASE_CHANNELS](#corewebview2_release_channels)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_RELEASE_CHANNELS_NONE            | No release channel.
COREWEBVIEW2_RELEASE_CHANNELS_STABLE            | The stable WebView2 Runtime that is released every 4 weeks.
COREWEBVIEW2_RELEASE_CHANNELS_BETA            | The Beta release channel that is released every 4 weeks, a week before the stable release.
COREWEBVIEW2_RELEASE_CHANNELS_DEV            | The Dev release channel that is released weekly.
COREWEBVIEW2_RELEASE_CHANNELS_CANARY            | The Canary release channel that is released daily.

The WebView2 release channels.

Use `ReleaseChannels` and `ChannelSearchKind` on [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) to control which channel is searched for during environment creation.

Channel   |Primary purpose   |How often updated with new features
--------- | --------- | ---------
Stable (WebView2 Runtime)   |Broad Deployment   |Monthly
Beta   |Flighting with inner rings, automated testing   |Monthly
Dev   |Automated testing, selfhosting to test new APIs and features   |Weekly
Canary   |Automated testing, selfhosting to test new APIs and features   |Daily

#### COREWEBVIEW2_SAVE_AS_KIND

> enum [COREWEBVIEW2_SAVE_AS_KIND](#corewebview2_save_as_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SAVE_AS_KIND_DEFAULT            | Default kind to save non-HTML content.
COREWEBVIEW2_SAVE_AS_KIND_HTML_ONLY            | Save the page as HTML.
COREWEBVIEW2_SAVE_AS_KIND_SINGLE_FILE            | Save the page as [MHTML](https://en.wikipedia.org/wiki/MHTML).
COREWEBVIEW2_SAVE_AS_KIND_COMPLETE            | Save the page as HTML and download the page-related source files (for example: CSS, JavaScript, images, etc.) in a directory with the same filename prefix.

Specifies Save As kind selection options for [ICoreWebView2SaveAsUIShowingEventArgs](icorewebview2saveasuishowingeventargs.md#icorewebview2saveasuishowingeventargs).

For HTML documents, we support 3 Save As kinds: HTML_ONLY, SINGLE_FILE and COMPLETE. For non-HTML documents, you must use DEFAULT. MIME types of `text/html` and `application/xhtml+xml` are considered HTML documents.

#### COREWEBVIEW2_SAVE_AS_UI_RESULT

> enum [COREWEBVIEW2_SAVE_AS_UI_RESULT](#corewebview2_save_as_ui_result)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SAVE_AS_UI_RESULT_SUCCESS            | The ShowSaveAsUI method call completed successfully.
COREWEBVIEW2_SAVE_AS_UI_RESULT_INVALID_PATH            | Could not perform Save As because the destination file path is an invalid path.
COREWEBVIEW2_SAVE_AS_UI_RESULT_FILE_ALREADY_EXISTS            | Could not perform Save As because the destination file path already exists and replacing files was not allowed by the `AllowReplace` property.
COREWEBVIEW2_SAVE_AS_UI_RESULT_KIND_NOT_SUPPORTED            | Could not perform Save As because the `Kind` property selection is not supported due to content MIME type or system limits.
COREWEBVIEW2_SAVE_AS_UI_RESULT_CANCELLED            | Did not perform Save As because the end user cancelled or the `Cancel` property on [ICoreWebView2SaveAsUIShowingEventArgs](icorewebview2saveasuishowingeventargs.md#icorewebview2saveasuishowingeventargs) was set to TRUE.

Status of a programmatic Save As call.

Indicates the result of the `ShowSaveAsUI` method.

#### COREWEBVIEW2_SCRIPT_DIALOG_KIND

> enum [COREWEBVIEW2_SCRIPT_DIALOG_KIND](#corewebview2_script_dialog_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SCRIPT_DIALOG_KIND_ALERT            | Indicates that the dialog uses the `window.alert` JavaScript function.
COREWEBVIEW2_SCRIPT_DIALOG_KIND_CONFIRM            | Indicates that the dialog uses the `window.confirm` JavaScript function.
COREWEBVIEW2_SCRIPT_DIALOG_KIND_PROMPT            | Indicates that the dialog uses the `window.prompt` JavaScript function.
COREWEBVIEW2_SCRIPT_DIALOG_KIND_BEFOREUNLOAD            | Indicates that the dialog uses the `beforeunload` JavaScript event.

Specifies the JavaScript dialog type used in the [ICoreWebView2ScriptDialogOpeningEventHandler](icorewebview2scriptdialogopeningeventhandler.md#icorewebview2scriptdialogopeningeventhandler) interface.

#### COREWEBVIEW2_SCROLLBAR_STYLE

> enum [COREWEBVIEW2_SCROLLBAR_STYLE](#corewebview2_scrollbar_style)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SCROLLBAR_STYLE_DEFAULT            | Browser default ScrollBar style.
COREWEBVIEW2_SCROLLBAR_STYLE_FLUENT_OVERLAY            | Window style fluent overlay scroll bar Please see [Fluent UI](https://developer.microsoft.com/fluentui#/) for more details on fluent UI.

Set ScrollBar style on [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) during environment creation.

#### COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION

> enum [COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION](#corewebview2_server_certificate_error_action)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_ALWAYS_ALLOW            | Indicates to ignore the warning and continue the request with the TLS certificate.
COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_CANCEL            | Indicates to reject the certificate and cancel the request.
COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_DEFAULT            | Indicates to display the default TLS interstitial error page to user for page navigations.

Specifies the action type when server certificate error is detected to be used in the [ICoreWebView2ServerCertificateErrorDetectedEventArgs](icorewebview2servercertificateerrordetectedeventargs.md#icorewebview2servercertificateerrordetectedeventargs) interface.

#### COREWEBVIEW2_SHARED_BUFFER_ACCESS

> enum [COREWEBVIEW2_SHARED_BUFFER_ACCESS](#corewebview2_shared_buffer_access)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_ONLY            | Script from web page only has read access to the shared buffer.
COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_WRITE            | Script from web page has read and write access to the shared buffer.

Specifies the desired access from script to `CoreWebView2SharedBuffer`.

#### COREWEBVIEW2_TEXT_DIRECTION_KIND

> enum [COREWEBVIEW2_TEXT_DIRECTION_KIND](#corewebview2_text_direction_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_TEXT_DIRECTION_KIND_DEFAULT            | Indicates that the notification text direction adopts the browser's language setting behavior.
COREWEBVIEW2_TEXT_DIRECTION_KIND_LEFT_TO_RIGHT            | Indicates that the notification text is left-to-right.
COREWEBVIEW2_TEXT_DIRECTION_KIND_RIGHT_TO_LEFT            | Indicates that the notification text is right-to-left.

Indicates the text direction of the notification.

#### COREWEBVIEW2_TRACKING_PREVENTION_LEVEL

> enum [COREWEBVIEW2_TRACKING_PREVENTION_LEVEL](#corewebview2_tracking_prevention_level)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_NONE            | Tracking prevention is turned off.
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_BASIC            | The least restrictive level of tracking prevention.
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_BALANCED            | The default level of tracking prevention.
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_STRICT            | The most restrictive level of tracking prevention.

Tracking prevention levels.

#### COREWEBVIEW2_WEB_ERROR_STATUS

> enum [COREWEBVIEW2_WEB_ERROR_STATUS](#corewebview2_web_error_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_WEB_ERROR_STATUS_UNKNOWN            | Indicates that an unknown error occurred.
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_COMMON_NAME_IS_INCORRECT            | Indicates that the SSL certificate common name does not match the web address.
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_EXPIRED            | Indicates that the SSL certificate has expired.
COREWEBVIEW2_WEB_ERROR_STATUS_CLIENT_CERTIFICATE_CONTAINS_ERRORS            | Indicates that the SSL client certificate contains errors.
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_REVOKED            | Indicates that the SSL certificate has been revoked.
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_IS_INVALID            | Indicates that the SSL certificate is not valid.
COREWEBVIEW2_WEB_ERROR_STATUS_SERVER_UNREACHABLE            | Indicates that the host is unreachable.
COREWEBVIEW2_WEB_ERROR_STATUS_TIMEOUT            | Indicates that the connection has timed out.
COREWEBVIEW2_WEB_ERROR_STATUS_ERROR_HTTP_INVALID_SERVER_RESPONSE            | Indicates that the server returned an invalid or unrecognized response.
COREWEBVIEW2_WEB_ERROR_STATUS_CONNECTION_ABORTED            | Indicates that the connection was stopped.
COREWEBVIEW2_WEB_ERROR_STATUS_CONNECTION_RESET            | Indicates that the connection was reset.
COREWEBVIEW2_WEB_ERROR_STATUS_DISCONNECTED            | Indicates that the Internet connection has been lost.
COREWEBVIEW2_WEB_ERROR_STATUS_CANNOT_CONNECT            | Indicates that a connection to the destination was not established.
COREWEBVIEW2_WEB_ERROR_STATUS_HOST_NAME_NOT_RESOLVED            | Indicates that the provided host name was not able to be resolved.
COREWEBVIEW2_WEB_ERROR_STATUS_OPERATION_CANCELED            | Indicates that the operation was canceled.
COREWEBVIEW2_WEB_ERROR_STATUS_REDIRECT_FAILED            | Indicates that the request redirect failed.
COREWEBVIEW2_WEB_ERROR_STATUS_UNEXPECTED_ERROR            | Indicates that an unexpected error occurred.
COREWEBVIEW2_WEB_ERROR_STATUS_VALID_AUTHENTICATION_CREDENTIALS_REQUIRED            | Indicates that user is prompted with a login, waiting on user action.
COREWEBVIEW2_WEB_ERROR_STATUS_VALID_PROXY_AUTHENTICATION_REQUIRED            | Indicates that user lacks proper authentication credentials for a proxy server.

Indicates the error status values for web navigations.

#### COREWEBVIEW2_WEB_RESOURCE_CONTEXT

> enum [COREWEBVIEW2_WEB_RESOURCE_CONTEXT](#corewebview2_web_resource_context)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_ALL            | Specifies all resources.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_DOCUMENT            | Specifies a document resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_STYLESHEET            | Specifies a CSS resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE            | Specifies an image resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_MEDIA            | Specifies another media resource such as a video.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_FONT            | Specifies a font resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_SCRIPT            | Specifies a script resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_XML_HTTP_REQUEST            | Specifies an XML HTTP request, Fetch and EventSource API communication.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_FETCH            | Specifies a Fetch API communication.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_TEXT_TRACK            | Specifies a TextTrack resource.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_EVENT_SOURCE            | Specifies an EventSource API communication.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_WEBSOCKET            | Specifies a WebSocket API communication.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_MANIFEST            | Specifies a Web App Manifest.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_SIGNED_EXCHANGE            | Specifies a Signed HTTP Exchange.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_PING            | Specifies a Ping request.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_CSP_VIOLATION_REPORT            | Specifies a CSP Violation Report.
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_OTHER            | Specifies an other resource.

Specifies the web resource request contexts.

#### COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS

> enum [COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS](#corewebview2_web_resource_request_source_kinds)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_NONE            | 
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_DOCUMENT            | Indicates that web resource is requested from main page including dedicated workers, iframes and main script for shared workers.
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_SHARED_WORKER            | Indicates that web resource is requested from shared worker.
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_SERVICE_WORKER            | Indicates that web resource is requested from service worker.
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_ALL            | Indicates that web resource is requested from any supported source.

Specifies the source of `WebResourceRequested` event.

#### CompareBrowserVersions

> public STDAPI [CompareBrowserVersions](#comparebrowserversions)(PCWSTR version1, PCWSTR version2, int * result)

This method is for anyone want to compare version correctly to determine which version is newer, older or same.

Use it to determine whether to use webview2 or certain feature based upon version. Sets the value of result to `-1`, `0` or `1` if `version1` is less than, equal or greater than `version2` respectively. Returns `E_INVALIDARG` if it fails to parse any of the version strings or any input parameter is `null`. Directly use the `versionInfo` obtained from `GetAvailableCoreWebView2BrowserVersionString` with input, channel information is ignored.

#### CreateCoreWebView2Environment

> public STDAPI [CreateCoreWebView2Environment](#createcorewebview2environment)([ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler](icorewebview2createcorewebview2environmentcompletedhandler.md#icorewebview2createcorewebview2environmentcompletedhandler) * environmentCreatedHandler)

Creates an evergreen WebView2 Environment using the installed WebView2 Runtime version.

This is equivalent to running `CreateCoreWebView2EnvironmentWithOptions` with `nullptr` for `browserExecutableFolder`, `userDataFolder`, `additionalBrowserArguments`. For more information, navigate to `CreateCoreWebView2EnvironmentWithOptions`.

#### CreateCoreWebView2EnvironmentWithOptions

> public STDAPI [CreateCoreWebView2EnvironmentWithOptions](#createcorewebview2environmentwithoptions)(PCWSTR browserExecutableFolder, PCWSTR userDataFolder, [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) * environmentOptions, [ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler](icorewebview2createcorewebview2environmentcompletedhandler.md#icorewebview2createcorewebview2environmentcompletedhandler) * environmentCreatedHandler)

DLL export to create a WebView2 environment with a custom version of WebView2 Runtime, user data folder, and with or without additional options.

When WebView2 experimental APIs are used, make sure to provide a valid `environmentOptions` so that WebView2 runtime knows which version of the SDK that the app is using. Otherwise, WebView2 runtime assumes that the version of the SDK being used is the latest version known to it, which might not be the version of the SDK being used. This wrong SDK version assumption could result in some experimental APIs not being available.

The WebView2 environment and all other WebView2 objects are single threaded and have dependencies on Windows components that require COM to be initialized for a single-threaded apartment. The app is expected to run `CoInitializeEx` before running `CreateCoreWebView2EnvironmentWithOptions`.

```text
CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED);
```

If `CoInitializeEx` did not run or previously ran with `COINIT_MULTITHREADED`, `CreateCoreWebView2EnvironmentWithOptions` fails with one of the following errors.

```text
CO_E_NOTINITIALIZED -  if CoInitializeEx was not called
RPC_E_CHANGED_MODE  -  if CoInitializeEx was previously called with
                       COINIT_MULTITHREADED
```

Use `browserExecutableFolder` to specify whether WebView2 controls use a fixed or installed version of the WebView2 Runtime that exists on a user machine. To use a fixed version of the WebView2 Runtime, pass the folder path that contains the fixed version of the WebView2 Runtime to `browserExecutableFolder`. BrowserExecutableFolder supports both relative (to the application's executable) and absolute files paths. To create WebView2 controls that use the installed version of the WebView2 Runtime that exists on user machines, pass a `null` or empty string to `browserExecutableFolder`. In this scenario, the API tries to find a compatible version of the WebView2 Runtime that is installed on the user machine (first at the machine level, and then per user) using the selected channel preference. The path of fixed version of the WebView2 Runtime should not contain `\Edge\Application\`. When such a path is used, the API fails with `HRESULT_FROM_WIN32(ERROR_NOT_SUPPORTED)`.

By default, the channel search order is `COREWEBVIEW2_CHANNEL_SEARCH_KIND_MOST_STABLE`, which means that environment creation searches for an installation in the following order: the WebView2 Runtime, Beta, Dev, and Canary. The channel search order is reversed when the `ChannelSearchKind` property on [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) is set to `COREWEBVIEW2_CHANNEL_SEARCH_KIND_LEAST_STABLE`, or when the corresponding environment variable or registry override is set to `1`. See below for descriptions of overrides. If `ReleaseChannels` on [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) is provided, environment creation will only consider channels in this set, following the `ChannelSearchKind` order.

You may specify the `userDataFolder` to change the default user data folder location for WebView2. The path is either an absolute file path or a relative file path that is interpreted as relative to the compiled code for the current process. For UWP apps, the default user data folder is the app data folder for the package. For non-UWP apps, the default user data (`{Executable File Name}.WebView2`) folder is created in the same directory next to the compiled code for the app. WebView2 creation fails if the compiled code is running in a directory in which the process does not have permission to create a new directory. The app is responsible to clean up the associated user data folder when it is done.

&gt; [!NOTE]
&gt; As a browser process may be shared among WebViews, WebView creation fails with `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)` if the specified options does not match the options of the WebViews that are currently running in the shared browser process.

`environmentCreatedHandler` is the handler result to the async operation that contains the `WebView2Environment` that was created.

The `browserExecutableFolder`, `channelSearchKind`, `releaseChannels`, `userDataFolder` and `additionalBrowserArguments` of the `environmentOptions` may be overridden by values either specified in environment variables or in the registry.

When creating a `WebView2Environment` the following environment variables are verified.

```text
WEBVIEW2_BROWSER_EXECUTABLE_FOLDER
WEBVIEW2_USER_DATA_FOLDER
WEBVIEW2_ADDITIONAL_BROWSER_ARGUMENTS
WEBVIEW2_CHANNEL_SEARCH_KIND
WEBVIEW2_RELEASE_CHANNELS
```

If you find an override environment variable, use the `browserExecutableFolder` and `userDataFolder` values as replacements for the corresponding values in `CreateCoreWebView2EnvironmentWithOptions` parameters. If `additionalBrowserArguments` is specified in environment variable or in the registry, it is appended to the corresponding values in `CreateCoreWebView2EnvironmentWithOptions` parameters. See `ReleaseChannels` on [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) for more details on how to construct the registry key and environment variable values.

While not strictly overrides, additional environment variables may be set.

```text
WEBVIEW2_WAIT_FOR_SCRIPT_DEBUGGER
```

When found with a non-empty value, this indicates that the WebView is being launched under a script debugger. In this case, the WebView issues a `Page.waitForDebugger` CDP command that runs the script inside the WebView to pause on launch, until a debugger issues a corresponding `Runtime.runIfWaitingForDebugger` CDP command to resume the runtime.

&gt; [!NOTE]
&gt; The following environment variable does not have a registry key equivalent: `WEBVIEW2_WAIT_FOR_SCRIPT_DEBUGGER`.

When found with a non-empty value, it indicates that the WebView is being launched under a script debugger that also supports host apps that use multiple WebViews. The value is used as the identifier for a named pipe that is opened and written to when a new WebView is created by the host app. The payload should match the payload of the `remote-debugging-port` JSON target and an external debugger may use it to attach to a specific WebView instance. The format of the pipe created by the debugger should be `\\.\pipe\WebView2\Debugger\{app_name}\{pipe_name}`, where the following are true.

* `{app_name}` is the host app exe file name, for example, `WebView2Example.exe`

* `{pipe_name}` is the value set for `WEBVIEW2_PIPE_FOR_SCRIPT_DEBUGGER`

To enable debugging of the targets identified by the JSON, you must set the `WEBVIEW2_ADDITIONAL_BROWSER_ARGUMENTS` environment variable to send `--remote-debugging-port={port_num}`, where the following is true.

* `{port_num}` is the port on which the CDP server binds.

&gt; [!WARNING]
&gt; If you set both `WEBVIEW2_PIPE_FOR_SCRIPT_DEBUGGER` and `WEBVIEW2_ADDITIONAL_BROWSER_ARGUMENTS` environment variables, the WebViews hosted in your app and associated contents may exposed to 3rd party apps such as debuggers.

&gt; [!NOTE]
&gt; The following environment variable does not have a registry key equivalent: `WEBVIEW2_PIPE_FOR_SCRIPT_DEBUGGER`.

If none of those environment variables exist, then the registry is examined next. The following registry values are verified.

```text
[{Root}]\Software\Policies\Microsoft\Edge\WebView2\BrowserExecutableFolder
"{AppId}"=""

[{Root}]\Software\Policies\Microsoft\Edge\WebView2\ChannelSearchKind
"{AppId}"=""

[{Root}]\Software\Policies\Microsoft\Edge\WebView2\ReleaseChannels
"{AppId}"=""

[{Root}]\Software\Policies\Microsoft\Edge\WebView2\AdditionalBrowserArguments
"{AppId}"=""

[{Root}]\Software\Policies\Microsoft\Edge\WebView2\UserDataFolder
"{AppId}"=""
```

You can use a group policy under **Administrative Templates** > **Microsoft Edge WebView2** to configure `browserExecutableFolder`, `channelSearchKind`, and `releaseChannels`.

In the unlikely scenario where some instances of WebView are open during a browser update, the deletion of the previous WebView2 Runtime may be blocked. To avoid running out of disk space, a new WebView creation fails with `HRESULT_FROM_WIN32(ERROR_DISK_FULL)` if it detects that too many previous WebView2 Runtime versions exist.

The default maximum number of WebView2 Runtime versions allowed is `20`. To override the maximum number of the previous WebView2 Runtime versions allowed, set the value of the following environment variable.

```text
COREWEBVIEW2_MAX_INSTANCES
```

If the Webview depends upon an installed WebView2 Runtime version and it is uninstalled, any subsequent creation fails with `HRESULT_FROM_WIN32(ERROR_PRODUCT_UNINSTALLED)`.

First verify with Root as `HKLM` and then `HKCU`. `AppId` is first set to the Application User Model ID of the process, then if no corresponding registry key, the `AppId` is set to the compiled code name of the process, or if that is not a registry key then `*`. A registry setting with `*` as the value name will apply to all WebView2 apps, and cannot be used for the `userDataFolder` option. If an override registry key is found, use the `browserExecutableFolder` and `userDataFolder` registry values as replacements and append `additionalBrowserArguments` registry values for the corresponding values in `CreateCoreWebView2EnvironmentWithOptions` parameters.

The following summarizes the possible error values that can be returned from `CreateCoreWebView2EnvironmentWithOptions` and a description of why these errors occur.

Error value   |Description
--------- | ---------
`CO_E_NOTINITIALIZED`|CoInitializeEx was not called.
`RPC_E_CHANGED_MODE`|CoInitializeEx was previously called with COINIT_MULTITHREADED.
`HRESULT_FROM_WIN32(ERROR_NOT_SUPPORTED)`|*\Edge\Application* path used in browserExecutableFolder.
`HRESULT_FROM_WIN32(ERROR_INVALID_STATE)`|Specified options do not match the options of the WebViews that are currently running in the shared browser process.
`HRESULT_FROM_WIN32(ERROR_DISK_FULL)`|In the unlikely scenario where some instances of WebView are open during a browser update, the deletion of the previous WebView2 Runtime may be blocked. To avoid running out of disk space, a new WebView creation fails with `HRESULT_FROM_WIN32(ERROR_DISK_FULL)` if it detects that too many previous WebView2 Runtime versions exist.
`HRESULT_FROM_WIN32(ERROR_PRODUCT_UNINSTALLED)`|If the Webview depends upon an installed WebView2 Runtime version and it is uninstalled.
`HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)`|Could not find Edge installation.
`HRESULT_FROM_WIN32(ERROR_FILE_EXISTS)`|User data folder cannot be created because a file with the same name already exists.
`E_ACCESSDENIED`|Unable to create user data folder, Access Denied.
`E_FAIL`|Edge runtime unable to start.

#### CreateWebViewEnvironmentWithOptionsInternal

> public STDAPI [CreateWebViewEnvironmentWithOptionsInternal](#createwebviewenvironmentwithoptionsinternal)(bool checkRunningInstance, int runtimeType, PCWSTR userDataFolder, IUnknown * environmentOptions, [ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler](icorewebview2createcorewebview2environmentcompletedhandler.md#icorewebview2createcorewebview2environmentcompletedhandler) * webViewEnvironmentCreatedHandler)

This is a DLL export out of `EmbeddedBrowserWebView.dll` which can be found in the installation folder of the WebView2 Runtime you wish to use.

> [!NOTE]
> This function may be modified or removed in future versions. It is recommended you use `CreateCoreWebView2EnvironmentWithOptions` instead of this function.

This function creates a WebView2 environment with a specified version of WebView2 Runtime, user data folder, and with or without additional options.

This is an internal method used by `CreateCoreWebView2EnvironmentWithOptions` that acts similar to `CreateCoreWebView2EnvironmentWithOptions`, but it will only create an [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) from the WebView2 Runtime of the module on which you call `CreateWebViewEnvironmentWithOptionsInternal`. This is unlike `CreateCoreWebView2EnvironmentWithOptions` which handles many other cases including: falling back to other non-stable WebView2 Runtime channels when the stable WebView2 Runtime is not available, handling developer environment variables to change the runtime, handling policy registry keys to change the runtime, and others. You should use `CreateCoreWebView2EnvironmentWithOptions` rather than this method.

If `checkRunningInstance` is set then `CreateWebViewEnvironmentWithOptionsInternal` will forward the creation call to a different WebView2 Runtime if there is already a different WebView2 Runtime running for the specified user data folder. This matches `CreateCoreWebView2EnvironmentWithOptions` behavior. If not set, then this forwarding will not occur and creation will fail if there is already a different WebView2 Runtime running for the specified user data folder.

The `runtimeType` parameter is used to indicate if the WebView2 Runtime is fixed version with value `1`, evergreen with value `0`, or unknown with value `-1`.

See the `CreateCoreWebView2EnvironmentWithOptions` documentation for information on the `userDataFolder`, `environmentOptions`, and `webViewEnvironmentCreatedHandler` parameters which match the parameters from `CreateCoreWebView2EnvironmentWithOptions`.

#### GetAvailableCoreWebView2BrowserVersionString

> public STDAPI [GetAvailableCoreWebView2BrowserVersionString](#getavailablecorewebview2browserversionstring)(PCWSTR browserExecutableFolder, LPWSTR * versionInfo)

Get the browser version info including channel name if it is not the WebView2 Runtime.

Channel names are Beta, Dev, and Canary. If an override exists for the `browserExecutableFolder` or the channel preference, the override is used. If an override is not specified, then the parameter value passed to `GetAvailableCoreWebView2BrowserVersionString` is used. Returns `HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)` if it fails to find an installed WebView2 runtime or non-stable Microsoft Edge installation.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetAvailableCoreWebView2BrowserVersionStringWithOptions

> public STDAPI [GetAvailableCoreWebView2BrowserVersionStringWithOptions](#getavailablecorewebview2browserversionstringwithoptions)(PCWSTR browserExecutableFolder, [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) * environmentOptions, LPWSTR * versionInfo)

This function will tell you the browser version info of the release channel used when creating an environment with the same options.

Browser version info includes channel name if it is not the WebView2 Runtime. Channel names are Beta, Dev, and Canary. The format of the return string matches the format of `BrowserVersionString` on [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment).

If an override exists for `browserExecutableFolder`, `releaseChannels`, or `ChannelSearchKind`, the override is used. The presence of an override can result in a different channel used than the one expected based on the environment options object. `browserExecutableFolder` takes precedence over the other options, regardless of whether or not its channel is included in the `releaseChannels`. See `CreateCoreWebView2EnvironmentWithOptions` for more details on overrides. If an override is not specified, then the parameters passed to `GetAvailableCoreWebView2BrowserVersionStringWithOptions` are used. Returns `HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)` if it fails to find an installed WebView2 Runtime or non-stable Microsoft Edge installation. Use `GetAvailableCoreWebView2BrowserVersionString` to get the version info without the environment options.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

