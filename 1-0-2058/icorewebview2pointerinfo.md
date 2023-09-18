---
description: 
title: WebView2 Win32 C++ ICoreWebView2PointerInfo
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PointerInfo
topic_type: 
- APIRef
api_name:
- ICoreWebView2PointerInfo
- ICoreWebView2PointerInfo.get_ButtonChangeKind
- ICoreWebView2PointerInfo.get_DisplayRect
- ICoreWebView2PointerInfo.get_FrameId
- ICoreWebView2PointerInfo.get_HimetricLocation
- ICoreWebView2PointerInfo.get_HimetricLocationRaw
- ICoreWebView2PointerInfo.get_HistoryCount
- ICoreWebView2PointerInfo.get_InputData
- ICoreWebView2PointerInfo.get_KeyStates
- ICoreWebView2PointerInfo.get_PenFlags
- ICoreWebView2PointerInfo.get_PenMask
- ICoreWebView2PointerInfo.get_PenPressure
- ICoreWebView2PointerInfo.get_PenRotation
- ICoreWebView2PointerInfo.get_PenTiltX
- ICoreWebView2PointerInfo.get_PenTiltY
- ICoreWebView2PointerInfo.get_PerformanceCount
- ICoreWebView2PointerInfo.get_PixelLocation
- ICoreWebView2PointerInfo.get_PixelLocationRaw
- ICoreWebView2PointerInfo.get_PointerDeviceRect
- ICoreWebView2PointerInfo.get_PointerFlags
- ICoreWebView2PointerInfo.get_PointerId
- ICoreWebView2PointerInfo.get_PointerKind
- ICoreWebView2PointerInfo.get_Time
- ICoreWebView2PointerInfo.get_TouchContact
- ICoreWebView2PointerInfo.get_TouchContactRaw
- ICoreWebView2PointerInfo.get_TouchFlags
- ICoreWebView2PointerInfo.get_TouchMask
- ICoreWebView2PointerInfo.get_TouchOrientation
- ICoreWebView2PointerInfo.get_TouchPressure
- ICoreWebView2PointerInfo.put_ButtonChangeKind
- ICoreWebView2PointerInfo.put_DisplayRect
- ICoreWebView2PointerInfo.put_FrameId
- ICoreWebView2PointerInfo.put_HimetricLocation
- ICoreWebView2PointerInfo.put_HimetricLocationRaw
- ICoreWebView2PointerInfo.put_HistoryCount
- ICoreWebView2PointerInfo.put_InputData
- ICoreWebView2PointerInfo.put_KeyStates
- ICoreWebView2PointerInfo.put_PenFlags
- ICoreWebView2PointerInfo.put_PenMask
- ICoreWebView2PointerInfo.put_PenPressure
- ICoreWebView2PointerInfo.put_PenRotation
- ICoreWebView2PointerInfo.put_PenTiltX
- ICoreWebView2PointerInfo.put_PenTiltY
- ICoreWebView2PointerInfo.put_PerformanceCount
- ICoreWebView2PointerInfo.put_PixelLocation
- ICoreWebView2PointerInfo.put_PixelLocationRaw
- ICoreWebView2PointerInfo.put_PointerDeviceRect
- ICoreWebView2PointerInfo.put_PointerFlags
- ICoreWebView2PointerInfo.put_PointerId
- ICoreWebView2PointerInfo.put_PointerKind
- ICoreWebView2PointerInfo.put_Time
- ICoreWebView2PointerInfo.put_TouchContact
- ICoreWebView2PointerInfo.put_TouchContactRaw
- ICoreWebView2PointerInfo.put_TouchFlags
- ICoreWebView2PointerInfo.put_TouchMask
- ICoreWebView2PointerInfo.put_TouchOrientation
- ICoreWebView2PointerInfo.put_TouchPressure
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PointerInfo

