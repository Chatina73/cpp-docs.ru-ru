---
description: 'Дополнительные сведения: неограниченные элементы управления редактирования с нижними возможностями'
title: Элементы управления "Rich Edit" "без дна"
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: ad3f78fb4a5e172c16faf3421b6a9da91d422888
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339817"
---
# <a name="bottomless-rich-edit-controls"></a>Элементы управления "Rich Edit" "без дна"

Приложение может изменить размер элемента управления Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) по мере необходимости, чтобы он всегда был таким же, как и его содержимое. Форматированный элемент управления "поле ввода" поддерживает эту функцию "без нижнего уровня", отправляя родительское окно [EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize) сообщение уведомления при изменении размера его содержимого.

При обработке сообщения уведомления **EN_REQUESTRESIZE** приложение должно изменить размер элемента управления до размеров в указанной структуре [рекресизе](/windows/win32/api/richedit/ns-richedit-reqresize) . Приложение также может перемещать любые сведения, расположенные рядом с элементом управления, чтобы обеспечить изменение высоты элемента управления. Чтобы изменить размер элемента управления, можно использовать `CWnd` функцию [SetWindowPos](reference/cwnd-class.md#setwindowpos).

Вы можете принудительно применить неформатированный элемент управления "поле с небольшими значениями" для отправки **EN_REQUESTRESIZE** уведомления с помощью функции-члена [рекуестресизе](reference/cricheditctrl-class.md#requestresize) . Это сообщение может быть полезно в обработчике [OnSize](reference/cwnd-class.md#onsize) .

Чтобы получить **EN_REQUESTRESIZE** уведомления, необходимо включить уведомление с помощью `SetEventMask` функции члена.

## <a name="see-also"></a>См. также раздел

[Использование CRichEditCtrl](using-cricheditctrl.md)<br/>
[Элементы управления](controls-mfc.md)
