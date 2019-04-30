---
title: Операторы &lt;deque&gt;
ms.date: 11/04/2016
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: a5e88d421df2746cf2ca0aab5be4c19953162559
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394004"
---
# <a name="ltdequegt-operators"></a>Операторы &lt;deque&gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[оператор&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[оператор&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

Проверяет неравенство объекта deque слева от оператора объекту deque справа от оператора.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*left*<br/>
Объект типа `deque`.

*right*<br/>
Объект типа `deque`.

### <a name="return-value"></a>Возвращаемое значение

Значение **true**, если объекты deque не равны, значение **false**, если объекты deque равны.

### <a name="remarks"></a>Примечания

Сравнение между объектами deque основывается на попарном сравнении элементов этих списков. Два объекта deque, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// deque_op_ne.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 2 );

   if ( c1 != c2 )
      cout << "The deques are not equal." << endl;
   else
      cout << "The deques are equal." << endl;
}
/* Output:
The deques are not equal.
*/
```

## <a name="op_lt"></a> operator&lt;

Проверяет, меньше ли объект deque слева от оператора объекта deque справа от оператора.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*left*<br/>
Объект типа `deque`.

*right*<br/>
Объект типа `deque`.

### <a name="return-value"></a>Возвращаемое значение

**true**, если объект deque слева от оператора меньше объекта deque справа от оператора (и не равен ему); в противном случае **false**.

### <a name="remarks"></a>Примечания

Сравнение между объектами deque основывается на попарном сравнении элементов этих списков. Отношение «меньше» между двумя объектами основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// deque_op_lt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "Deque c1 is less than deque c2." << endl;
   else
      cout << "Deque c1 is not less than deque c2." << endl;
}
/* Output:
Deque c1 is less than deque c2.
*/
```

## <a name="op_lt_eq"></a> operator&lt;=

Проверяет, меньше или равен объект deque слева от оператора объекту deque справа от оператора.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*left*<br/>
Объект типа `deque`.

*right*<br/>
Объект типа `deque`.

### <a name="return-value"></a>Возвращаемое значение

**true**, если объект deque слева от оператора меньше объекта deque справа от оператора (или равен ему); в противном случае **false**.

### <a name="remarks"></a>Примечания

Сравнение между объектами deque основывается на попарном сравнении элементов этих списков. Отношение «меньше или равно» между двумя объектами основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// deque_op_le.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "Deque c1 is less than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is greater than deque c2." << endl;
}
/* Output:
Deque c1 is less than or equal to deque c2.
*/
```

## <a name="op_eq_eq"></a> operator==

Проверяет равенство объекта deque слева от оператора объекту deque справа от оператора.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*left*<br/>
Объект типа `deque`.

*right*<br/>
Объект типа `deque`.

### <a name="return-value"></a>Возвращаемое значение

**true**, если объект deque слева от оператора равен объекту deque справа от оператора; в противном случае **false**.

### <a name="remarks"></a>Примечания

Сравнение между объектами deque основывается на попарном сравнении элементов этих списков. Два объекта deque равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// deque_op_eq.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;

   c1.push_back( 1 );
   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;
}
/* Output:
The deques are equal.
The deques are not equal.
*/
```

## <a name="op_gt"></a> operator&gt;

Проверяет, больше ли объект deque слева от оператора объекта deque справа от оператора.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*left*<br/>
Объект типа `deque`.

*right*<br/>
Объект типа `deque`.

### <a name="return-value"></a>Возвращаемое значение

**true**, если объект deque слева от оператора больше объекта deque справа от оператора; в противном случае **false**.

### <a name="remarks"></a>Примечания

Сравнение между объектами deque основывается на попарном сравнении элементов этих списков. Отношение «больше» между двумя объектами основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// deque_op_gt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "Deque c1 is greater than deque c2." << endl;
   else
      cout << "Deque c1 is not greater than deque c2." << endl;
}
/* Output:
Deque c1 is greater than deque c2.
*/
```

## <a name="op_gt_eq"></a> operator&gt;=

Проверяет, больше или равен ли объект deque слева от оператора объекту deque справа от оператора.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*left*<br/>
Объект типа `deque`.

*right*<br/>
Объект типа `deque`.

### <a name="return-value"></a>Возвращаемое значение

**true**, если объект deque слева от оператора больше объекта deque справа от оператора (или равен ему); в противном случае **false**.

### <a name="remarks"></a>Примечания

Сравнение между объектами deque основывается на попарном сравнении элементов этих списков. Отношение «больше или равно» между двумя объектами основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// deque_op_ge.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "Deque c1 is greater than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is less than deque c2." << endl;
}
/* Output:
Deque c1 is greater than or equal to deque c2.
*/
```

## <a name="see-also"></a>См. также

[\<deque>](../standard-library/deque.md)<br/>
