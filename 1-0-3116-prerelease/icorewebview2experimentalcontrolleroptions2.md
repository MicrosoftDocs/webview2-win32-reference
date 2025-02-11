---
description: Controller option used to allow user input pass through the browser and make them received in the host app process.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalControllerOptions2
ms.date: 02/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalControllerOptions2
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalControllerOptions2
- ICoreWebView2ExperimentalControllerOptions2.get_AllowHostInputProcessing
- ICoreWebView2ExperimentalControllerOptions2.put_AllowHostInputProcessing
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalControllerOptions2

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalControllerOptions2
  : public IUnknown
```

Controller option used to allow user input pass through the browser and make them received in the host app process.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AllowHostInputProcessing](#get_allowhostinputprocessing) | Gets the `AllowHostInputProcessing` property.
[put_AllowHostInputProcessing](#put_allowhostinputprocessing) | `AllowHostInputProcessing` property is to enable/disable input passing through the app before being delivered to the WebView2.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2415

## Members

#### get_AllowHostInputProcessing

Gets the `AllowHostInputProcessing` property.

> public HRESULT [get_AllowHostInputProcessing](#get_allowhostinputprocessing)(BOOL * value)

#### put_AllowHostInputProcessing

`AllowHostInputProcessing` property is to enable/disable input passing through the app before being delivered to the WebView2.

> public HRESULT [put_AllowHostInputProcessing](#put_allowhostinputprocessing)(BOOL value)

This property is only applicable to controllers created with `CoreWebView2Environment.CreateCoreWebView2ControllerAsync` and not composition controllers created with `CoreWebView2Environment.CreateCoreWebView2CompositionControllerAsync`. By default the value is `FALSE`. Setting this property has no effect when using visual hosting. 
```cpp
    if (m_creationModeId == IDM_CREATION_MODE_HOST_INPUT_PROCESSING)
    {
        wil::com_ptr<ICoreWebView2ExperimentalControllerOptions2>
            webView2ExperimentalControllerOptions2;
        if (SUCCEEDED(
                options->QueryInterface(IID_PPV_ARGS(&webView2ExperimentalControllerOptions2))))
        {
            CHECK_FAILURE(
                webView2ExperimentalControllerOptions2->put_AllowHostInputProcessing(TRUE));
        }
    }
```

