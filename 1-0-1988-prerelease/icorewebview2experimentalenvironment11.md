---
description: This is the ICoreWebView2ExperimentalEnvironment11 interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment11
ms.date: 08/30/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment11
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalEnvironment11
- ICoreWebView2ExperimentalEnvironment11.GetProcessInfosWithDetails
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalEnvironment11

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment11
  : public IUnknown
```

This is the ICoreWebView2ExperimentalEnvironment11 interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetProcessInfosWithDetails](#getprocessinfoswithdetails) | Gets a snapshot collection of `ProcessInfo`s corresponding to all currently running processes associated with this [ICoreWebView2Environment](icorewebview2environment.md) except for crashpad process.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### GetProcessInfosWithDetails

Gets a snapshot collection of `ProcessInfo`s corresponding to all currently running processes associated with this ICoreWebView2Environment except for crashpad process.

> public HRESULT [GetProcessInfosWithDetails](#getprocessinfoswithdetails)([ICoreWebView2ExperimentalGetProcessInfosWithDetailsCompletedHandler](icorewebview2experimentalgetprocessinfoswithdetailscompletedhandler.md) * handler)

This provides the same list of `ProcessInfo`s as what's provided in `GetProcessInfos`, but additionally provides a list of associated `FrameInfo`s which are actively running (showing UI elements) in the renderer process. See `AssociatedFrameInfos` for more information.

```cpp
        CHECK_FAILURE(environmentExperimental11->GetProcessInfosWithDetails(
            Callback<ICoreWebView2ExperimentalGetProcessInfosWithDetailsCompletedHandler>(
                [this](HRESULT error, ICoreWebView2ProcessInfoCollection* processCollection)
                    -> HRESULT
                {
                    UINT32 processCount = 0;
                    UINT32 rendererProcessCount = 0;
                    CHECK_FAILURE(processCollection->get_Count(&processCount));
                    std::wstring result;
                    std::wstring otherProcessResult;
                    for (UINT32 i = 0; i < processCount; i++)
                    {
                        Microsoft::WRL::ComPtr<ICoreWebView2ProcessInfo> processInfo;
                        CHECK_FAILURE(processCollection->GetValueAtIndex(i, &processInfo));
                        COREWEBVIEW2_PROCESS_KIND kind;
                        CHECK_FAILURE(processInfo->get_Kind(&kind));
                        INT32 processId = 0;
                        CHECK_FAILURE(processInfo->get_ProcessId(&processId));
                        if (kind == COREWEBVIEW2_PROCESS_KIND_RENDERER)
                        {
                            std::wstring rendererProcessResult;
                            wil::com_ptr<ICoreWebView2ExperimentalProcessInfo>
                                processInfoExperimental;
                            CHECK_FAILURE(processInfo->QueryInterface(
                                IID_PPV_ARGS(&processInfoExperimental)));
                            wil::com_ptr<ICoreWebView2FrameInfoCollection> frameInfoCollection;
                            CHECK_FAILURE(processInfoExperimental->get_AssociatedFrameInfos(
                                &frameInfoCollection));
                            wil::com_ptr<ICoreWebView2FrameInfoCollectionIterator> iterator;
                            CHECK_FAILURE(frameInfoCollection->GetIterator(&iterator));
                            BOOL hasCurrent = FALSE;
                            UINT32 frameInfoCount = 0;
                            while (SUCCEEDED(iterator->get_HasCurrent(&hasCurrent)) &&
                                   hasCurrent)
                            {
                                wil::com_ptr<ICoreWebView2FrameInfo> frameInfo;
                                CHECK_FAILURE(iterator->GetCurrent(&frameInfo));

                                AppendFrameInfo(frameInfo, rendererProcessResult);
                                AppendAncestorFrameInfo(frameInfo, rendererProcessResult);

                                BOOL hasNext = FALSE;
                                CHECK_FAILURE(iterator->MoveNext(&hasNext));
                                frameInfoCount++;
                            }
                            rendererProcessResult.insert(
                                0, std::to_wstring(frameInfoCount) +
                                       L" frameInfo(s) found in Renderer Process ID:" +
                                       std::to_wstring(processId) + L"\n");
                            result.append(rendererProcessResult + L"\n");
                            rendererProcessCount++;
                        }
                        else
                        {
                            otherProcessResult.append(
                                L"Process Id:" + std::to_wstring(processId) +
                                L" | Process Kind:" + ProcessKindToString(kind) + L"\n");
                        }
                    }
                    result.insert(
                        0, std::to_wstring(processCount) + L" process(es) found, from which " +
                               std::to_wstring(rendererProcessCount) +
                               L" renderer process(es) found\n\n");
                    otherProcessResult.insert(
                        0, L"\nRemaining " +
                               std::to_wstring(processCount - rendererProcessCount) +
                               L" Process(es) Infos:\n");
                    result.append(otherProcessResult);
                    MessageBox(
                        nullptr, result.c_str(), L"Process Info with Associated Frames", MB_OK);
                    return S_OK;
                })
                .Get()));
```

