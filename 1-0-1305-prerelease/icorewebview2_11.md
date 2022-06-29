---
description: This interface is an extension of ICoreWebView2_10 that supports sessionId for CDP method calls and ContextMenuRequested event.
title: WebView2 Win32 C++ ICoreWebView2_11
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_11
---

# interface ICoreWebView2_11

```
interface ICoreWebView2_11
  : public ICoreWebView2_10
```

This interface is an extension of [ICoreWebView2_10](icorewebview2_10.md) that supports sessionId for CDP method calls and ContextMenuRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ContextMenuRequested](#add_contextmenurequested) | Add an event handler for the `ContextMenuRequested` event.
[CallDevToolsProtocolMethodForSession](#calldevtoolsprotocolmethodforsession) | Runs an asynchronous `DevToolsProtocol` method for a specific session of an attached target.
[remove_ContextMenuRequested](#remove_contextmenurequested) | Remove an event handler previously added with `add_ContextMenuRequested`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### add_ContextMenuRequested

Add an event handler for the `ContextMenuRequested` event.

> public HRESULT [add_ContextMenuRequested](#add_contextmenurequested)([ICoreWebView2ContextMenuRequestedEventHandler](icorewebview2contextmenurequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`ContextMenuRequested` event is raised when a context menu is requested by the user and the content inside WebView hasn't disabled context menus. The host has the option to create their own context menu with the information provided in the event or can add items to or remove items from WebView context menu. If the host doesn't handle the event, WebView will display the default context menu.

```cpp
            if (m_allowCustomMenus)
            {
                m_webView2_11->add_ContextMenuRequested(
                    Callback<ICoreWebView2ContextMenuRequestedEventHandler>(
                        [this](
                            ICoreWebView2* sender,
                            ICoreWebView2ContextMenuRequestedEventArgs* eventArgs) {
                            wil::com_ptr<ICoreWebView2ContextMenuRequestedEventArgs> args =
                                eventArgs;
                            wil::com_ptr<ICoreWebView2ContextMenuItemCollection> items;
                            CHECK_FAILURE(args->get_MenuItems(&items));

                            UINT32 itemsCount;
                            CHECK_FAILURE(items->get_Count(&itemsCount));

                            wil::com_ptr<ICoreWebView2ContextMenuTarget> target;
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
                                wil::com_ptr<ICoreWebView2ContextMenuItem> current;
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
                            // Adding a custom context menu item for the page that will display
                            // the page's URI.
                            else if (targetKind == COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_PAGE)
                            {
                                // Custom items should be reused whenever possible.
                                if (!m_displayPageUrlContextSubMenuItem)
                                {
                                    wil::com_ptr<ICoreWebView2Environment9> webviewEnvironment;
                                    CHECK_FAILURE(
                                        m_appWindow->GetWebViewEnvironment()->QueryInterface(
                                            IID_PPV_ARGS(&webviewEnvironment)));
                                    wil::com_ptr<ICoreWebView2ContextMenuItem>
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
                                        Callback<ICoreWebView2CustomItemSelectedEventHandler>(
                                            [appWindow = m_appWindow, target](
                                                ICoreWebView2ContextMenuItem* sender,
                                                IUnknown* args) {
                                                wil::unique_cotaskmem_string pageUri;
                                                CHECK_FAILURE(target->get_PageUri(&pageUri));
                                                appWindow->AsyncMessageBox(
                                                    pageUri.get(), L"Display Page Uri");
                                                return S_OK;
                                            })
                                            .Get(),
                                        nullptr));
                                    CHECK_FAILURE(webviewEnvironment->CreateContextMenuItem(
                                        L"New Submenu", nullptr,
                                        COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SUBMENU,
                                        &m_displayPageUrlContextSubMenuItem));
                                    wil::com_ptr<ICoreWebView2ContextMenuItemCollection>
                                        m_displayPageUrlContextSubMenuItemChildren;
                                    CHECK_FAILURE(
                                        m_displayPageUrlContextSubMenuItem->get_Children(
                                            &m_displayPageUrlContextSubMenuItemChildren));
                                    m_displayPageUrlContextSubMenuItemChildren
                                        ->InsertValueAtIndex(0, displayPageUrlItem.get());
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
                m_webView2_11->remove_ContextMenuRequested(m_contextMenuRequestedToken);
                MessageBox(
                    nullptr, L"Custom Context menus are now disabled.", L"Settings change",
                    MB_OK);
            }
```

#### CallDevToolsProtocolMethodForSession

Runs an asynchronous `DevToolsProtocol` method for a specific session of an attached target.

> public HRESULT [CallDevToolsProtocolMethodForSession](#calldevtoolsprotocolmethodforsession)(LPCWSTR sessionId, LPCWSTR methodName, LPCWSTR parametersAsJson, [ICoreWebView2CallDevToolsProtocolMethodCompletedHandler](icorewebview2calldevtoolsprotocolmethodcompletedhandler.md) * handler)

There could be multiple `DevToolsProtocol` targets in a WebView. Besides the top level page, iframes from different origin and web workers are also separate targets. Attaching to these targets allows interaction with them. When the DevToolsProtocol is attached to a target, the connection is identified by a sessionId. To use this API, you must set the `flatten` parameter to true when calling `Target.attachToTarget` or `Target.setAutoAttach``DevToolsProtocol` method. Using `Target.setAutoAttach` is recommended as that would allow you to attach to dedicated worker targets, which are not discoverable via other APIs like `Target.getTargets`. For more information about targets and sessions, navigate to [DevTools Protocol Viewer](https://chromedevtools.github.io/devtools-protocol/tot/Target). For more information about available methods, navigate to [DevTools Protocol Viewer](https://chromedevtools.github.io/devtools-protocol/tot) The `sessionId` parameter is the sessionId for an attached target. nullptr or empty string is treated as the session for the default target for the top page. The `methodName` parameter is the full name of the method in the `{domain}.{method}` format. The `parametersAsJson` parameter is a JSON formatted string containing the parameters for the corresponding method. The `Invoke` method of the `handler` is run when the method asynchronously completes. `Invoke` is run with the return object of the method as a JSON string.

```cpp
void ScriptComponent::HandleCDPTargets()
{
    wil::com_ptr<ICoreWebView2DevToolsProtocolEventReceiver> receiver;
    // Enable Runtime events to receive Runtime.consoleAPICalled events.
    m_webView->CallDevToolsProtocolMethod(L"Runtime.enable", L"{}", nullptr);
    CHECK_FAILURE(
        m_webView->GetDevToolsProtocolEventReceiver(L"Runtime.consoleAPICalled", &receiver));
    CHECK_FAILURE(receiver->add_DevToolsProtocolEventReceived(
        Callback<ICoreWebView2DevToolsProtocolEventReceivedEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args) -> HRESULT
            {
                // Get console.log message details and which target it comes from.
                wil::unique_cotaskmem_string parameterObjectAsJson;
                CHECK_FAILURE(args->get_ParameterObjectAsJson(&parameterObjectAsJson));
                std::wstring eventSourceLabel;
                std::wstring eventDetails = parameterObjectAsJson.get();
                wil::com_ptr<ICoreWebView2DevToolsProtocolEventReceivedEventArgs2> args2;
                if (SUCCEEDED(args->QueryInterface(IID_PPV_ARGS(&args2))))
                {
                    wil::unique_cotaskmem_string sessionId;
                    CHECK_FAILURE(args2->get_SessionId(&sessionId));
                    if (sessionId.get() && *sessionId.get())
                    {
                        std::wstring targetId = m_devToolsSessionMap[sessionId.get()];
                        eventSourceLabel = m_devToolsTargetLabelMap[targetId];
                    }
                }
                // else, leave eventSourceLabel as empty string for the default target of top
                // page.

                // Log events to debug output, not using dialog as there could be a lot of
                // console.log events.
                std::wstring message = L"console.log Event: ";
                if (!eventSourceLabel.empty())
                {
                    message = message + L"(from " + eventSourceLabel + L")";
                }
                message += eventDetails + L"\n";
                OutputDebugString(message.c_str());
                return S_OK;
            })
            .Get(),
        &m_consoleAPICalledToken));
    receiver.reset();
    // Track Target and session info via CDP events.
    CHECK_FAILURE(
        m_webView->GetDevToolsProtocolEventReceiver(L"Target.attachedToTarget", &receiver));
    CHECK_FAILURE(receiver->add_DevToolsProtocolEventReceived(
        Callback<ICoreWebView2DevToolsProtocolEventReceivedEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args) -> HRESULT
            {
                // A new target is attached, add its info to maps.
                wil::unique_cotaskmem_string jsonMessage;
                CHECK_FAILURE(args->get_ParameterObjectAsJson(&jsonMessage));
                std::wstring sessionId = GetJSONStringField(jsonMessage.get(), L"sessionId");
                std::wstring targetId = GetJSONStringField(jsonMessage.get(), L"targetId");
                m_devToolsSessionMap[sessionId] = targetId;
                std::wstring type = GetJSONStringField(jsonMessage.get(), L"type");
                std::wstring url = GetJSONStringField(jsonMessage.get(), L"url");
                m_devToolsTargetLabelMap.insert_or_assign(targetId, type + L"," + url);
                wil::com_ptr<ICoreWebView2_11> webview2 =
                    m_webView.try_query<ICoreWebView2_11>();
                if (webview2)
                {
                    // Auto-attach to targets further created from this target (identified by
                    // its session ID), like dedicated worker target created in the iframe.
                    webview2->CallDevToolsProtocolMethodForSession(
                        sessionId.c_str(), L"Target.setAutoAttach",
                        LR"({"autoAttach":true,"waitForDebuggerOnStart":false,"flatten":true})",
                        nullptr);
                    // Also enable Runtime events to receive Runtime.consoleAPICalled from the
                    // target.
                    webview2->CallDevToolsProtocolMethodForSession(
                        sessionId.c_str(), L"Runtime.enable", L"{}", nullptr);
                }
                return S_OK;
            })
            .Get(),
        &m_targetAttachedToken));
    receiver.reset();
    CHECK_FAILURE(
        m_webView->GetDevToolsProtocolEventReceiver(L"Target.detachedFromTarget", &receiver));
    CHECK_FAILURE(receiver->add_DevToolsProtocolEventReceived(
        Callback<ICoreWebView2DevToolsProtocolEventReceivedEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args) -> HRESULT
            {
                // A target is detached, remove it from the maps.
                wil::unique_cotaskmem_string jsonMessage;
                CHECK_FAILURE(args->get_ParameterObjectAsJson(&jsonMessage));
                std::wstring sessionId = GetJSONStringField(jsonMessage.get(), L"sessionId");
                auto session = m_devToolsSessionMap.find(sessionId);
                if (session != m_devToolsSessionMap.end())
                {
                    m_devToolsTargetLabelMap.erase(session->second);
                    m_devToolsSessionMap.erase(session);
                }
                return S_OK;
            })
            .Get(),
        &m_targetDetachedToken));
    receiver.reset();
    CHECK_FAILURE(
        m_webView->GetDevToolsProtocolEventReceiver(L"Target.targetCreated", &receiver));
    CHECK_FAILURE(receiver->add_DevToolsProtocolEventReceived(
        Callback<ICoreWebView2DevToolsProtocolEventReceivedEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args) -> HRESULT
            {
                // Shared worker targets are not auto attached. Have to attach it explicitly.
                wil::unique_cotaskmem_string jsonMessage;
                CHECK_FAILURE(args->get_ParameterObjectAsJson(&jsonMessage));
                std::wstring type = GetJSONStringField(jsonMessage.get(), L"type");
                if (type == L"shared_worker")
                {
                    std::wstring targetId = GetJSONStringField(jsonMessage.get(), L"targetId");
                    std::wstring parameters =
                        L"{\"targetId\":\"" + targetId + L"\",\"flatten\": true}";
                    // Call Target.attachToTarget and ignore returned value, let
                    // Target.attachedToTarget to handle the result.
                    m_webView->CallDevToolsProtocolMethod(
                        L"Target.attachToTarget", parameters.c_str(), nullptr);
                }
                return S_OK;
            })
            .Get(),
        &m_targetCreatedToken));
    receiver.reset();
    CHECK_FAILURE(
        m_webView->GetDevToolsProtocolEventReceiver(L"Target.targetInfoChanged", &receiver));
    CHECK_FAILURE(receiver->add_DevToolsProtocolEventReceived(
        Callback<ICoreWebView2DevToolsProtocolEventReceivedEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args) -> HRESULT
            {
                // A target's info (such as its URL) has changed, so update its label in the
                // target label map.
                wil::unique_cotaskmem_string jsonMessage;
                CHECK_FAILURE(args->get_ParameterObjectAsJson(&jsonMessage));
                std::wstring targetId = GetJSONStringField(jsonMessage.get(), L"targetId");
                if (m_devToolsTargetLabelMap.find(targetId) !=
                    m_devToolsTargetLabelMap.end())
                {
                    // This is a target that we are interested in, update label.
                    std::wstring type = GetJSONStringField(jsonMessage.get(), L"type");
                    std::wstring url = GetJSONStringField(jsonMessage.get(), L"url");
                    m_devToolsTargetLabelMap[targetId] = type + L"," + url;
                }
                return S_OK;
            })
            .Get(),
        &m_targetInfoChangedToken));
    // Setup CDP targets operation mode.
    // Set auto attach to attach to dedicated worker target.
    m_webView->CallDevToolsProtocolMethod(
        L"Target.setAutoAttach",
        LR"({"autoAttach":true,"waitForDebuggerOnStart":false,"flatten":true})", nullptr);
    // Set setDiscoverTargets to get targetCreated event for shared worker target.
    m_webView->CallDevToolsProtocolMethod(
        L"Target.setDiscoverTargets", LR"({"discover":true})", nullptr);
}
```

```cpp
// Prompt the user for the sessionid, name and parameters of a CDP method, then call it.
void ScriptComponent::CallCdpMethodForSession()
{
    wil::com_ptr<ICoreWebView2_11> webview2 = m_webView.try_query<ICoreWebView2_11>();
    CHECK_FEATURE_RETURN_EMPTY(webview2);
    std::wstring sessionList = L"Sessions:";
    for (auto& target : m_devToolsSessionMap)
    {
        sessionList += L"\r\n";
        sessionList += target.first;
        sessionList += L":";
        sessionList += m_devToolsTargetLabelMap[target.second];
    }
    std::wstring description =
        L"Enter the sessionId, CDP method name to call, and parameters in JSON format, "
        L"separated by space,\r\n" +
        sessionList;
    TextInputDialog dialog(
        m_appWindow->GetMainWindow(), L"Call CDP Method For Session", L"Parameters:",
        description.c_str(),
        L"<sessionId> Runtime.getHeapUsage {}");
    if (dialog.confirmed)
    {
        size_t delimiter1Pos = dialog.input.find(L' ');
        std::wstring sessionId = dialog.input.substr(0, delimiter1Pos);
        size_t delimiter2Pos = dialog.input.find(L' ', delimiter1Pos+1);
        std::wstring methodName =
            dialog.input.substr(delimiter1Pos+1, delimiter2Pos - delimiter1Pos - 1);
        std::wstring methodParams =
            (delimiter2Pos < dialog.input.size() ? dialog.input.substr(delimiter2Pos + 1)
                                                : L"{}");

        webview2->CallDevToolsProtocolMethodForSession(
            sessionId.c_str(), methodName.c_str(), methodParams.c_str(),
            Callback<ICoreWebView2CallDevToolsProtocolMethodCompletedHandler>(
                [this](HRESULT error, PCWSTR resultJson) -> HRESULT
                {
                    m_appWindow->AsyncMessageBox(resultJson, L"CDP method call result");
                    return S_OK;
                })
                .Get());
    }
}
```

#### remove_ContextMenuRequested

Remove an event handler previously added with `add_ContextMenuRequested`.

> public HRESULT [remove_ContextMenuRequested](#remove_contextmenurequested)(EventRegistrationToken token)

