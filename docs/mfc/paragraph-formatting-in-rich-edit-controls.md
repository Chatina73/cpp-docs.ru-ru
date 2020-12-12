---
description: Дополнительные сведения см. в статье Форматирование абзацев в элементах управления Rich Edit
title: Форматирование абзацев с использованием элементов управления "Rich Edit"
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: 69c853c6b552b9950769fc9e3509bd4b5e55ea43
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205919"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Форматирование абзацев с использованием элементов управления "Rich Edit"

Функции-члены элемента управления Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) можно использовать для форматирования абзацев и получения сведений о форматировании. Атрибуты форматирования абзаца включают выравнивание, табуляцию, отступы и нумерацию.

Форматирование абзаца можно применить с помощью функции члена [сетпараформат](reference/cricheditctrl-class.md#setparaformat) . Чтобы определить текущее форматирование абзаца для выделенного текста, используйте функцию члена [жетпараформат](reference/cricheditctrl-class.md#getparaformat) . Структура [формата](/windows/win32/api/richedit/ns-richedit-paraformat) с этими функциями-членами используется для указания атрибутов абзаца. Один из важных элементов **формата** \ *двмаск*. В `SetParaFormat` *двмаск* указывает, какие атрибуты абзаца будут заданы этим вызовом функции. `GetParaFormat` сообщает об атрибутах первого абзаца в выделенном фрагменте. *двмаск* задает атрибуты, согласованные по всему выбору.

## <a name="see-also"></a>См. также раздел

[Использование CRichEditCtrl](using-cricheditctrl.md)<br/>
[Элементы управления](controls-mfc.md)
