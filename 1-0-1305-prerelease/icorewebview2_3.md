---
description: A continuation of the ICoreWebView2_2 interface.
title: WebView2 Win32 C++ ICoreWebView2_3
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_3
---

# interface ICoreWebView2_3

```
interface ICoreWebView2_3
  : public ICoreWebView2_2
```

A continuation of the [ICoreWebView2_2](icorewebview2_2.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[ClearVirtualHostNameToFolderMapping](#clearvirtualhostnametofoldermapping) | Clears a host name mapping for local folder that was added by `SetVirtualHostNameToFolderMapping`.
[get_IsSuspended](#get_issuspended) | Whether WebView is suspended.
[Resume](#resume) | Resumes the WebView so that it resumes activities on the web page.
[SetVirtualHostNameToFolderMapping](#setvirtualhostnametofoldermapping) | Sets a mapping between a virtual host name and a folder path to make available to web sites via that host name.
[TrySuspend](#trysuspend) | An app may call the `TrySuspend` API to have the WebView2 consume less memory.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### ClearVirtualHostNameToFolderMapping

Clears a host name mapping for local folder that was added by `SetVirtualHostNameToFolderMapping`.

> public HRESULT [ClearVirtualHostNameToFolderMapping](#clearvirtualhostnametofoldermapping)(LPCWSTR hostName)

#### get_IsSuspended

Whether WebView is suspended.

> public HRESULT [get_IsSuspended](#get_issuspended)(BOOL * isSuspended)

`TRUE` when WebView is suspended, from the time when TrySuspend has completed successfully until WebView is resumed.

#### Resume

Resumes the WebView so that it resumes activities on the web page.

> public HRESULT [Resume](#resume)()

This API can be called while the WebView2 controller is invisible. The app can interact with the WebView immediately after `Resume`. WebView will be automatically resumed when it becomes visible.

```cpp
    if (message == WM_SIZE)
    {
        if (wParam == SIZE_MINIMIZED)
        {
            // Hide the webview when the app window is minimized.
            m_controller->put_IsVisible(FALSE);
            Suspend();
        }
        else if (wParam == SIZE_RESTORED)
        {
            // When the app window is restored, show the webview
            // (unless the user has toggle visibility off).
            if (m_isVisible)
            {
                Resume();
                m_controller->put_IsVisible(TRUE);
            }
        }
    }
```

```cpp
void ViewComponent::Resume()
{
    wil::com_ptr<ICoreWebView2_3> webView;
    webView = m_webView.try_query<ICoreWebView2_3>();
    if (!webView)
    {
        ShowFailure(E_NOINTERFACE, L"Resume API not available");
        return;
    }
    webView->Resume();
}
```

#### SetVirtualHostNameToFolderMapping

Sets a mapping between a virtual host name and a folder path to make available to web sites via that host name.

> public HRESULT [SetVirtualHostNameToFolderMapping](#setvirtualhostnametofoldermapping)(LPCWSTR hostName, LPCWSTR folderPath, [COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND](icorewebview2.md) accessKind)

After setting the mapping, documents loaded in the WebView can use HTTP or HTTPS URLs at the specified host name specified by hostName to access files in the local folder specified by folderPath.

This mapping applies to both top-level document and iframe navigations as well as subresource references from a document. This also applies to web workers including dedicated/shared worker and service worker, for loading either worker scripts or subresources (importScripts(), fetch(), XHR, etc.) issued from within a worker. For virtual host mapping to work with service worker, please keep the virtual host name mappings consistent among all WebViews sharing the same browser instance. As service worker works independently of WebViews, we merge mappings from all WebViews when resolving virtual host name, inconsistent mappings between WebViews would lead unexpected behavior.

Due to a current implementation limitation, media files accessed using virtual host name can be very slow to load. As the resource loaders for the current page might have already been created and running, changes to the mapping might not be applied to the current page and a reload of the page is needed to apply the new mapping.

Both absolute and relative paths are supported for folderPath. Relative paths are interpreted as relative to the folder where the exe of the app is in.

Note that the folderPath length must not exceed the Windows MAX_PATH limit.

accessKind specifies the level of access to resources under the virtual host from other sites.

For example, after calling 
```cpp
SetVirtualHostNameToFolderMapping(
    L"appassets.example", L"assets",
    COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY);
```
 navigating to `https://appassets.example/my-local-file.html` will show the content from my-local-file.html in the assets subfolder located on disk under the same path as the app's executable file.

DOM elements that want to reference local files will have their host reference virtual host in the source. If there are multiple folders being used, define one unique virtual host per folder. For example, you can embed a local image like this 
```cpp
WCHAR c_navString[] = L"<img src=\"http://appassets.example/wv2.png\"/>";
m_webView->NavigateToString(c_navString);
```
 The example above shows the image wv2.png by resolving the folder mapping above.

You should typically choose virtual host names that are never used by real sites. If you own a domain such as example.com, another option is to use a subdomain reserved for the app (like my-app.example.com).

[RFC 6761](https://tools.ietf.org/html/rfc6761) has reserved several special-use domain names that are guaranteed to not be used by real sites (for example, .example, .test, and .invalid.)

Note that using `.local` as the top-level domain name will work but can cause a delay during navigations. You should avoid using `.local` if you can.

Apps should use distinct domain names when mapping folder from different sources that should be isolated from each other. For instance, the app might use app-file.example for files that ship as part of the app, and book1.example might be used for files containing books from a less trusted source that were previously downloaded and saved to the disk by the app.

The host name used in the APIs is canonicalized using Chromium's host name parsing logic before being used internally. For more information see [HTML5 2.6 URLs](https://dev.w3.org/html5/spec-LC/urls.html).

All host names that are canonicalized to the same string are considered identical. For example, `EXAMPLE.COM` and `example.com` are treated as the same host name. An international host name and its Punycode-encoded host name are considered the same host name. There is no DNS resolution for host name and the trailing '.' is not normalized as part of canonicalization.

Therefore `example.com` and `example.com.` are treated as different host names. Similarly, `virtual-host-name` and `virtual-host-name.example.com` are treated as different host names even if the machine has a DNS suffix of `example.com`.

Specify the minimal cross-origin access necessary to run the app. If there is not a need to access local resources from other origins, use COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY.

```cpp
            // Setup host resource mapping for local files.
            m_webView3->SetVirtualHostNameToFolderMapping(
                L"appassets.example", L"assets",
                COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY_CORS);
```

```cpp
        const std::wstring localFileRootUrl = L"https://appassets.example/";
        return localFileRootUrl + regex_replace(relativePath, std::wregex(L"\\\\"), L"/");
```

#### TrySuspend

An app may call the `TrySuspend` API to have the WebView2 consume less memory.

> public HRESULT [TrySuspend](#trysuspend)([ICoreWebView2TrySuspendCompletedHandler](icorewebview2trysuspendcompletedhandler.md) * handler)

This is useful when a Win32 app becomes invisible, or when a Universal Windows Platform app is being suspended, during the suspended event handler before completing the suspended event. The CoreWebView2Controller's IsVisible property must be false when the API is called. Otherwise, the API fails with `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)`. Suspending is similar to putting a tab to sleep in the Edge browser. Suspending pauses WebView script timers and animations, minimizes CPU usage for the associated browser renderer process and allows the operating system to reuse the memory that was used by the renderer process for other processes. Note that Suspend is best effort and considered completed successfully once the request is sent to browser renderer process. If there is a running script, the script will continue to run and the renderer process will be suspended after that script is done. See [Sleeping Tabs FAQ](https://techcommunity.microsoft.com/t5/articles/sleeping-tabs-faq/m-p/1705434) for conditions that might prevent WebView from being suspended. In those situations, the completed handler will be invoked with isSuccessful as false and errorCode as S_OK. The WebView will be automatically resumed when it becomes visible. Therefore, the app normally does not have to call `Resume` explicitly. The app can call `Resume` and then `TrySuspend` periodically for an invisible WebView so that the invisible WebView can sync up with latest data and the page ready to show fresh content when it becomes visible. All WebView APIs can still be accessed when a WebView is suspended. Some APIs like Navigate will auto resume the WebView. To avoid unexpected auto resume, check `IsSuspended` property before calling APIs that might change WebView state.

```cpp
    if (message == WM_SIZE)
    {
        if (wParam == SIZE_MINIMIZED)
        {
            // Hide the webview when the app window is minimized.
            m_controller->put_IsVisible(FALSE);
            Suspend();
        }
        else if (wParam == SIZE_RESTORED)
        {
            // When the app window is restored, show the webview
            // (unless the user has toggle visibility off).
            if (m_isVisible)
            {
                Resume();
                m_controller->put_IsVisible(TRUE);
            }
        }
    }
```

```cpp
void ViewComponent::Suspend()
{
    wil::com_ptr<ICoreWebView2_3> webView;
    webView = m_webView.try_query<ICoreWebView2_3>();
    if (!webView)
    {
        ShowFailure(E_NOINTERFACE, L"TrySuspend API not available");
        return;
    }
    HRESULT hr = webView->TrySuspend(
        Callback<ICoreWebView2TrySuspendCompletedHandler>(
            [this](HRESULT errorCode, BOOL isSuccessful) -> HRESULT {
                if ((errorCode != S_OK) || !isSuccessful)
                {
                    std::wstringstream formattedMessage;
                    formattedMessage << "TrySuspend result (0x" << std::hex << errorCode
                                     << ") " << (isSuccessful ? "succeeded" : "failed");
                    m_appWindow->AsyncMessageBox(
                        std::move(formattedMessage.str()), L"TrySuspend result");
                }
                return S_OK;
            })
            .Get());
    if (FAILED(hr))
        ShowFailure(hr, L"Call to TryFreeze failed");
}
```

