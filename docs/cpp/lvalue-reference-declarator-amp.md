---
description: 'Дополнительные сведения о: декларатор ссылки lvalue: &amp;'
title: 'Декларатор ссылки lvalue: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 99160f0eac10922e95b131d4246f898b3f59705e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312284"
---
# <a name="lvalue-reference-declarator-amp"></a>Декларатор ссылки lvalue: &amp;

Содержит адрес объекта, но синтаксически ведет себя подобно объекту.

## <a name="syntax"></a>Синтаксис

```
type-id & cast-expression
```

## <a name="remarks"></a>Remarks

Ссылку lvalue можно считать другим именем для объекта. Объявление ссылки lvalue состоит из необязательного списка спецификаторов, за которым следует декларатор ссылки. Ссылка должна быть инициализирована и не может быть изменена.

Любой объект, адрес которого можно преобразовать в некоторый тип указателя, можно также преобразовать в аналогичный ссылочный тип. Например, любой объект, адрес которого можно преобразовать в тип `char *`, можно также преобразовать в тип `char &`.

Не путайте объявления ссылок с использованием [оператора взятия адреса](../cpp/address-of-operator-amp.md). Если `&` *идентификатору* предшествует тип, например **`int`** или **`char`** , *идентификатор* объявляется как ссылка на тип. Когда `&` *идентификатору* не предшествует тип, использование является оператором взятия адреса.

## <a name="example"></a>Пример

В следующем примере демонстрируется декларатор ссылки путем объявления объекта `Person` и ссылки на этот объект. Поскольку `rFriend` является ссылкой на `myFriend`, при обновлении любой из этих переменных изменяется один и тот же объект.

```cpp
// reference_declarator.cpp
// compile with: /EHsc
// Demonstrates the reference declarator.
#include <iostream>
using namespace std;

struct Person
{
    char* Name;
    short Age;
};

int main()
{
   // Declare a Person object.
   Person myFriend;

   // Declare a reference to the Person object.
   Person& rFriend = myFriend;

   // Set the fields of the Person object.
   // Updating either variable changes the same object.
   myFriend.Name = "Bill";
   rFriend.Age = 40;

   // Print the fields of the Person object to the console.
   cout << rFriend.Name << " is " << myFriend.Age << endl;
}
```

```Output
Bill is 40
```

## <a name="see-also"></a>См. также раздел

[Справочные материалы](../cpp/references-cpp.md)<br/>
[Аргументы функции ссылочного типа](../cpp/reference-type-function-arguments.md)<br/>
[Функции ссылочного типа возвращают](../cpp/reference-type-function-returns.md)<br/>
[Ссылки на указатели](../cpp/references-to-pointers.md)
