---
description: 'Дополнительные сведения: класс Array (стандартная библиотека C++)'
title: Класс array (стандартная библиотека C++ ) | Документы Майкрософт
ms.date: 11/13/2019
f1_keywords:
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
helpviewer_keywords:
- std::array [C++]
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
- ', '
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
ms.openlocfilehash: ba5fe51420d2f81bfd2ba90b02fe530ba5441d3d
ms.sourcegitcommit: a89eac9acdbd54a181e3bd5d5bc71a3ef3c1abca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106506017"
---
# <a name="array-class-c-standard-library"></a>`array` Class (стандартная библиотека C++)

Описывает объект, управляющий последовательностью из элементов `N` типа `Ty`. Последовательность хранится как массив `Ty` в объекте `array<Ty, N>`.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>Параметры

`Ty`\
Тип элемента.

`N`\
Число элементов.

## <a name="members"></a>Элементы

|Определение типа|Описание|
|-|-|
|[`const_iterator`](#const_iterator)|Тип постоянного итератора для управляемой последовательности.|
|[`const_pointer`](#const_pointer)|Тип постоянного указателя на элемент.|
|[`const_reference`](#const_reference)|Тип постоянной ссылки на элемент.|
|[`const_reverse_iterator`](#const_reverse_iterator)|Тип постоянного обратного итератора для управляемой последовательности.|
|[`difference_type`](#difference_type)|Тип расстояния со знаком между двумя элементами.|
|[`iterator`](#iterator)|Тип итератора для управляемой последовательности.|
|[`pointer`](#pointer)|Тип указателя на элемент.|
|[`reference`](#reference)|Тип ссылки на элемент.|
|[`reverse_iterator`](#reverse_iterator)|Тип обратного итератора для управляемой последовательности.|
|[`size_type`](#size_type)|Тип беззнакового расстояния между двумя элементами.|
|[`value_type`](#value_type)|Тип элемента.|

|Функция-член|Описание|
|-|-|
|[`array`](#array)|Создает объект массива.|
|[`assign`](#assign)|Устаревшие. Используйте `fill` .) Заменяет все элементы.|
|[`at`](#at)|Обращается к элементу в указанной позиции.|
|[`back`](#back)|Обращается к последнему элементу.|
|[`begin`](#begin)|Задает начало управляемой последовательности.|
|[`cbegin`](#cbegin)|Возвращает постоянный итератор произвольного доступа, указывающий на первый элемент в массиве.|
|[`cend`](#cend)|Возвращает постоянный итератор произвольного доступа, указывающий на предпоследнюю позицию массива.|
|[`crbegin`](#crbegin)|Возвращает константный итератор, который указывает на первый элемент в обращенном массиве.|
|[`crend`](#crend)|Возвращает постоянный итератор, который указывает на последний элемент в обратном массиве.|
|[`data`](#data)|Получает адрес первого элемента.|
|[`empty`](#empty)|Проверяет наличие элементов.|
|[`end`](#end)|Задает конец управляемой последовательности.|
|[`fill`](#fill)|Заменяет все элементы указанным значением.|
|[`front`](#front)|Обращается к первому элементу.|
|[`max_size`](#max_size)|Подсчитывает количество элементов.|
|[`rbegin`](#rbegin)|Задает начало обратной управляемой последовательности.|
|[`rend`](#rend)|Задает конец обратной управляемой последовательности.|
|[`size`](#size)|Подсчитывает количество элементов.|
|[`swap`](#swap)|Меняет местами содержимое двух контейнеров.|

|Оператор|Описание|
|-|-|
|[`array::operator=`](#op_eq)|Заменяет управляемую последовательность.|
|[`array::operator[]`](#op_at)|Обращается к элементу в указанной позиции.|

## <a name="remarks"></a>Remarks

У этого типа есть конструктор по умолчанию `array()` и оператор присваивания по умолчанию `operator=`. Тип удовлетворяет требованиям для `aggregate`. Поэтому объекты типа `array<Ty, N>` можно инициализировать с помощью агрегатного инициализатора. Например,

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

создает объект `ai`, содержащий четыре целочисленных значения, инициализирует первые три элемента как 1, 2 и 3 соответственно и инициализирует четвертый элемент как 0.

## <a name="requirements"></a>Требования

**Заголовок:**`<array>`

**Пространство имен:** `std`

## <a name="arrayarray"></a><a name="array"></a> `array::array`

Создает объект массива.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Объект или диапазон для вставки.

### <a name="remarks"></a>Remarks

Конструктор по умолчанию `array()` оставляет управляемую последовательность неинициализированной (или инициализированной по умолчанию). Он используется для указания неинициализированной управляемой последовательности.

Конструктор копий `array(const array& right)` инициализирует управляемую последовательность с помощью последовательности [*right* `.begin()` , *right* `.end()` ). Он используется для указания начальной управляемой последовательности, которая является копией последовательности, управляемой объектом array *`right`* .

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    typedef std::array<int, 4> Myarray;

    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1(c0);

    // display contents " 0 1 2 3"
    for (const auto& it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arrayassign"></a><a name="assign"></a> `array::assign`

Устарело в C++ 11, заменено на [`fill`](#fill) . Заменяет все элементы.

## <a name="arrayat"></a><a name="at"></a> `array::at`

Обращается к элементу в указанной позиции.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Параметры

*`off`*\
Позиция элемента, к которому осуществляется доступ.

### <a name="remarks"></a>Remarks

Функции-члены возвращают ссылку на элемент управляемой последовательности в позиции *`off`* . Если эта позиция недопустима, функция выдает объект класса `out_of_range`.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
}
```

## <a name="arrayback"></a><a name="back"></a> `array::back`

Обращается к последнему элементу.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Remarks

Функции-члены возвращают ссылку на последний элемент управляемой последовательности, который должен быть не пустым.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    std::cout << " " << c0.back();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraybegin"></a><a name="begin"></a> `array::begin`

Задает начало управляемой последовательности.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>Remarks

Функции-члены возвращают итератор произвольного доступа, указывающий на первый элемент последовательности (или на место сразу за концом пустой последовательности)).

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::iterator it2 = c0.begin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arraycbegin"></a><a name="cbegin"></a> `array::cbegin`

Возвращает **`const`** итератор, который обращается к первому элементу в диапазоне.

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Возвращаемое значение

**`const`** Итератор произвольного доступа, указывающий на первый элемент диапазона, или расположение непосредственно за концом пустого диапазона (для пустого диапазона `cbegin() == cend()` ).

### <a name="remarks"></a>Remarks

Элементы в диапазоне нельзя изменить с помощью возвращаемого значения `cbegin`.

Эту функцию-член можно использовать вместо функции-члена `begin()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `begin()` и `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="arraycend"></a><a name="cend"></a> `array::cend`

Возвращает **`const`** итератор, который обращается к расположению сразу за последним элементом в диапазоне.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Возвращаемое значение

Итератор произвольного доступа, который указывает на место сразу после конца диапазона.

### <a name="remarks"></a>Remarks

`cend` используется для проверки того, прошел ли итератор конец диапазона.

Эту функцию-член можно использовать вместо функции-члена `end()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `end()` и `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Значение, возвращаемое `cend`, не должно быть подвергнуто удалению ссылки.

## <a name="arrayconst_iterator"></a><a name="const_iterator"></a> `array::const_iterator`

Тип постоянного итератора для управляемой последовательности.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Remarks

Этот тип описывает объект, который можно использовать в качестве постоянного итератора с произвольным доступом для управляемой последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::const_iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::const_iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3
it2: 0
```

## <a name="arrayconst_pointer"></a><a name="const_pointer"></a> `array::const_pointer`

Тип постоянного указателя на элемент.

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>Remarks

Этот тип описывает объект, который можно использовать в качестве постоянного указателя на элементы последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayconst_reference"></a><a name="const_reference"></a> `array::const_reference`

Тип постоянной ссылки на элемент.

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>Remarks

Тип описывает объект, который можно использовать в качестве постоянной ссылки на элемент управляемой последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> `array::const_reverse_iterator`

Тип постоянного обратного итератора для управляемой последовательности.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Remarks

Этот тип описывает объект, который можно использовать в качестве постоянного обратного итератора для управляемой последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraycrbegin"></a><a name="crbegin"></a> `array::crbegin`

Возвращает константный итератор, который указывает на первый элемент в обращенном массиве.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

Константный обратный итератор произвольного доступа, указывающий на первый элемент в обращенном массиве или на элемент, который был последним в массиве до его обращения.

### <a name="remarks"></a>Remarks

Если возвращается значение `crbegin`, то объект массива невозможно изменить.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator v1_Iter;
   array<int, 2>::const_reverse_iterator v1_rIter;

   v1_Iter = v1.begin( );
   cout << "The first element of array is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed array is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of array is 1.
The first element of the reversed array is 2.
```

## <a name="arraycrend"></a><a name="crend"></a> `array::crend`

Возвращает константный итератор, который обращается к месту, следующему за последним элементом в обращенном массиве.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Возвращаемое значение

Константный обратный итератор произвольного доступа, адресующий расположение после последнего элемента в обращенном массиве (расположение перед первым элементом в необращенном массиве).

### <a name="remarks"></a>Remarks

`crend` используется с обратным массивом точно так же, как [`array::cend`](#cend) используется с массивом.

Если возвращается значение `crend` (соответственно уменьшенное), объект массива нельзя изменить.

`crend` используется, чтобы проверить, достиг ли обратный итератор конца массива.

Значение, возвращаемое `crend`, не должно быть подвергнуто удалению ссылки.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::const_reverse_iterator v1_rIter;

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="arraydata"></a><a name="data"></a> `array::data`

Получает адрес первого элемента.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>Remarks

Функции-члены возвращают адрес первого элемента в управляемой последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = c0.data();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arraydifference_type"></a><a name="difference_type"></a> `array::difference_type`

Тип расстояния со знаком между двумя элементами.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Remarks

Тип целого числа со знаком описывает объект, который может представлять разницу между адресами любых двух элементов в управляемой последовательности. Это синоним для типа `std::ptrdiff_t`.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance first-last " -4"
    Myarray::difference_type diff = c0.begin() - c0.end();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
-4
```

## <a name="arrayempty"></a><a name="empty"></a> `array::empty`

Проверяет отсутствие элементов.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает значение true, только если `N == 0`.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display whether c0 is empty " false"
    std::cout << std::boolalpha << " " << c0.empty();
    std::cout << std::endl;

    std::array<int, 0> c1;

    // display whether c1 is empty " true"
    std::cout << std::boolalpha << " " << c1.empty();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
false
true
```

## <a name="arrayend"></a><a name="end"></a> `array::end`

Задает конец управляемой последовательности.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>Remarks

Первые две функции-члена возвращают итератор произвольного доступа, указывающий на место сразу за концом последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::iterator it2 = c0.end();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arrayfill"></a><a name="fill"></a> `array::fill`

Удаляет массив и копирует указанные элементы в пустой массив.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Параметры

*`val`*\
Значение элемента, вставляемого в массив.

### <a name="remarks"></a>Remarks

`fill` заменяет каждый элемент массива на указанное значение.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

int main()
{
    using namespace std;
    array<int, 2> v1 = { 1, 2 };

    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;

    v1.fill(3);
    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;
}
```

## <a name="arrayfront"></a><a name="front"></a> `array::front`

Обращается к первому элементу.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Remarks

Функции-члены возвращают ссылку на первый элемент управляемой последовательности, который должен быть не пустым.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    std::cout << " " << c0.front();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayiterator"></a><a name="iterator"></a> `array::iterator`

Тип итератора для управляемой последовательности.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Remarks

Этот тип описывает объект, который можно использовать в качестве итератора с произвольным доступом для управляемой последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3

it2: 0
```

## <a name="arraymax_size"></a><a name="max_size"></a> `array::max_size`

Подсчитывает количество элементов.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает значение `N`.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display (maximum) size " 4"
    std::cout << " " << c0.max_size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arrayoperator"></a><a name="op_at"></a> `array::operator[]`

Обращается к элементу в указанной позиции.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Параметры

*`off`*\
Позиция элемента, к которому осуществляется доступ.

### <a name="remarks"></a>Remarks

Функции-члены возвращают ссылку на элемент управляемой последовательности в позиции *`off`* . Если эта позиция недопустима, поведение станет неопределенным.

Также существует функция, не относящаяся к члену, [`get`](array-functions.md#get) для получения ссылки на элемент **`array`** .

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0[1];
    std::cout << " " << c0[3];
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
1 3
```

## <a name="arrayoperator"></a><a name="op_eq"></a> `array::operator=`

Заменяет управляемую последовательность.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Контейнер для копирования.

### <a name="remarks"></a>Remarks

Оператор члена присваивает каждый элемент *`right`* в соответствующем элементе управляемой последовательности, а затем возвращает **`*this`** . Он используется для замены управляемой последовательности копией управляемой последовательности в *`right`* .

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

    // display copied contents " 0 1 2 3"
        // display contents " 0 1 2 3"
    for (auto it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arraypointer"></a><a name="pointer"></a> `array::pointer`

Тип указателя на элемент.

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>Remarks

Этот тип описывает объект, который можно использовать в качестве указателя на элементы последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayrbegin"></a><a name="rbegin"></a> `array::rbegin`

Задает начало обратной управляемой последовательности.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Remarks

Первые две функции-члена возвращают обратный итератор, указывающий на место сразу за концом управляемой последовательности. Таким образом, задается начало обратной последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arrayreference"></a><a name="reference"></a> `array::reference`

Тип ссылки на элемент.

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>Remarks

Тип описывает объект, который можно использовать в качестве ссылки на элемент управляемой последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayrend"></a><a name="rend"></a> `array::rend`

Задает конец обратной управляемой последовательности.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Remarks

Функции-члены возвращают обратный итератор, указывающий на первый элемент последовательности (или непосредственно за окончание пустой последовательности)). Таким образом, он задает конец обратной последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reverse_iterator it2 = c0.rend();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayreverse_iterator"></a><a name="reverse_iterator"></a> `array::reverse_iterator`

Тип обратного итератора для управляемой последовательности.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Remarks

Этот тип описывает объект, который можно использовать в качестве обратного итератора для управляемой последовательности.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraysize"></a><a name="size"></a> `array::size`

Подсчитывает количество элементов.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает значение `N`.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display size " 4"
    std::cout << " " << c0.size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arraysize_type"></a><a name="size_type"></a> `array::size_type`

Тип беззнакового расстояния между двумя элементами.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Remarks

Целочисленный тип без знака описывает объект, который может представлять длину любой управляемой последовательности. Это синоним для типа `std::size_t`.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance last-first " 4"
    Myarray::size_type diff = c0.end() - c0.begin();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arrayswap"></a><a name="swap"></a> `array::swap`

Выполняет обмен содержимым между этим и другим массивом.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Массив для обмена содержимым.

### <a name="remarks"></a>Remarks

Функция – член меняет местами управляемые последовательности между **`*this`** и *вправо*. Он выполняет присваивания элементов и вызовы конструктора у количестве, пропорционально пропорциональном `N`.

Также существует функция, не относящаяся к члену, [`swap`](array-functions.md#swap) для переключения двух **`array`** экземпляров.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="arrayvalue_type"></a><a name="value_type"></a> `array::value_type`

Тип элемента.

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>Remarks

Этот тип является синонимом для параметра шаблона `Ty`.

### <a name="example"></a>Пример

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        Myarray::value_type val = it;
        std::cout << " " << val;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>См. также раздел

[`<array>`](../standard-library/array.md)
