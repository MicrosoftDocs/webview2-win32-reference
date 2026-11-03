---
description: Extends ICoreWebView2ContextMenuTarget with spell check support for custom context menus.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalContextMenuTarget2
ms.date: 10/28/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalContextMenuTarget2
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalContextMenuTarget2
- ICoreWebView2ExperimentalContextMenuTarget2.get_HasSpellingError
- ICoreWebView2ExperimentalContextMenuTarget2.GetSpellCheckSuggestions
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalContextMenuTarget2

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalContextMenuTarget2
  : public IUnknown
```

Extends [ICoreWebView2ContextMenuTarget](icorewebview2contextmenutarget.md#icorewebview2contextmenutarget) with spell check support for custom context menus.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HasSpellingError](#get_hasspellingerror) | Returns TRUE if the context menu target contains a spelling error.
[GetSpellCheckSuggestions](#getspellchecksuggestions) | Asynchronously retrieves spelling corrections for the misspelled word associated with the context menu target as a read-only collection.

Obtain this interface by `QueryInterface` on the [ICoreWebView2ContextMenuTarget](icorewebview2contextmenutarget.md#icorewebview2contextmenutarget) returned by [ICoreWebView2ContextMenuRequestedEventArgs::get_ContextMenuTarget](icorewebview2contextmenurequestedeventargs.md#get_contextmenutarget).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_HasSpellingError

Returns TRUE if the context menu target contains a spelling error.

> public HRESULT [get_HasSpellingError](#get_hasspellingerror)(BOOL * value)

When TRUE, call `GetSpellCheckSuggestions` to retrieve the available spelling correction suggestions asynchronously. `HasSpellingError` can be read synchronously when the `ContextMenuRequested` event fires.

#### GetSpellCheckSuggestions

Asynchronously retrieves spelling corrections for the misspelled word associated with the context menu target as a read-only collection.

> public HRESULT [GetSpellCheckSuggestions](#getspellchecksuggestions)([ICoreWebView2ExperimentalGetSpellCheckSuggestionsCompletedHandler](icorewebview2experimentalgetspellchecksuggestionscompletedhandler.md#icorewebview2experimentalgetspellchecksuggestionscompletedhandler) * handler)

Each suggestion contains the correction text and an opaque `CommandId`. The `CommandId` can be passed to [ICoreWebView2ContextMenuRequestedEventArgs::put_SelectedCommandId](icorewebview2contextmenurequestedeventargs.md#put_selectedcommandid) to apply the correction, using the same commanding path as built-in context menu items.

To use the result asynchronously, set `Handled` to TRUE and obtain a deferral from the `ContextMenuRequested` event args before returning from the event handler. Hold the deferral until the custom menu closes. If a suggestion is selected, assign its `CommandId` to `SelectedCommandId` before completing the deferral. Complete the deferral even if no suggestion is selected.

If suggestions are ready, the handler may be invoked before `GetSpellCheckSuggestions` returns. Otherwise, it is invoked when they become available. Multiple concurrent calls are supported. Each handler receives a collection containing the same suggestions in the same order when its call completes. Collection and suggestion object identity across calls is unspecified. When `errorCode` is `S_OK`, `result` is non-null and may be empty. If `errorCode` indicates failure, `result` is null and must not be used. An empty collection represents no spelling error or no available suggestions. Returns `E_POINTER` if `handler` is null.

```cpp
bool SettingsComponent::TryShowSpellCheckContextMenu(
    wil::com_ptr<ICoreWebView2ContextMenuRequestedEventArgs> args,
    wil::com_ptr<ICoreWebView2ContextMenuItemCollection> items,
    wil::com_ptr<ICoreWebView2ContextMenuTarget> target)
{
    auto spellCheckTarget = target.try_query<ICoreWebView2ExperimentalContextMenuTarget2>();
    if (!spellCheckTarget)
    {
        return false;
    }
    BOOL hasSpellingError = FALSE;
    CHECK_FAILURE(spellCheckTarget->get_HasSpellingError(&hasSpellingError));
    if (!hasSpellingError)
    {
        return false;
    }

    wil::com_ptr<ICoreWebView2Deferral> deferral;
    CHECK_FAILURE(args->GetDeferral(&deferral));
    CHECK_FAILURE(args->put_Handled(TRUE));
    CHECK_FAILURE(spellCheckTarget->GetSpellCheckSuggestions(
        Callback<ICoreWebView2ExperimentalGetSpellCheckSuggestionsCompletedHandler>(
            [appWindow = m_appWindow, webView = m_webView, args, items, deferral](
                HRESULT errorCode,
                ICoreWebView2ExperimentalSpellCheckSuggestionCollectionView* suggestions)
                -> HRESULT
            {
                if (FAILED(errorCode))
                {
                    CHECK_FAILURE(deferral->Complete());
                    if (errorCode != E_ABORT)
                    {
                        CHECK_FAILURE(errorCode);
                    }
                    return S_OK;
                }
                wil::com_ptr<ICoreWebView2ExperimentalSpellCheckSuggestionCollectionView>
                    suggestionItems = suggestions;
                appWindow->RunAsync(
                    [appWindow, webView, args, items, suggestionItems, deferral]()
                    {
                        auto completeDeferral = wil::scope_exit(
                            [deferral]() { CHECK_FAILURE(deferral->Complete()); });
                        auto settings = appWindow->GetComponent<SettingsComponent>();
                        if (!settings || settings->m_webView.get() != webView.get())
                        {
                            return;
                        }
                        wil::unique_hmenu hPopupMenu(CreatePopupMenu());

                        UINT32 suggestionCount = 0;
                        if (suggestionItems)
                        {
                            CHECK_FAILURE(suggestionItems->get_Count(&suggestionCount));
                        }
                        for (UINT32 i = 0; i < suggestionCount; i++)
                        {
                            wil::com_ptr<ICoreWebView2ExperimentalSpellCheckSuggestion>
                                suggestion;
                            CHECK_FAILURE(suggestionItems->GetValueAtIndex(i, &suggestion));
                            wil::unique_cotaskmem_string label;
                            CHECK_FAILURE(suggestion->get_SuggestionText(&label));
                            INT32 commandId = 0;
                            CHECK_FAILURE(suggestion->get_CommandId(&commandId));
                            AppendMenu(
                                hPopupMenu.get(), MF_STRING, static_cast<UINT_PTR>(commandId),
                                label.get());
                        }
                        if (suggestionCount > 0)
                        {
                            AppendMenu(hPopupMenu.get(), MF_SEPARATOR, 0, nullptr);
                        }

                        UINT32 defaultItemsCount = 0;
                        CHECK_FAILURE(items->get_Count(&defaultItemsCount));
                        for (UINT32 i = defaultItemsCount; i > 0; --i)
                        {
                            wil::com_ptr<ICoreWebView2ContextMenuItem> item;
                            CHECK_FAILURE(items->GetValueAtIndex(i - 1, &item));
                            wil::unique_cotaskmem_string name;
                            CHECK_FAILURE(item->get_Name(&name));
                            if (wcscmp(name.get(), L"spellcheck") == 0)
                            {
                                CHECK_FAILURE(items->RemoveValueAtIndex(i - 1));
                                --defaultItemsCount;
                            }
                        }
                        while (defaultItemsCount > 0)
                        {
                            wil::com_ptr<ICoreWebView2ContextMenuItem> item;
                            CHECK_FAILURE(items->GetValueAtIndex(0, &item));
                            COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND kind;
                            CHECK_FAILURE(item->get_Kind(&kind));
                            if (kind != COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SEPARATOR)
                            {
                                break;
                            }
                            CHECK_FAILURE(items->RemoveValueAtIndex(0));
                            --defaultItemsCount;
                        }
                        settings->AddMenuItems(hPopupMenu.get(), items);

                        INT32 selectedCommandId =
                            settings->ShowCustomContextMenu(hPopupMenu.get(), args);
                        if (selectedCommandId != 0)
                        {
                            CHECK_FAILURE(args->put_SelectedCommandId(selectedCommandId));
                        }
                    });
                return S_OK;
            })
            .Get()));
    return true;
}

```

