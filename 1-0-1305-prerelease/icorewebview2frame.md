---
description: WebView2Frame provides direct access to the iframes information.
title: WebView2 Win32 C++ ICoreWebView2Frame
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Frame
---

# interface ICoreWebView2Frame

```
interface ICoreWebView2Frame
  : public IUnknown
```

WebView2Frame provides direct access to the iframes information.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_Destroyed](#add_destroyed) | The Destroyed event is raised when the iframe corresponding to this CoreWebView2Frame object is removed or the document containing that iframe is destroyed.
[add_NameChanged](#add_namechanged) | Raised when the iframe changes its window.name property.
[AddHostObjectToScriptWithOrigins](#addhostobjecttoscriptwithorigins) | Add the provided host object to script running in the iframe with the specified name for the list of the specified origins.
[get_Name](#get_name) | The name of the iframe from the iframe html tag declaring it.
[IsDestroyed](#isdestroyed) | Check whether a frame is destroyed.
[remove_Destroyed](#remove_destroyed) | Remove an event handler previously added with add_Destroyed.
[remove_NameChanged](#remove_namechanged) | Remove an event handler previously added with add_NameChanged.
[RemoveHostObjectFromScript](#removehostobjectfromscript) | Remove the host object specified by the name so that it is no longer accessible from JavaScript code in the iframe.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### add_Destroyed

The Destroyed event is raised when the iframe corresponding to this CoreWebView2Frame object is removed or the document containing that iframe is destroyed.

> public HRESULT [add_Destroyed](#add_destroyed)([ICoreWebView2FrameDestroyedEventHandler](icorewebview2framedestroyedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_NameChanged

Raised when the iframe changes its window.name property.

> public HRESULT [add_NameChanged](#add_namechanged)([ICoreWebView2FrameNameChangedEventHandler](icorewebview2framenamechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### AddHostObjectToScriptWithOrigins

Add the provided host object to script running in the iframe with the specified name for the list of the specified origins.

> public HRESULT [AddHostObjectToScriptWithOrigins](#addhostobjecttoscriptwithorigins)(LPCWSTR name, VARIANT * object, UINT32 originsCount, LPCWSTR * origins)

The host object will be accessible for this iframe only if the iframe's origin during access matches one of the origins which are passed. The provided origins will be normalized before comparing to the origin of the document. So the scheme name is made lower case, the host will be punycode decoded as appropriate, default port values will be removed, and so on. This means the origin's host may be punycode encoded or not and will match regardless. If list contains malformed origin the call will fail. The method can be called multiple times in a row without calling RemoveHostObjectFromScript for the same object name. It will replace the previous object with the new object and new list of origins. List of origins will be treated as following:

1. empty list - call will succeed and object will be added for the iframe but it will not be exposed to any origin;

1. list with origins - during access to host object from iframe the origin will be checked that it belongs to this list;

1. list with "*" element - host object will be available for iframe for all origins. We suggest not to use this feature without understanding security implications of giving access to host object from from iframes with unknown origins. Calling this method fails if it is called after the iframe is destroyed. 
```cpp
                wil::unique_variant remoteObjectAsVariant;
                // It will throw if m_hostObject fails the QI, but because it is our object
                // it should always succeed.
                m_hostObject.query_to<IDispatch>(&remoteObjectAsVariant.pdispVal);
                remoteObjectAsVariant.vt = VT_DISPATCH;

                // Create list of origins which will be checked.
                // iframe will have access to host object only if its origin belongs
                // to this list.
                LPCWSTR origin = L"https://appassets.example/";

                CHECK_FAILURE(webviewFrame->AddHostObjectToScriptWithOrigins(
                    L"sample", &remoteObjectAsVariant, 1, &origin));
```
 For more information about host objects navigate to [ICoreWebView2::AddHostObjectToScript](icorewebview2.md).

#### get_Name

The name of the iframe from the iframe html tag declaring it.

> public HRESULT [get_Name](#get_name)(LPWSTR * name)

You can access this property even if the iframe is destroyed.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### IsDestroyed

Check whether a frame is destroyed.

> public HRESULT [IsDestroyed](#isdestroyed)(BOOL * destroyed)

Returns true during the Destroyed event.

#### remove_Destroyed

Remove an event handler previously added with add_Destroyed.

> public HRESULT [remove_Destroyed](#remove_destroyed)(EventRegistrationToken token)

#### remove_NameChanged

Remove an event handler previously added with add_NameChanged.

> public HRESULT [remove_NameChanged](#remove_namechanged)(EventRegistrationToken token)

#### RemoveHostObjectFromScript

Remove the host object specified by the name so that it is no longer accessible from JavaScript code in the iframe.

> public HRESULT [RemoveHostObjectFromScript](#removehostobjectfromscript)(LPCWSTR name)

While new access attempts are denied, if the object is already obtained by JavaScript code in the iframe, the JavaScript code continues to have access to that object. Calling this method for a name that is already removed or was never added fails. If the iframe is destroyed this method will return fail also.

