---
description: 'Дополнительные сведения: Отключение параметра активировать при отображении'
title: Отключение параметра "Активация при отображении"
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
ms.openlocfilehash: fcb5f7ef0518cbf257ef9ee7a659c9617092b7d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263872"
---
# <a name="turning-off-the-activate-when-visible-option"></a>Отключение параметра "Активация при отображении"

Элемент управления имеет два основных состояния: активный и неактивный. Обычно эти Штаты были различны, когда элемент управления имел окно. Активный элемент управления имел окно; неактивный элемент управления не был. С появлением безоконной активации это различие больше не является универсальным, но по-прежнему применяется ко многим элементам управления.

По сравнению с остальной частью инициализации, обычно выполняемой элементом управления ActiveX, создание окна является чрезвычайно дорогостоящей операцией. В идеале элемент управления будет откладывать создание своего окна до абсолютной необходимости.

Многие элементы управления не обязательно должны быть активными в течение всего времени, видимого в контейнере. Часто элемент управления может оставаться в неактивном состоянии до тех пор, пока пользователь не выполнит операцию, которая должна стать активной (например, щелкнув мышью или нажав клавишу TAB). Чтобы элемент управления оставался неактивным до тех пор, пока контейнер не потребует его активации, удалите флаг **OLEMISC_ACTIVATEWHENVISIBLE** из различных флагов элемента управления:

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

Флаг **OLEMISC_ACTIVATEWHENVISIBLE** автоматически опускается, если отключить параметр **активировать при отображении** на странице [Параметры управления](../mfc/reference/control-settings-mfc-activex-control-wizard.md) мастера элементов управления MFC ActiveX при создании элемента управления.

## <a name="see-also"></a>См. также раздел

[Элементы ActiveX в MFC. Оптимизация](../mfc/mfc-activex-controls-optimization.md)
