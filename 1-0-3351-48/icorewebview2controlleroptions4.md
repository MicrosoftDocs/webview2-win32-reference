---
description: Controller option used to allow user input pass through the browser and make them received in the host app process.
title: WebView2 Win32 C++ ICoreWebView2ControllerOptions4
ms.date: 06/23/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ControllerOptions4
topic_type: 
- APIRef
api_name:
- ICoreWebView2ControllerOptions4
- ICoreWebView2ControllerOptions4.get_AllowHostInputProcessing
- ICoreWebView2ControllerOptions4.put_AllowHostInputProcessing
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ControllerOptions4

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ControllerOptions4
  : public ICoreWebView2ControllerOptions3
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
WebView2 Win32 Prerelease |    1.0.3344

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
        wil::com_ptr<ICoreWebView2ControllerOptions4> webView2ControllerOptions4;
        if (SUCCEEDED(options->QueryInterface(IID_PPV_ARGS(&webView2ControllerOptions4))))
        {
            CHECK_FAILURE(webView2ControllerOptions4->put_AllowHostInputProcessing(TRUE));
        }
    }
```

