---
description: Interface defining the find options.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFindOptions
ms.date: 01/16/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFindOptions
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFindOptions
- ICoreWebView2ExperimentalFindOptions.get_FindTerm
- ICoreWebView2ExperimentalFindOptions.get_IsCaseSensitive
- ICoreWebView2ExperimentalFindOptions.get_ShouldHighlightAllMatches
- ICoreWebView2ExperimentalFindOptions.get_ShouldMatchWord
- ICoreWebView2ExperimentalFindOptions.get_SuppressDefaultFindDialog
- ICoreWebView2ExperimentalFindOptions.put_FindTerm
- ICoreWebView2ExperimentalFindOptions.put_IsCaseSensitive
- ICoreWebView2ExperimentalFindOptions.put_ShouldHighlightAllMatches
- ICoreWebView2ExperimentalFindOptions.put_ShouldMatchWord
- ICoreWebView2ExperimentalFindOptions.put_SuppressDefaultFindDialog
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFindOptions

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFindOptions
  : public IUnknown
```

Interface defining the find options.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FindTerm](#get_findterm) | Gets the `FindTerm` property.
[get_IsCaseSensitive](#get_iscasesensitive) | Gets the `IsCaseSensitive` property.
[get_ShouldHighlightAllMatches](#get_shouldhighlightallmatches) | Gets the `ShouldHighlightAllMatches` property.
[get_ShouldMatchWord](#get_shouldmatchword) | Gets the `ShouldMatchWord` property.
[get_SuppressDefaultFindDialog](#get_suppressdefaultfinddialog) | Gets the `SuppressDefaultFindDialog` property.
[put_FindTerm](#put_findterm) | Gets or sets the word or phrase to be searched in the current page.
[put_IsCaseSensitive](#put_iscasesensitive) | Determines if the find session is case sensitive.
[put_ShouldHighlightAllMatches](#put_shouldhighlightallmatches) | Gets or sets the state of whether all matches are highlighted.
[put_ShouldMatchWord](#put_shouldmatchword) | Similar to case sensitivity, word matching also can vary by locale, which may be influenced by both the browser's UI locale and the document's language settings.
[put_SuppressDefaultFindDialog](#put_suppressdefaultfinddialog) | Sets this property to hide the default Find UI.

This interface provides the necessary methods and properties to configure a find session.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_FindTerm

Gets the `FindTerm` property.

> public HRESULT [get_FindTerm](#get_findterm)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_IsCaseSensitive

Gets the `IsCaseSensitive` property.

> public HRESULT [get_IsCaseSensitive](#get_iscasesensitive)(BOOL * value)

#### get_ShouldHighlightAllMatches

Gets the `ShouldHighlightAllMatches` property.

> public HRESULT [get_ShouldHighlightAllMatches](#get_shouldhighlightallmatches)(BOOL * value)

#### get_ShouldMatchWord

Gets the `ShouldMatchWord` property.

> public HRESULT [get_ShouldMatchWord](#get_shouldmatchword)(BOOL * value)

#### get_SuppressDefaultFindDialog

Gets the `SuppressDefaultFindDialog` property.

> public HRESULT [get_SuppressDefaultFindDialog](#get_suppressdefaultfinddialog)(BOOL * value)

#### put_FindTerm

Gets or sets the word or phrase to be searched in the current page.

> public HRESULT [put_FindTerm](#put_findterm)(LPCWSTR value)

You can set `FindTerm` to any text you want to find on the page. This will take effect the next time you call the `Start()` method.

```cpp
bool AppWindow::FindTerm()
{
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));

    TextInputDialog dialog(
        GetMainWindow(), L"Find on Page Term", L"Find on Page Term:", L"Enter Find Term");

    auto m_env18 = m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment18>();
    CHECK_FEATURE_RETURN(m_env18);
    CHECK_FAILURE(webView2find->Stop());

    if (!findOptions)
    {
        findOptions = SetDefaultFindOptions();
    }
    CHECK_FAILURE(findOptions->put_FindTerm(dialog.input.c_str()));
    CHECK_FAILURE(webView2find->Start(
        findOptions.get(), Callback<ICoreWebView2ExperimentalFindStartCompletedHandler>(
                               [this](HRESULT result) -> HRESULT { return S_OK; })
                               .Get()));
    return true;
}
```

#### put_IsCaseSensitive

Determines if the find session is case sensitive.

> public HRESULT [put_IsCaseSensitive](#put_iscasesensitive)(BOOL value)

Returns TRUE if the find is case sensitive, FALSE otherwise. When toggling case sensitivity, the behavior can vary by locale, which may be influenced by both the browser's UI locale and the document's language settings. The browser's UI locale typically provides a default handling approach, while the document's language settings (e.g., specified using the HTML lang attribute) can override these defaults to apply locale-specific rules. This dual consideration ensures that text is processed in a manner consistent with user expectations and the linguistic context of the content.

```cpp
bool AppWindow::IsCaseSensitive()
{
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));

    auto m_env18 = m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment18>();
    CHECK_FEATURE_RETURN(m_env18);
    CHECK_FAILURE(webView2find->Stop());

    if (!findOptions)
    {
        findOptions = SetDefaultFindOptions();
    }
    BOOL caseSensitive;
    findOptions->get_IsCaseSensitive(&caseSensitive);
    CHECK_FAILURE(findOptions->put_IsCaseSensitive(!caseSensitive));

    CHECK_FAILURE(webView2find->Start(
        findOptions.get(), Callback<ICoreWebView2ExperimentalFindStartCompletedHandler>(
                               [this](HRESULT result) -> HRESULT { return S_OK; })
                               .Get()));
    return true;
}
```

#### put_ShouldHighlightAllMatches

Gets or sets the state of whether all matches are highlighted.

> public HRESULT [put_ShouldHighlightAllMatches](#put_shouldhighlightallmatches)(BOOL value)

Returns TRUE if all matches are highlighted, FALSE otherwise. Note: Changes to this property take effect only when Start, FindNext, or FindPrevious is called. Preferences for the session cannot be updated unless another call to the Start function on the server-side is made. Therefore, changes will not take effect until one of these functions is called.

```cpp
bool AppWindow::ShouldHighlightAllMatches()
{
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));

    auto m_env18 = m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment18>();
    CHECK_FEATURE_RETURN(m_env18);
    CHECK_FAILURE(webView2find->Stop());

    if (!findOptions)
    {
        findOptions = SetDefaultFindOptions();
    }
    BOOL shouldHighlightAllMatches;
    CHECK_FAILURE(findOptions->get_ShouldHighlightAllMatches(&shouldHighlightAllMatches));
    CHECK_FAILURE(findOptions->put_ShouldHighlightAllMatches(!shouldHighlightAllMatches));
    CHECK_FAILURE(webView2find->Start(
        findOptions.get(), Callback<ICoreWebView2ExperimentalFindStartCompletedHandler>(
                               [this](HRESULT result) -> HRESULT { return S_OK; })
                               .Get()));
    return true;
}
```

#### put_ShouldMatchWord

Similar to case sensitivity, word matching also can vary by locale, which may be influenced by both the browser's UI locale and the document's language settings.

> public HRESULT [put_ShouldMatchWord](#put_shouldmatchword)(BOOL value)

The browser's UI locale typically provides a default handling approach, while the document's language settings (e.g., specified using the HTML lang attribute) can override these defaults to apply locale-specific rules. This dual consideration ensures that text is processed in a manner consistent with user expectations and the linguistic context of the content. ShouldMatchWord determines if only whole words should be matched during the find session. Returns TRUE if only whole words should be matched, FALSE otherwise.

```cpp
bool AppWindow::ShouldMatchWord()
{
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));

    auto m_env18 = m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment18>();
    CHECK_FEATURE_RETURN(m_env18);
    CHECK_FAILURE(webView2find->Stop());

    if (!findOptions)
    {
        findOptions = SetDefaultFindOptions();
    }
    BOOL shouldMatchWord;
    findOptions->get_ShouldMatchWord(&shouldMatchWord);
    CHECK_FAILURE(findOptions->put_ShouldMatchWord(!shouldMatchWord));
    CHECK_FAILURE(webView2find->Start(
        findOptions.get(), Callback<ICoreWebView2ExperimentalFindStartCompletedHandler>(
                               [this](HRESULT result) -> HRESULT { return S_OK; })
                               .Get()));
    return true;
}
```

#### put_SuppressDefaultFindDialog

Sets this property to hide the default Find UI.

> public HRESULT [put_SuppressDefaultFindDialog](#put_suppressdefaultfinddialog)(BOOL value)

You can use this to hide the default UI so that you can show your own custom UI or programmatically interact with the Find API while showing no Find UI. Returns TRUE if hiding the default Find UI and FALSE if using showing the default Find UI. Note: Changes to this property take effect only when Start, FindNext, or FindPrevious is called. Preferences for the session cannot be updated unless another call to the Start function on the server-side is made. Therefore, changes will not take effect until one of these functions is called.

```cpp
bool AppWindow::SuppressDefaultFindDialog()
{
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));

    auto m_env18 = m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment18>();
    CHECK_FEATURE_RETURN(m_env18);
    CHECK_FAILURE(webView2find->Stop());

    if (!findOptions)
    {
        findOptions = SetDefaultFindOptions();
    }
    BOOL suppressDefaultDialog;
    findOptions->get_SuppressDefaultFindDialog(&suppressDefaultDialog);
    CHECK_FAILURE(findOptions->put_SuppressDefaultFindDialog(!suppressDefaultDialog));
    CHECK_FAILURE(webView2find->Stop());
    CHECK_FAILURE(webView2find->Start(
        findOptions.get(), Callback<ICoreWebView2ExperimentalFindStartCompletedHandler>(
                               [this](HRESULT result) -> HRESULT { return S_OK; })
                               .Get()));
    return true;
}
```

