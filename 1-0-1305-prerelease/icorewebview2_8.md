---
description: This interface is an extension of ICoreWebView2_7 that supports media features.
title: WebView2 Win32 C++ ICoreWebView2_8
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_8
---

# interface ICoreWebView2_8

```
interface ICoreWebView2_8
  : public ICoreWebView2_7
```

This interface is an extension of [ICoreWebView2_7](icorewebview2_7.md) that supports media features.

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
WebView2 Win32            |    1.0.1072.54
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### add_IsDocumentPlayingAudioChanged

Adds an event handler for the `IsDocumentPlayingAudioChanged` event.

> public HRESULT [add_IsDocumentPlayingAudioChanged](#add_isdocumentplayingaudiochanged)([ICoreWebView2IsDocumentPlayingAudioChangedEventHandler](icorewebview2isdocumentplayingaudiochangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`IsDocumentPlayingAudioChanged` is raised when the IsDocumentPlayingAudio property changes value.

```cpp
AudioComponent::AudioComponent(AppWindow* appWindow)
    : m_appWindow(appWindow), m_webView(appWindow->GetWebView())
{
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
    {
        // Register a handler for the IsDocumentPlayingAudioChanged event.
        CHECK_FAILURE(webview2_8->add_IsDocumentPlayingAudioChanged(
            Callback<ICoreWebView2IsDocumentPlayingAudioChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
                    return S_OK;
                })
                .Get(),
            &m_isDocumentPlayingAudioChangedToken));

        // Register a handler for the IsMutedChanged event.
        CHECK_FAILURE(webview2_8->add_IsMutedChanged(
            Callback<ICoreWebView2IsMutedChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
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
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
     {
         BOOL isMuted;
         CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));
         CHECK_FAILURE(webview2_8->put_IsMuted(!isMuted));
         std::wstring result = !isMuted ? L"WebView is Now Muted" : L"WebView is Now Unmuted";
         MessageBox(nullptr, result.c_str(), L"Mute State Changed", MB_OK);
     }
 }

 void AudioComponent::UpdateTitleWithMuteState(wil::com_ptr<ICoreWebView2_8> webview2_8)
 {
     BOOL isDocumentPlayingAudio;
     CHECK_FAILURE(webview2_8->get_IsDocumentPlayingAudio(&isDocumentPlayingAudio));

     BOOL isMuted;
     CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));

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

> public HRESULT [add_IsMutedChanged](#add_ismutedchanged)([ICoreWebView2IsMutedChangedEventHandler](icorewebview2ismutedchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`IsMutedChanged` is raised when the IsMuted property changes value.

```cpp
AudioComponent::AudioComponent(AppWindow* appWindow)
    : m_appWindow(appWindow), m_webView(appWindow->GetWebView())
{
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
    {
        // Register a handler for the IsDocumentPlayingAudioChanged event.
        CHECK_FAILURE(webview2_8->add_IsDocumentPlayingAudioChanged(
            Callback<ICoreWebView2IsDocumentPlayingAudioChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
                    return S_OK;
                })
                .Get(),
            &m_isDocumentPlayingAudioChangedToken));

        // Register a handler for the IsMutedChanged event.
        CHECK_FAILURE(webview2_8->add_IsMutedChanged(
            Callback<ICoreWebView2IsMutedChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
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
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
     {
         BOOL isMuted;
         CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));
         CHECK_FAILURE(webview2_8->put_IsMuted(!isMuted));
         std::wstring result = !isMuted ? L"WebView is Now Muted" : L"WebView is Now Unmuted";
         MessageBox(nullptr, result.c_str(), L"Mute State Changed", MB_OK);
     }
 }

 void AudioComponent::UpdateTitleWithMuteState(wil::com_ptr<ICoreWebView2_8> webview2_8)
 {
     BOOL isDocumentPlayingAudio;
     CHECK_FAILURE(webview2_8->get_IsDocumentPlayingAudio(&isDocumentPlayingAudio));

     BOOL isMuted;
     CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));

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

#### get_IsDocumentPlayingAudio

Indicates whether any audio output from this CoreWebView2 is playing.

