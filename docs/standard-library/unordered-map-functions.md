---
description: 'Дополнительные сведения: &lt; функции unordered_map &gt;'
title: Функции &lt;unordered_map&gt;
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::swap
- unordered_map/std::swap (unordered_map)
- unordered_map/std::swap (unordered_multimap)
ms.assetid: cf2e4115-f205-4a0e-90be-a143ffcc1f44
helpviewer_keywords:
- std::swap (unordered_map/multimap)
ms.openlocfilehash: 2a1374935fa8116a3cb7e5447a659235acc0ebaf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321505"
---
# <a name="ltunordered_mapgt-functions"></a>Функции &lt;unordered_map&gt;

[Swap (unordered_map)](#swap) 
 [Swap (unordered_multimap)](#swap_function_multimap)

## <a name="swap-unordered_map"></a><a name="swap"></a> Swap (unordered_map)

Меняет местами содержимое двух контейнеров.

```cpp
template <class Key, class Ty, class Hash, class Pred, class Alloc>
void swap(
    unordered_map <Key, Ty, Hash, Pred, Alloc>& left,
    unordered_map <Key, Ty, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>Параметры

*Раздел*\
Тип ключа.

*Ty*\
Сопоставленный тип.

*Функции*\
Тип объекта хэш-функции.

*Возможен*\
Тип объекта функции сравнения на предмет равенства.

*Идентификатор*\
Класс распределителя.

*слева*\
Первый контейнер для замены.

*Правильно*\
Второй контейнер для замены.

### <a name="remarks"></a>Комментарии

Функция шаблона выполняет `left.` [unordered_map:: Swap](../standard-library/unordered-map-class.md#swap) `(right)` .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__u_m_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

// display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="swap-unordered_multimap"></a><a name="swap_function_multimap"></a> Swap (unordered_multimap)

Меняет местами содержимое двух контейнеров.

```cpp
template <class Key, class Ty, class Hash, class Pred, class Alloc>
void swap(
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& left,
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>Параметры

*Раздел*\
Тип ключа.

*Ty*\
Сопоставленный тип.

*Функции*\
Тип объекта хэш-функции.

*Возможен*\
Тип объекта функции сравнения на предмет равенства.

*Идентификатор*\
Класс распределителя.

*слева*\
Первый контейнер для замены.

*Правильно*\
Второй контейнер для замены.

### <a name="remarks"></a>Комментарии

Функция шаблона выполняет `left.` [unordered_multimap:: Swap](../standard-library/unordered-multimap-class.md#swap) `(right)` .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__u_mm_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_multimap<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

    // display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="see-also"></a>См. также раздел

[<unordered_map>](../standard-library/unordered-map.md)
