---
description: Дополнительные сведения об pragma директиве pointers_to_members в Microsoft C/C++
title: pointers_to_members pragma
ms.date: 04/13/2021
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragma, pointers_to_members
- members, pointers to
- pointers_to_members pragma
no-loc:
- pragma
ms.openlocfilehash: 287f00dcca5f041fc8c17cc8f14c0274a77f13ea
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107576901"
---
# <a name="pointers_to_members-pragma"></a>`pointers_to_members` pragma

**Блок, относящийся только к языку C++**

Указывает, можно ли объявить указатель на член класса до определения связанного класса. Используется для управления размером указателя и кодом, необходимым для интерпретации указателя.

## <a name="syntax"></a>Синтаксис

> **`#pragma pointers_to_members( best_case )`**\
> **`#pragma pointers_to_members( full_generality`** [ **`,`** *`most-general-representation`* ] **`)`**

## <a name="remarks"></a>Замечания

Можно поместить **`pointers_to_members`** pragma в исходный файл в качестве альтернативы использованию параметров компилятора [ `/vmb` или `/vmg`](../build/reference/vmb-vmg-representation-method.md) и [ `/vmm` , `/vms` , `/vmv`](../build/reference/vmm-vms-vmv-general-purpose-representation.md) или [ключевых слов наследования](../cpp/inheritance-keywords.md), характерных для Microsoft.

Аргумент объявления указателя указывает, был ли объявлен указатель на член до или после определения связанной функции. *`pointer-declaration`* Аргумент является одним из следующих двух символов:

- **`full_generality`**\
  Создает безопасный, но не всегда оптимальный код. Используйте, **`full_generality`** Если какой-либо указатель на член объявлен перед связанным определением класса. Этот аргумент всегда использует представление указателя, заданное *`most-general-representation`* аргументом. Эквивалентно **`/vmg`** .

- **`best_case`**\
  Создает оптимальный код, используя лучшее представление для всех указателей на члены. Перед объявлением указателя на член необходимо определить класс. Значение по умолчанию — **`best_case`** .

*`most-general-representation`* Аргумент задает наименьшее представление указателя, которое компилятор должен использовать для безопасного обращения к любому указателю на член класса в записи преобразования. Аргумент может принимать одно из следующих значений:

- **`single_inheritance`**\
  Самым общим представлением является указатель с одним наследованием на функцию-член. Эквивалентно **`/vmg /vms`** . Вызывает ошибку, если модель наследования определения класса является либо кратной, либо виртуальной.

- **`multiple_inheritance`**\
  Самым общим представлением является указатель множественного наследования для функции-члена. Эквивалентно **`/vmg /vmm`** . Вызывает ошибку, если модель наследования определения класса является виртуальной.

- **`virtual_inheritance`**\
  Самым общим представлением является указатель на виртуальное наследование для функции-члена. Эквивалентно **`/vmg /vmv`** .  Никогда не вызывает ошибку. **`virtual_inheritance`** аргумент по умолчанию, если `#pragma pointers_to_members(full_generality)` используется.

> [!CAUTION]
> Мы рекомендуем разместить **`pointers_to_members`** pragma только в файле исходного кода, который требуется изменить, и только после любых `#include` директив. Это снижает риск того, что компонент pragma повлияет на другие файлы и вы случайно указали несколько определений для одной переменной, функции или имени класса.

## <a name="example"></a>Пример

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**Завершение блока, относящегося только к языку C++**

## <a name="see-also"></a>См. также раздел

[Директивы pragma и `__pragma` `_Pragma` Ключевые слова и](./pragma-directives-and-the-pragma-keyword.md)
