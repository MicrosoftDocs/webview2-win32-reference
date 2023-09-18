---
description: WebView2 Win32 Globals
title: Globals
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
topic_type: 
- APIRef
api_name:
- CreateWebViewEnvironmentWithOptionsInternal
api_type:
- DllExport
api_location:
- WebView2Loader.dll
---

# Globals

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[COREWEBVIEW2_BOUNDS_MODE](#corewebview2_bounds_mode) | 
[COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND](#corewebview2_browser_process_exit_kind) | 
[COREWEBVIEW2_BROWSING_DATA_KINDS](#corewebview2_browsing_data_kinds) | 
[COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT](#corewebview2_capture_preview_image_format) | 
[COREWEBVIEW2_CLIENT_CERTIFICATE_KIND](#corewebview2_client_certificate_kind) | 
[COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND](#corewebview2_context_menu_item_kind) | 
[COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND](#corewebview2_context_menu_target_kind) | 
[COREWEBVIEW2_COOKIE_SAME_SITE_KIND](#corewebview2_cookie_same_site_kind) | 
[COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT](#corewebview2_default_download_dialog_corner_alignment) | 
[COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON](#corewebview2_download_interrupt_reason) | 
[COREWEBVIEW2_DOWNLOAD_STATE](#corewebview2_download_state) | 
[COREWEBVIEW2_FAVICON_IMAGE_FORMAT](#corewebview2_favicon_image_format) | 
[COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND](#corewebview2_host_resource_access_kind) | 
[COREWEBVIEW2_KEY_EVENT_KIND](#corewebview2_key_event_kind) | 
[COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL](#corewebview2_memory_usage_target_level) | 
[COREWEBVIEW2_MOUSE_EVENT_KIND](#corewebview2_mouse_event_kind) | 
[COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS](#corewebview2_mouse_event_virtual_keys) | 
[COREWEBVIEW2_MOVE_FOCUS_REASON](#corewebview2_move_focus_reason) | 
[COREWEBVIEW2_NAVIGATION_KIND](#corewebview2_navigation_kind) | 
[COREWEBVIEW2_PDF_TOOLBAR_ITEMS](#corewebview2_pdf_toolbar_items) | 
[COREWEBVIEW2_PERMISSION_KIND](#corewebview2_permission_kind) | 
[COREWEBVIEW2_PERMISSION_STATE](#corewebview2_permission_state) | 
[COREWEBVIEW2_POINTER_EVENT_KIND](#corewebview2_pointer_event_kind) | 
[COREWEBVIEW2_PREFERRED_COLOR_SCHEME](#corewebview2_preferred_color_scheme) | 
[COREWEBVIEW2_PRINT_COLLATION](#corewebview2_print_collation) | 
[COREWEBVIEW2_PRINT_COLOR_MODE](#corewebview2_print_color_mode) | 
[COREWEBVIEW2_PRINT_DIALOG_KIND](#corewebview2_print_dialog_kind) | 
[COREWEBVIEW2_PRINT_DUPLEX](#corewebview2_print_duplex) | 
[COREWEBVIEW2_PRINT_MEDIA_SIZE](#corewebview2_print_media_size) | 
[COREWEBVIEW2_PRINT_ORIENTATION](#corewebview2_print_orientation) | 
[COREWEBVIEW2_PRINT_STATUS](#corewebview2_print_status) | 
[COREWEBVIEW2_PROCESS_FAILED_KIND](#corewebview2_process_failed_kind) | 
[COREWEBVIEW2_PROCESS_FAILED_REASON](#corewebview2_process_failed_reason) | 
[COREWEBVIEW2_PROCESS_KIND](#corewebview2_process_kind) | 
[COREWEBVIEW2_SCRIPT_DIALOG_KIND](#corewebview2_script_dialog_kind) | 
[COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION](#corewebview2_server_certificate_error_action) | 
[COREWEBVIEW2_SHARED_BUFFER_ACCESS](#corewebview2_shared_buffer_access) | 
[COREWEBVIEW2_TRACKING_PREVENTION_LEVEL](#corewebview2_tracking_prevention_level) | 
[COREWEBVIEW2_WEB_ERROR_STATUS](#corewebview2_web_error_status) | 
[COREWEBVIEW2_WEB_RESOURCE_CONTEXT](#corewebview2_web_resource_context) | 
[CreateWebViewEnvironmentWithOptionsInternal](#createwebviewenvironmentwithoptionsinternal) | This is a DLL export out of `EmbeddedBrowserWebView.dll` which can be found in the installation folder of the WebView2 Runtime you wish to use.

## Members

#### COREWEBVIEW2_BOUNDS_MODE

> enum [COREWEBVIEW2_BOUNDS_MODE](#corewebview2_bounds_mode)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_BOUNDS_MODE_USE_RAW_PIXELS            | 
COREWEBVIEW2_BOUNDS_MODE_USE_RASTERIZATION_SCALE            | 

#### COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND

> enum [COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND](#corewebview2_browser_process_exit_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_NORMAL            | 
COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_FAILED            | 

#### COREWEBVIEW2_BROWSING_DATA_KINDS

> enum [COREWEBVIEW2_BROWSING_DATA_KINDS](#corewebview2_browsing_data_kinds)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_BROWSING_DATA_KINDS_FILE_SYSTEMS            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_INDEXED_DB            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_LOCAL_STORAGE            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_WEB_SQL            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_CACHE_STORAGE            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_ALL_DOM_STORAGE            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_COOKIES            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_ALL_SITE            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_DISK_CACHE            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_DOWNLOAD_HISTORY            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_GENERAL_AUTOFILL            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_PASSWORD_AUTOSAVE            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_BROWSING_HISTORY            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_SETTINGS            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_ALL_PROFILE            | 
COREWEBVIEW2_BROWSING_DATA_KINDS_SERVICE_WORKERS            | 

#### COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT

> enum [COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT](#corewebview2_capture_preview_image_format)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT_PNG            | 
COREWEBVIEW2_CAPTURE_PREVIEW_IMAGE_FORMAT_JPEG            | 

#### COREWEBVIEW2_CLIENT_CERTIFICATE_KIND

> enum [COREWEBVIEW2_CLIENT_CERTIFICATE_KIND](#corewebview2_client_certificate_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CLIENT_CERTIFICATE_KIND_SMART_CARD            | 
COREWEBVIEW2_CLIENT_CERTIFICATE_KIND_PIN            | 
COREWEBVIEW2_CLIENT_CERTIFICATE_KIND_OTHER            | 

#### COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND

> enum [COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND](#corewebview2_context_menu_item_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_COMMAND            | 
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_CHECK_BOX            | 
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_RADIO            | 
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SEPARATOR            | 
COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SUBMENU            | 

#### COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND

> enum [COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND](#corewebview2_context_menu_target_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_PAGE            | 
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_IMAGE            | 
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_SELECTED_TEXT            | 
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_AUDIO            | 
COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_VIDEO            | 

#### COREWEBVIEW2_COOKIE_SAME_SITE_KIND

> enum [COREWEBVIEW2_COOKIE_SAME_SITE_KIND](#corewebview2_cookie_same_site_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_COOKIE_SAME_SITE_KIND_NONE            | 
COREWEBVIEW2_COOKIE_SAME_SITE_KIND_LAX            | 
COREWEBVIEW2_COOKIE_SAME_SITE_KIND_STRICT            | 

#### COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT

> enum [COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT](#corewebview2_default_download_dialog_corner_alignment)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT_TOP_LEFT            | 
COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT_TOP_RIGHT            | 
COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT_BOTTOM_LEFT            | 
COREWEBVIEW2_DEFAULT_DOWNLOAD_DIALOG_CORNER_ALIGNMENT_BOTTOM_RIGHT            | 

#### COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON

> enum [COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON](#corewebview2_download_interrupt_reason)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NONE            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_FAILED            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_ACCESS_DENIED            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_NO_SPACE            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_NAME_TOO_LONG            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_TOO_LARGE            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_MALICIOUS            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_TRANSIENT_ERROR            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_BLOCKED_BY_POLICY            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_SECURITY_CHECK_FAILED            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_TOO_SHORT            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_FILE_HASH_MISMATCH            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_FAILED            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_TIMEOUT            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_DISCONNECTED            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_SERVER_DOWN            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_NETWORK_INVALID_REQUEST            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_FAILED            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_NO_RANGE            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_BAD_CONTENT            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_UNAUTHORIZED            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_CERTIFICATE_PROBLEM            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_FORBIDDEN            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_UNEXPECTED_RESPONSE            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_CONTENT_LENGTH_MISMATCH            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_SERVER_CROSS_ORIGIN_REDIRECT            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_USER_CANCELED            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_USER_SHUTDOWN            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_USER_PAUSED            | 
COREWEBVIEW2_DOWNLOAD_INTERRUPT_REASON_DOWNLOAD_PROCESS_CRASHED            | 

#### COREWEBVIEW2_DOWNLOAD_STATE

> enum [COREWEBVIEW2_DOWNLOAD_STATE](#corewebview2_download_state)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_DOWNLOAD_STATE_IN_PROGRESS            | 
COREWEBVIEW2_DOWNLOAD_STATE_INTERRUPTED            | 
COREWEBVIEW2_DOWNLOAD_STATE_COMPLETED            | 

#### COREWEBVIEW2_FAVICON_IMAGE_FORMAT

> enum [COREWEBVIEW2_FAVICON_IMAGE_FORMAT](#corewebview2_favicon_image_format)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_FAVICON_IMAGE_FORMAT_PNG            | 
COREWEBVIEW2_FAVICON_IMAGE_FORMAT_JPEG            | 

#### COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND

> enum [COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND](#corewebview2_host_resource_access_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY            | 
COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_ALLOW            | 
COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY_CORS            | 

#### COREWEBVIEW2_KEY_EVENT_KIND

> enum [COREWEBVIEW2_KEY_EVENT_KIND](#corewebview2_key_event_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_KEY_EVENT_KIND_KEY_DOWN            | 
COREWEBVIEW2_KEY_EVENT_KIND_KEY_UP            | 
COREWEBVIEW2_KEY_EVENT_KIND_SYSTEM_KEY_DOWN            | 
COREWEBVIEW2_KEY_EVENT_KIND_SYSTEM_KEY_UP            | 

#### COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL

> enum [COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL](#corewebview2_memory_usage_target_level)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_NORMAL            | 
COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_LOW            | 

#### COREWEBVIEW2_MOUSE_EVENT_KIND

> enum [COREWEBVIEW2_MOUSE_EVENT_KIND](#corewebview2_mouse_event_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MOUSE_EVENT_KIND_HORIZONTAL_WHEEL            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_LEFT_BUTTON_DOUBLE_CLICK            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_LEFT_BUTTON_DOWN            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_LEFT_BUTTON_UP            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_LEAVE            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_MIDDLE_BUTTON_DOUBLE_CLICK            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_MIDDLE_BUTTON_DOWN            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_MIDDLE_BUTTON_UP            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_MOVE            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_RIGHT_BUTTON_DOUBLE_CLICK            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_RIGHT_BUTTON_DOWN            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_RIGHT_BUTTON_UP            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_WHEEL            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_X_BUTTON_DOUBLE_CLICK            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_X_BUTTON_DOWN            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_X_BUTTON_UP            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_NON_CLIENT_RIGHT_BUTTON_DOWN            | 
COREWEBVIEW2_MOUSE_EVENT_KIND_NON_CLIENT_RIGHT_BUTTON_UP            | 

#### COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS

> enum [COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS](#corewebview2_mouse_event_virtual_keys)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_NONE            | 
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_LEFT_BUTTON            | 
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_RIGHT_BUTTON            | 
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_SHIFT            | 
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_CONTROL            | 
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_MIDDLE_BUTTON            | 
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_X_BUTTON1            | 
COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS_X_BUTTON2            | 

#### COREWEBVIEW2_MOVE_FOCUS_REASON

> enum [COREWEBVIEW2_MOVE_FOCUS_REASON](#corewebview2_move_focus_reason)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MOVE_FOCUS_REASON_PROGRAMMATIC            | 
COREWEBVIEW2_MOVE_FOCUS_REASON_NEXT            | 
COREWEBVIEW2_MOVE_FOCUS_REASON_PREVIOUS            | 

#### COREWEBVIEW2_NAVIGATION_KIND

> enum [COREWEBVIEW2_NAVIGATION_KIND](#corewebview2_navigation_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_NAVIGATION_KIND_RELOAD            | 
COREWEBVIEW2_NAVIGATION_KIND_BACK_OR_FORWARD            | 
COREWEBVIEW2_NAVIGATION_KIND_NEW_DOCUMENT            | 

#### COREWEBVIEW2_PDF_TOOLBAR_ITEMS

> enum [COREWEBVIEW2_PDF_TOOLBAR_ITEMS](#corewebview2_pdf_toolbar_items)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_NONE            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SAVE            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PRINT            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SAVE_AS            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_ZOOM_IN            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_ZOOM_OUT            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_ROTATE            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_FIT_PAGE            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PAGE_LAYOUT            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_BOOKMARKS            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PAGE_SELECTOR            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SEARCH            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_FULL_SCREEN            | 
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_MORE_SETTINGS            | 

#### COREWEBVIEW2_PERMISSION_KIND

> enum [COREWEBVIEW2_PERMISSION_KIND](#corewebview2_permission_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PERMISSION_KIND_UNKNOWN_PERMISSION            | 
COREWEBVIEW2_PERMISSION_KIND_MICROPHONE            | 
COREWEBVIEW2_PERMISSION_KIND_CAMERA            | 
COREWEBVIEW2_PERMISSION_KIND_GEOLOCATION            | 
COREWEBVIEW2_PERMISSION_KIND_NOTIFICATIONS            | 
COREWEBVIEW2_PERMISSION_KIND_OTHER_SENSORS            | 
COREWEBVIEW2_PERMISSION_KIND_CLIPBOARD_READ            | 
COREWEBVIEW2_PERMISSION_KIND_MULTIPLE_AUTOMATIC_DOWNLOADS            | 
COREWEBVIEW2_PERMISSION_KIND_FILE_READ_WRITE            | 
COREWEBVIEW2_PERMISSION_KIND_AUTOPLAY            | 
COREWEBVIEW2_PERMISSION_KIND_LOCAL_FONTS            | 
COREWEBVIEW2_PERMISSION_KIND_MIDI_SYSTEM_EXCLUSIVE_MESSAGES            | 
COREWEBVIEW2_PERMISSION_KIND_WINDOW_MANAGEMENT            | 

#### COREWEBVIEW2_PERMISSION_STATE

> enum [COREWEBVIEW2_PERMISSION_STATE](#corewebview2_permission_state)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PERMISSION_STATE_DEFAULT            | 
COREWEBVIEW2_PERMISSION_STATE_ALLOW            | 
COREWEBVIEW2_PERMISSION_STATE_DENY            | 

#### COREWEBVIEW2_POINTER_EVENT_KIND

> enum [COREWEBVIEW2_POINTER_EVENT_KIND](#corewebview2_pointer_event_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_POINTER_EVENT_KIND_ACTIVATE            | 
COREWEBVIEW2_POINTER_EVENT_KIND_DOWN            | 
COREWEBVIEW2_POINTER_EVENT_KIND_ENTER            | 
COREWEBVIEW2_POINTER_EVENT_KIND_LEAVE            | 
COREWEBVIEW2_POINTER_EVENT_KIND_UP            | 
COREWEBVIEW2_POINTER_EVENT_KIND_UPDATE            | 

#### COREWEBVIEW2_PREFERRED_COLOR_SCHEME

> enum [COREWEBVIEW2_PREFERRED_COLOR_SCHEME](#corewebview2_preferred_color_scheme)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PREFERRED_COLOR_SCHEME_AUTO            | 
COREWEBVIEW2_PREFERRED_COLOR_SCHEME_LIGHT            | 
COREWEBVIEW2_PREFERRED_COLOR_SCHEME_DARK            | 

#### COREWEBVIEW2_PRINT_COLLATION

> enum [COREWEBVIEW2_PRINT_COLLATION](#corewebview2_print_collation)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_COLLATION_DEFAULT            | 
COREWEBVIEW2_PRINT_COLLATION_COLLATED            | 
COREWEBVIEW2_PRINT_COLLATION_UNCOLLATED            | 

#### COREWEBVIEW2_PRINT_COLOR_MODE

> enum [COREWEBVIEW2_PRINT_COLOR_MODE](#corewebview2_print_color_mode)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_COLOR_MODE_DEFAULT            | 
COREWEBVIEW2_PRINT_COLOR_MODE_COLOR            | 
COREWEBVIEW2_PRINT_COLOR_MODE_GRAYSCALE            | 

#### COREWEBVIEW2_PRINT_DIALOG_KIND

> enum [COREWEBVIEW2_PRINT_DIALOG_KIND](#corewebview2_print_dialog_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_DIALOG_KIND_BROWSER            | 
COREWEBVIEW2_PRINT_DIALOG_KIND_SYSTEM            | 

#### COREWEBVIEW2_PRINT_DUPLEX

> enum [COREWEBVIEW2_PRINT_DUPLEX](#corewebview2_print_duplex)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_DUPLEX_DEFAULT            | 
COREWEBVIEW2_PRINT_DUPLEX_ONE_SIDED            | 
COREWEBVIEW2_PRINT_DUPLEX_TWO_SIDED_LONG_EDGE            | 
COREWEBVIEW2_PRINT_DUPLEX_TWO_SIDED_SHORT_EDGE            | 

#### COREWEBVIEW2_PRINT_MEDIA_SIZE

> enum [COREWEBVIEW2_PRINT_MEDIA_SIZE](#corewebview2_print_media_size)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_MEDIA_SIZE_DEFAULT            | 
COREWEBVIEW2_PRINT_MEDIA_SIZE_CUSTOM            | 

#### COREWEBVIEW2_PRINT_ORIENTATION

> enum [COREWEBVIEW2_PRINT_ORIENTATION](#corewebview2_print_orientation)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_ORIENTATION_PORTRAIT            | 
COREWEBVIEW2_PRINT_ORIENTATION_LANDSCAPE            | 

#### COREWEBVIEW2_PRINT_STATUS

> enum [COREWEBVIEW2_PRINT_STATUS](#corewebview2_print_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_STATUS_SUCCEEDED            | 
COREWEBVIEW2_PRINT_STATUS_PRINTER_UNAVAILABLE            | 
COREWEBVIEW2_PRINT_STATUS_OTHER_ERROR            | 

#### COREWEBVIEW2_PROCESS_FAILED_KIND

> enum [COREWEBVIEW2_PROCESS_FAILED_KIND](#corewebview2_process_failed_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PROCESS_FAILED_KIND_BROWSER_PROCESS_EXITED            | 
COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_EXITED            | 
COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_UNRESPONSIVE            | 
COREWEBVIEW2_PROCESS_FAILED_KIND_FRAME_RENDER_PROCESS_EXITED            | 
COREWEBVIEW2_PROCESS_FAILED_KIND_UTILITY_PROCESS_EXITED            | 
COREWEBVIEW2_PROCESS_FAILED_KIND_SANDBOX_HELPER_PROCESS_EXITED            | 
COREWEBVIEW2_PROCESS_FAILED_KIND_GPU_PROCESS_EXITED            | 
COREWEBVIEW2_PROCESS_FAILED_KIND_PPAPI_PLUGIN_PROCESS_EXITED            | 
COREWEBVIEW2_PROCESS_FAILED_KIND_PPAPI_BROKER_PROCESS_EXITED            | 
COREWEBVIEW2_PROCESS_FAILED_KIND_UNKNOWN_PROCESS_EXITED            | 

#### COREWEBVIEW2_PROCESS_FAILED_REASON

> enum [COREWEBVIEW2_PROCESS_FAILED_REASON](#corewebview2_process_failed_reason)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PROCESS_FAILED_REASON_UNEXPECTED            | 
COREWEBVIEW2_PROCESS_FAILED_REASON_UNRESPONSIVE            | 
COREWEBVIEW2_PROCESS_FAILED_REASON_TERMINATED            | 
COREWEBVIEW2_PROCESS_FAILED_REASON_CRASHED            | 
COREWEBVIEW2_PROCESS_FAILED_REASON_LAUNCH_FAILED            | 
COREWEBVIEW2_PROCESS_FAILED_REASON_OUT_OF_MEMORY            | 
COREWEBVIEW2_PROCESS_FAILED_REASON_PROFILE_DELETED            | 

#### COREWEBVIEW2_PROCESS_KIND

> enum [COREWEBVIEW2_PROCESS_KIND](#corewebview2_process_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PROCESS_KIND_BROWSER            | 
COREWEBVIEW2_PROCESS_KIND_RENDERER            | 
COREWEBVIEW2_PROCESS_KIND_UTILITY            | 
COREWEBVIEW2_PROCESS_KIND_SANDBOX_HELPER            | 
COREWEBVIEW2_PROCESS_KIND_GPU            | 
COREWEBVIEW2_PROCESS_KIND_PPAPI_PLUGIN            | 
COREWEBVIEW2_PROCESS_KIND_PPAPI_BROKER            | 

#### COREWEBVIEW2_SCRIPT_DIALOG_KIND

> enum [COREWEBVIEW2_SCRIPT_DIALOG_KIND](#corewebview2_script_dialog_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SCRIPT_DIALOG_KIND_ALERT            | 
COREWEBVIEW2_SCRIPT_DIALOG_KIND_CONFIRM            | 
COREWEBVIEW2_SCRIPT_DIALOG_KIND_PROMPT            | 
COREWEBVIEW2_SCRIPT_DIALOG_KIND_BEFOREUNLOAD            | 

#### COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION

> enum [COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION](#corewebview2_server_certificate_error_action)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_ALWAYS_ALLOW            | 
COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_CANCEL            | 
COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_DEFAULT            | 

#### COREWEBVIEW2_SHARED_BUFFER_ACCESS

> enum [COREWEBVIEW2_SHARED_BUFFER_ACCESS](#corewebview2_shared_buffer_access)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_ONLY            | 
COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_WRITE            | 

#### COREWEBVIEW2_TRACKING_PREVENTION_LEVEL

> enum [COREWEBVIEW2_TRACKING_PREVENTION_LEVEL](#corewebview2_tracking_prevention_level)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_NONE            | 
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_BASIC            | 
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_BALANCED            | 
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_STRICT            | 

#### COREWEBVIEW2_WEB_ERROR_STATUS

> enum [COREWEBVIEW2_WEB_ERROR_STATUS](#corewebview2_web_error_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_WEB_ERROR_STATUS_UNKNOWN            | 
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_COMMON_NAME_IS_INCORRECT            | 
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_EXPIRED            | 
COREWEBVIEW2_WEB_ERROR_STATUS_CLIENT_CERTIFICATE_CONTAINS_ERRORS            | 
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_REVOKED            | 
COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_IS_INVALID            | 
COREWEBVIEW2_WEB_ERROR_STATUS_SERVER_UNREACHABLE            | 
COREWEBVIEW2_WEB_ERROR_STATUS_TIMEOUT            | 
COREWEBVIEW2_WEB_ERROR_STATUS_ERROR_HTTP_INVALID_SERVER_RESPONSE            | 
COREWEBVIEW2_WEB_ERROR_STATUS_CONNECTION_ABORTED            | 
COREWEBVIEW2_WEB_ERROR_STATUS_CONNECTION_RESET            | 
COREWEBVIEW2_WEB_ERROR_STATUS_DISCONNECTED            | 
COREWEBVIEW2_WEB_ERROR_STATUS_CANNOT_CONNECT            | 
COREWEBVIEW2_WEB_ERROR_STATUS_HOST_NAME_NOT_RESOLVED            | 
COREWEBVIEW2_WEB_ERROR_STATUS_OPERATION_CANCELED            | 
COREWEBVIEW2_WEB_ERROR_STATUS_REDIRECT_FAILED            | 
COREWEBVIEW2_WEB_ERROR_STATUS_UNEXPECTED_ERROR            | 
COREWEBVIEW2_WEB_ERROR_STATUS_VALID_AUTHENTICATION_CREDENTIALS_REQUIRED            | 
COREWEBVIEW2_WEB_ERROR_STATUS_VALID_PROXY_AUTHENTICATION_REQUIRED            | 

#### COREWEBVIEW2_WEB_RESOURCE_CONTEXT

> enum [COREWEBVIEW2_WEB_RESOURCE_CONTEXT](#corewebview2_web_resource_context)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_ALL            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_DOCUMENT            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_STYLESHEET            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_MEDIA            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_FONT            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_SCRIPT            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_XML_HTTP_REQUEST            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_FETCH            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_TEXT_TRACK            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_EVENT_SOURCE            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_WEBSOCKET            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_MANIFEST            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_SIGNED_EXCHANGE            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_PING            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_CSP_VIOLATION_REPORT            | 
COREWEBVIEW2_WEB_RESOURCE_CONTEXT_OTHER            | 

#### CreateWebViewEnvironmentWithOptionsInternal

> public STDAPI [CreateWebViewEnvironmentWithOptionsInternal](#createwebviewenvironmentwithoptionsinternal)(bool checkRunningInstance, int runtimeType, PCWSTR userDataFolder, IUnknown * environmentOptions, ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler * webViewEnvironmentCreatedHandler)

This is a DLL export out of `EmbeddedBrowserWebView.dll` which can be found in the installation folder of the WebView2 Runtime you wish to use.

> [!NOTE]
> This function may be modified or removed in future versions. It is recommended you use `CreateCoreWebView2EnvironmentWithOptions` instead of this function.

This function creates a WebView2 environment with a specified version of WebView2 Runtime, user data folder, and with or without additional options.

This is an internal method used by `CreateCoreWebView2EnvironmentWithOptions` that acts similar to `CreateCoreWebView2EnvironmentWithOptions`, but it will only create an [ICoreWebView2Environment](icorewebview2environment.md) from the WebView2 Runtime of the module on which you call `CreateWebViewEnvironmentWithOptionsInternal`. This is unlike `CreateCoreWebView2EnvironmentWithOptions` which handles many other cases including: falling back to other non-stable WebView2 Runtime channels when the stable WebView2 Runtime is not available, handling developer environment variables to change the runtime, handling policy registry keys to change the runtime, and others. You should use `CreateCoreWebView2EnvironmentWithOptions` rather than this method.

If `checkRunningInstance` is set then `CreateWebViewEnvironmentWithOptionsInternal` will forward the creation call to a different WebView2 Runtime if there is already a different WebView2 Runtime running for the specified user data folder. This matches `CreateCoreWebView2EnvironmentWithOptions` behavior. If not set, then this forwarding will not occur and creation will fail if there is already a different WebView2 Runtime running for the specified user data folder.

The `runtimeType` parameter is used to indicate if the WebView2 Runtime is fixed version with value `1`, evergreen with value `0`, or unknown with value `-1`.

See the `CreateCoreWebView2EnvironmentWithOptions` documentation for information on the `userDataFolder`, `environmentOptions`, and `webViewEnvironmentCreatedHandler` parameters which match the parameters from `CreateCoreWebView2EnvironmentWithOptions`.

