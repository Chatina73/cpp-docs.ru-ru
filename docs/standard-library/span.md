---
title: <span>
description: Справочник по API для пространства имен, охватывающего библиотеку стандартных шаблонов (STL), который предоставляет упрощенное представление для непрерывной последовательности объектов.
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: 6f8a7e6ecbc02adeae7301dfc7eead2812c3c1f5
ms.sourcegitcommit: bac5dde649d5b0447de1d26a73365e36d74595f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107381159"
---
# `<span>`

`span`Представляет собой представление для непрерывной последовательности объектов. Он обеспечивает быстрый и ограниченный доступ. В отличие от `vector` или `array` , он не "владеет" элементами, к которым он предоставляет доступ.

Подробные сведения см. в разделе [класс span](span-class.md) . Ниже приведен пример того, как можно использовать диапазон.

```cpp
#include <span>
#include <iostream>

void Show(std::span<int> someValues)
{
    // show values in reverse
    for (auto rIt = someValues.rbegin(); rIt != someValues.rend(); ++rIt)
    {
        std::cout << *rIt;
    }

    // show a subspan
    for (auto& i : someValues.subspan(1, 2))
    {
        std::cout << i;
    }
}

int main()
{
    int numbers[]{ 0,1,2,3,4 };
    Show(numbers); // note conversion from array to span
}
```

## <a name="requirements"></a>Требования

**Заголовок:**\<span>

**Пространство имен:** std

**Параметр компилятора:** [/std: c + + Latest](../build/reference/std-specify-language-standard-version.md)

## <a name="members"></a>Члены

### <a name="classes"></a>Классы

|name|Описание|
|-|:-|
|[размещать](span-class.md)| Предоставляет представление для непрерывной последовательности объектов. |

### <a name="operators"></a>Операторы

|Имя|Описание|
|-|:-|
|[Оператор =](span-class.md#op_eq)| Назначение диапазона |
|[станции\[\]](span-class.md#op_at)| Доступ к элементам |

### <a name="functions"></a>Функции

|Имя|Описание|
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| Возвращает базовые байты, которые доступны только для чтения. |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | Получение базовых байтов диапазона. |

### <a name="constants"></a>Константы

|Имя|Описание|
|-|:-|
| **dynamic_extent** | Указывает, что размер диапазона определяется во время выполнения, а не во времени компиляции. Когда число элементов в диапазоне известно во время компиляции, оно указывается в качестве `Extent` параметра шаблона. Если число неизвестно до времени выполнения, укажите `dynamic_extent` вместо него. |

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)
