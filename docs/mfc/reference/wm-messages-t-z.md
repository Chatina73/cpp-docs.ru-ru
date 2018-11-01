---
title: Сообщения WM_ T — Z
ms.date: 11/04/2016
f1_keywords:
- ON_WM_TCARD
- ON_WM_WININICHANGE
- ON_WM_VSCROLLCLIPBOARD
- ON_WM_VSCROLL
- ON_WM_WINDOWPOSCHANGED
- ON_WM_TIMECHANGE
- ON_WM_TIMER
- ON_WM_VKEYTOITEM
- ON_WM_WINDOWPOSCHANGING
helpviewer_keywords:
- ON_WM_VSCROLLCLIPBOARD [MFC]
- ON_WM_WININICHANGE [MFC]
- ON_WM_WINDOWPOSCHANGED [MFC]
- ON_WM_TCARD [MFC]
- ON_WM_TIMECHANGE [MFC]
- ON_WM_TIMER [MFC]
- WM_ messages [MFC]
- ON_WM_WINDOWPOSCHANGING [MFC]
- ON_WM_VKEYTOITEM [MFC]
- ON_WM_VSCROLL
ms.assetid: c528bb2e-ddb5-4da6-b652-432a387408b8
ms.openlocfilehash: 1f543489271c6bc6e5cef2bc61de0d6df3f52748
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433557"
---
# <a name="wm-messages-t---z"></a>Сообщения WM_ T — Z

Следующие записи карты соответствуют прототипов функций:

|Запись сопоставления|Прототип функции|
|---------------|------------------------|
|ON_WM_TCARD()|afx_msg void [OnTCard](../../mfc/reference/cwnd-class.md#ontcard)(целое число без знака, DWORD);|
|ON_WM_TIMECHANGE()|afx_msg void [OnTimeChange](../../mfc/reference/cwnd-class.md#ontimechange)();|
|ON_WM_TIMER()|afx_msg void [OnTimer](../../mfc/reference/cwnd-class.md#ontimer)(UINT_PTR);|
|ON_WM_UNICHAR()|afx_msg void [OnUniChar](../../mfc/reference/cwnd-class.md#onunichar)(целое число без знака, целое число без знака, целое число без знака);|
|ON_WM_UNINITMENUPOPUP()|afx_msg void [OnUnInitMenuPopup](../../mfc/reference/cwnd-class.md#onuninitmenupopup)(CMenu *, целое число без знака);|
|ON_WM_USERCHANGED()|afx_msg void [OnUserChanged](../../mfc/reference/cwnd-class.md#onuserchanged)();|
|ON_WM_VKEYTOITEM()|afx_msg int [OnVKeyToItem](../../mfc/reference/cwnd-class.md#onvkeytoitem)(целое число без знака, CWnd *, целое число без знака);|
|ON_WM_VSCROLL()|afx_msg void [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)(целое число без знака, целое число без знака, CWnd *);|
|ON_WM_VSCROLLCLIPBOARD()|afx_msg void [OnVScrollClipboard](../../mfc/reference/cwnd-class.md#onvscrollclipboard)(CWnd *, UINT, целое число без знака);|
|ON_WM_WINDOWPOSCHANGED()|afx_msg void [OnWindowPosChanged](../../mfc/reference/cwnd-class.md#onwindowposchanged)(WINDOWPOS *);|
|ON_WM_WINDOWPOSCHANGING()|afx_msg void [OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)(WINDOWPOS *);|
|ON_WM_WININICHANGE()|afx_msg void [OnWinIniChange](../../mfc/reference/cwnd-class.md#onwininichange)(LPSTR);|
|ON_WM_WTSSESSION_CHANGE()|afx_msg void [OnSessionChange](../../mfc/reference/cwnd-class.md#onsessionchange)(целое число без знака, целое число без знака);|
|ON_WM_XBUTTONDBLCLK()|afx_msg void [OnXButtonDblClk](../../mfc/reference/cwnd-class.md#onxbuttondblclk)(целое число без знака, целое число без знака, CPoint);|
|ON_WM_XBUTTONDOWN()|afx_msg void [OnXButtonDown](../../mfc/reference/cwnd-class.md#onxbuttondown)(целое число без знака, целое число без знака, CPoint);|
|ON_WM_XBUTTONUP()|afx_msg void [OnXButtonUp](../../mfc/reference/cwnd-class.md#onxbuttonup)(целое число без знака, целое число без знака, CPoint);|

## <a name="see-also"></a>См. также

[Схемы сообщений](../../mfc/reference/message-maps-mfc.md)<br/>
[Обработчики для сообщений WM_](../../mfc/reference/handlers-for-wm-messages.md)

