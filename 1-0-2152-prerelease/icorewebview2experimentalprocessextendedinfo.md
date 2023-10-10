---
description: This is the ICoreWebView2ExperimentalProcessExtendedInfo interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProcessExtendedInfo
ms.date: 10/10/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProcessExtendedInfo
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProcessExtendedInfo
- ICoreWebView2ExperimentalProcessExtendedInfo.get_AssociatedFrameInfos
- ICoreWebView2ExperimentalProcessExtendedInfo.get_ProcessInfo
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProcessExtendedInfo

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProcessExtendedInfo
  : public IUnknown
```

This is the ICoreWebView2ExperimentalProcessExtendedInfo interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AssociatedFrameInfos](#get_associatedframeinfos) | The collection of associated `FrameInfo`s which are actively running (showing or hiding UI elements) in this renderer process.
[get_ProcessInfo](#get_processinfo) | The process info of the current process.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2106

## Members

#### get_AssociatedFrameInfos

The collection of associated `FrameInfo`s which are actively running (showing or hiding UI elements) in this renderer process.

> public HRESULT [get_AssociatedFrameInfos](#get_associatedframeinfos)([ICoreWebView2FrameInfoCollection](icorewebview2frameinfocollection.md) ** frames)

`AssociatedFrameInfos` will only be populated when this `CoreWebView2ProcessExtendedInfo` corresponds to a renderer process. Non-renderer processes will always have an empty `AssociatedFrameInfos`. The `AssociatedFrameInfos` may also be empty for renderer processes that have no active frames.

```cpp
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
```

#### get_ProcessInfo

The process info of the current process.

> public HRESULT [get_ProcessInfo](#get_processinfo)([ICoreWebView2ProcessInfo](icorewebview2processinfo.md) ** processInfo)

