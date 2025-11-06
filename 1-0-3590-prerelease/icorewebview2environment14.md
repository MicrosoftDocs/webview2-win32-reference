---
description: This is ICoreWebView2Environment14 that exposes new methods to create Filesystem access related DOM objects.
title: WebView2 Win32 C++ ICoreWebView2Environment14
ms.date: 10/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment14
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment14
- ICoreWebView2Environment14.CreateObjectCollection
- ICoreWebView2Environment14.CreateWebFileSystemDirectoryHandle
- ICoreWebView2Environment14.CreateWebFileSystemFileHandle
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment14

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Environment14
  : public ICoreWebView2Environment13
```

This is ICoreWebView2Environment14 that exposes new methods to create Filesystem access related DOM objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateObjectCollection](#createobjectcollection) | Create a generic object collection.
[CreateWebFileSystemDirectoryHandle](#createwebfilesystemdirectoryhandle) | Create a [ICoreWebView2FileSystemHandle](icorewebview2filesystemhandle.md#icorewebview2filesystemhandle) object from a path that represents a Web [FileSystemDirectoryHandle](https://developer.mozilla.org/docs/Web/API/FileSystemDirectoryHandle).
[CreateWebFileSystemFileHandle](#createwebfilesystemfilehandle) | Create a [ICoreWebView2FileSystemHandle](icorewebview2filesystemhandle.md#icorewebview2filesystemhandle) object from a path that represents a Web [FileSystemFileHandle](https://developer.mozilla.org/docs/Web/API/FileSystemFileHandle).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2651.64
WebView2 Win32 Prerelease |    1.0.2646

## Members

#### CreateObjectCollection

Create a generic object collection.

> public HRESULT [CreateObjectCollection](#createobjectcollection)(UINT32 length, IUnknown ** items, [ICoreWebView2ObjectCollection](icorewebview2objectcollection.md#icorewebview2objectcollection) ** objectCollection)

#### CreateWebFileSystemDirectoryHandle

Create a [ICoreWebView2FileSystemHandle](icorewebview2filesystemhandle.md#icorewebview2filesystemhandle) object from a path that represents a Web [FileSystemDirectoryHandle](https://developer.mozilla.org/docs/Web/API/FileSystemDirectoryHandle).

> public HRESULT [CreateWebFileSystemDirectoryHandle](#createwebfilesystemdirectoryhandle)(LPCWSTR path, COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION permission, [ICoreWebView2FileSystemHandle](icorewebview2filesystemhandle.md#icorewebview2filesystemhandle) ** value)

The `path` is the path pointed by the directory and must be a syntactically correct fully qualified path, but it is not checked here whether it currently points to a directory. Any other state validation will be done when this handle is accessed from web content and will cause DOM exceptions if access operations fail. If an invalid path is passed, an E_INVALIDARG will be returned and the object will fail to create.

`Permission` property is used to specify whether the Handle should be created with a Read-only or Read-and-write web permission. For the `permission` value specified here, the Web [PermissionStatus](https://developer.mozilla.org/docs/Web/API/PermissionStatus) will be [granted](https://developer.mozilla.org/docs/Web/API/PermissionStatus/state) and the unspecified permission will be [prompt](https://developer.mozilla.org/docs/Web/API/PermissionStatus/state). Therefore, the web content then does not need to call [requestPermission](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/requestPermission) for the permission that was specified before attempting the permitted operation, but if it does, the promise will immediately be resolved with 'granted' PermissionStatus without firing the WebView2 [PermissionRequested](/microsoft-edge/webview2/reference/win32/icorewebview2permissionrequestedeventargs) event or prompting the user for permission. Otherwise, `requestPermission` will behave as the status of permission is currently `Prompt`, which means the `PermissionRequested` event will fire or the user will be prompted. Additionally, the app must have the same OS permissions that have propagated to the [WebView2 browser process](/microsoft-edge/webview2/concepts/process-model) for the path it wishes to give the web content to make any operations on the directory. Specifically, the WebView2 browser process will run in same user, package identity, and app container of the app, but other means such as security context impersonations do not get propagated, so such permissions that the app has, will not be effective in WebView2. Note: An exception to this is, if there is a parent directory handle that has broader permissions in the same page context than specified in here, the handle will automatically inherit the most permissive permission of the parent handle when posted to that page context. i.e. If there is already a `FileSystemDirectoryHandle` to `C:\example` that has write permission on a page, even though a WebFileSystemHandle to directory `C:\example\directory` is created with `COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION_READ_ONLY` permission, when posted to that page, write permission will be automatically granted to the created handle.

An app needs to be mindful that this object, when posted to the web content, provides it with unusual access to OS file system via the Web FileSystem API! The app should therefore only post objects for paths that it wants to allow access to the web content and it is not recommended that the web content "asks" for this path. The app should also check the source property of the target to ensure that it is sending to the web content of intended origin.

Once the object is passed to web content, the path must point to a directory as if it was chosen via [directory picker](https://developer.mozilla.org/docs/Web/API/Window/showDirectoryPicker) otherwise any IO operation done on the `FileSystemDirectoryHandle` will throw a DOM exception.

#### CreateWebFileSystemFileHandle

Create a [ICoreWebView2FileSystemHandle](icorewebview2filesystemhandle.md#icorewebview2filesystemhandle) object from a path that represents a Web [FileSystemFileHandle](https://developer.mozilla.org/docs/Web/API/FileSystemFileHandle).

> public HRESULT [CreateWebFileSystemFileHandle](#createwebfilesystemfilehandle)(LPCWSTR path, COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION permission, [ICoreWebView2FileSystemHandle](icorewebview2filesystemhandle.md#icorewebview2filesystemhandle) ** value)

The `path` is the path pointed by the file and must be a syntactically correct fully qualified path, but it is not checked here whether it currently points to a file. If an invalid path is passed, an E_INVALIDARG will be returned and the object will fail to create. Any other state validation will be done when this handle is accessed from web content and will cause the DOM exceptions described in [FileSystemFileHandle methods](https://developer.mozilla.org/docs/Web/API/FileSystemDirectoryHandle#instance_methods) if access operations fail.

`Permission` property is used to specify whether the Handle should be created with a Read-only or Read-and-write web permission. For the `permission` value specified here, the DOM [PermissionStatus](https://developer.mozilla.org/docs/Web/API/PermissionStatus) property will be [granted](https://developer.mozilla.org/docs/Web/API/PermissionStatus/state) and the unspecified permission will be [prompt](https://developer.mozilla.org/docs/Web/API/PermissionStatus/state). Therefore, the web content then does not need to call [requestPermission](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/requestPermission) for the permission that was specified before attempting the permitted operation, but if it does, the promise will immediately be resolved with 'granted' PermissionStatus without firing the WebView2 [PermissionRequested](/microsoft-edge/webview2/reference/win32/icorewebview2permissionrequestedeventargs) event or prompting the user for permission. Otherwise, `requestPermission` will behave as the status of permission is currently `prompt`, which means the `PermissionRequested` event will fire or the user will be prompted. Additionally, the app must have the same OS permissions that have propagated to the [WebView2 browser process](/microsoft-edge/webview2/concepts/process-model) for the path it wishes to give the web content to read/write the file. Specifically, the WebView2 browser process will run in same user, package identity, and app container of the app, but other means such as security context impersonations do not get propagated, so such permissions that the app has, will not be effective in WebView2. Note: An exception to this is, if there is a parent directory handle that has broader permissions in the same page context than specified in here, the handle will automatically inherit the most permissive permission of the parent handle when posted to that page context. i.e. If there is already a `FileSystemDirectoryHandle` to `C:\example` that has write permission on a page, even though a WebFileSystemHandle to file `C:\example\file.txt` is created with `COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION_READ_ONLY` permission, when posted to that page, write permission will be automatically granted to the created handle.

An app needs to be mindful that this object, when posted to the web content, provides it with unusual access to OS file system via the Web FileSystem API! The app should therefore only post objects for paths that it wants to allow access to the web content and it is not recommended that the web content "asks" for this path. The app should also check the source property of the target to ensure that it is sending to the web content of intended origin.

Once the object is passed to web content, if the content is attempting a read, the file must be existing and available to read similar to a file chosen by [open file picker](https://developer.mozilla.org/docs/Web/API/Window/showOpenFilePicker), otherwise the read operation will [throw a DOM exception](https://developer.mozilla.org/docs/Web/API/FileSystemFileHandle/getFile#exceptions). For write operations, the file does not need to exist as `FileSystemFileHandle` will behave as a file path chosen by [save file picker](https://developer.mozilla.org/docs/Web/API/Window/showSaveFilePicker) and will create or overwrite the file, but the parent directory structure pointed by the file must exist and an existing file must be available to write and delete or the write operation will [throw a DOM exception](https://developer.mozilla.org/docs/Web/API/FileSystemFileHandle/createWritable#exceptions).

