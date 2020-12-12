---
description: 'Дополнительные сведения: &lt; операторы потоков &gt;'
title: Операторы &lt;thread&gt;
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 3992dccf051622bcf854c1843f1bdeb15d227731
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207427"
---
# <a name="ltthreadgt-operators"></a>Операторы &lt;thread&gt;

[operator! =](#op_neq)\
[станции&gt;](#op_gt)\
[станции&gt;=](#op_gt_eq)\
[станции&lt;](#op_lt)\
[станции&lt;&lt;](#op_lt_lt)\
[станции&lt;=](#op_lt_eq)\
[Оператор = =](#op_eq_eq)

## <a name="operatorgt"></a><a name="op_gt_eq"></a> станции&gt;=

Определяет, справедливо ли, что один из объектов `thread::id` больше другого или равен ему.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Параметры

*Слева*\
Левый объект `thread::id`.

*Правильно*\
Правой объект `thread::id`.

### <a name="return-value"></a>Возвращаемое значение

`!(Left < Right)`

### <a name="remarks"></a>Комментарии

Эта функция не вызывает исключений.

## <a name="operatorgt"></a><a name="op_gt"></a> станции&gt;

Определяет, справедливо ли, что один из объектов `thread::id` больше другого или равен ему.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Параметры

*Слева*\
Левый объект `thread::id`.

*Правильно*\
Правой объект `thread::id`.

### <a name="return-value"></a>Возвращаемое значение

`Right < Left`

### <a name="remarks"></a>Комментарии

Эта функция не вызывает исключений.

## <a name="operatorlt"></a><a name="op_lt_eq"></a> станции&lt;=

Определяет, справедливо ли, что один из объектов `thread::id` меньше другого или равен ему.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Параметры

*Слева*\
Левый объект `thread::id`.

*Правильно*\
Правой объект `thread::id`.

### <a name="return-value"></a>Возвращаемое значение

`!(Right < Left)`

### <a name="remarks"></a>Комментарии

Эта функция не вызывает исключений.

## <a name="operatorlt"></a><a name="op_lt"></a> станции&lt;

Определяет, справедливо ли, что один объект `thread::id` меньше другого.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Параметры

*Слева*\
Левый объект `thread::id`.

*Правильно*\
Правой объект `thread::id`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если *Left* стоит *справа* в общем порядке; в противном случае — **`false`** .

### <a name="remarks"></a>Комментарии

Оператор определяет общий порядок всех объектов `thread::id`. Эти объекты могут использоваться в качестве ключей в ассоциативных контейнерах.

Эта функция не вызывает исключений.

## <a name="operator"></a><a name="op_neq"></a> operator! =

Проверяет неравенство двух объектов `thread::id`.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Параметры

*Слева*\
Левый объект `thread::id`.

*Правильно*\
Правой объект `thread::id`.

### <a name="return-value"></a>Возвращаемое значение

`!(Left == Right)`

### <a name="remarks"></a>Комментарии

Эта функция не вызывает исключений.

## <a name="operator"></a><a name="op_eq_eq"></a> Оператор = =

Сравнивает два объекта `thread::id` на равенство.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Параметры

*Слева*\
Левый объект `thread::id`.

*Правильно*\
Правой объект `thread::id`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если два объекта представляют один и тот же поток выполнения или если ни один из объектов не представляет поток выполнения; в противном случае — **`false`** .

### <a name="remarks"></a>Комментарии

Эта функция не вызывает исключений.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> станции&lt;&lt;

Вставляет текстовое представление объекта `thread::id` в поток.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Параметры

*OSTR*\
Объект [basic_ostream](../standard-library/basic-ostream-class.md).

*Удостоверения*\
Объект `thread::id`.

### <a name="return-value"></a>Возвращаемое значение

*OSTR*.

### <a name="remarks"></a>Комментарии

Эта функция вставляет *идентификатор* в *OSTR*.

Если два объекта `thread::id` равны, вставленные текстовые представления этих объектов совпадают.

## <a name="see-also"></a>См. также раздел

[\<thread>](../standard-library/thread.md)
