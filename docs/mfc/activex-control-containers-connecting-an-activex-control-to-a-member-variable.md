---
title: Контейнеры элементов управления ActiveX. Соединение элемента управления ActiveX с переменной-членом
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: 2234647e933e37ff82845c4b40dc93cefeb55575
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446467"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Контейнеры элементов управления ActiveX. Соединение элемента управления ActiveX с переменной-членом

Для доступа к элемента управления ActiveX в его приложение контейнера элемента управления проще всего связать элемент управления ActiveX с переменную-член класса диалогового окна, который будет содержать элемент управления.

> [!NOTE]
>  Это не единственный способ открыть внедренный элемент управления из класса контейнера, но для целей этой статьи достаточно.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Добавление переменной-члена в класс диалоговых окон

1. Из представления классов щелкните правой кнопкой мыши класс диалогового окна, чтобы открыть контекстное меню. Например, `CContainerDlg`.

1. В контекстном меню, щелкните **добавить** и затем **добавить переменную**.

1. В мастере добавления члена переменной, щелкните **управляющей переменной**.

1. В **идентификатор элемента управления** выберите идентификатор элемента управления внедренного элемента управления ActiveX. Например, `IDC_CIRCCTRL1`.

1. В **имя переменной** введите имя.

   Например *m_circctl*.

1. Нажмите кнопку **Готово** чтобы принять выбранные параметры и закрыть мастер добавления переменной-члена.

## <a name="see-also"></a>См. также

[Контейнеры для элементов ActiveX](../mfc/activex-control-containers.md)

