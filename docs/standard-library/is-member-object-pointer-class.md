---
title: Класс is_member_object_pointer
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_member_object_pointer
helpviewer_keywords:
- is_member_object_pointer class
- is_member_object_pointer
ms.assetid: 64f9cdf3-4621-4310-a076-a7bc986926b9
ms.openlocfilehash: 401beed2a45be0492ba1a5cbd57cc92153dbaa91
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521132"
---
# <a name="ismemberobjectpointer-class"></a>Класс is_member_object_pointer

Проверяет, является ли тип указателем на объект члена.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Ty>
struct is_member_object_pointer;
```

### <a name="parameters"></a>Параметры

*Ty*<br/>
Запрашиваемый тип.

## <a name="remarks"></a>Примечания

Экземпляр предиката типа содержит значение true, если тип *Ty* является указателем на объект члена или `cv-qualified` указатель на объект-член, в противном случае он содержит значение false. Обратите внимание, что `is_member_object_pointer` содержит значение false, если *Ty* является указателем на функцию-член.

## <a name="example"></a>Пример

```cpp
// std__type_traits__is_member_object_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_member_object_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_object_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_object_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_object_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_object_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_object_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }
```

```Output
is_member_object_pointer<trivial *> == false
is_member_object_pointer<int trivial::*> == true
is_member_object_pointer<int (functional::*)()> == false
```

## <a name="requirements"></a>Требования

**Заголовок:** \<type_traits>

**Пространство имен:** std

## <a name="see-also"></a>См. также

[<type_traits>](../standard-library/type-traits.md)<br/>
[Класс is_member_pointer](../standard-library/is-member-pointer-class.md)<br/>
