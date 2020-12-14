---
description: Дополнительные сведения о сопоставлении сообщений Windows с классом
title: Сопоставление сообщений Windows с классом
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: cca13c4b262c6373fa3d968438331d5e0ce5f7d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280785"
---
# <a name="mapping-windows-messages-to-your-class"></a>Сопоставление сообщений Windows с классом

Если диалоговое окно требуется для обработки сообщений Windows, переопределите соответствующие функции обработчика. Для этого выберите вкладку **представление классов** в **Обозреватель решений**, щелкните правой кнопкой мыши класс, представляющий диалоговое окно, и выберите пункт [мастер классов](reference/mfc-class-wizard.md). С помощью мастера [сопоставьте сообщения](reference/mapping-messages-to-functions.md) с классом диалогового окна. При этом записывается запись схемы сообщения для каждого сообщения и добавляются функции-члены обработчика сообщений в класс. Используйте редактор кода для написания кода в обработчиках сообщений.

Можно также переопределить функции элементов класса [CDialog](reference/cdialog-class.md) и его базовых классов, особенно [CWnd](reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Что вы хотите узнать подробнее

- [Обработка и сопоставление сообщений](message-handling-and-mapping.md)

- [Часто переопределяемые функции-члены](commonly-overridden-member-functions.md)

- [Часто добавляемые функции-члены](commonly-added-member-functions.md)

## <a name="see-also"></a>См. также раздел

[Диалоговые окна](dialog-boxes.md)<br/>
[Работа с диалоговыми окнами в MFC](life-cycle-of-a-dialog-box.md)
