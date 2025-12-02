---
description: Interface for different sensitivity label kinds used in WebView2.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSensitivityLabel
ms.date: 12/02/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSensitivityLabel
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSensitivityLabel
- ICoreWebView2ExperimentalSensitivityLabel.get_LabelKind
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSensitivityLabel

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSensitivityLabel
  : public IUnknown
```

Interface for different sensitivity label kinds used in WebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_LabelKind](#get_labelkind) | Gets the type of the sensitivity label applied to the web content.

This interface provides functionality for accessing sensitivity label information applied to web content. Different label types (such as `ICoreWebView2MipSensitivityLabel`) provide specific label information and metadata.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3590

## Members

#### get_LabelKind

Gets the type of the sensitivity label applied to the web content.

> public HRESULT [get_LabelKind](#get_labelkind)(COREWEBVIEW2_SENSITIVITY_LABEL_KIND * value)

This property identifies which sensitivity label system is being used (such as Microsoft Information Protection or other label providers). Applications can use this information to determine how to interpret and handle the label data, as different label types may have different metadata formats, protection requirements, and policy enforcement mechanisms.

