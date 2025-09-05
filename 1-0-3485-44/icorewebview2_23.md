---
description: This is the ICoreWebView_23 interface for PostWebMessageAsJsonWithAdditionalObjects.
title: WebView2 Win32 C++ ICoreWebView2_23
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_23
topic_type: 
- APIRef
api_name:
- ICoreWebView2_23
- ICoreWebView2_23.PostWebMessageAsJsonWithAdditionalObjects
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_23

```
interface ICoreWebView2_23
  : public ICoreWebView2_22
```

This is the ICoreWebView_23 interface for PostWebMessageAsJsonWithAdditionalObjects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[PostWebMessageAsJsonWithAdditionalObjects](#postwebmessageasjsonwithadditionalobjects) | Same as `PostWebMessageAsJson`, but also has support for posting DOM objects to page content.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2651.64
WebView2 Win32 Prerelease |    1.0.2646

## Members

#### PostWebMessageAsJsonWithAdditionalObjects

Same as `PostWebMessageAsJson`, but also has support for posting DOM objects to page content.

> public HRESULT [PostWebMessageAsJsonWithAdditionalObjects](#postwebmessageasjsonwithadditionalobjects)(LPCWSTR webMessageAsJson, [ICoreWebView2ObjectCollectionView](icorewebview2objectcollectionview.md#icorewebview2objectcollectionview) * additionalObjects)

The `additionalObjects` property in the DOM MessageEvent fired on the page content is an array-like list of DOM objects that can be posted to the web content. Currently these can be the following types of objects:

Win32   |DOM type
--------- | ---------
[ICoreWebView2FileSystemHandle](icorewebview2filesystemhandle.md#icorewebview2filesystemhandle)|[FileSystemHandle](https://developer.mozilla.org/docs/Web/API/FileSystemHandle)
nullptr   |null
The objects are posted to the web content, following the [structured-clone](https://developer.mozilla.org/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) semantics, meaning only objects that can be cloned can be posted. They will also behave as if they had been created by the web content they are posted to. For example, if a FileSystemFileHandle is posted to a web content it can only be re-transferred via postMessage to other web content [with the same origin](https://fs.spec.whatwg.org/#filesystemhandle). Warning: An app needs to be mindful when using this API to post DOM objects as this API provides the web content with unusual access to sensitive Web Platform features such as filesystem access! Similar to PostWebMessageAsJson the app should check the `Source` property of WebView2 right before posting the message to ensure the message and objects will only be sent to the target web content that it expects to receive the DOM objects. Additionally, the order of messages that are posted between `PostWebMessageAsJson` and `PostWebMessageAsJsonWithAdditionalObjects` may not be preserved. 
```cpp
ScenarioFileSystemHandleShare::ScenarioFileSystemHandleShare(AppWindow* appWindow)
    : m_appWindow(appWindow)
{
    m_webView = m_appWindow->GetWebView();

    CHECK_FAILURE(m_webView->Navigate(m_appWindow->GetLocalUri(c_samplePath).c_str()));

    CHECK_FAILURE(m_webView->add_NavigationCompleted(
        Callback<ICoreWebView2NavigationCompletedEventHandler>(
            [this, appWindow](
                ICoreWebView2* sender,
                ICoreWebView2NavigationCompletedEventArgs* args) -> HRESULT
            {
                wil::com_ptr<ICoreWebView2_23> webview23 =
                    m_webView.try_query<ICoreWebView2_23>();
                CHECK_FEATURE_RETURN_HRESULT(webview23);
                wil::com_ptr<ICoreWebView2Environment> environment =
                    appWindow->GetWebViewEnvironment();
                wil::com_ptr<ICoreWebView2Environment14>
                    environment14 =
                        environment.try_query<ICoreWebView2Environment14>();
                CHECK_FEATURE_RETURN_HRESULT(environment14);
                wil::com_ptr<ICoreWebView2FileSystemHandle> rootHandle;
                CHECK_FAILURE(environment14->CreateWebFileSystemDirectoryHandle(
                    L"C:\\", COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION_READ_ONLY,
                    &rootHandle));
                wil::com_ptr<ICoreWebView2ObjectCollection> webObjectCollection;
                IUnknown* webObjects[] = {rootHandle.get()};
                CHECK_FAILURE(environment14->CreateObjectCollection(
                    ARRAYSIZE(webObjects), webObjects, &webObjectCollection));
                wil::unique_cotaskmem_string source;
                CHECK_FAILURE(m_webView->get_Source(&source));

                static const wchar_t* expectedDomain = L"appassets.example";
                wil::unique_bstr sourceDomain = GetDomainOfUri(source.get());

                // Check the source to ensure the message is sent to the correct target content.
                if (std::wstring(expectedDomain) == sourceDomain.get())
                {
                    CHECK_FAILURE(webview23->PostWebMessageAsJsonWithAdditionalObjects(
                        L"{ \"messageType\" : \"RootDirectoryHandle\" }",
                        webObjectCollection.get()));
                }

                return S_OK;
            })
            .Get(),
        &m_navigationCompletedToken));
}
```

