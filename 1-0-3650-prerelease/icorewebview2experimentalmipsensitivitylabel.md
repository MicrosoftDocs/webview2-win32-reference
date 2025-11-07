---
description: Interface for Microsoft Information Protection (MIP) sensitivity labels.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalMipSensitivityLabel
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalMipSensitivityLabel
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalMipSensitivityLabel
- ICoreWebView2ExperimentalMipSensitivityLabel.get_LabelId
- ICoreWebView2ExperimentalMipSensitivityLabel.get_OrganizationId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalMipSensitivityLabel

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalMipSensitivityLabel
  : public IUnknown
```

Interface for Microsoft Information Protection (MIP) sensitivity labels.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_LabelId](#get_labelid) | The unique identifier for the Microsoft Information Protection label.
[get_OrganizationId](#get_organizationid) | The unique identifier for the organization that owns the MIP label.

This interface provides specific information about MIP labels, including label identification and organizational context.

```cpp
            Microsoft::WRL::ComPtr<ICoreWebView2ExperimentalMipSensitivityLabel> mipLabel;
            if (SUCCEEDED(sensitivityLabel.As(&mipLabel)))
            {
                wil::unique_cotaskmem_string labelId;
                wil::unique_cotaskmem_string organizationId;
                CHECK_FAILURE(mipLabel->get_LabelId(&labelId));
                CHECK_FAILURE(mipLabel->get_OrganizationId(&organizationId));

                // Store the label id and organization id as a pair. Can be used
                // to query Purview for the allowed rights on the document
                labelInfos.emplace_back(
                    std::wstring(labelId.get()), std::wstring(organizationId.get()));
            }
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3590

## Members

#### get_LabelId

The unique identifier for the Microsoft Information Protection label.

> public HRESULT [get_LabelId](#get_labelid)(LPWSTR * value)

This string contains a GUID that uniquely identifies the specific sensitivity label within the organization's MIP policy configuration. The GUID follows the format: `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` (with dashes, no extra braces). eg: `3fa85f64-5717-4562-b3fc-2c963f66afa6`

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_OrganizationId

The unique identifier for the organization that owns the MIP label.

> public HRESULT [get_OrganizationId](#get_organizationid)(LPWSTR * value)

This string contains a GUID that identifies the Azure Active Directory tenant or organization that configured and deployed the sensitivity label. The GUID follows the format: `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` (with dashes, no extra braces). eg: `44567f64-8712-1789-ac3f-15aa3f66ab12`

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

