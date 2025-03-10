---
description: Interface providing methods and properties for finding and navigating through text in the web view.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFind
ms.date: 02/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFind
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFind
- ICoreWebView2ExperimentalFind.add_ActiveMatchIndexChanged
- ICoreWebView2ExperimentalFind.add_MatchCountChanged
- ICoreWebView2ExperimentalFind.FindNext
- ICoreWebView2ExperimentalFind.FindPrevious
- ICoreWebView2ExperimentalFind.get_ActiveMatchIndex
- ICoreWebView2ExperimentalFind.get_MatchCount
- ICoreWebView2ExperimentalFind.remove_ActiveMatchIndexChanged
- ICoreWebView2ExperimentalFind.remove_MatchCountChanged
- ICoreWebView2ExperimentalFind.Start
- ICoreWebView2ExperimentalFind.Stop
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFind

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFind
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3079

## Members

#### add_ActiveMatchIndexChanged

Adds an event handler for the `ActiveMatchIndexChanged` event.

> public HRESULT [add_ActiveMatchIndexChanged](#add_activematchindexchanged)([ICoreWebView2ExperimentalFindActiveMatchIndexChangedEventHandler](icorewebview2experimentalfindactivematchindexchangedeventhandler.md#icorewebview2experimentalfindactivematchindexchangedeventhandler) * eventHandler, EventRegistrationToken * token)

Registers an event handler for the ActiveMatchIndexChanged event. This event is raised when the index of the currently active match changes. This can happen when the user navigates to a different match or when the active match is changed programmatically. The parameter is the event handler to be added. Returns a token representing the added event handler. This token can be used to unregister the event handler.

#### add_MatchCountChanged

Adds an event handler for the `MatchCountChanged` event.

> public HRESULT [add_MatchCountChanged](#add_matchcountchanged)([ICoreWebView2ExperimentalFindMatchCountChangedEventHandler](icorewebview2experimentalfindmatchcountchangedeventhandler.md#icorewebview2experimentalfindmatchcountchangedeventhandler) * eventHandler, EventRegistrationToken * token)

Registers an event handler for the MatchCountChanged event. This event is raised when the total count of matches in the document changes due to a new find session or changes in the document. The parameter is the event handler to be added. Returns a token representing the added event handler. This token can be used to unregister the event handler.

#### FindNext

Navigates to the next match in the document.

> public HRESULT [FindNext](#findnext)()

If there are no matches to find, FindNext will wrap around to the first match's index. If called when there is no find session active, FindNext will silently fail.

```cpp
bool AppWindow::FindNext()
{
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));
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
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));

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
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));
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
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));
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

> public HRESULT [Start](#start)([ICoreWebView2ExperimentalFindOptions](icorewebview2experimentalfindoptions.md#icorewebview2experimentalfindoptions) * options, [ICoreWebView2ExperimentalFindStartCompletedHandler](icorewebview2experimentalfindstartcompletedhandler.md#icorewebview2experimentalfindstartcompletedhandler) * handler)

Displays the Find bar and starts the find session. If a find session was already ongoing, it will be stopped and replaced with this new instance. If called with an empty string, the Find bar is displayed but no finding occurs. Changing the FindOptions object after initiation won't affect the ongoing find session. To change the ongoing find session, Start must be called again with a new or modified FindOptions object. Start supports HTML and TXT document queries. In general, this API is designed for text-based find sessions. If you start a find session programmatically on another file format that doesn't have text fields, the find session will try to execute but will fail to find any matches. (It will silently fail) Note: The asynchronous action completes when the UI has been displayed with the find term in the UI bar, and the matches have populated on the counter on the find bar. There may be a slight latency between the UI display and the matches populating in the counter. The MatchCountChanged and ActiveMatchIndexChanged events are only raised after Start has completed; otherwise, they will have their default values (-1 for active match index and 0 for match count). To start a new find session (beginning the search from the first match), call `Stop` before invoking `Start`. If `Start` is called consecutively with the same options and without calling `Stop`, the find session will continue from the current position in the existing session. Calling `Start` without altering its parameters will behave either as `FindNext` or `FindPrevious`, depending on the most recent search action performed. Start will default to forward if neither have been called. However, calling Start again during an ongoing find session does not resume from the point of the current active match. For example, given the text "1 1 A 1 1" and initiating a find session for "A", then starting another find session for "1", it will start searching from the beginning of the document, regardless of the previous active match. This behavior indicates that changing the find query initiates a completely new find session, rather than continuing from the previous match index.

```cpp
bool AppWindow::Start(const std::wstring& searchTerm)
{
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);

    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));
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
        findOptions.get(), Callback<ICoreWebView2ExperimentalFindStartCompletedHandler>(
                               [this](HRESULT result) -> HRESULT { return S_OK; })
                               .Get()));
    return true;
}
```

#### Stop

Stops the current 'Find' session and hides the Find bar.

> public HRESULT [Stop](#stop)()

If called with no Find session active, it will silently do nothing.

```cpp
bool AppWindow::StopFind()
{
    auto webView2Experimental29 = m_webView.try_query<ICoreWebView2Experimental29>();
    CHECK_FEATURE_RETURN(webView2Experimental29);
    wil::com_ptr<ICoreWebView2ExperimentalFind> webView2find;
    CHECK_FAILURE(webView2Experimental29->get_Find(&webView2find));
    // Note, I am not 100% sure if this is the best way to remove the event handlers
    // Because it would rely on the user clicking stopfind. Maybe put in destructor or when
    // startfind completes?
    CHECK_FAILURE(webView2find->remove_MatchCountChanged(m_matchCountChangedToken));
    CHECK_FAILURE(webView2find->remove_ActiveMatchIndexChanged(m_activeMatchIndexChangedToken));
    CHECK_FAILURE(webView2find->Stop());
    return true;
}
```

