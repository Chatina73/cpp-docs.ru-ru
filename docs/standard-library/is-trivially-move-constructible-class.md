---
title: Класс is_trivially_move_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: a1aef356716fac903b4e44a358602c709572e8ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544356"
---
# <a name="istriviallymoveconstructible-class"></a>Класс is_trivially_move_constructible

Проверяет, есть ли у типа тривиальный конструктор перемещения.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Параметры

*Ty*<br/>
Запрашиваемый тип.

## <a name="remarks"></a>Примечания

Экземпляр предиката типа содержит значение true, если тип *Ty* является классом, имеющим тривиальный конструктор перемещения, в противном случае он содержит значение false.

Конструктор перемещения для класса *Ty* является тривиальным если:

он неявно объявлен;

его типы параметров эквивалентны типам неявного объявления;

Класс *Ty* не имеет виртуальных функций

Класс *Ty* не имеет виртуальных баз

класс не содержит изменчивых нестатических элементов данных;

все прямые базы класса *Ty* имеют тривиальные конструкторы перемещения

классы всех нестатических элементов данных типа класса имеют тривиальные конструкторы перемещения;

классы всех нестатических элементов данных массива типов класса имеют тривиальные конструкторы перемещения.

## <a name="requirements"></a>Требования

**Заголовок:** \<type_traits>

**Пространство имен:** std

## <a name="see-also"></a>См. также

[<type_traits>](../standard-library/type-traits.md)<br/>