> public HRESULT [get_IsDocumentPlayingAudio](#get_isdocumentplayingaudio)(BOOL * value)

This property will be true if audio is playing even if IsMuted is true.

```cpp
AudioComponent::AudioComponent(AppWindow* appWindow)
    : m_appWindow(appWindow), m_webView(appWindow->GetWebView())
{
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
    {
        // Register a handler for the IsDocumentPlayingAudioChanged event.
        CHECK_FAILURE(webview2_8->add_IsDocumentPlayingAudioChanged(
            Callback<ICoreWebView2IsDocumentPlayingAudioChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
                    return S_OK;
                })
                .Get(),
            &m_isDocumentPlayingAudioChangedToken));

        // Register a handler for the IsMutedChanged event.
        CHECK_FAILURE(webview2_8->add_IsMutedChanged(
            Callback<ICoreWebView2IsMutedChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
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
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
     {
         BOOL isMuted;
         CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));
         CHECK_FAILURE(webview2_8->put_IsMuted(!isMuted));
         std::wstring result = !isMuted ? L"WebView is Now Muted" : L"WebView is Now Unmuted";
         MessageBox(nullptr, result.c_str(), L"Mute State Changed", MB_OK);
     }
 }

 void AudioComponent::UpdateTitleWithMuteState(wil::com_ptr<ICoreWebView2_8> webview2_8)
 {
     BOOL isDocumentPlayingAudio;
     CHECK_FAILURE(webview2_8->get_IsDocumentPlayingAudio(&isDocumentPlayingAudio));

     BOOL isMuted;
     CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));

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
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
    {
        // Register a handler for the IsDocumentPlayingAudioChanged event.
        CHECK_FAILURE(webview2_8->add_IsDocumentPlayingAudioChanged(
            Callback<ICoreWebView2IsDocumentPlayingAudioChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
                    return S_OK;
                })
                .Get(),
            &m_isDocumentPlayingAudioChangedToken));

        // Register a handler for the IsMutedChanged event.
        CHECK_FAILURE(webview2_8->add_IsMutedChanged(
            Callback<ICoreWebView2IsMutedChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
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
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
     {
         BOOL isMuted;
         CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));
         CHECK_FAILURE(webview2_8->put_IsMuted(!isMuted));
         std::wstring result = !isMuted ? L"WebView is Now Muted" : L"WebView is Now Unmuted";
         MessageBox(nullptr, result.c_str(), L"Mute State Changed", MB_OK);
     }
 }

 void AudioComponent::UpdateTitleWithMuteState(wil::com_ptr<ICoreWebView2_8> webview2_8)
 {
     BOOL isDocumentPlayingAudio;
     CHECK_FAILURE(webview2_8->get_IsDocumentPlayingAudio(&isDocumentPlayingAudio));

     BOOL isMuted;
     CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));

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
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
    {
        // Register a handler for the IsDocumentPlayingAudioChanged event.
        CHECK_FAILURE(webview2_8->add_IsDocumentPlayingAudioChanged(
            Callback<ICoreWebView2IsDocumentPlayingAudioChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
                    return S_OK;
                })
                .Get(),
            &m_isDocumentPlayingAudioChangedToken));

        // Register a handler for the IsMutedChanged event.
        CHECK_FAILURE(webview2_8->add_IsMutedChanged(
            Callback<ICoreWebView2IsMutedChangedEventHandler>(
                [this, webview2_8](ICoreWebView2* sender, IUnknown* args) -> HRESULT
                {
                    UpdateTitleWithMuteState(webview2_8);
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
    auto webview2_8 = m_webView.try_query<ICoreWebView2_8>();
    if (webview2_8)
     {
         BOOL isMuted;
         CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));
         CHECK_FAILURE(webview2_8->put_IsMuted(!isMuted));
         std::wstring result = !isMuted ? L"WebView is Now Muted" : L"WebView is Now Unmuted";
         MessageBox(nullptr, result.c_str(), L"Mute State Changed", MB_OK);
     }
 }

 void AudioComponent::UpdateTitleWithMuteState(wil::com_ptr<ICoreWebView2_8> webview2_8)
 {
     BOOL isDocumentPlayingAudio;
     CHECK_FAILURE(webview2_8->get_IsDocumentPlayingAudio(&isDocumentPlayingAudio));

     BOOL isMuted;
     CHECK_FAILURE(webview2_8->get_IsMuted(&isMuted));

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

