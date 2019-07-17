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
ms.openlocfilehash: 868909ac4346a59cade3660f288a0f0e71bc4ed0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245658"
---
# <a name="ltdequegt-operators"></a>Операторы &lt;deque&gt;

## <a name="op_neq"></a> оператор! =

Проверяет неравенство объекта deque слева от оператора объекту deque справа от оператора.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Слева*\
Объект типа `deque`.

*Правильно*\
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
```

```Output
The deques are not equal.
```

## <a name="op_lt"></a> Оператор&lt;

Проверяет, меньше ли объект deque слева от оператора объекта deque справа от оператора.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Слева*\
Объект типа `deque`.

*Правильно*\
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
```

```Output
Deque c1 is less than deque c2.
```

## <a name="op_lt_eq"></a> Оператор&lt;=

Проверяет, меньше или равен объект deque слева от оператора объекту deque справа от оператора.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Слева*\
Объект типа `deque`.

*Правильно*\
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
```

```Output
Deque c1 is less than or equal to deque c2.
```

## <a name="op_eq_eq"></a> оператор ==

Проверяет равенство объекта deque слева от оператора объекту deque справа от оператора.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Слева*\
Объект типа `deque`.

*Правильно*\
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
```

```Output
The deques are equal.
The deques are not equal.
```

## <a name="op_gt"></a> Оператор&gt;

Проверяет, больше ли объект deque слева от оператора объекта deque справа от оператора.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Слева*\
Объект типа `deque`.

*Правильно*\
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
```

```Output
Deque c1 is greater than deque c2.
```

## <a name="op_gt_eq"></a> Оператор&gt;=

Проверяет, больше или равен ли объект deque слева от оператора объекту deque справа от оператора.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Слева*\
Объект типа `deque`.

*Правильно*\
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
```

```Output
Deque c1 is greater than or equal to deque c2.
```
