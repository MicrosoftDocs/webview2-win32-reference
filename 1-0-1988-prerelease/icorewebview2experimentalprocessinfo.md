---
description: This is the ICoreWebView2ExperimentalProcessInfo interface that provides the collection of `FrameInfo`s running in that process.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProcessInfo
ms.date: 07/19/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProcessInfo
---

# interface ICoreWebView2ExperimentalProcessInfo

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProcessInfo
  : public IUnknown
```

This is the ICoreWebView2ExperimentalProcessInfo interface that provides the collection of `FrameInfo`s running in that process.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AssociatedFrameInfos](#get_associatedframeinfos) | The collection of associated `FrameInfo`s which are actively running (showing UI elements) in this renderer process.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### get_AssociatedFrameInfos

The collection of associated `FrameInfo`s which are actively running (showing UI elements) in this renderer process.

> public HRESULT [get_AssociatedFrameInfos](#get_associatedframeinfos)([ICoreWebView2FrameInfoCollection](icorewebview2frameinfocollection.md) ** frames)

`AssociatedFrameInfos` will only be populated when obtained via calling `CoreWebView2Environment.GetProcessInfosWithDetails` and when this `CoreWebView2ProcessInfo` corresponds to a renderer process. `CoreWebView2ProcessInfo` objects obtained via `CoreWebView2Environment .GetProcessInfos` or for non-renderer processes will always have an empty `AssociatedFrameInfos`. The `AssociatedFrameInfos` may also be empty for renderer processes that have no active frames.

```cpp
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
```

