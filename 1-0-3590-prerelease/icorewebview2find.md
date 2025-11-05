---
description: Interface providing methods and properties for finding and navigating through text in the web view.
title: WebView2 Win32 C++ ICoreWebView2Find
ms.date: 10/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Find
topic_type: 
- APIRef
api_name:
- ICoreWebView2Find
- ICoreWebView2Find.add_ActiveMatchIndexChanged
- ICoreWebView2Find.add_MatchCountChanged
- ICoreWebView2Find.FindNext
- ICoreWebView2Find.FindPrevious
- ICoreWebView2Find.get_ActiveMatchIndex
- ICoreWebView2Find.get_MatchCount
- ICoreWebView2Find.remove_ActiveMatchIndexChanged
- ICoreWebView2Find.remove_MatchCountChanged
- ICoreWebView2Find.Start
- ICoreWebView2Find.Stop
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Find

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Find
  : public IUnknown
```

Interface providing methods and properties for finding and navigating through text in the web view.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ActiveMatchIndexChanged](#add_activematchindexchanged) | Adds an event handler for the `ActiveMatchIndexChanged` event.
[add_MatchCountChanged](#add_matchcountchanged) | Adds an event handler for the `MatchCountChanged` event.
[FindNext](#findnext) | Navigates to the next match in the document.
[FindPrevious](#findprevious) | Navigates to the previous match in the document.
[get_ActiveMatchIndex](#get_activematchindex) | Retrieves the index of the currently active match in the find session.
[get_MatchCount](#get_matchcount) | Gets the total count of matches found in the current document based on the last find sessions criteria.
[remove_ActiveMatchIndexChanged](#remove_activematchindexchanged) | Removes an event handler previously added with `add_ActiveMatchIndexChanged`.
[remove_MatchCountChanged](#remove_matchcountchanged) | Removes an event handler previously added with `add_MatchCountChanged`.
[Start](#start) | Initiates a find using the specified find options asynchronously.
[Stop](#stop) | Stops the current 'Find' session and hides the Find bar.

This interface allows for finding text, navigation between matches, and customization of the find UI.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.3405.78
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### add_ActiveMatchIndexChanged

Adds an event handler for the `ActiveMatchIndexChanged` event.

> public HRESULT [add_ActiveMatchIndexChanged](#add_activematchindexchanged)([ICoreWebView2FindActiveMatchIndexChangedEventHandler](icorewebview2findactivematchindexchangedeventhandler.md#icorewebview2findactivematchindexchangedeventhandler) * eventHandler, EventRegistrationToken * token)

Registers an event handler for the ActiveMatchIndexChanged event. This event is raised when the index of the currently active match changes. This can happen when the user navigates to a different match or when the active match is changed programmatically. The parameter is the event handler to be added. Returns a token representing the added event handler. This token can be used to unregister the event handler.

#### add_MatchCountChanged

Adds an event handler for the `MatchCountChanged` event.

> public HRESULT [add_MatchCountChanged](#add_matchcountchanged)([ICoreWebView2FindMatchCountChangedEventHandler](icorewebview2findmatchcountchangedeventhandler.md#icorewebview2findmatchcountchangedeventhandler) * eventHandler, EventRegistrationToken * token)

Registers an event handler for the MatchCountChanged event. This event is raised when the total count of matches in the document changes due to a new find session or changes in the document. The parameter is the event handler to be added. Returns a token representing the added event handler. This token can be used to unregister the event handler.

#### FindNext

Navigates to the next match in the document.

> public HRESULT [FindNext](#findnext)()

If there are no matches to find, FindNext will wrap around to the first match's index. If called when there is no find session active, FindNext will silently fail.

```cpp
bool AppWindow::FindNext()
{
    auto webView2_28 = m_webView.try_query<ICoreWebView2_28>();
    CHECK_FEATURE_RETURN(webView2_28);
    wil::com_ptr<ICoreWebView2Find> webView2find;
    CHECK_FAILURE(webView2_28->get_Find(&webView2find));
    CHECK_FAILURE(webView2find->FindNext());

    return true;
}
```

#### FindPrevious

Navigates to the previous match in the document.

> public HRESULT [FindPrevious](#findprevious)()

If there are no matches to find, FindPrevious will wrap around to the last match's index. If called when there is no find session active, FindPrevious will silently fail.

```cpp
bool AppWindow::FindPrevious()
{
    auto webView2_28 = m_webView.try_query<ICoreWebView2_28>();
    CHECK_FEATURE_RETURN(webView2_28);
    wil::com_ptr<ICoreWebView2Find> webView2find;
    CHECK_FAILURE(webView2_28->get_Find(&webView2find));

    CHECK_FAILURE(webView2find->FindPrevious());

    return true;
}
```

#### get_ActiveMatchIndex

Retrieves the index of the currently active match in the find session.

> public HRESULT [get_ActiveMatchIndex](#get_activematchindex)(INT32 * value)

Returns the index of the currently active match, or -1 if there is no active match. The index starts at 1 for the first match.

```cpp
bool AppWindow::GetActiveMatchIndex()
{
    auto webView2_28 = m_webView.try_query<ICoreWebView2_28>();
    CHECK_FEATURE_RETURN(webView2_28);
    wil::com_ptr<ICoreWebView2Find> webView2find;
    CHECK_FAILURE(webView2_28->get_Find(&webView2find));
    int32_t activeMatchIndex;
    CHECK_FAILURE(webView2find->get_ActiveMatchIndex(&activeMatchIndex));

    std::wstring activeMatchIndexStr =
        L"Active Match Index: " + std::to_wstring(activeMatchIndex);
    MessageBox(m_mainWindow, activeMatchIndexStr.c_str(), L"Find Operation", MB_OK);

    return true;
}
```

#### get_MatchCount

Gets the total count of matches found in the current document based on the last find sessions criteria.

> public HRESULT [get_MatchCount](#get_matchcount)(INT32 * value)

Returns the total count of matches.

```cpp
bool AppWindow::GetMatchCount()
{
    auto webView2_28 = m_webView.try_query<ICoreWebView2_28>();
    CHECK_FEATURE_RETURN(webView2_28);
    wil::com_ptr<ICoreWebView2Find> webView2find;
    CHECK_FAILURE(webView2_28->get_Find(&webView2find));
    int32_t matchCount;
    CHECK_FAILURE(webView2find->get_MatchCount(&matchCount));

    std::wstring matchCountStr = L"Match Count: " + std::to_wstring(matchCount);
    MessageBox(m_mainWindow, matchCountStr.c_str(), L"Find Operation", MB_OK);

    return true;
}
```

#### remove_ActiveMatchIndexChanged

Removes an event handler previously added with `add_ActiveMatchIndexChanged`.

> public HRESULT [remove_ActiveMatchIndexChanged](#remove_activematchindexchanged)(EventRegistrationToken token)

#### remove_MatchCountChanged

Removes an event handler previously added with `add_MatchCountChanged`.

> public HRESULT [remove_MatchCountChanged](#remove_matchcountchanged)(EventRegistrationToken token)

#### Start

Initiates a find using the specified find options asynchronously.

> public HRESULT [Start](#start)([ICoreWebView2FindOptions](icorewebview2findoptions.md#icorewebview2findoptions) * options, [ICoreWebView2FindStartCompletedHandler](icorewebview2findstartcompletedhandler.md#icorewebview2findstartcompletedhandler) * handler)

Initiates a find operation using the specified options asynchronously. Starting find is an asynchronous operation and can be configured with notification handlers to know when the starting find operation has completed. The Find dialog will appear after the StartAsync operation completes. Note that the async behavior only applies to starting the find, not to the entire find dialog session.

Displays the Find bar and starts the find session, replacing any existing session. Shows the Find bar even with empty search strings (no actual finding occurs). Supports HTML and TXT document queries; silently fails on unsupported formats. FindOptions changes after initiation don't affect the active session.

The async action completes when the Find bar UI displays the search term and the match counter populates (may have slight latency). The MatchCountChanged and ActiveMatchIndexChanged events fire only after completion with default values of -1 for active match index and 0 for match count before completion.

To start a new session from the first match, call Stop() before StartAsync(). Consecutive calls with the same options continue from the current position. Without parameters, it behaves as FindNext or FindPrevious based on the last action (defaults to forward). Different search terms always start a new session from the document beginning.

```cpp
bool AppWindow::Start(const std::wstring& searchTerm)
{
    auto webView2_28 = m_webView.try_query<ICoreWebView2_28>();
    CHECK_FEATURE_RETURN(webView2_28);

    wil::com_ptr<ICoreWebView2Find> webView2find;
    CHECK_FAILURE(webView2_28->get_Find(&webView2find));
    SetupFindEventHandlers(webView2find);

    // Initialize find configuration/settings
    if (!findOptions)
    {
        findOptions = SetDefaultFindOptions();
    }

    // Check if the search term has changed to determine if UI needs to be updated
    if (m_findOnPageLastSearchTerm != searchTerm)
    {
        m_findOnPageLastSearchTerm =
            searchTerm; // Update the last search term for future comparisons
    }

    // Start the find operation
    CHECK_FAILURE(webView2find->Start(
        findOptions.get(), Callback<ICoreWebView2FindStartCompletedHandler>(
                               [this](HRESULT result) -> HRESULT { return S_OK; })
                               .Get()));
    return true;
}
```

#### Stop

Stops the current 'Find' session and hides the Find bar. Stopping Find is an asynchronous operation and can be configured with notification handlers to know when stopping find operation has completed. The Find dialog will disappear before the Stop operation completes.

> public HRESULT [Stop](#stop)()

If called with no Find session active, it will silently do nothing.

```cpp
bool AppWindow::StopFind()
{
    auto webView2_28 = m_webView.try_query<ICoreWebView2_28>();
    CHECK_FEATURE_RETURN(webView2_28);
    wil::com_ptr<ICoreWebView2Find> webView2find;
    CHECK_FAILURE(webView2_28->get_Find(&webView2find));
    // Note, I am not 100% sure if this is the best way to remove the event handlers
    // Because it would rely on the user clicking stopfind. Maybe put in destructor or when
    // startfind completes?
    CHECK_FAILURE(webView2find->remove_MatchCountChanged(m_matchCountChangedToken));
    CHECK_FAILURE(webView2find->remove_ActiveMatchIndexChanged(m_activeMatchIndexChangedToken));
    CHECK_FAILURE(webView2find->Stop());
    return true;
}
```

