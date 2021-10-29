---
description: This interface is an extension of ICoreWebView2.
title: WebView2 Win32 C++ ICoreWebView2Experimental9
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/28/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental9
---

# interface ICoreWebView2Experimental9

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental9
  : public IUnknown
```

This interface is an extension of [ICoreWebView2](icorewebview2.md).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_IsDocumentPlayingAudioChanged](#add_isdocumentplayingaudiochanged) | Adds an event handler for the `IsDocumentPlayingAudioChanged` event.
[add_IsMutedChanged](#add_ismutedchanged) | Adds an event handler for the `IsMutedChanged` event.
[get_IsDocumentPlayingAudio](#get_isdocumentplayingaudio) | Indicates whether any audio output from this CoreWebView2 is playing.
[get_IsMuted](#get_ismuted) | Indicates whether all audio output from this CoreWebView2 is muted or not.
[put_IsMuted](#put_ismuted) | Sets the `IsMuted` property.
[remove_IsDocumentPlayingAudioChanged](#remove_isdocumentplayingaudiochanged) | Remove an event handler previously added with `add_IsDocumentPlayingAudioChanged`.
[remove_IsMutedChanged](#remove_ismutedchanged) | Remove an event handler previously added with `add_IsMutedChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1018

## Members

#### add_IsDocumentPlayingAudioChanged

Adds an event handler for the `IsDocumentPlayingAudioChanged` event.

