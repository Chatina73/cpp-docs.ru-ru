---
title: Типы сообщений, связанных с объектами пользовательского интерфейса
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.uiobject.msgs
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
ms.openlocfilehash: 42584a6514a48e7c02d98e1b619c06a11a8f277b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641692"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Типы сообщений, связанных с объектами пользовательского интерфейса

Ниже приведены типы объектов, с которыми работают и типы сообщений, связанных с ними.

### <a name="user-interface-objects-and-associated-messages"></a>Объекты пользовательского интерфейса и связанные сообщения

|Идентификатор объекта|Сообщения|
|---------------|--------------|
|Класс, представляющий имя содержащего его окна|Сообщения Windows, допустимые для [CWnd](../../mfc/reference/cwnd-class.md)-производный класс: диалоговое окно, окно, дочернее окно, дочернее окно MDI или верхний фрейм окна.|
|Идентификатор меню или сочетание клавиш|-Сообщение КОМАНДЫ (выполнение функции программы).<br />-Сообщение UPDATE_COMMAND_UI (динамически обновляет элемент меню).|
|Идентификатор элемента управления|Уведомляющих сообщений элемента управления типа выбранного элемента управления.|

## <a name="see-also"></a>См. также

[Сопоставление сообщений с функциями](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Добавление функциональных возможностей с помощью мастеров кода](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Добавление класса](../../ide/adding-a-class-visual-cpp.md)<br/>
[Добавление функции-члена](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Добавление переменной-члена](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Переопределение виртуальной функции](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Обработчик сообщений MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Перемещение по структуре класса](../../ide/navigating-the-class-structure-visual-cpp.md)
