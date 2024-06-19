---
description: This interface is an extension of ICoreWebView2_18 that manages memory usage target level.
title: WebView2 Win32 C++ ICoreWebView2_19
ms.date: 06/19/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_19
topic_type: 
- APIRef
api_name:
- ICoreWebView2_19
- ICoreWebView2_19.get_MemoryUsageTargetLevel
- ICoreWebView2_19.put_MemoryUsageTargetLevel
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_19

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2_19
  : public ICoreWebView2_18
```

This interface is an extension of [ICoreWebView2_18](icorewebview2_18.md#icorewebview2_18) that manages memory usage target level.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_MemoryUsageTargetLevel](#get_memoryusagetargetlevel) | `MemoryUsageTargetLevel` indicates desired memory consumption level of WebView.
[put_MemoryUsageTargetLevel](#put_memoryusagetargetlevel) | An app may set `MemoryUsageTargetLevel` to indicate desired memory consumption level of WebView.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    1.0.1905

## Members

#### get_MemoryUsageTargetLevel

`MemoryUsageTargetLevel` indicates desired memory consumption level of WebView.

> public HRESULT [get_MemoryUsageTargetLevel](#get_memoryusagetargetlevel)(COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL * level)

#### put_MemoryUsageTargetLevel

An app may set `MemoryUsageTargetLevel` to indicate desired memory consumption level of WebView.

> public HRESULT [put_MemoryUsageTargetLevel](#put_memoryusagetargetlevel)(COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL level)

Scripts will not be impacted and continue to run. This is useful for inactive apps that still want to run scripts and/or keep network connections alive and therefore could not call `TrySuspend` and `Resume` to reduce memory consumption. These apps can set memory usage target level to `COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_LOW` when the app becomes inactive, and set back to `COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_NORMAL` when the app becomes active. It is not necessary to set CoreWebView2Controller's IsVisible property to false when setting the property. It is a best effort operation to change memory usage level, and the API will return before the operation completes. Setting the level to `COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_LOW` could potentially cause memory for some WebView browser processes to be swapped out to disk in some circumstances. It is a best effort to reduce memory usage as much as possible. If a script runs after its related memory has been swapped out, the memory will be swapped back in to ensure the script can still run, but performance might be impacted. Therefore, the app should set the level back to `COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_NORMAL` when the app becomes active again. Setting memory usage target level back to normal will not happen automatically. An app should choose to use either the combination of `TrySuspend` and `Resume` or the combination of setting MemoryUsageTargetLevel to low and normal. It is not advisable to mix them. Trying to set `MemoryUsageTargetLevel` while suspended will be ignored. The `TrySuspend` and `Resume` methods will change the `MemoryUsageTargetLevel`. `TrySuspend` will automatically set `MemoryUsageTargetLevel` to low while `Resume` on suspended WebView will automatically set `MemoryUsageTargetLevel` to normal. Calling `Resume` when the WebView is not suspended would not change `MemoryUsageTargetLevel`.

```cpp
void ViewComponent::ToggleMemoryUsageTargetLevel()
{
    wil::com_ptr<ICoreWebView2_19> webView;
    webView = m_webView.try_query<ICoreWebView2_19>();
    CHECK_FEATURE_RETURN_EMPTY(webView);
    COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL memory_target_level =
        COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_NORMAL;
    CHECK_FAILURE(webView->get_MemoryUsageTargetLevel(&memory_target_level));
    memory_target_level = (memory_target_level == COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_LOW)
                              ? COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_NORMAL
                              : COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_LOW;
    CHECK_FAILURE(webView->put_MemoryUsageTargetLevel(memory_target_level));
    MessageBox(
        nullptr,
        (memory_target_level == COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_LOW)
            ? L"MemoryUsageTargetLevel is set to LOW."
            : L"MemoryUsageTargetLevel is set to NORMAL.",
        L"MemoryUsageTargetLevel change", MB_OK);
}
```