> public HRESULT [add_IsDocumentPlayingAudioChanged](#add_isdocumentplayingaudiochanged)([ICoreWebView2ExperimentalIsDocumentPlayingAudioChangedEventHandler](icorewebview2experimentalisdocumentplayingaudiochangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`IsDocumentPlayingAudioChanged` is raised when the IsDocumentPlayingAudio property changes value.

```cpp
AudioComponent::AudioComponent(AppWindow* appWindow)
    : m_appWindow(appWindow), m_webView(appWindow->GetWebView())
{
    auto webviewExperimental9 = m_webView.try_query<ICoreWebView2Experimental9>();
    if (webviewExperimental9)
    {
        // Register a handler for the IsDocumentPlayingAudioChanged event.
        CHECK_FAILURE(webviewExperimental9->add_IsDocumentPlayingAudioChanged(
            Callback<ICoreWebView2ExperimentalIsDocumentPlayingAudioChangedEventHandler>(
                [this, webviewExperimental9](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                    UpdateTitleWithMuteState(webviewExperimental9);
                    return S_OK;
                })
                .Get(),
            &m_isDocumentPlayingAudioChangedToken));

        // Register a handler for the IsMutedChanged event.
        CHECK_FAILURE(webviewExperimental9->add_IsMutedChanged(
            Callback<ICoreWebView2ExperimentalIsMutedChangedEventHandler>(
                [this, webviewExperimental9](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                    UpdateTitleWithMuteState(webviewExperimental9);
                    return S_OK;
                })
                .Get(),
            &m_isMutedChangedToken));
    }
}

bool AudioComponent::HandleWindowMessage(
    HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam, LRESULT* result)
{
    if (message == WM_COMMAND)
    {
        switch (LOWORD(wParam))
        {
        case IDM_TOGGLE_MUTE_STATE:
            ToggleMuteState();
            return true;
        }
    }
    return false;
}

// Toggle the mute state of the current window and show a mute or unmute icon on the title bar
void AudioComponent::ToggleMuteState()
{
    auto webviewExperimental9 = m_webView.try_query<ICoreWebView2Experimental9>();
    if (webviewExperimental9)
     {
         BOOL isMuted;
         CHECK_FAILURE(webviewExperimental9->get_IsMuted(&isMuted));
         CHECK_FAILURE(webviewExperimental9->put_IsMuted(!isMuted));
     }
 }

 void AudioComponent::UpdateTitleWithMuteState(
     wil::com_ptr<ICoreWebView2Experimental9> webviewExperimental9)
 {
     BOOL isDocumentPlayingAudio;
     CHECK_FAILURE(webviewExperimental9->get_IsDocumentPlayingAudio(&isDocumentPlayingAudio));

     BOOL isMuted;
     CHECK_FAILURE(webviewExperimental9->get_IsMuted(&isMuted));

     wil::unique_cotaskmem_string title;
     CHECK_FAILURE(m_webView->get_DocumentTitle(&title));
     std::wstring result = L"";

     if (isDocumentPlayingAudio)
     {
         if (isMuted)
         {
             result = L"???? " + std::wstring(title.get());
         }
         else
         {
             result = L"???? " + std::wstring(title.get());
         }
     }
     else
     {
         result = std::wstring(title.get());
     }

     m_appWindow->SetDocumentTitle(result.c_str());
 }
```

#### add_IsMutedChanged

Adds an event handler for the `IsMutedChanged` event.

> public HRESULT [add_IsMutedChanged](#add_ismutedchanged)([ICoreWebView2ExperimentalIsMutedChangedEventHandler](icorewebview2experimentalismutedchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`IsMutedChanged` is raised when the IsMuted property changes value.

```cpp
```

#### get_IsDocumentPlayingAudio

Indicates whether any audio output from this CoreWebView2 is playing.

> public HRESULT [get_IsDocumentPlayingAudio](#get_isdocumentplayingaudio)(BOOL * value)

This property will be true if audio is playing even if IsMuted is true.

```cpp
AudioComponent::AudioComponent(AppWindow* appWindow)
    : m_appWindow(appWindow), m_webView(appWindow->GetWebView())
{
    auto webviewExperimental9 = m_webView.try_query<ICoreWebView2Experimental9>();
    if (webviewExperimental9)
    {
        // Register a handler for the IsDocumentPlayingAudioChanged event.
        CHECK_FAILURE(webviewExperimental9->add_IsDocumentPlayingAudioChanged(
            Callback<ICoreWebView2ExperimentalIsDocumentPlayingAudioChangedEventHandler>(
                [this, webviewExperimental9](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                    UpdateTitleWithMuteState(webviewExperimental9);
                    return S_OK;
                })
                .Get(),
            &m_isDocumentPlayingAudioChangedToken));

        // Register a handler for the IsMutedChanged event.
        CHECK_FAILURE(webviewExperimental9->add_IsMutedChanged(
            Callback<ICoreWebView2ExperimentalIsMutedChangedEventHandler>(
                [this, webviewExperimental9](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                    UpdateTitleWithMuteState(webviewExperimental9);
                    return S_OK;
                })
                .Get(),
            &m_isMutedChangedToken));
    }
}

bool AudioComponent::HandleWindowMessage(
    HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam, LRESULT* result)
{
    if (message == WM_COMMAND)
    {
        switch (LOWORD(wParam))
        {
        case IDM_TOGGLE_MUTE_STATE:
            ToggleMuteState();
            return true;
        }
    }
    return false;
}

// Toggle the mute state of the current window and show a mute or unmute icon on the title bar
void AudioComponent::ToggleMuteState()
{
    auto webviewExperimental9 = m_webView.try_query<ICoreWebView2Experimental9>();
    if (webviewExperimental9)
     {
         BOOL isMuted;
         CHECK_FAILURE(webviewExperimental9->get_IsMuted(&isMuted));
         CHECK_FAILURE(webviewExperimental9->put_IsMuted(!isMuted));
     }
 }

 void AudioComponent::UpdateTitleWithMuteState(
     wil::com_ptr<ICoreWebView2Experimental9> webviewExperimental9)
 {
     BOOL isDocumentPlayingAudio;
     CHECK_FAILURE(webviewExperimental9->get_IsDocumentPlayingAudio(&isDocumentPlayingAudio));

     BOOL isMuted;
     CHECK_FAILURE(webviewExperimental9->get_IsMuted(&isMuted));

     wil::unique_cotaskmem_string title;
     CHECK_FAILURE(m_webView->get_DocumentTitle(&title));
     std::wstring result = L"";

     if (isDocumentPlayingAudio)
     {
         if (isMuted)
         {
             result = L"???? " + std::wstring(title.get());
         }
         else
         {
             result = L"???? " + std::wstring(title.get());
         }
     }
     else
     {
         result = std::wstring(title.get());
     }

     m_appWindow->SetDocumentTitle(result.c_str());
 }
```

#### get_IsMuted

Indicates whether all audio output from this CoreWebView2 is muted or not.

> public HRESULT [get_IsMuted](#get_ismuted)(BOOL * value)

```cpp
AudioComponent::AudioComponent(AppWindow* appWindow)
    : m_appWindow(appWindow), m_webView(appWindow->GetWebView())
{
    auto webviewExperimental9 = m_webView.try_query<ICoreWebView2Experimental9>();
    if (webviewExperimental9)
    {
        // Register a handler for the IsDocumentPlayingAudioChanged event.
        CHECK_FAILURE(webviewExperimental9->add_IsDocumentPlayingAudioChanged(
            Callback<ICoreWebView2ExperimentalIsDocumentPlayingAudioChangedEventHandler>(
                [this, webviewExperimental9](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                    UpdateTitleWithMuteState(webviewExperimental9);
                    return S_OK;
                })
                .Get(),
            &m_isDocumentPlayingAudioChangedToken));

        // Register a handler for the IsMutedChanged event.
        CHECK_FAILURE(webviewExperimental9->add_IsMutedChanged(
            Callback<ICoreWebView2ExperimentalIsMutedChangedEventHandler>(
                [this, webviewExperimental9](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                    UpdateTitleWithMuteState(webviewExperimental9);
                    return S_OK;
                })
                .Get(),
            &m_isMutedChangedToken));
    }
}

bool AudioComponent::HandleWindowMessage(
    HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam, LRESULT* result)
{
    if (message == WM_COMMAND)
    {
        switch (LOWORD(wParam))
        {
        case IDM_TOGGLE_MUTE_STATE:
            ToggleMuteState();
            return true;
        }
    }
    return false;
}

// Toggle the mute state of the current window and show a mute or unmute icon on the title bar
void AudioComponent::ToggleMuteState()
{
    auto webviewExperimental9 = m_webView.try_query<ICoreWebView2Experimental9>();
    if (webviewExperimental9)
     {
         BOOL isMuted;
         CHECK_FAILURE(webviewExperimental9->get_IsMuted(&isMuted));
         CHECK_FAILURE(webviewExperimental9->put_IsMuted(!isMuted));
     }
 }

 void AudioComponent::UpdateTitleWithMuteState(
     wil::com_ptr<ICoreWebView2Experimental9> webviewExperimental9)
 {
     BOOL isDocumentPlayingAudio;
     CHECK_FAILURE(webviewExperimental9->get_IsDocumentPlayingAudio(&isDocumentPlayingAudio));

     BOOL isMuted;
     CHECK_FAILURE(webviewExperimental9->get_IsMuted(&isMuted));

     wil::unique_cotaskmem_string title;
     CHECK_FAILURE(m_webView->get_DocumentTitle(&title));
     std::wstring result = L"";

     if (isDocumentPlayingAudio)
     {
         if (isMuted)
         {
             result = L"???? " + std::wstring(title.get());
         }
         else
         {
             result = L"???? " + std::wstring(title.get());
         }
     }
     else
     {
         result = std::wstring(title.get());
     }

     m_appWindow->SetDocumentTitle(result.c_str());
 }
```

#### put_IsMuted

Sets the `IsMuted` property.

> public HRESULT [put_IsMuted](#put_ismuted)(BOOL value)

```cpp
AudioComponent::AudioComponent(AppWindow* appWindow)
    : m_appWindow(appWindow), m_webView(appWindow->GetWebView())
{
    auto webviewExperimental9 = m_webView.try_query<ICoreWebView2Experimental9>();
    if (webviewExperimental9)
    {
        // Register a handler for the IsDocumentPlayingAudioChanged event.
        CHECK_FAILURE(webviewExperimental9->add_IsDocumentPlayingAudioChanged(
            Callback<ICoreWebView2ExperimentalIsDocumentPlayingAudioChangedEventHandler>(
                [this, webviewExperimental9](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                    UpdateTitleWithMuteState(webviewExperimental9);
                    return S_OK;
                })
                .Get(),
            &m_isDocumentPlayingAudioChangedToken));

        // Register a handler for the IsMutedChanged event.
        CHECK_FAILURE(webviewExperimental9->add_IsMutedChanged(
            Callback<ICoreWebView2ExperimentalIsMutedChangedEventHandler>(
                [this, webviewExperimental9](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                    UpdateTitleWithMuteState(webviewExperimental9);
                    return S_OK;
                })
                .Get(),
            &m_isMutedChangedToken));
    }
}

bool AudioComponent::HandleWindowMessage(
    HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam, LRESULT* result)
{
    if (message == WM_COMMAND)
    {
        switch (LOWORD(wParam))
        {
        case IDM_TOGGLE_MUTE_STATE:
            ToggleMuteState();
            return true;
        }
    }
    return false;
}

// Toggle the mute state of the current window and show a mute or unmute icon on the title bar
void AudioComponent::ToggleMuteState()
{
    auto webviewExperimental9 = m_webView.try_query<ICoreWebView2Experimental9>();
    if (webviewExperimental9)
     {
         BOOL isMuted;
         CHECK_FAILURE(webviewExperimental9->get_IsMuted(&isMuted));
         CHECK_FAILURE(webviewExperimental9->put_IsMuted(!isMuted));
     }
 }

 void AudioComponent::UpdateTitleWithMuteState(
     wil::com_ptr<ICoreWebView2Experimental9> webviewExperimental9)
 {
     BOOL isDocumentPlayingAudio;
     CHECK_FAILURE(webviewExperimental9->get_IsDocumentPlayingAudio(&isDocumentPlayingAudio));

     BOOL isMuted;
     CHECK_FAILURE(webviewExperimental9->get_IsMuted(&isMuted));

     wil::unique_cotaskmem_string title;
     CHECK_FAILURE(m_webView->get_DocumentTitle(&title));
     std::wstring result = L"";

     if (isDocumentPlayingAudio)
     {
         if (isMuted)
         {
             result = L"???? " + std::wstring(title.get());
         }
         else
         {
             result = L"???? " + std::wstring(title.get());
         }
     }
     else
     {
         result = std::wstring(title.get());
     }

     m_appWindow->SetDocumentTitle(result.c_str());
 }
```

#### remove_IsDocumentPlayingAudioChanged

Remove an event handler previously added with `add_IsDocumentPlayingAudioChanged`.

> public HRESULT [remove_IsDocumentPlayingAudioChanged](#remove_isdocumentplayingaudiochanged)(EventRegistrationToken token)

#### remove_IsMutedChanged

Remove an event handler previously added with `add_IsMutedChanged`.

> public HRESULT [remove_IsMutedChanged](#remove_ismutedchanged)(EventRegistrationToken token)