```
interface ICoreWebView2PointerInfo
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ButtonChangeKind](#get_buttonchangekind) | Gets the `ButtonChangeKind` property.
[get_DisplayRect](#get_displayrect) | Gets the `DisplayRect` property.
[get_FrameId](#get_frameid) | Gets the `FrameId` property.
[get_HimetricLocation](#get_himetriclocation) | Gets the `HimetricLocation` property.
[get_HimetricLocationRaw](#get_himetriclocationraw) | Gets the `HimetricLocationRaw` property.
[get_HistoryCount](#get_historycount) | Gets the `HistoryCount` property.
[get_InputData](#get_inputdata) | Gets the `InputData` property.
[get_KeyStates](#get_keystates) | Gets the `KeyStates` property.
[get_PenFlags](#get_penflags) | Gets the `PenFlags` property.
[get_PenMask](#get_penmask) | Gets the `PenMask` property.
[get_PenPressure](#get_penpressure) | Gets the `PenPressure` property.
[get_PenRotation](#get_penrotation) | Gets the `PenRotation` property.
[get_PenTiltX](#get_pentiltx) | Gets the `PenTiltX` property.
[get_PenTiltY](#get_pentilty) | Gets the `PenTiltY` property.
[get_PerformanceCount](#get_performancecount) | Gets the `PerformanceCount` property.
[get_PixelLocation](#get_pixellocation) | Gets the `PixelLocation` property.
[get_PixelLocationRaw](#get_pixellocationraw) | Gets the `PixelLocationRaw` property.
[get_PointerDeviceRect](#get_pointerdevicerect) | Gets the `PointerDeviceRect` property.
[get_PointerFlags](#get_pointerflags) | Gets the `PointerFlags` property.
[get_PointerId](#get_pointerid) | Gets the `PointerId` property.
[get_PointerKind](#get_pointerkind) | Gets the `PointerKind` property.
[get_Time](#get_time) | Gets the `Time` property.
[get_TouchContact](#get_touchcontact) | Gets the `TouchContact` property.
[get_TouchContactRaw](#get_touchcontactraw) | Gets the `TouchContactRaw` property.
[get_TouchFlags](#get_touchflags) | Gets the `TouchFlags` property.
[get_TouchMask](#get_touchmask) | Gets the `TouchMask` property.
[get_TouchOrientation](#get_touchorientation) | Gets the `TouchOrientation` property.
[get_TouchPressure](#get_touchpressure) | Gets the `TouchPressure` property.
[put_ButtonChangeKind](#put_buttonchangekind) | Sets the `ButtonChangeKind` property.
[put_DisplayRect](#put_displayrect) | Sets the `DisplayRect` property.
[put_FrameId](#put_frameid) | Sets the `FrameId` property.
[put_HimetricLocation](#put_himetriclocation) | Sets the `HimetricLocation` property.
[put_HimetricLocationRaw](#put_himetriclocationraw) | Sets the `HimetricLocationRaw` property.
[put_HistoryCount](#put_historycount) | Sets the `HistoryCount` property.
[put_InputData](#put_inputdata) | Sets the `InputData` property.
[put_KeyStates](#put_keystates) | Sets the `KeyStates` property.
[put_PenFlags](#put_penflags) | Sets the `PenFlags` property.
[put_PenMask](#put_penmask) | Sets the `PenMask` property.
[put_PenPressure](#put_penpressure) | Sets the `PenPressure` property.
[put_PenRotation](#put_penrotation) | Sets the `PenRotation` property.
[put_PenTiltX](#put_pentiltx) | Sets the `PenTiltX` property.
[put_PenTiltY](#put_pentilty) | Sets the `PenTiltY` property.
[put_PerformanceCount](#put_performancecount) | Sets the `PerformanceCount` property.
[put_PixelLocation](#put_pixellocation) | Sets the `PixelLocation` property.
[put_PixelLocationRaw](#put_pixellocationraw) | Sets the `PixelLocationRaw` property.
[put_PointerDeviceRect](#put_pointerdevicerect) | Sets the `PointerDeviceRect` property.
[put_PointerFlags](#put_pointerflags) | Sets the `PointerFlags` property.
[put_PointerId](#put_pointerid) | Sets the `PointerId` property.
[put_PointerKind](#put_pointerkind) | Sets the `PointerKind` property.
[put_Time](#put_time) | Sets the `Time` property.
[put_TouchContact](#put_touchcontact) | Sets the `TouchContact` property.
[put_TouchContactRaw](#put_touchcontactraw) | Sets the `TouchContactRaw` property.
[put_TouchFlags](#put_touchflags) | Sets the `TouchFlags` property.
[put_TouchMask](#put_touchmask) | Sets the `TouchMask` property.
[put_TouchOrientation](#put_touchorientation) | Sets the `TouchOrientation` property.
[put_TouchPressure](#put_touchpressure) | Sets the `TouchPressure` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### get_ButtonChangeKind

Gets the `ButtonChangeKind` property.

> public HRESULT [get_ButtonChangeKind](#get_buttonchangekind)(INT32 * value)

#### get_DisplayRect

Gets the `DisplayRect` property.

> public HRESULT [get_DisplayRect](#get_displayrect)(RECT * value)

#### get_FrameId

Gets the `FrameId` property.

> public HRESULT [get_FrameId](#get_frameid)(UINT32 * value)

#### get_HimetricLocation

Gets the `HimetricLocation` property.

> public HRESULT [get_HimetricLocation](#get_himetriclocation)(POINT * value)

#### get_HimetricLocationRaw

Gets the `HimetricLocationRaw` property.

> public HRESULT [get_HimetricLocationRaw](#get_himetriclocationraw)(POINT * value)

#### get_HistoryCount

Gets the `HistoryCount` property.

> public HRESULT [get_HistoryCount](#get_historycount)(UINT32 * value)

#### get_InputData

Gets the `InputData` property.

> public HRESULT [get_InputData](#get_inputdata)(INT32 * value)

#### get_KeyStates

Gets the `KeyStates` property.

> public HRESULT [get_KeyStates](#get_keystates)(UINT32 * value)

#### get_PenFlags

Gets the `PenFlags` property.

> public HRESULT [get_PenFlags](#get_penflags)(UINT32 * value)

#### get_PenMask

Gets the `PenMask` property.

> public HRESULT [get_PenMask](#get_penmask)(UINT32 * value)

#### get_PenPressure

Gets the `PenPressure` property.

> public HRESULT [get_PenPressure](#get_penpressure)(UINT32 * value)

#### get_PenRotation

Gets the `PenRotation` property.

> public HRESULT [get_PenRotation](#get_penrotation)(UINT32 * value)

#### get_PenTiltX

Gets the `PenTiltX` property.

> public HRESULT [get_PenTiltX](#get_pentiltx)(INT32 * value)

#### get_PenTiltY

Gets the `PenTiltY` property.

> public HRESULT [get_PenTiltY](#get_pentilty)(INT32 * value)

#### get_PerformanceCount

Gets the `PerformanceCount` property.

> public HRESULT [get_PerformanceCount](#get_performancecount)(UINT64 * value)

#### get_PixelLocation

Gets the `PixelLocation` property.

> public HRESULT [get_PixelLocation](#get_pixellocation)(POINT * value)

#### get_PixelLocationRaw

Gets the `PixelLocationRaw` property.

> public HRESULT [get_PixelLocationRaw](#get_pixellocationraw)(POINT * value)

#### get_PointerDeviceRect

Gets the `PointerDeviceRect` property.

> public HRESULT [get_PointerDeviceRect](#get_pointerdevicerect)(RECT * value)

#### get_PointerFlags

Gets the `PointerFlags` property.

> public HRESULT [get_PointerFlags](#get_pointerflags)(UINT32 * value)

#### get_PointerId

Gets the `PointerId` property.

> public HRESULT [get_PointerId](#get_pointerid)(UINT32 * value)

#### get_PointerKind

Gets the `PointerKind` property.

> public HRESULT [get_PointerKind](#get_pointerkind)(UINT32 * value)

#### get_Time

Gets the `Time` property.

> public HRESULT [get_Time](#get_time)(UINT32 * value)

#### get_TouchContact

Gets the `TouchContact` property.

> public HRESULT [get_TouchContact](#get_touchcontact)(RECT * value)

#### get_TouchContactRaw

Gets the `TouchContactRaw` property.

> public HRESULT [get_TouchContactRaw](#get_touchcontactraw)(RECT * value)

#### get_TouchFlags

Gets the `TouchFlags` property.

> public HRESULT [get_TouchFlags](#get_touchflags)(UINT32 * value)

#### get_TouchMask

Gets the `TouchMask` property.

> public HRESULT [get_TouchMask](#get_touchmask)(UINT32 * value)

#### get_TouchOrientation

Gets the `TouchOrientation` property.

> public HRESULT [get_TouchOrientation](#get_touchorientation)(UINT32 * value)

#### get_TouchPressure

Gets the `TouchPressure` property.

> public HRESULT [get_TouchPressure](#get_touchpressure)(UINT32 * value)

#### put_ButtonChangeKind

Sets the `ButtonChangeKind` property.

> public HRESULT [put_ButtonChangeKind](#put_buttonchangekind)(INT32 value)

#### put_DisplayRect

Sets the `DisplayRect` property.

> public HRESULT [put_DisplayRect](#put_displayrect)(RECT value)

#### put_FrameId

Sets the `FrameId` property.

> public HRESULT [put_FrameId](#put_frameid)(UINT32 value)

#### put_HimetricLocation

Sets the `HimetricLocation` property.

> public HRESULT [put_HimetricLocation](#put_himetriclocation)(POINT value)

#### put_HimetricLocationRaw

Sets the `HimetricLocationRaw` property.

> public HRESULT [put_HimetricLocationRaw](#put_himetriclocationraw)(POINT value)

#### put_HistoryCount

Sets the `HistoryCount` property.

> public HRESULT [put_HistoryCount](#put_historycount)(UINT32 value)

#### put_InputData

Sets the `InputData` property.

> public HRESULT [put_InputData](#put_inputdata)(INT32 value)

#### put_KeyStates

Sets the `KeyStates` property.

> public HRESULT [put_KeyStates](#put_keystates)(UINT32 value)

#### put_PenFlags

Sets the `PenFlags` property.

> public HRESULT [put_PenFlags](#put_penflags)(UINT32 value)

#### put_PenMask

Sets the `PenMask` property.

> public HRESULT [put_PenMask](#put_penmask)(UINT32 value)

#### put_PenPressure

Sets the `PenPressure` property.

> public HRESULT [put_PenPressure](#put_penpressure)(UINT32 value)

#### put_PenRotation

Sets the `PenRotation` property.

> public HRESULT [put_PenRotation](#put_penrotation)(UINT32 value)

#### put_PenTiltX

Sets the `PenTiltX` property.

> public HRESULT [put_PenTiltX](#put_pentiltx)(INT32 value)

#### put_PenTiltY

Sets the `PenTiltY` property.

> public HRESULT [put_PenTiltY](#put_pentilty)(INT32 value)

#### put_PerformanceCount

Sets the `PerformanceCount` property.

> public HRESULT [put_PerformanceCount](#put_performancecount)(UINT64 value)

#### put_PixelLocation

Sets the `PixelLocation` property.

> public HRESULT [put_PixelLocation](#put_pixellocation)(POINT value)

#### put_PixelLocationRaw

Sets the `PixelLocationRaw` property.

> public HRESULT [put_PixelLocationRaw](#put_pixellocationraw)(POINT value)

#### put_PointerDeviceRect

Sets the `PointerDeviceRect` property.

> public HRESULT [put_PointerDeviceRect](#put_pointerdevicerect)(RECT value)

#### put_PointerFlags

Sets the `PointerFlags` property.

> public HRESULT [put_PointerFlags](#put_pointerflags)(UINT32 value)

#### put_PointerId

Sets the `PointerId` property.

> public HRESULT [put_PointerId](#put_pointerid)(UINT32 value)

#### put_PointerKind

Sets the `PointerKind` property.

> public HRESULT [put_PointerKind](#put_pointerkind)(UINT32 value)

#### put_Time

Sets the `Time` property.

> public HRESULT [put_Time](#put_time)(UINT32 value)

#### put_TouchContact

Sets the `TouchContact` property.

> public HRESULT [put_TouchContact](#put_touchcontact)(RECT value)

#### put_TouchContactRaw

Sets the `TouchContactRaw` property.

> public HRESULT [put_TouchContactRaw](#put_touchcontactraw)(RECT value)

#### put_TouchFlags

Sets the `TouchFlags` property.

> public HRESULT [put_TouchFlags](#put_touchflags)(UINT32 value)

#### put_TouchMask

Sets the `TouchMask` property.

> public HRESULT [put_TouchMask](#put_touchmask)(UINT32 value)

#### put_TouchOrientation

Sets the `TouchOrientation` property.

> public HRESULT [put_TouchOrientation](#put_touchorientation)(UINT32 value)

#### put_TouchPressure

Sets the `TouchPressure` property.

> public HRESULT [put_TouchPressure](#put_touchpressure)(UINT32 value)

