---
description: Provides process with associated extended information in the ICoreWebView2Environment.
title: WebView2 Win32 C++ ICoreWebView2ProcessExtendedInfo
ms.date: 04/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessExtendedInfo
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProcessExtendedInfo
- ICoreWebView2ProcessExtendedInfo.get_AssociatedFrameInfos
- ICoreWebView2ProcessExtendedInfo.get_ProcessInfo
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProcessExtendedInfo

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ProcessExtendedInfo
  : public IUnknown
```

Provides process with associated extended information in the [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AssociatedFrameInfos](#get_associatedframeinfos) | The collection of associated `FrameInfo`s which are actively running (showing or hiding UI elements) in this renderer process.
[get_ProcessInfo](#get_processinfo) | The process info of the current process.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### get_AssociatedFrameInfos

The collection of associated `FrameInfo`s which are actively running (showing or hiding UI elements) in this renderer process.

> public HRESULT [get_AssociatedFrameInfos](#get_associatedframeinfos)([ICoreWebView2FrameInfoCollection](icorewebview2frameinfocollection.md#icorewebview2frameinfocollection) ** frames)

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

> public HRESULT [get_ProcessInfo](#get_processinfo)([ICoreWebView2ProcessInfo](icorewebview2processinfo.md#icorewebview2processinfo) ** processInfo)

