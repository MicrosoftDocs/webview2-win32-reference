---
description: A continuation of the ICoreWebView2Environment interface for getting process with associated information.
title: WebView2 Win32 C++ ICoreWebView2Environment13
ms.date: 02/26/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment13
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment13
- ICoreWebView2Environment13.GetProcessExtendedInfos
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment13

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Environment13
  : public ICoreWebView2Environment12
```

A continuation of the [ICoreWebView2Environment](icorewebview2environment.md) interface for getting process with associated information.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetProcessExtendedInfos](#getprocessextendedinfos) | Gets a snapshot collection of `ProcessExtendedInfo`s corresponding to all currently running processes associated with this `CoreWebView2Environment` excludes crashpad process.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    

## Members

#### GetProcessExtendedInfos

Gets a snapshot collection of `ProcessExtendedInfo`s corresponding to all currently running processes associated with this `CoreWebView2Environment` excludes crashpad process.

> public HRESULT [GetProcessExtendedInfos](#getprocessextendedinfos)([ICoreWebView2GetProcessExtendedInfosCompletedHandler](icorewebview2getprocessextendedinfoscompletedhandler.md) * handler)

This provides the same list of `ProcessInfo`s as what's provided in `GetProcessInfos`, but additionally provides a list of associated `FrameInfo`s which are actively running (showing or hiding UI elements) in the renderer process. See `AssociatedFrameInfos` for more information.

```cpp
        CHECK_FAILURE(environment13->GetProcessExtendedInfos(
            Callback<ICoreWebView2GetProcessExtendedInfosCompletedHandler>(
                [this](
                    HRESULT error,
                    ICoreWebView2ProcessExtendedInfoCollection* processCollection) -> HRESULT
                {
                    UINT32 processCount = 0;
                    UINT32 rendererProcessCount = 0;
                    CHECK_FAILURE(processCollection->get_Count(&processCount));
                    std::wstringstream otherProcessInfos;
                    std::wstringstream rendererProcessInfos;
                    for (UINT32 i = 0; i < processCount; i++)
                    {
                        Microsoft::WRL::ComPtr<ICoreWebView2ProcessExtendedInfo>
                            processExtendedInfo;
                        CHECK_FAILURE(
                            processCollection->GetValueAtIndex(i, &processExtendedInfo));
                        Microsoft::WRL::ComPtr<ICoreWebView2ProcessInfo> processInfo;
                        CHECK_FAILURE(processExtendedInfo->get_ProcessInfo(&processInfo));
                        COREWEBVIEW2_PROCESS_KIND kind;
                        CHECK_FAILURE(processInfo->get_Kind(&kind));
                        INT32 processId = 0;
                        CHECK_FAILURE(processInfo->get_ProcessId(&processId));
                        if (kind == COREWEBVIEW2_PROCESS_KIND_RENDERER)
                        {
                            std::wstringstream rendererProcess;
                            wil::com_ptr<ICoreWebView2FrameInfoCollection> frameInfoCollection;
                            CHECK_FAILURE(processExtendedInfo->get_AssociatedFrameInfos(
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

                                AppendFrameInfo(frameInfo, rendererProcess);

                                BOOL hasNext = FALSE;
                                CHECK_FAILURE(iterator->MoveNext(&hasNext));
                                frameInfoCount++;
                            }
                            rendererProcessInfos
                                << frameInfoCount
                                << L" frameInfo(s) found in Renderer Process ID:" << processId
                                << L"\n"
                                << rendererProcess.str() << std::endl;
                            rendererProcessCount++;
                        }
                        else
                        {
                            otherProcessInfos << L"Process Id:" << processId
                                              << L" | Process Kind:"
                                              << ProcessKindToString(kind) << std::endl;
                        }
                    }
                    std::wstringstream message;
                    message << processCount << L" process(es) found, from which "
                            << rendererProcessCount << L" renderer process(es) found\n\n"
                            << rendererProcessInfos.str() << L"Remaining Process(es) Infos:\n"
                            << otherProcessInfos.str();

                    m_appWindow->AsyncMessageBox(
                        std::move(message.str()), L"Process Extended Info");
                    return S_OK;
                })
                .Get()));
```

