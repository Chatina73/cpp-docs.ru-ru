---
description: 'Дополнительные сведения: класс hash'
title: Класс hash
ms.date: 11/04/2016
f1_keywords:
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
- vector/std::hash
- XSTDDEF/std::hash
- xstring/std::hash
helpviewer_keywords:
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
ms.openlocfilehash: 124740486482722ec065c01f0d71e9bbc413f8f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324165"
---
# <a name="hash-class"></a>Класс hash

Вычисляет хэш-код для значения.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Ty>
struct hash {
    size_t operator()(Ty val) const;
};
```

## <a name="remarks"></a>Remarks

Объект функции определяет хэш-функцию для сопоставления значений типа *Ty* с распределением значений индекса. Член `operator()` возвращает хэш-код для *Val*, подходящий для использования с шаблонами классов `unordered_map` , `unordered_multimap` , `unordered_set` и `unordered_multiset` . Стандартная библиотека предоставляет специализации для основных типов: *Ty* может иметь любой скалярный тип, включая типы указателей и типы перечисления. Кроме того, имеются специализации для типов библиотек `string`, `wstring`, `u16string`, `u32string`, `string_view`, `wstring_view`, `u16string_view`, `u32string_view`, `bitset`, `error_code`, `error_condition`, `optional`, `shared_ptr`, `thread`, `type_index`, `unique_ptr`, `variant` и `vector<bool>`.

## <a name="example"></a>Пример

```cpp
// std__functional__hash.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <unordered_set>

int main()
    {
    std::unordered_set<int, std::hash<int> > c0;
    c0.insert(3);
    std::cout << *c0.find(3) << std::endl;

    return (0);
    }
```

```Output
3
```

## <a name="requirements"></a>Требования

**Заголовок:**\<functional>

**Пространство имен:** std

## <a name="see-also"></a>См. также раздел

[<unordered_map>](../standard-library/unordered-map.md)\
[Класс unordered_multimap](../standard-library/unordered-multimap-class.md)\
[Класс unordered_multiset](../standard-library/unordered-multiset-class.md)\
[<unordered_set>](../standard-library/unordered-set.md)
