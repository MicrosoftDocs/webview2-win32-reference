---
description: This interface is an extension of ICoreWebView2 that supports ContextMenuRequested event.
title: WebView2 Win32 C++ ICoreWebView2Experimental6
ms.date: 01/14/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental6
---

# interface ICoreWebView2Experimental6

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental6
  : public IUnknown
```

This interface is an extension of [ICoreWebView2](icorewebview2.md) that supports ContextMenuRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ContextMenuRequested](#add_contextmenurequested) | Add an event handler for the `ContextMenuRequested` event.
[remove_ContextMenuRequested](#remove_contextmenurequested) | Remove an event handler previously added with `add_ContextMenuRequested`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### add_ContextMenuRequested

Add an event handler for the `ContextMenuRequested` event.

> public HRESULT [add_ContextMenuRequested](#add_contextmenurequested)([ICoreWebView2ExperimentalContextMenuRequestedEventHandler](icorewebview2experimentalcontextmenurequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ContextMenuRequested` event is raised when a context menu is requested by the user and the content inside WebView hasn't disabled context menus. The host has the option to create their own context menu with the information provided in the event or can add items to or remove items from WebView context menu. If the host doesn't handle the event, WebView will display the default context menu.

```cpp
            if (m_allowCustomMenus)
            {
                m_webViewExperimental6->add_ContextMenuRequested(
                    Callback<ICoreWebView2ExperimentalContextMenuRequestedEventHandler>(
                        [this](
                            ICoreWebView2* sender,
                            ICoreWebView2ExperimentalContextMenuRequestedEventArgs* eventArgs) {
                            wil::com_ptr<ICoreWebView2ExperimentalContextMenuRequestedEventArgs>
                                args = eventArgs;
                            wil::com_ptr<ICoreWebView2ExperimentalContextMenuItemCollection> items;
                            CHECK_FAILURE(args->get_MenuItems(&items));
                            UINT32 itemsCount;
                            CHECK_FAILURE(items->get_Count(&itemsCount));

                            wil::com_ptr<ICoreWebView2ExperimentalContextMenuTarget> target;
                            CHECK_FAILURE(args->get_ContextMenuTarget(&target));

                            COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND targetKind;
                            CHECK_FAILURE(target->get_Kind(&targetKind));
                            // Custom UI Context Menu rendered if invoked on selected text
                            if (targetKind ==
                                COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_SELECTED_TEXT)
                            {
                                auto showMenu = [this, args, itemsCount, items, target] {
                                    CHECK_FAILURE(args->put_Handled(true));
                                    HMENU hPopupMenu = CreatePopupMenu();
                                    AddMenuItems(hPopupMenu, items);
                                    HWND hWnd;
                                    m_controller->get_ParentWindow(&hWnd);
                                    SetForegroundWindow(hWnd);
                                    RECT rct;
                                    GetClientRect(hWnd, &rct);
                                    POINT topLeft;
                                    topLeft.x = rct.left;
                                    topLeft.y = rct.top;
                                    ClientToScreen(hWnd, &topLeft);
                                    POINT p;
                                    CHECK_FAILURE(args->get_Location(&p));
                                    RECT bounds;
                                    CHECK_FAILURE(m_controller->get_Bounds(&bounds));
                                    double scale;
                                    m_controller3->get_RasterizationScale(&scale);
                                    INT32 selectedCommandId = TrackPopupMenu(
                                        hPopupMenu,
                                        TPM_TOPALIGN | TPM_LEFTALIGN | TPM_RETURNCMD,
                                        bounds.left + topLeft.x + ((int)(p.x * scale)),
                                        bounds.top + topLeft.y + ((int)(p.y * scale)), 0, hWnd,
                                        NULL);
                                    CHECK_FAILURE(
                                        args->put_SelectedCommandId(selectedCommandId));
                                };
                                wil::com_ptr<ICoreWebView2Deferral> deferral;
                                CHECK_FAILURE(args->GetDeferral(&deferral));
                                m_appWindow->RunAsync([deferral, showMenu]() {
                                    showMenu();
                                    CHECK_FAILURE(deferral->Complete());
                                });
                            }
                            // Removing the 'Save image as' context menu item for image context
                            // selections.
                            else if (targetKind == COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_IMAGE)
                            {
                                UINT32 removeIndex = itemsCount;
                                wil::com_ptr<ICoreWebView2ExperimentalContextMenuItem> current;
                                for (UINT32 i = 0; i < itemsCount; i++)
                                {
                                    CHECK_FAILURE(items->GetValueAtIndex(i, &current));
                                    wil::unique_cotaskmem_string name;
                                    CHECK_FAILURE(current->get_Name(&name));
                                    if (std::wstring(L"saveImageAs") == name.get())
                                    {
                                        removeIndex = i;
                                    }
                                }
                                if (removeIndex < itemsCount)
                                {
                                    CHECK_FAILURE(items->RemoveValueAtIndex(removeIndex));
                                }
                            }
                            // Adding a custom context menu item for the page that will display the
                            // page's URI.
                            else if (targetKind == COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_PAGE)
                            {
                                // Custom items should be reused whenever possible.
                                if (!m_displayPageUrlContextSubMenuItem)
                                {
                                    wil::com_ptr<ICoreWebView2ExperimentalEnvironment6>
                                        webviewEnvironment;
                                    CHECK_FAILURE(
                                        m_appWindow->GetWebViewEnvironment()->QueryInterface(
                                            IID_PPV_ARGS(&webviewEnvironment)));
                                    wil::com_ptr<ICoreWebView2ExperimentalContextMenuItem>
                                        displayPageUrlItem;
                                    wil::com_ptr<IStream> iconStream;
                                    CHECK_FAILURE(SHCreateStreamOnFileEx(
                                        L"small.ico", STGM_READ, FILE_ATTRIBUTE_NORMAL, FALSE,
                                        nullptr, &iconStream));
                                    CHECK_FAILURE(webviewEnvironment->CreateContextMenuItem(
                                        L"Display Page Url", iconStream.get(),
                                        COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_COMMAND,
                                        &displayPageUrlItem));
                                    CHECK_FAILURE(displayPageUrlItem->add_CustomItemSelected(
                                        Callback<
                                            ICoreWebView2ExperimentalCustomItemSelectedEventHandler>(
                                            [this, target](
                                                ICoreWebView2ExperimentalContextMenuItem*
                                                    sender,
                                                IUnknown* args)
                                            {
                                                wil::unique_cotaskmem_string pageUri;
                                                CHECK_FAILURE(target->get_PageUri(&pageUri));
                                                std::wstring pageString = pageUri.get();
                                                m_appWindow->RunAsync(
                                                    [this, pageString]() {
                                                        MessageBox(
                                                            m_appWindow->GetMainWindow(),
                                                            pageString.c_str(),
                                                            L"Display Page Uri", MB_OK);
                                                    });
                                                return S_OK;
                                            })
                                            .Get(),
                                        nullptr));
                                    CHECK_FAILURE(webviewEnvironment->CreateContextMenuItem(
                                        L"New Submenu", nullptr,
                                        COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SUBMENU,
                                        &m_displayPageUrlContextSubMenuItem));
                                    wil::com_ptr<
                                        ICoreWebView2ExperimentalContextMenuItemCollection>
                                        m_displayPageUrlContextSubMenuItemChildren;
                                    CHECK_FAILURE(
                                        m_displayPageUrlContextSubMenuItem->get_Children(
                                        &m_displayPageUrlContextSubMenuItemChildren));
                                    m_displayPageUrlContextSubMenuItemChildren
                                        ->InsertValueAtIndex(
                                        0, displayPageUrlItem.get());
                                }

                                CHECK_FAILURE(items->InsertValueAtIndex(
                                    itemsCount, m_displayPageUrlContextSubMenuItem.get()));
                            }
                            // If type is not an image, video, or page, the regular Edge context
                            // menu will be displayed
                            return S_OK;
                        })
                        .Get(),
                    &m_contextMenuRequestedToken);

                MessageBox(
                    nullptr, L"Custom Context menus are now enabled.", L"Settings change",
                    MB_OK);
            }
            else
            {
                m_webViewExperimental6->remove_ContextMenuRequested(m_contextMenuRequestedToken);
                MessageBox(
                    nullptr, L"Custom Context menus are now disabled.", L"Settings change",
                    MB_OK);
            }
```

#### remove_ContextMenuRequested

Remove an event handler previously added with `add_ContextMenuRequested`.

> public HRESULT [remove_ContextMenuRequested](#remove_contextmenurequested)(EventRegistrationToken token)

