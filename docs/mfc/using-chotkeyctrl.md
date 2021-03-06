---
description: 'Дополнительные сведения о: использование CHotKeyCtrl'
title: Использование CHotKeyCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: 7f17063a4fb3732a9b121e2b93f5d55e51d5654a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271685"
---
# <a name="using-chotkeyctrl"></a>Использование CHotKeyCtrl

Ключевым элементом управления, представленным классом [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), является окно, в котором отображается текстовое представление сочетания клавиш, которое пользователь вводит в него, например Ctrl + Shift + Q. Он также поддерживает внутреннее представление этого ключа в виде кода виртуального ключа и набора флагов, представляющих состояние сдвига. Элемент управления горячими ключами фактически не устанавливает горячие клавиши — это делается в программе. (Список стандартных виртуальных клавиш см. в разделе Winuser. h.)

Используйте элемент управления "горячий ключ", чтобы получить входные данные пользователя, для которого горячая клавиша должна быть связана с окном или потоком. Элементы управления горячими ключами часто используются в диалоговых окнах, например при запросе пользователя о назначении сочетания клавиш. Ответственность за получение значений, описывающих горячие клавиши, из элемента управления горячими ключами и вызов соответствующих функций для связывания горячих клавиш с окном или потоком осуществляется программой.

## <a name="what-do-you-want-to-know-more-about"></a>Что вы хотите узнать подробнее

- [Использование элемента управления горячими ключами](../mfc/using-a-hot-key-control.md)

- [Установка сочетания клавиш](../mfc/setting-a-hot-key.md)

- [Глобальные горячие клавиши](../mfc/global-hot-keys.md)

- [Горячие клавиши для конкретного потока](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>См. также раздел

[Элементы управления](../mfc/controls-mfc.md)
