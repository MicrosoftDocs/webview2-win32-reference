---
description: This interface provides information about sensitivity of a web page loaded in the WebView2 control.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSensitivityInfo
ms.date: 02/09/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSensitivityInfo
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSensitivityInfo
- ICoreWebView2ExperimentalSensitivityInfo.get_SensitivityLabels
- ICoreWebView2ExperimentalSensitivityInfo.get_SensitivityLabelsState
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSensitivityInfo

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSensitivityInfo
  : public IUnknown
```

This interface provides information about sensitivity of a web page loaded in the WebView2 control.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_SensitivityLabels](#get_sensitivitylabels) | Gets a read-only collection of all sensitivity labels detected in the current web document.
[get_SensitivityLabelsState](#get_sensitivitylabelsstate) | Gets the current state of sensitivity label detection.

It contains the current state of sensitivity label detection and a collection of all sensitivity labels that have been reported by the web page via [`Page Interaction Restriction Manager`](https://github.com/MicrosoftEdge/MSEdgeExplainers/blob/main/PageInteractionRestrictionManager/explainer.md).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3590

## Members

#### get_SensitivityLabels

Gets a read-only collection of all sensitivity labels detected in the current web document.

> public HRESULT [get_SensitivityLabels](#get_sensitivitylabels)([ICoreWebView2ExperimentalSensitivityLabelCollectionView](icorewebview2experimentalsensitivitylabelcollectionview.md#icorewebview2experimentalsensitivitylabelcollectionview) ** value)

This collection contains list of sensitivity labels that have been reported by the web content. `SensitivityLabels` are valid only if SensitivityLabelsState is `COREWEBVIEW2_SENSITIVITY_LABELS_STATE_AVAILABLE`. In case SensitivityLabelsState is `COREWEBVIEW2_SENSITIVITY_LABELS_STATE_NOT_APPLICABLE` this collection will be empty. In case SensitivityLabelsState is `COREWEBVIEW2_SENSITIVITY_LABELS_STATE_PENDING` this will return nullptr.

```cpp
std::vector<std::pair<std::wstring, std::wstring>> ScenarioSensitivityLabel::
    ExtractSensitivityLabelInfo(
        ICoreWebView2ExperimentalSensitivityLabelCollectionView* labelCollection)
{
    std::vector<std::pair<std::wstring, std::wstring>> labelInfos;

    if (!labelCollection)
    {
        return labelInfos;
    }

    UINT32 labelCount = 0;
    CHECK_FAILURE(labelCollection->get_Count(&labelCount));

    for (UINT32 i = 0; i < labelCount; ++i)
    {
        Microsoft::WRL::ComPtr<ICoreWebView2ExperimentalSensitivityLabel> sensitivityLabel;
        CHECK_FAILURE(labelCollection->GetValueAtIndex(i, &sensitivityLabel));

        COREWEBVIEW2_SENSITIVITY_LABEL_KIND labelKind;
        CHECK_FAILURE(sensitivityLabel->get_LabelKind(&labelKind));
        if (labelKind == COREWEBVIEW2_SENSITIVITY_LABEL_KIND_MIP)
        {
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
        }
    }
    return labelInfos;
}
```

#### get_SensitivityLabelsState

Gets the current state of sensitivity label detection.

> public HRESULT [get_SensitivityLabelsState](#get_sensitivitylabelsstate)([COREWEBVIEW2_SENSITIVITY_LABELS_STATE](https://review.learn.microsoft.com/en-us/microsoft-edge/webview2/reference/win32/webview2experimental-idl?view=webview2-1.0.3848-prerelease&branch=pr-en-us-136#corewebview2_sensitivity_labels_state) * value)

Refer `COREWEBVIEW2_SENSITIVITY_LABELS_STATE` for different states.

