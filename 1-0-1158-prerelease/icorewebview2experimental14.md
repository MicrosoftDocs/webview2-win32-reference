---
description: This is the ICoreWebView experimental interface for sessionId support for CDP method calls.
title: WebView2 Win32 C++ ICoreWebView2Experimental14
ms.date: 03/10/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental14
---

# interface ICoreWebView2Experimental14

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental14
  : public IUnknown
```

This is the ICoreWebView experimental interface for sessionId support for CDP method calls.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CallDevToolsProtocolMethodForSession](#calldevtoolsprotocolmethodforsession) | Runs an asynchronous `DevToolsProtocol` method for a specific session of an attached target.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### CallDevToolsProtocolMethodForSession

Runs an asynchronous `DevToolsProtocol` method for a specific session of an attached target.

> public HRESULT [CallDevToolsProtocolMethodForSession](#calldevtoolsprotocolmethodforsession)(LPCWSTR sessionId, LPCWSTR methodName, LPCWSTR parametersAsJson, ICoreWebView2CallDevToolsProtocolMethodCompletedHandler * handler)

There could be multiple `DevToolsProtocol` targets in a WebView. Besides the top level page, iframes from different origin and web workers are also separate targets. Attaching to these targets allows interaction with them. When the DevToolsProtocol is attached to a target, the connection is identified by a sessionId. To use this API, you must set `flatten` parameter to true when calling `Target.attachToTarget` or `Target.setAutoAttach``DevToolsProtocol` method. Using `Target.setAutoAttach` is recommended as that would allow you to attach to dedicated worker target, which is not discoverable via other APIs like `Target.getTargets`. For more information about targets and sessions, navigate to [DevTools Protocol Viewer][GithubChromedevtoolsDevtoolsProtocolTotTarget]. For more information about available methods, navigate to [DevTools Protocol Viewer][GithubChromedevtoolsDevtoolsProtocolTot] The `sessionId` parameter is the sessionId for an attached target. nullptr or empty string is treated as the session for the default target for the top page. The `methodName` parameter is the full name of the method in the `{domain}.{method}` format. The `parametersAsJson` parameter is a JSON formatted string containing the parameters for the corresponding method. The `Invoke` method of the `handler` is run when the method asynchronously completes. `Invoke` is run with the return object of the method as a JSON string.

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
                wil::com_ptr<ICoreWebView2ExperimentalDevToolsProtocolEventReceivedEventArgs>
                    args2;
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
                wil::com_ptr<ICoreWebView2Experimental14> webview2 =
                    m_webView.try_query<ICoreWebView2Experimental14>();
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
    wil::com_ptr<ICoreWebView2Experimental14> webview2 = m_webView.try_query<ICoreWebView2Experimental14>();
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
                    // Use TextInputDialog to show the result for easy copy & paste.
                    TextInputDialog resultDialog(
                        m_appWindow->GetMainWindow(), L"CDP Method Call Result",
                        L"CDP method Result:", resultJson, L"", true);
                    return S_OK;
                })
                .Get());
    }
}
```
 [GithubChromedevtoolsDevtoolsProtocolTot]: https://chromedevtools.github.io/devtools-protocol/tot "latest (tip-of-tree) protocol - Chrome DevTools Protocol | GitHub" [GithubChromedevtoolsDevtoolsProtocolTotTarget]: https://chromedevtools.github.io/devtools-protocol/tot/Target "Chrome DevTools Protocol - Target domain"

