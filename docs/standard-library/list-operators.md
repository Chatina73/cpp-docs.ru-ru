---
description: 'Дополнительные сведения: &lt; список &gt; операторов'
title: Операторы &lt;list&gt;
ms.date: 11/04/2016
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: 86f032a201943e6b42a997c2fc6ff29df353351e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284698"
---
# <a name="ltlistgt-operators"></a>Операторы &lt;list&gt;

## <a name="operator"></a><a name="op_neq"></a> operator! =

Проверяет неравенство объекта-списка слева от оператора объекту-списку справа от оператора.

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `list`.

*Правильно*\
Объект типа `list`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если списки не равны; **`false`** значение, если списки равны.

### <a name="remarks"></a>Комментарии

Сравнение между объектами списков основывается на попарном сравнении элементов этих списков. Два списка равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// list_op_ne.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
using namespace std;
list <int> c1, c2;
c1.push_back( 1 );
c2.push_back( 2 );

if ( c1 != c2 )
cout << "Lists not equal." << endl;
else
cout << "Lists equal." << endl;
}
/* Output:
Lists not equal.
*/
```

## <a name="operatorlt"></a><a name="op_lt"></a> станции&lt;

Проверяет, меньше ли объект-список слева от оператора, чем объект-список справа от оператора.

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `list`.

*Правильно*\
Объект типа `list`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если список слева от оператора меньше, но не равен списку с правой стороны оператора; в противном случае — значение **`false`** .

### <a name="remarks"></a>Комментарии

Сравнение между объектами списков основывается на попарном сравнении элементов этих списков. Отношение «меньше» между двумя объектами основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// list_op_lt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "List c1 is less than list c2." << endl;
   else
      cout << "List c1 is not less than list c2." << endl;
}
/* Output:
List c1 is less than list c2.
*/
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> станции&lt;=

Проверяет, что объект-список слева от оператора меньше или равен объекту-списку справа от оператора.

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `list`.

*Правильно*\
Объект типа `list`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если список слева от оператора меньше или равен списку с правой стороны оператора; в противном случае — значение **`false`** .

### <a name="remarks"></a>Комментарии

Сравнение между объектами списков основывается на попарном сравнении элементов этих списков. Отношение «меньше или равно» между двумя объектами основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// list_op_le.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "List c1 is less than or equal to list c2." << endl;
   else
      cout << "List c1 is greater than list c2." << endl;
}
/* Output:
List c1 is less than or equal to list c2.
*/
```

## <a name="operator"></a><a name="op_eq_eq"></a> Оператор = =

Проверяет, равен ли объект-список слева от оператора объекту-списку справа от оператора.

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `list`.

*Правильно*\
Объект типа `list`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если список слева от оператора равен списку с правой стороны оператора; в противном случае — значение **`false`** .

### <a name="remarks"></a>Комментарии

Сравнение между объектами списков основывается на попарном сравнении элементов этих списков. Два списка равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// list_op_eq.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;

   list <int> c1, c2;
   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The lists are equal." << endl;
   else
      cout << "The lists are not equal." << endl;
}
/* Output:
The lists are equal.
*/
```

## <a name="operatorgt"></a><a name="op_gt"></a> станции&gt;

Проверяет, больше ли объект-список слева от оператора, чем объект-список справа от оператора.

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `list`.

*Правильно*\
Объект типа `list`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если список в левой части оператора больше списка с правой стороны оператора; в противном случае — значение **`false`** .

### <a name="remarks"></a>Комментарии

Сравнение между объектами списков основывается на попарном сравнении элементов этих списков. Отношение «больше» между двумя объектами основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// list_op_gt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "List c1 is greater than list c2." << endl;
   else
      cout << "List c1 is not greater than list c2." << endl;
}
/* Output:
List c1 is greater than list c2.
*/
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> станции&gt;=

Проверяет, что объект-список слева от оператора больше или равен объекту-списку справа от оператора.

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `list`.

*Правильно*\
Объект типа `list`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если список слева от оператора больше или равен списку с правой стороны оператора; в противном случае — значение **`false`** .

### <a name="remarks"></a>Комментарии

Сравнение между объектами списков основывается на попарном сравнении элементов этих списков. Отношение «больше или равно» между двумя объектами основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// list_op_ge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "List c1 is greater than or equal to list c2." << endl;
   else
      cout << "List c1 is less than list c2." << endl;
}
/* Output:
List c1 is greater than or equal to list c2.
*/
```
