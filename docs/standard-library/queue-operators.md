---
description: 'Дополнительные сведения: &lt; операторы очереди &gt;'
title: Операторы &lt;queue&gt;
ms.date: 11/04/2016
f1_keywords:
- queue/std::operator!=
- queue/std::operator&gt;
- queue/std::operator&gt;=
- queue/std::operator&lt;
- queue/std::operator&lt;=
- queue/std::operator==
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
helpviewer_keywords:
- std::operator!= (queue)
- std::operator&gt; (queue)
- std::operator&gt;= (queue)
- std::operator&lt; (queue)
- std::operator&lt;= (queue)
- std::operator== (queue)
ms.openlocfilehash: 6d6280ca4fe1e1277a79862a5016d55dfbecc425
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327582"
---
# <a name="ltqueuegt-operators"></a>Операторы &lt;queue&gt;

## <a name="operator"></a><a name="op_neq"></a> operator! =

Проверяет неравенство объекта queue слева от оператора объекту queue справа от оператора.

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `queue`.

*Правильно*\
Объект типа `queue`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если очереди не равны; значение **`false`** , если очереди равны.

### <a name="remarks"></a>Комментарии

Сравнение объектов-очередей основывается на попарном сравнении их элементов. Две очереди равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// queue_op_ne.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a> станции&lt;

Проверяет, меньше ли объект queue слева от оператора, чем объект queue справа от оператора.

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `queue`.

*Правильно*\
Объект типа `queue`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** Если очередь в левой части оператора меньше и не равна очереди в правой части оператора; в противном случае — значение **`false`** .

### <a name="remarks"></a>Комментарии

Сравнение объектов-очередей основывается на попарном сравнении их элементов. Отношение "меньше" между двумя объектами-очередями основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// queue_op_lt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 < q2 )
      cout << "The queue q1 is less than the queue q2." << endl;
   else
      cout << "The queue q1 is not less than the queue q2." << endl;

   if ( q1 < q3 )
      cout << "The queue q1 is less than the queue q3." << endl;
   else
      cout << "The queue q1 is not less than the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is not less than the queue q3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> станции&lt;=

Проверяет, меньше ли объект queue слева от оператора, чем объект queue справа от оператора, или равен ему.

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `queue`.

*Правильно*\
Объект типа `queue`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** Если очередь в левой части оператора строго меньше очереди с правой стороны оператора; в противном случае — значение **`false`** .

### <a name="remarks"></a>Комментарии

Сравнение объектов-очередей основывается на попарном сравнении их элементов. Отношение "меньше или равно" между двумя объектами-очередями основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// queue_op_le.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 5 );
   q1.push( 10 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 5 );
   q3.push( 10 );

   if ( q1 <= q2 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;

   if ( q1 <= q3 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is greater than the queue q2.
The queue q1 is less than or equal to the queue q3.
```

## <a name="operator"></a><a name="op_eq_eq"></a> Оператор = =

Проверяет равенство объекта-очереди слева от оператора объекту-очереди справа от оператора.

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `queue`.

*Правильно*\
Объект типа `queue`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если очереди не равны; значение **`false`** , если очереди равны.

### <a name="remarks"></a>Комментарии

Сравнение объектов-очередей основывается на попарном сравнении их элементов. Две очереди равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// queue_op_eq.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a> станции&gt;

Проверяет, больше ли объект queue слева от оператора, чем объект queue справа от оператора.

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `queue`.

*Правильно*\
Объект типа `queue`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** Если очередь в левой части оператора строго меньше очереди с правой стороны оператора; в противном случае — значение **`false`** .

### <a name="remarks"></a>Комментарии

Сравнение объектов-очередей основывается на попарном сравнении их элементов. Отношение "больше" между двумя объектам-очередями основывается на сравнении первой пары неравных элементов.

### <a name="example"></a>Пример

```cpp
// queue_op_gt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q1.push( 3 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 > q2 )
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q2." << endl;

   if ( q1> q3 )
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is not greater than the queue q2.
The queue q1 is greater than the queue q3.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> станции&gt;=

Проверяет, больше ли объект queue слева от оператора, чем объект queue справа от оператора, или равен ему.

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `queue`.

*Правильно*\
Объект типа `queue`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** Если очередь в левой части оператора строго меньше очереди с правой стороны оператора; в противном случае — значение **`false`** .

### <a name="remarks"></a>Комментарии

Сравнение объектов-очередей основывается на попарном сравнении их элементов. Две очереди равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// queue_op_ge.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 >= q2 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q2." << endl;

   if ( q1>= q3 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is greater than or equal to the queue q3.
```
