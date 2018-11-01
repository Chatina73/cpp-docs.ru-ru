---
title: Всплывающие подсказки в Windows, не являющиеся производными CFrameWnd
ms.date: 11/04/2016
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
ms.openlocfilehash: 2545bda725428835c256ad81edc9070bd004d474
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620302"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Всплывающие подсказки в Windows, не являющиеся производными CFrameWnd

Этой статье рассматриваются Включение всплывающих подсказок для элементов управления в окно, которое не является производным от [CFrameWnd](../mfc/reference/cframewnd-class.md). Статья [всплывающие подсказки панели инструментов](../mfc/toolbar-tool-tips.md) предоставляет сведения о всплывающих подсказок для элементов управления в `CFrameWnd`.

В этой статье семейство рассматриваются:

- [Включение подсказок](../mfc/enabling-tool-tips.md)

- [Обработка уведомления TTN_NEEDTEXT для подсказок](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [Структура TOOLTIPTEXT](../mfc/tooltiptext-structure.md)

Всплывающие подсказки отображаются автоматически для кнопок и других элементов управления, содержащихся в родительском окне, производный от `CFrameWnd`. Это обусловлено `CFrameWnd` имеет обработчик по умолчанию для [TTN_GETDISPINFO](/windows/desktop/Controls/ttn-getdispinfo) уведомление, которое обрабатывает **TTN_NEEDTEXT** уведомления от средства совет элементы управления, связанные с элементами управления.

Тем не менее, этот обработчик по умолчанию не вызывается, когда **TTN_NEEDTEXT** из элемента управления всплывающей подсказки, связанный с элементом управления в окне, не отправляется уведомление `CFrameWnd`, такой как элемент управления в диалоговое окно или представление формы. Таким образом, она необходима для предоставления функцию обработчика событий для **TTN_NEEDTEXT** сообщение уведомления, чтобы отобразить всплывающие подсказки для дочерних элементов управления.

Всплывающие подсказки по умолчанию, для windows с [CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) нет текст, связанный с ними. Чтобы получить текст подсказки для отображения, **TTN_NEEDTEXT** уведомление отправляется на родительском окне управления всплывающей подсказки, непосредственно перед отображением подсказки. Если отсутствует обработчик для этого сообщения назначить либо значение для *pszText* членом **TOOLTIPTEXT** структуры, не будет не текст, отображаемый для всплывающей подсказки.

## <a name="see-also"></a>См. также

[Подсказки](../mfc/tool-tips.md)

