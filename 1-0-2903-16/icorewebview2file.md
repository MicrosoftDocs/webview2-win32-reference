---
description: Representation of a DOM File object passed via WebMessage.
title: WebView2 Win32 C++ ICoreWebView2File
ms.date: 10/29/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2File
topic_type: 
- APIRef
api_name:
- ICoreWebView2File
- ICoreWebView2File.get_Path
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2File

```
interface ICoreWebView2File
  : public IUnknown
```

Representation of a DOM [File](https://developer.mozilla.org/docs/Web/API/File) object passed via WebMessage.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Path](#get_path) | Get the absolute file path.

You can use this object to obtain the path of a File dropped on WebView2. 
```cpp
    CHECK_FAILURE(m_webView->add_WebMessageReceived(
        Callback<ICoreWebView2WebMessageReceivedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2WebMessageReceivedEventArgs* args)
            {
                wil::com_ptr<ICoreWebView2WebMessageReceivedEventArgs2> args2 =
                    wil::com_ptr<ICoreWebView2WebMessageReceivedEventArgs>(args)
                        .query<ICoreWebView2WebMessageReceivedEventArgs2>();
                wil::com_ptr<ICoreWebView2ObjectCollectionView> objectsCollection;
                args2->get_AdditionalObjects(&objectsCollection);
                unsigned int length;
                objectsCollection->get_Count(&length);

                // Array of file paths to be sent back to the webview as JSON
                std::wstring pathObjects = L"[";
                for (unsigned int i = 0; i < length; i++)
                {
                    wil::com_ptr<IUnknown> object;
                    objectsCollection->GetValueAtIndex(i, &object);

                    wil::com_ptr<ICoreWebView2File> file = object.query<ICoreWebView2File>();
                    if (file)
                    {
                        // Add the file to message to be sent back to webview
                        wil::unique_cotaskmem_string path;
                        file->get_Path(&path);
                        std::wstring pathObject =
                            L"{\"path\":\"" + std::wstring(path.get()) + L"\"}";
                        // Escape backslashes
                        std::wstring pathObjectEscaped;
                        for (const auto& c : pathObject)
                        {
                            if (c == L'\\')
                            {
                                pathObjectEscaped += L"\\\\";
                            }
                            else
                            {
                                pathObjectEscaped += c;
                            }
                        }
                        pathObjects += pathObjectEscaped;

                        if (i < length - 1)
                        {
                            pathObjects += L",";
                        }
                    }
                }
                pathObjects += L"]";

                // Post the message back to the webview so path is accessible to content
                m_webView->PostWebMessageAsJson(pathObjects.c_str());

                return S_OK;
            })
            .Get(),
        &m_webMessageReceivedToken));
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1774.30
WebView2 Win32 Prerelease |    1.0.1777

## Members

#### get_Path

Get the absolute file path.

> public HRESULT [get_Path](#get_path)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

