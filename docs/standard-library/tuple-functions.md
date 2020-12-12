---
description: 'Дополнительные сведения: &lt; функции кортежей &gt;'
title: Функции &lt;tuple&gt;
ms.date: 11/04/2016
f1_keywords:
- tuple/std::get
- tuple/std::make_tuple
- tuple/std::tie
ms.assetid: bc6be38f-5258-4c14-b81b-63caa335fd44
helpviewer_keywords:
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
ms.openlocfilehash: cf58cab5f222594a935156cf7e7f2e886639da2b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168960"
---
# <a name="lttuplegt-functions"></a>Функции &lt;tuple&gt;

## <a name="apply"></a><a name="apply"></a> касаться

```cpp
template <class F, class Tuple> constexpr decltype(auto) apply(F&& f, Tuple&& t);
```

### <a name="remarks"></a>Комментарии

Вызывает функцию *F* с кортежем *t*.

## <a name="forward_as_tuple"></a><a name="forward"></a> forward_as_tuple

```cpp
template <class... TTypes>
    constexpr tuple<TTypes&&...> forward_as_tuple(TTypes&&...) noexcept;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает `tuple<TTypes&&...>(std::forward<TTypes>(t)...)`.

### <a name="remarks"></a>Комментарии

Конструирует кортеж ссылок на аргументы в *t* , подходящие для пересылки в качестве аргументов в функцию.

## <a name="get"></a><a name="get"></a> Получить

Получает элемент из объекта `tuple` по индексу или по типу (в C++14).

```cpp
// by index:
// get reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>& get(tuple<Types...>& Tuple) noexcept;

// get const reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr const tuple_element_t<Index, tuple<Types...>>& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>&& get(tuple<Types...>&& Tuple) noexcept;

// (C++14) by type:
// get reference to T element of tuple
template <class T, class... Types>
   constexpr T& get(tuple<Types...>& Tuple) noexcept;

// get const reference to T element of tuple
template <class T, class... Types>
   constexpr const T& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to T element of tuple
template <class T, class... Types>
   constexpr T&& get(tuple<Types...>&& Tuple) noexcept;
```

### <a name="parameters"></a>Параметры

*Номер*\
Индекс элемента, который нужно получить.

*Типов*\
Последовательность типов, заявленных в кортеж, в порядке объявления.

*T*\
Тип элемента, который нужно получить.

*Кортеж*\
Значение типа `std::tuple` , содержащее любое количество элементов.

### <a name="remarks"></a>Комментарии

Функции-шаблоны возвращают ссылку на значение *по индексу индекса или* типа *T* в `tuple` объекте.

Вызов функции `get<T>(Tuple)` приведет к ошибке компилятора, если кортеж содержит больше или меньше одного элемента типа T.

### <a name="example"></a>Пример

```cpp
#include <tuple>
#include <iostream>
#include <string>

using namespace std;

int main() {
    tuple<int, double, string> tup(0, 1.42, "Call me Tuple");

    // get elements by index
    cout << " " << get<0>(tup);
    cout << " " << get<1>(tup);
    cout << " " << get<2>(tup) << endl;

    // get elements by type
    cout << " " << get<int>(tup);
    cout << " " << get<double>(tup);
    cout << " " << get<string>(tup) << endl;
}
```

```Output
0 1.42 Call me Tuple
0 1.42 Call me Tuple
```

## <a name="make_from_tuple"></a><a name="make_from_tuple"></a> make_from_tuple

```cpp
template <class T, class Tuple> constexpr T make_from_tuple(Tuple&& t);
```

### <a name="remarks"></a>Комментарии

Эквивалентно `return make_from_tuple_impl<T>(forward<Tuple>(t), make_index_sequence<tuple_size_v<decay_t<Tuple>>>{})`.

## <a name="make_tuple"></a><a name="make_tuple"></a> make_tuple

Создает `tuple` из значений элементов.

```cpp
template <class T1, class T2, ..., class TN>
   tuple<V1, V2, ..., VN> make_tuple(const T1& t1, const T2& t2, ..., const TN& tN);
```

### <a name="parameters"></a>Параметры

*КОД*\
Тип этого N-ного параметра функции.

*Код*\
Значение N-ного параметра функции.

### <a name="remarks"></a>Комментарии

Функция-шаблон возвращает `tuple<V1, V2, ..., VN>(t1, t2, ..., tN)` , где каждый тип `Vi` имеет значение, `X&` если соответствующий тип. `Ti` `cv` `reference_wrapper<X>` в противном случае — значение `Ti` .

Одно из преимуществ `make_tuple` заключается в том, что сохраненные типы объектов автоматически определяются компилятором, и их не требуется задавать явным образом. Не используйте явные аргументы шаблона, например `make_tuple<int, int>(1, 2)`, при использовании `make_tuple`, так как для них характерна избыточная подробность, которая создает дополнительные проблемы со сложными ссылками rvalue, способные вызвать сбой компиляции.

### <a name="example"></a>Пример

```cpp
// std__tuple__make_tuple.cpp
// compile by using: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    c0 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
```

## <a name="swap"></a><a name="swap"></a> позиции

```cpp
template <class... Types>
    void swap(tuple<Types...>& x, tuple<Types...>& y) noexcept(see below );
```

## <a name="tie"></a><a name="tie"></a> привязать

Создает `tuple` из ссылок на элементы.

```cpp
template <class T1, class T2, ..., class TN>
tuple<T1&, T2&, ..., TN&> tie(T1& t1, T2& t2, ..., TN& tN);
```

### <a name="parameters"></a>Параметры

*КОД*\
Базовый тип N-го элемента кортежа.

### <a name="remarks"></a>Комментарии

Функция шаблона возвращает `tuple<T1&, T2&, ..., TN&>(t1, t2, ..., tN)`.

### <a name="example"></a>Пример

```cpp
// std__tuple__tie.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    int v4 = 4;
    double v5 = 5;
    int v6 = 6;
    double v7 = 7;
    std::tie(v4, v5, v6, v7) = c0;

// display contents " 0 1 2 3"
    std::cout << " " << v4;
    std::cout << " " << v5;
    std::cout << " " << v6;
    std::cout << " " << v7;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="tuple_cat"></a><a name="tuple_cat"></a> tuple_cat

```cpp
template <class... Tuples> constexpr tuple<CTypes...> tuple_cat(Tuples&&...);
```

### <a name="return-value"></a>Возвращаемое значение

Объект кортежа, созданный путем инициализации каждого элемента типа.

## <a name="tuple_element_t"></a><a name="tuple_element_t"></a> tuple_element_t

```cpp
template <size_t I, class T>
    using tuple_element_t = typename tuple_element<I, T>::type;
```

## <a name="tuple_size_v"></a><a name="tuple_size_v"></a> tuple_size_v

```cpp
template <class T>
    inline constexpr size_t tuple_size_v = tuple_size<T>::value;
```
