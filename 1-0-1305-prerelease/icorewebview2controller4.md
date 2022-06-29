---
description: This is the ICoreWebView2Controller4 interface.
title: WebView2 Win32 C++ ICoreWebView2Controller4
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Controller4
---

# interface ICoreWebView2Controller4

```
interface ICoreWebView2Controller4
  : public ICoreWebView2Controller3
```

This is the ICoreWebView2Controller4 interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AllowExternalDrop](#get_allowexternaldrop) | Gets the `AllowExternalDrop` property which is used to configure the capability that dragging objects from outside the bounds of webview2 and dropping into webview2 is allowed or disallowed.
[put_AllowExternalDrop](#put_allowexternaldrop) | Sets the `AllowExternalDrop` property which is used to configure the capability that dragging objects from outside the bounds of webview2 and dropping into webview2 is allowed or disallowed.

The ICoreWebView2Controller4 provides interface to enable/disable external drop.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_AllowExternalDrop

Gets the `AllowExternalDrop` property which is used to configure the capability that dragging objects from outside the bounds of webview2 and dropping into webview2 is allowed or disallowed.

> public HRESULT [get_AllowExternalDrop](#get_allowexternaldrop)(BOOL * value)

The default value is TRUE.

```cpp
            wil::com_ptr<ICoreWebView2Controller> controller =
                m_appWindow->GetWebViewController();
            wil::com_ptr<ICoreWebView2Controller4> controller4 =
                controller.try_query<ICoreWebView2Controller4>();
            if (controller4)
            {
                BOOL allowExternalDrop;
                CHECK_FAILURE(controller4->get_AllowExternalDrop(&allowExternalDrop));
                if (allowExternalDrop)
                {
                    CHECK_FAILURE(controller4->put_AllowExternalDrop(FALSE));
                    MessageBox(
                        nullptr, L"WebView disallows dropping files now.",
                        L"WebView AllowExternalDrop property changed", MB_OK);
                }
                else
                {
                    CHECK_FAILURE(controller4->put_AllowExternalDrop(TRUE));
                    MessageBox(
                        nullptr, L"WebView allows dropping files now.",
                        L"WebView AllowExternalDrop property changed", MB_OK);
                }
            }
```

#### put_AllowExternalDrop

Sets the `AllowExternalDrop` property which is used to configure the capability that dragging objects from outside the bounds of webview2 and dropping into webview2 is allowed or disallowed.

> public HRESULT [put_AllowExternalDrop](#put_allowexternaldrop)(BOOL value)

```cpp
            wil::com_ptr<ICoreWebView2Controller> controller =
                m_appWindow->GetWebViewController();
            wil::com_ptr<ICoreWebView2Controller4> controller4 =
                controller.try_query<ICoreWebView2Controller4>();
            if (controller4)
            {
                BOOL allowExternalDrop;
                CHECK_FAILURE(controller4->get_AllowExternalDrop(&allowExternalDrop));
                if (allowExternalDrop)
                {
                    CHECK_FAILURE(controller4->put_AllowExternalDrop(FALSE));
                    MessageBox(
                        nullptr, L"WebView disallows dropping files now.",
                        L"WebView AllowExternalDrop property changed", MB_OK);
                }
                else
                {
                    CHECK_FAILURE(controller4->put_AllowExternalDrop(TRUE));
                    MessageBox(
                        nullptr, L"WebView allows dropping files now.",
                        L"WebView AllowExternalDrop property changed", MB_OK);
                }
            }
```

