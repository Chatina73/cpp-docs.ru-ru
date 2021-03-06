---
description: 'Дополнительные сведения: основные сведения о характеристиках окон'
title: Признаки окна ATL
ms.date: 11/04/2016
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
ms.openlocfilehash: a42ef66afe09e0e528f05419799dce48c43b1bbf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157299"
---
# <a name="understanding-window-traits"></a>Основные сведения о характеристиках окна

Классы признаков окон предоставляют простой метод стандартизации стилей, используемых для создания объекта окна ATL. Признаки окон принимаются как параметры шаблона с помощью [квиндовимпл](../atl/reference/cwindowimpl-class.md) и других классов окон ATL как способ предоставления стилей окна по умолчанию на уровне класса.

Если создатель экземпляра окна не предоставляет стили явно в вызове метода [CREATE](../atl/reference/cwindowimpl-class.md#create), можно использовать класс признаков, чтобы убедиться, что окно все еще создано с правильными стилями. Можно даже убедиться, что определенные стили заданы для всех экземпляров этого класса окон, при этом другие стили могут быть установлены для каждого экземпляра.

## <a name="atl-window-traits-templates"></a>Шаблоны признаков окна ATL

ATL предоставляет два шаблона признаков окон, позволяющих задавать стили по умолчанию во время компиляции с помощью их параметров шаблона.

|Класс|Описание|
|-----------|-----------------|
|[квинтраитс](../atl/reference/cwintraits-class.md)|Этот шаблон используется, если требуется предоставить стили окна по умолчанию, которые будут использоваться только в том случае, если в вызове не указаны другие стили `Create` . Стили, предоставленные во время выполнения, имеют приоритет над стилями, заданными во время компиляции.|
|[квинтраитсор](../atl/reference/cwintraitsor-class.md)|Этот класс используется, если требуется указать стили, которые всегда должны быть заданы для класса Window. Стили, предоставленные во время выполнения, объединяются со стилями, заданными во время компиляции с помощью побитового оператора или.|

Помимо этих шаблонов, ATL предоставляет ряд предопределенных специализаций `CWinTraits` шаблона для часто используемых сочетаний стилей окон. Полные сведения см. в справочной документации по [квинтраитс](../atl/reference/cwintraits-class.md) .

## <a name="custom-window-traits"></a>Пользовательские признаки

В маловероятной ситуации, когда специализируется на одном из шаблонов, предоставляемых библиотекой ATL, и вам нужно создать собственный класс признаков, нужно просто создать класс, реализующий две статические функции: `GetWndStyle` и `GetWndStyleEx` :

[!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]

Каждой из этих функций будет передаваться некоторое значение стиля во время выполнения, которое можно использовать для создания нового значения стиля. Если класс признаков окна используется в качестве аргумента шаблона для класса окна ATL, то значения стиля, передаваемые в эти статические функции, будут передаваться в качестве [создаваемых](../atl/reference/cwindowimpl-class.md#create)аргументов стиля.

## <a name="see-also"></a>См. также раздел

[Классы окон](../atl/atl-window-classes.md)
