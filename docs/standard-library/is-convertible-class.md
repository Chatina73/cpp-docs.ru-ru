---
title: Класс is_convertible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_convertible
helpviewer_keywords:
- is_convertible class
- is_convertible
ms.assetid: 75614008-1894-42ea-bd57-974399628536
ms.openlocfilehash: cdc3276f229fb9c1ac059a9eeb29e77655b4fc69
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520088"
---
# <a name="isconvertible-class"></a>Класс is_convertible

Проверяет, можно ли преобразовать один тип в другой.

## <a name="syntax"></a>Синтаксис

```cpp
template <class From, class To>
struct is_convertible;
```

### <a name="parameters"></a>Параметры

*From*<br/>
Преобразовываемый тип.

*Ty*<br/>
Целевой тип преобразования.

## <a name="remarks"></a>Примечания

Экземпляр предиката типа содержит значение true, если выражение `To to = from;`, где `from` является объектом типа `From`, имеет правильный формат.

## <a name="example"></a>Пример

```cpp
// std__type_traits__is_convertible.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_convertible<trivial, int> == " << std::boolalpha
        << std::is_convertible<trivial, int>::value << std::endl;
    std::cout << "is_convertible<trivial, trivial> == " << std::boolalpha
        << std::is_convertible<trivial, trivial>::value << std::endl;
    std::cout << "is_convertible<char, int> == " << std::boolalpha
        << std::is_convertible<char, int>::value << std::endl;

    return (0);
    }
```

```Output
is_convertible<trivial, int> == false
is_convertible<trivial, trivial> == true
is_convertible<char, int> == true
```

## <a name="requirements"></a>Требования

**Заголовок:** \<type_traits>

**Пространство имен:** std

## <a name="see-also"></a>См. также

[<type_traits>](../standard-library/type-traits.md)<br/>
[Класс is_base_of](../standard-library/is-base-of-class.md)<br/>
