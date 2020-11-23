---
description: The ICoreWebView2 Experimental interface to manage mappings between virtual host names and folder paths.
title: WebView2 Win32 C++ ICoreWebView2Experimental2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental2
---

# interface ICoreWebView2Experimental2 

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental2
  : public IUnknown
```

The ICoreWebView2 Experimental interface to manage mappings between virtual host names and folder paths.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[ClearVirtualHostNameToFolderMapping](#clearvirtualhostnametofoldermapping) | Clear a host name mapping for local folder that was added by SetVirtualHostNameToFolderMapping.
[SetVirtualHostNameToFolderMapping](#setvirtualhostnametofoldermapping) | Set a mapping between a virtual host name and a folder path to make available to web sites via that host name.

## Members

#### ClearVirtualHostNameToFolderMapping 

Clear a host name mapping for local folder that was added by SetVirtualHostNameToFolderMapping.

> public HRESULT [ClearVirtualHostNameToFolderMapping](#clearvirtualhostnametofoldermapping)(LPCWSTR hostName)

#### SetVirtualHostNameToFolderMapping 

Set a mapping between a virtual host name and a folder path to make available to web sites via that host name.

> public HRESULT [SetVirtualHostNameToFolderMapping](#setvirtualhostnametofoldermapping)(LPCWSTR hostName, LPCWSTR folderPath, COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND accessKind)

After setting the mapping, documents loaded in the WebView can use HTTP or HTTPS URLs at the specified host name specified by hostName to access files in the local folder specified by folderPath.

This mapping applies to both top-level document and iframe navigations as well as subresource references from a document. This also applies to dedicated and shared worker scripts but does not apply to service worker scripts.

Both absolute and relative paths are supported for folderPath. Relative paths are interpreted as relative to the folder where the exe of the app is in.

accessKind specifies the level of access to resources under the virtual host from other sites.

For example, after calling 
```cpp
SetVirtualHostNameToFolderMapping(
    L"appassets.example", L"assets",
    COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY);
```
 navigating to `[https://appassets.example/my-local-file.html](https://appassets.example/my-local-file.html)` will show content from my-local-file.html in the assets subfolder located on disk under the same path as the app's executable file.

You should typically choose virtual host names that are never used by real sites. If you own a domain such as example.com, another option is to use a subdomain reserved for the app (like my-app.example.com).

[RFC 6761](https://tools.ietf.org/html/rfc6761) has reserved several special-use domain names that are guaranteed to not be used by real sites (for example, .example, .test, and .invalid.)

Apps should use distinct domain names when mapping folder from different sources that should be isolated from each other. For instance, the app might use app-file.example for files that ship as part of the app, and book1.example might be used for files containing books from a less trusted source that were previously downloaded and saved to the disk by the app.

The host name used in the APIs is canonicalized using Chromium's host name parsing logic before being used internally.

All host names that are canonicalized to the same string are considered identical. For example, `EXAMPLE.COM` and `example.com` are treated as the same host name. An international host name and its Punycode-encoded host name are considered the same host name. There is no DNS resolution for host name and the trailing '.' is not normalized as part of canonicalization.

Therefore `example.com` and `example.com.` are treated as different host names. Similarly, `virtual-host-name` and `virtual-host-name.example.com` are treated as different host names even if the machine has a DNS suffix of `example.com`.

Specify the minimal cross-origin access necessary to run the app. If there is not a need to access local resources from other origins, use COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY.

```cpp
        // Setup host resource mapping for local files.
        webview2->SetVirtualHostNameToFolderMapping(
            L"appassets.example", L"assets", COREWEBVIEW2_HOST_RESOURCE_ACCESS_KIND_DENY_CORS);
```

```cpp
    const std::wstring localFileRootUrl = L"https://appassets.example/";
    return localFileRootUrl + regex_replace(relativePath, std::wregex(L"\\\\"), L"/");
```

