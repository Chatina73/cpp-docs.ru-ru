---
title: Класс unordered_map
description: Справочник по API для класса контейнера стандартной библиотеки C++ `unordered_map` , который управляет последовательностью элементов различной длины.
ms.date: 9/9/2020
f1_keywords:
- unordered_map/std::unordered_map
- unordered_map/std::unordered_map::allocator_type
- unordered_map/std::unordered_map::const_iterator
- unordered_map/std::unordered_map::const_local_iterator
- unordered_map/std::unordered_map::const_pointer
- unordered_map/std::unordered_map::const_reference
- unordered_map/std::unordered_map::difference_type
- unordered_map/std::unordered_map::hasher
- unordered_map/std::unordered_map::iterator
- unordered_map/std::unordered_map::key_equal
- unordered_map/std::unordered_map::key_type
- unordered_map/std::unordered_map::local_iterator
- unordered_map/std::unordered_map::mapped_type
- unordered_map/std::unordered_map::pointer
- unordered_map/std::unordered_map::reference
- unordered_map/std::unordered_map::size_type
- unordered_map/std::unordered_map::value_type
- unordered_map/std::unordered_map::at
- unordered_map/std::unordered_map::begin
- unordered_map/std::unordered_map::bucket
- unordered_map/std::unordered_map::bucket_count
- unordered_map/std::unordered_map::bucket_size
- unordered_map/std::unordered_map::cbegin
- unordered_map/std::unordered_map::cend
- unordered_map/std::unordered_map::clear
- unordered_map/std::unordered_map::contains
- unordered_map/std::unordered_map::count
- unordered_map/std::unordered_map::emplace
- unordered_map/std::unordered_map::emplace_hint
- unordered_map/std::unordered_map::empty
- unordered_map/std::unordered_map::end
- unordered_map/std::unordered_map::equal_range
- unordered_map/std::unordered_map::erase
- unordered_map/std::unordered_map::find
- unordered_map/std::unordered_map::get_allocator
- unordered_map/std::unordered_map::hash
- unordered_map/std::unordered_map::insert
- unordered_map/std::unordered_map::key_eq
- unordered_map/std::unordered_map::load_factor
- unordered_map/std::unordered_map::max_bucket_count
- unordered_map/std::unordered_map::max_load_factor
- unordered_map/std::unordered_map::max_size
- unordered_map/std::unordered_map::rehash
- unordered_map/std::unordered_map::size
- unordered_map/std::unordered_map::swap
- unordered_map/std::unordered_map::unordered_map
- unordered_map/std::unordered_map::hash_function
helpviewer_keywords:
- std::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::contains
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
- std::unordered_map::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash_function
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
ms.openlocfilehash: bb03215fd32159cd45fe5bc8780b77623def5f10
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721580"
---
# <a name="unordered_map-class"></a>Класс `unordered_map`

Шаблон класса описывает объект, управляющий последовательностью элементов типа с различной длиной `std::pair<const Key, Ty>` . Последовательность слабо упорядочена хэш-функцией, которая разделяет последовательность в упорядоченный набор подпоследовательностей, называемых блоками. В каждом блоке функция сравнения определяет, упорядочена ли каждая пара элементов соответствующим образом. Каждый элемент содержит два объекта: ключ и значение сортировки. Последовательность представляется в виде, позволяющем выполнять поиск, вставку и удаление произвольного элемента несколькими операциями, которые могут не зависеть от числа элементов в последовательности (постоянное время), по крайней мере, когда все блоки имеют примерно одинаковую длину. В худшем случае, когда все элементы находятся в одном блоке, количество операций пропорционально количеству элементов в последовательности (линейное время). Кроме того, вставка элементов не делает итераторы недействительными, а при удалении элементов недействительными становятся только итераторы, указывающие на удаленный элемент.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Key,
    class Ty,
    class Hash = std::hash<Key>,
    class Pred = std::equal_to<Key>,
    class Alloc = std::allocator<std::pair<const Key, Ty>>>
class unordered_map;
```

### <a name="parameters"></a>Параметры

*`Key`*\
Тип ключа.

*`Ty`*\
Сопоставленный тип.

*`Hash`*\
Тип объекта хэш-функции.

*`Pred`*\
Тип объекта функции сравнения на предмет равенства.

*`Alloc`*\
Класс распределителя.

## <a name="members"></a>Элементы

|Определение типа|Описание|
|-|-|
|[`allocator_type`](#allocator_type)|Тип распределителя для управления хранилищем.|
|[`const_iterator`](#const_iterator)|Тип постоянного итератора для управляемой последовательности.|
|[`const_local_iterator`](#const_local_iterator)|Тип постоянного итератора блока для управляемой последовательности.|
|[`const_pointer`](#const_pointer)|Тип постоянного указателя на элемент.|
|[`const_reference`](#const_reference)|Тип постоянной ссылки на элемент.|
|[`difference_type`](#difference_type)|Тип расстояния со знаком между двумя элементами.|
|[`hasher`](#hasher)|Тип хэш-функции.|
|[`iterator`](#iterator)|Тип итератора для управляемой последовательности.|
|[`key_equal`](#key_equal)|Тип функции сравнения.|
|[`key_type`](#key_type)|Тип ключа упорядочения.|
|[`local_iterator`](#local_iterator)|Тип итератора блока для управляемой последовательности.|
|[`mapped_type`](#mapped_type)|Тип сопоставленного значения, связанного с каждым ключом.|
|[`pointer`](#pointer)|Тип указателя на элемент.|
|[`reference`](#reference)|Тип ссылки на элемент.|
|[`size_type`](#size_type)|Тип беззнакового расстояния между двумя элементами.|
|[`value_type`](#value_type)|Тип элемента.|

|Функция-член|Описание|
|-|-|
|[`at`](#at)|Поиск элемента с заданным ключом.|
|[`begin`](#begin)|Задает начало управляемой последовательности.|
|[`bucket`](#bucket)|Получает номер блока для значения ключа.|
|[`bucket_count`](#bucket_count)|Получает количество блоков.|
|[`bucket_size`](#bucket_size)|Получает размер блока.|
|[`cbegin`](#cbegin)|Задает начало управляемой последовательности.|
|[`cend`](#cend)|Задает конец управляемой последовательности.|
|[`clear`](#clear)|Удаляет все элементы.|
|[`count`](#count)|Определяет количество элементов, соответствующих заданному ключу.|
|[`contains`](#contains)<sup>C++ 20</sup>|Проверьте, существует ли элемент с указанным ключом в `unordered_map` .|
|[`emplace`](#emplace)|Добавляет элемент, созданный на месте.|
|[`emplace_hint`](#emplace_hint)|Добавляет элемент, созданный на месте, с подсказкой.|
|[`empty`](#empty)|Проверяет отсутствие элементов.|
|[`end`](#end)|Задает конец управляемой последовательности.|
|[`equal_range`](#equal_range)|Находит диапазон, соответствующий указанному ключу.|
|[`erase`](#erase)|Удаляет элементы в указанных позициях.|
|[`find`](#find)|Определяет элемент, соответствующий указанному ключу.|
|[`get_allocator`](#get_allocator)|Возвращает сохраненный объект распределителя.|
|[`hash_function`](#hash)|Получает сохраненный объект хэш-функции.|
|[`insert`](#insert)|Добавляет элементы.|
|[`key_eq`](#key_eq)|Получает сохраненный объект функции сравнения.|
|[`load_factor`](#load_factor)|Подсчитывает среднее число элементов в блоке.|
|[`max_bucket_count`](#max_bucket_count)|Получает максимальное количество блоков.|
|[`max_load_factor`](#max_load_factor)|Возвращает или задает максимальное количество элементов в блоке.|
|[`max_size`](#max_size)|Возвращает максимальный размер управляемой последовательности.|
|[`rehash`](#rehash)|Повторно создает хэш-таблицу.|
|[`size`](#size)|Подсчитывает количество элементов.|
|[`swap`](#swap)|Меняет местами содержимое двух контейнеров.|
|[`unordered_map`](#unordered_map)|Создает объект контейнера.|

|Оператор|Описание|
|-|-|
|[`unordered_map::operator[]`](#op_at)|Находит или вставляет элемент с указанным ключом.|
|[`unordered_map::operator=`](#op_eq)|Копирует хэш-таблицу.|

## <a name="remarks"></a>Замечания

Объект упорядочивает последовательность, которую он управляет, вызывая два сохраненных объекта, объект функции сравнения типа [`unordered_map::key_equal`](#key_equal) и объект хэш-функции типа [`unordered_map::hasher`](#hasher) . Доступ к первому сохраненному объекту осуществляется путем вызова функции члена [`unordered_map::key_eq`](#key_eq) `()` ; доступ к второму сохраненному объекту осуществляется путем вызова функции члена [`unordered_map::hash_function`](#hash) `()` . В частности, для всех значений `X` и `Y` типа `Key` вызов `key_eq()(X, Y)` возвращает значение true, только если два значения аргументов имеют соответствующий порядок; вызов `hash_function()(keyval)` создает распределение значений типа `size_t`. В отличие от [ `unordered_multimap` класса](../standard-library/unordered-multimap-class.md)шаблона класса, объект типа `unordered_map` гарантирует, что `key_eq()(X, Y)` всегда имеет значение false для любого из двух элементов управляемой последовательности. (Ключи уникальны).

Объект также хранит максимальный коэффициент нагрузки, который определяет максимальное желаемое среднее количество элементов в блоке. Если вставка элемента приводит к [`unordered_map::load_factor`](#load_factor) `()` превышению максимального коэффициента загрузки, контейнер увеличивает количество сегментов и перестраивает хэш-таблицу по мере необходимости.

Фактический порядок элементов в управляемой последовательности зависит от хэш-функции, функции сравнения, порядка вставки, максимального коэффициента нагрузки и текущего числа блоков. Обычно невозможно предсказать порядок элементов в управляемой последовательности. Однако всегда можно сохранять уверенность, что любое подмножество элементов, имеющих соответствующий порядок, будет расположено по соседству в управляемой последовательности.

Объект выделяет и освобождает хранилище для последовательности, управление которой осуществляется с помощью сохраненного объекта распределителя типа [`unordered_map::allocator_type`](#allocator_type) . Такой объект распределителя должен иметь тот же внешний интерфейс, что и объект типа `allocator` . Обратите внимание, что сохраненный объект распределителя не копируется, когда назначается объект контейнера.

## <a name="requirements"></a>Требования

**Заголовок:**`<unordered_map>`

**Пространство имен:** std

## <a name="unordered_mapallocator_type"></a><a name="allocator_type"></a> `unordered_map::allocator_type`

Тип распределителя для управления хранилищем.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Замечания

Этот тип является синонимом для параметра шаблона `Alloc`.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_allocator_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_mapat"></a><a name="at"></a> `unordered_map::at`

Находит элемент в unordered_map с указанным значением ключа.

```cpp
Ty& at(const Key& key);
const Ty& at(const Key& key) const;
```

### <a name="parameters"></a>Параметры

*`key`*\
Значение ключа, которое необходимо найти.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на значение данных найденного элемента.

### <a name="remarks"></a>Замечания

Если значение ключа аргумента не найдено, функция создает объект класса `out_of_range`.

### <a name="example"></a>Пример

```cpp
// unordered_map_at.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
}
```

## <a name="unordered_mapbegin"></a><a name="begin"></a> `unordered_map::begin`

Задает начало управляемой последовательности или сегмента.

```cpp
iterator begin();
const_iterator begin() const;
local_iterator begin(size_type nbucket);
const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>Параметры

*`nbucket`*\
Номер сегмента.

### <a name="remarks"></a>Замечания

Первые две функции-члены возвращают прямой итератор, указывающий на первый элемент последовательности (или на место сразу за концом пустой последовательности). Последние две функции-члена возвращают прямой итератор, указывающий на первый элемент контейнера *`nbucket`* (или за конец пустого контейнера).

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_begin.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect first two items " [c 3] [b 2]"
    Mymap::iterator it2 = c1.begin();
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    ++it2;
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[c, 3] [b, 2]
[a, 1]
```

## <a name="unordered_mapbucket"></a><a name="bucket"></a> `unordered_map::bucket`

Получает номер блока для значения ключа.

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>Параметры

*`keyval`*\
Значение ключа для сопоставления.

### <a name="remarks"></a>Замечания

Функция члена возвращает номер контейнера, который в настоящее время соответствует значению ключа *`keyval`* .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_bucket.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapbucket_count"></a><a name="bucket_count"></a> `unordered_map::bucket_count`

Получает количество блоков.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает текущее число блоков.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3][b, 2][a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapbucket_size"></a><a name="bucket_size"></a> `unordered_map::bucket_size`

Получает размер сегмента.

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>Параметры

*`nbucket`*\
Номер сегмента.

### <a name="remarks"></a>Замечания

Функции элементов возвращают размер номера сегмента *`nbucket`* .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_bucket_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapcbegin"></a><a name="cbegin"></a> `unordered_map::cbegin`

Возвращает **`const`** итератор, который обращается к первому элементу в диапазоне.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`const`** Итератор прямого доступа, указывающий на первый элемент диапазона, или расположение непосредственно за концом пустого диапазона (для пустого диапазона `cbegin() == cend()` ).

### <a name="remarks"></a>Замечания

Элементы в диапазоне нельзя изменить с помощью возвращаемого значения `cbegin`.

Эту функцию-член можно использовать вместо функции-члена `begin()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `begin()` и `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="unordered_mapcend"></a><a name="cend"></a> `unordered_map::cend`

Возвращает **`const`** итератор, который обращается к расположению сразу за последним элементом в диапазоне.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`const`** Итератор прямого доступа, указывающий на место сразу за концом диапазона.

### <a name="remarks"></a>Замечания

`cend` используется для проверки того, прошел ли итератор конец диапазона.

Эту функцию-член можно использовать вместо функции-члена `end()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `end()` и `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();
// i2 is Container<T>::const_iterator
```

Значение, возвращаемое `cend`, не должно быть подвергнуто удалению ссылки.

## <a name="unordered_mapclear"></a><a name="clear"></a> `unordered_map::clear`

Удаляет все элементы.

```cpp
void clear();
```

### <a name="remarks"></a>Замечания

Функция члена вызывает `unordered_map::erase(unordered_map::begin(), unordered_map::end())` , см [`unordered_map::erase`](#erase) ., [`unordered_map::begin`](#begin) и [`unordered_map::end`](#end) .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_clear.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapconst_iterator"></a><a name="const_iterator"></a> `unordered_map::const_iterator`

Тип постоянного итератора для управляемой последовательности.

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>Замечания

Тип описывает объект, который можно использовать в качестве постоянного прямого итератора для управляемой последовательности. Он описан здесь как синоним для типа `T1`, определяемого реализацией.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_const_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_local_iterator"></a><a name="const_local_iterator"></a> `unordered_map::const_local_iterator`

Тип постоянного итератора блока для управляемой последовательности.

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>Замечания

Этот тип описывает объект, который можно использовать в качестве постоянного прямого итератора для блока. Он описан здесь как синоним для типа `T5`, определяемого реализацией.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapconst_pointer"></a><a name="const_pointer"></a> `unordered_map::const_pointer`

Тип постоянного указателя на элемент.

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>Замечания

Этот тип описывает объект, который можно использовать в качестве постоянного указателя на элемент управляемой последовательности.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_const_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_reference"></a><a name="const_reference"></a> `unordered_map::const_reference`

Тип постоянной ссылки на элемент.

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Замечания

Тип описывает объект, который можно использовать в качестве постоянной ссылки на элемент управляемой последовательности.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_const_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapcontains"></a><a name="contains"></a> `unordered_map::contains`

Проверяет, существует ли элемент в `unordered_map` с указанным ключом.
Представлено в C++ 20.

```cpp
bool contains(const Key& key) const;
<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>Параметры

*`K`*\
Тип ключа.

*`key`*\
Значение ключа искомого элемента.

### <a name="return-value"></a>Возвращаемое значение

`true` значение, если элемент найден в контейнере; `false` в противном случае — значение.

### <a name="remarks"></a>Замечания

`contains()` Новое в C++ 20. Чтобы использовать его, укажите [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) параметр компилятора.

`template<class K> bool contains(const K& key) const` принимает участие в разрешении перегрузки только в `key_compare` том случае, если является прозрачным.

### <a name="example"></a>Пример

```cpp
// Requires /std:c++latest
#include <unordered_map>
#include <iostream>

int main()
{
    std::unordered_map<int, bool> theUnorderedMap = {{0, false}, {1,true}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theUnorderedMap.contains(1) << '\n';
    std::cout << theUnorderedMap.contains(2) << '\n';

    return 0;
}
```

```Output
true
false
```

## <a name="unordered_mapcount"></a><a name="count"></a> `unordered_map::count`

Определяет количество элементов, соответствующих заданному ключу.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>Параметры

*`keyval`*\
Искомое значение ключа.

### <a name="remarks"></a>Замечания

Функция – член возвращает количество элементов в диапазоне, разделенном на [`unordered_map::equal_range(keyval)`](#equal_range) .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="unordered_mapdifference_type"></a><a name="difference_type"></a> `unordered_map::difference_type`

Тип расстояния со знаком между двумя элементами.

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>Замечания

Тип целого числа со знаком описывает объект, который может представлять разницу между адресами любых двух элементов в управляемой последовательности. Он описан здесь как синоним для типа `T3`, определяемого реализацией.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_difference_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Mymap::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
end()-begin() == 3
begin()-end() == -3
```

## <a name="unordered_mapemplace"></a><a name="emplace"></a> `unordered_map::emplace`

Вставляет созданный элемент на место (операции копирования или перемещения не выполняются) в объекте unordered_map.

```cpp
template <class... Args>
pair<iterator, bool>  emplace( Args&&... args);
```

### <a name="parameters"></a>Параметры

*`args`*\
Аргументы, перенаправляемые для создания элемента, который будет вставлен в объект, `unordered_map` если он уже не содержит элемент, значение которого эквивалентно упорядочено.

### <a name="return-value"></a>Возвращаемое значение

Объект `pair` , **`bool`** компонент которого возвращает значение true, если была произведена вставка, и значение false, если `unordered_map` уже содержал элемент, ключ которого имеет эквивалентное значение в упорядочении, а компонент итератора возвращает адрес, куда был вставлен новый элемент, или место, где элемент уже был найден.

Для доступа к компоненту итератора пары `pr`, возвращенной этой функцией-членом, используйте `pr.first` и разыменуйте ее с помощью `*(pr.first)`. Для доступа к **`bool`** компоненту пары `pr` , возвращаемой этой функцией-членом, используйте `pr.second` .

### <a name="remarks"></a>Замечания

Эта функция не делает недействительными никакие итераторы или ссылки.

Если во время вставки возникает исключение, но оно произошло не в хэш-функции контейнера, контейнер не изменяется. Если исключение вызывается в хэш-функции, результат не определен.

Пример кода см. в разделе [`map::emplace`](../standard-library/map-class.md#emplace) .

## <a name="unordered_mapemplace_hint"></a><a name="emplace_hint"></a> `unordered_map::emplace_hint`

Вставляет созданный элемент на место (операции копирования или перемещения не выполняются) с указанием о размещении.

```cpp
template <class... Args>
iterator emplace_hint(const_iterator where, Args&&... args);
```

### <a name="parameters"></a>Параметры

*`args`*\
Аргументы, передаваемые для создания элемента, который будет вставлен в объект unordered_map, если объект unordered_map не содержит этого элемента или, в более общем случае, если этот объект еще не содержит элемента, ключ которого упорядочен аналогичным образом.

*`where`*\
Подсказка о месте начала поиска правильной точки вставки.

### <a name="return-value"></a>Возвращаемое значение

Итератор, указывающий на вновь вставленный элемент.

Если не удалось вставить элемент, так как он уже существует, возвращается итератор на существующий элемент.

### <a name="remarks"></a>Замечания

Эта функция не делает ссылки недействительными.

Если во время вставки возникает исключение, но оно произошло не в хэш-функции контейнера, контейнер не изменяется. Если исключение вызывается в хэш-функции, результат не определен.

[`value_type`](../standard-library/map-class.md#value_type)Элемент является парой, поэтому значение элемента будет упорядоченной парой, первый компонент которой равен значению ключа, а второй компонент равен значению данных элемента.

Пример кода см. в разделе [`map::emplace_hint`](../standard-library/map-class.md#emplace_hint) .

## <a name="unordered_mapempty"></a><a name="empty"></a> `unordered_map::empty`

Проверяет отсутствие элементов.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Замечания

Эта функция-член возвращает значение true для пустой управляемой последовательности.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_empty.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapend"></a><a name="end"></a> `unordered_map::end`

Задает конец управляемой последовательности.

```cpp
iterator end();
const_iterator end() const;
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>Параметры

*`nbucket`*\
Номер сегмента.

### <a name="remarks"></a>Замечания

Первые две функции-члены возвращают прямой итератор, указывающий на место сразу за концом последовательности. Последние две функции-члена возвращают прямой итератор, указывающий сразу за концом сегмента *`nbucket`* .

## <a name="unordered_mapequal_range"></a><a name="equal_range"></a> `unordered_map::equal_range`

Находит диапазон, соответствующий указанному ключу.

```cpp
std::pair<iterator, iterator>  equal_range(const Key& keyval);
std::pair<const_iterator, const_iterator>  equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>Параметры

*`keyval`*\
Искомое значение ключа.

### <a name="remarks"></a>Замечания

Функция-член возвращает пару итераторов `X` , что `[X.first, X.second)` разделяет только те элементы управляемой последовательности, которые имеют эквивалентное упорядочение с *`keyval`* . Если таких элементов не существует, оба итератора имеют значение `end()`.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_equal_range.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
equal_range('x'):
equal_range('b'): [b, 2]
```

## <a name="unordered_maperase"></a><a name="erase"></a> `unordered_map::erase`

Удаляет элемент или диапазон элементов в объекте unordered_map с заданных позиций или удаляет элементы, соответствующие заданному ключу.

```cpp
iterator erase(const_iterator Where);
iterator erase(const_iterator First, const_iterator Last);
size_type erase(const key_type& Key);
```

### <a name="parameters"></a>Параметры

*`Where`*\
Положение удаляемого элемента.

*`First`*\
Положение первого удаляемого элемента.

*`Last`*\
Позиция после последнего элемента для удаления.

*`Key`*\
Значение ключа удаляемых элементов.

### <a name="return-value"></a>Возвращаемое значение

Для первых двух функций-членов это двунаправленный итератор, обозначающий первый элемент, остающийся после любых удаленных элементов, или элемент в конце сопоставления, если таких элементов нет.

Для третьей функции-члена возвращает число элементов, которые были удалены из объекта unordered_map.

### <a name="remarks"></a>Замечания

Пример кода см. в разделе [`map::erase`](../standard-library/map-class.md#erase) .

## <a name="unordered_mapfind"></a><a name="find"></a> unordered_map:: Find

Определяет элемент, соответствующий указанному ключу.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>Параметры

*`keyval`*\
Искомое значение ключа.

### <a name="remarks"></a>Замечания

Функция члена возвращает [`unordered_map::equal_range(keyval).first`](#equal_range) .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_find.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Mymap::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << it->first << ", " << it->second << "]" << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
find('A') == false
find('b') == true: [b, 2]
```

## <a name="unordered_mapget_allocator"></a><a name="get_allocator"></a> `unordered_map::get_allocator`

Возвращает сохраненный объект распределителя.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает сохраненный объект распределителя.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_get_allocator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_maphash_function"></a><a name="hash"></a> `unordered_map::hash_function`

Получает сохраненный объект хэш-функции.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает сохраненный объект хэш-функции.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_hash_function.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_maphasher"></a><a name="hasher"></a> `unordered_map::hasher`

Тип хэш-функции.

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>Замечания

Этот тип является синонимом для параметра шаблона `Hash`.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_hasher.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_mapinsert"></a><a name="insert"></a> `unordered_map::insert`

Вставляет элемент или диапазон элементов в unordered_map.

```cpp
// (1) single element
pair<iterator, bool> insert(    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(    ValTy&& Val);

// (3) single element with hint
iterator insert(    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Параметры

*`Val`*\
Значение элемента, вставляемого в unordered_map, если оно уже не содержит элемент, ключ которого эквивалентно упорядочен.

*`Where`*\
Место начала поиска правильной точки вставки.

*`ValTy`*\
Параметр шаблона, указывающий тип аргумента, который unordered_map может использовать для создания элемента [`value_type`](../standard-library/map-class.md#value_type) , и идеального перенаправления *`Val`* в качестве аргумента.

*`First`*\
Позиция первого элемента, который следует скопировать.

*`Last`*\
Позиция непосредственно перед последним элементом, который следует скопировать.

*`InputIterator`*\
Аргумент функции-шаблона, соответствующий требованиям [итератора ввода](../standard-library/input-iterator-tag-struct.md) , указывающего на элементы типа, которые могут использоваться для построения [`value_type`](../standard-library/map-class.md#value_type) объектов.

*`IList`*\
Объект, [`initializer_list`](../standard-library/initializer-list.md) из которого копируются элементы.

### <a name="return-value"></a>Возвращаемое значение

Одноэлементные функции-члены (1) и (2) возвращают объект, [`pair`](../standard-library/pair-structure.md) компонент которого имеет значение, **`bool`** `true` Если была произведена вставка, и `false` Если объект `unordered_map` уже содержал элемент, ключ которого имеет эквивалентные значения в упорядочении. Компонент итератора пары "возвращаемое значение" указывает на вновь вставленный элемент, если **`bool`** компонент имеет значение `true` , или на существующий элемент, если **`bool`** компонент имеет значение `false` .

Одноэлементные функции-члены с подсказкой (3) и (4) возвращают итератор, который указывает на позицию, где новый элемент был вставлен, или, если элемент с эквивалентным ключом уже существует, указывает на существующий элемент.

### <a name="remarks"></a>Замечания

Эта функция не делает никакие итераторы, указатели или ссылки недействительными.

Если исключение вызывается во время вставки одного элемента, но оно не вызывается в хэш-функции контейнера, состояние контейнера не изменяется. Если исключение вызывается в хэш-функции, результат не определен. Если во время вставки нескольких элементов вызывается исключение, контейнер остается в неопределенном, но допустимом состоянии.

Чтобы получить доступ к компоненту итератора `pair` `pr` , возвращаемому функциями-членами с одним элементом, используйте оператор `pr.first` ; для разыменования итератора в возвращенной паре используйте `*pr.first` , предоставив элемент. Чтобы получить доступ к **`bool`** компоненту, используйте `pr.second` . См. пример кода далее в этой статье.

[`value_type`](../standard-library/map-class.md#value_type)Контейнером является typedef, принадлежащий контейнеру, а для Map `map<K, V>::value_type` — `pair<const K, V>` . Значение элемента — это упорядоченная пара, в которой первый компонент эквивалентен значению ключа, а второй компонент — значению данных элемента.

Функция-член с диапазоном (5) вставляет последовательность значений элементов в unordered_map, соответствующее каждому элементу, адресованному итератором в диапазоне `[First, Last)`. Следовательно, `Last` не вставляется. Контейнер функции-члена `end()` ссылается на позицию сразу после последнего элемента в контейнере. Например, оператор `m.insert(v.begin(), v.end());` пытается вставить все элементы `v` в `m`. Вставляются только элементы с уникальными значениями в диапазоне. Повторяющиеся значения игнорируются. Чтобы увидеть, какие элементы отклонены, используйте одноэлементные версии `insert`.

Функция-член списка инициализаторов (6) использует [`initializer_list`](../standard-library/initializer-list.md) для копирования элементов в unordered_map.

Для вставки элемента, созданного на месте (т. е. не выполняются операции копирования или перемещения), [`unordered_map::emplace`](#emplace) см [`unordered_map::emplace_hint`](#emplace_hint) . и.

Пример кода см. в разделе [`map::insert`](../standard-library/map-class.md#insert) .

## <a name="unordered_mapiterator"></a><a name="iterator"></a> `unordered_map::iterator`

Тип итератора для управляемой последовательности.

```cpp
typedef T0 iterator;
```

### <a name="remarks"></a>Замечания

Тип описывает объект, который можно использовать в качестве прямого итератора для управляемой последовательности. Он описан здесь как синоним для типа `T0`, определяемого реализацией.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapkey_eq"></a><a name="key_eq"></a> `unordered_map::key_eq`

Получает сохраненный объект функции сравнения.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает сохраненный объект функции сравнения.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_key_eq.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="unordered_mapkey_equal"></a><a name="key_equal"></a> `unordered_map::key_equal`

Тип функции сравнения.

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>Замечания

Этот тип является синонимом для параметра шаблона `Pred`.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_key_equal.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="unordered_mapkey_type"></a><a name="key_type"></a> `unordered_map::key_type`

Тип ключа упорядочения.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Замечания

Этот тип является синонимом для параметра шаблона `Key`.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_key_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapload_factor"></a><a name="load_factor"></a> `unordered_map::load_factor`

Подсчитывает среднее число элементов в блоке.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>Замечания

Функция – член возвращает `(float)unordered_map::size() / (float)unordered_map::bucket_count()` Среднее количество элементов на сегмент, см [`unordered_map::size`](#size) . раздел и [`unordered_map::bucket_count`](#bucket_count) .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_maplocal_iterator"></a><a name="local_iterator"></a> `unordered_map::local_iterator`

Тип итератора контейнера.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>Замечания

Этот тип описывает объект, который можно использовать в качестве прямого итератора для контейнера. Он описан здесь как синоним для типа `T4`, определяемого реализацией.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect bucket containing 'a'
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapmapped_type"></a><a name="mapped_type"></a> `unordered_map::mapped_type`

Тип сопоставленного значения, связанного с каждым ключом.

```cpp
typedef Ty mapped_type;
```

### <a name="remarks"></a>Замечания

Этот тип является синонимом для параметра шаблона `Ty`.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_mapped_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapmax_bucket_count"></a><a name="max_bucket_count"></a> `unordered_map::max_bucket_count`

Получает максимальное количество блоков.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает максимальное количество блоков, которое разрешено в настоящее время.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapmax_load_factor"></a><a name="max_load_factor"></a> `unordered_map::max_load_factor`

Возвращает или задает максимальное количество элементов в блоке.

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>Параметры

*`factor`*\
Новый коэффициент максимальной нагрузки.

### <a name="remarks"></a>Замечания

Первая функция-член возвращает сохраненный коэффициент максимальной нагрузки. Вторая функция – член заменяет хранимый максимальный коэффициент нагрузки на *`factor`* .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapmax_size"></a><a name="max_size"></a> `unordered_map::max_size`

Возвращает максимальный размер управляемой последовательности.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает длину самой длинной последовательности, которой объект может управлять.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_max_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
    }
```

```Output
max_size() == 536870911
```

## <a name="unordered_mapoperator"></a><a name="op_at"></a> `unordered_map::operator[]`

Находит или вставляет элемент с указанным ключом.

```cpp
Ty& operator[](const Key& keyval);

Ty& operator[](Key&& keyval);
```

### <a name="parameters"></a>Параметры

*`Keyval`*\
Значение ключа, которое необходимо найти или вставить.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на значение данных вставленного элемента.

### <a name="remarks"></a>Замечания

Если значение ключа аргумента не найдено, он вставляется вместе со значением по умолчанию для такого типа данных.

`operator[]` может использоваться для вставки элементов в карту *`m`* с помощью *`m[Key] = DataValue;`* WHERE, где *`DataValue`* — это значение `mapped_type` элемента со значением ключа *`Key`* .

При использовании `operator[]` для вставки элементов возвращаемая ссылка не отображает, меняет ли вставка уже существующий элемент или создает новый. Функции-члены [`find`](../standard-library/map-class.md#find) и [`insert`](../standard-library/map-class.md#insert) могут использоваться для определения того, существует ли уже элемент с указанным ключом перед вставкой.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_operator_sub.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <string>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// try to find and fail
    std::cout << "c1['A'] == " << c1['A'] << std::endl;

// try to find and succeed
    std::cout << "c1['a'] == " << c1['a'] << std::endl;

// redisplay contents
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// insert by moving key
    std::unordered_map<string, int> c2;
    std::string str("abc");
    std::cout << "c2[std::move(str)] == " << c2[std::move(str)] << std::endl;
    std::cout << "c2["abc"] == " << c2["abc"] << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
c1['A'] == 0
c1['a'] == 1
[c, 3] [b, 2] [A, 0] [a, 1]
c2[move(str)] == 0
c2["abc"] == 1
```

### <a name="remarks"></a>Замечания

Функция члена определяет итератор `where` как возвращаемое значение `unordered_map::insert(unordered_map::value_type(keyval, Ty())` , см [`unordered_map::insert`](#insert) . раздел и [`unordered_map::value_type`](#value_type) . (Он вставляет элемент с указанным ключом, если такого элемента не существует.) Затем он возвращает ссылку на `(*where).second` .

## <a name="unordered_mapoperator"></a><a name="op_eq"></a> `unordered_map::operator=`

Заменяет элементы этого контейнера unordered_map, используя элементы из другого контейнера unordered_map.

```cpp
unordered_map& operator=(const unordered_map& right);

unordered_map& operator=(unordered_map&& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Контейнер unordered_map, из которого функция оператора назначает содержимое.

### <a name="remarks"></a>Замечания

Первая версия копирует все элементы из *`right`* в эту unordered_map.

Вторая версия перемещает все элементы из *`right`* в этот unordered_map.

Все элементы, которые находятся в этом unordered_map перед `operator=` выполнением, отбрасываются.

### <a name="example"></a>Пример

```cpp
// unordered_map_operator_as.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

int main( )
   {
   using namespace std;
   unordered_map<int, int> v1, v2, v3;
   unordered_map<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="unordered_mappointer"></a><a name="pointer"></a> `unordered_map::pointer`

Тип указателя на элемент.

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>Замечания

Этот тип описывает объект, который можно использовать в качестве указателя на элемент управляемой последовательности.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapreference"></a><a name="reference"></a> `unordered_map::reference`

Тип ссылки на элемент.

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>Замечания

Тип описывает объект, который можно использовать в качестве ссылки на элемент управляемой последовательности.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_maprehash"></a><a name="rehash"></a> `unordered_map::rehash`

Повторно создает хэш-таблицу.

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>Параметры

*`nbuckets`*\
Требуемое число сегментов.

### <a name="remarks"></a>Замечания

Функция-член изменяет количество сегментов, чтобы они были *`nbuckets`* как минимум, и перестраивает хэш-таблицу по мере необходимости.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_rehash.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_load_factor() == 0.1
```

## <a name="unordered_mapsize"></a><a name="size"></a> `unordered_map::size`

Подсчитывает количество элементов.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает длину управляемой последовательности.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

// display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapsize_type"></a><a name="size_type"></a> `unordered_map::size_type`

Тип беззнакового расстояния между двумя элементами.

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>Замечания

Целочисленный тип без знака описывает объект, который может представлять длину любой управляемой последовательности. Он описан здесь как синоним для типа `T2`, определяемого реализацией.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_size_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
    }
```

```Output
size == 0
```

## <a name="unordered_mapswap"></a><a name="swap"></a> `unordered_map::swap`

Меняет местами содержимое двух контейнеров.

```cpp
void swap(unordered_map& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Контейнер для замены.

### <a name="remarks"></a>Замечания

Функция – член меняет местами управляемые последовательности между **`*this`** и *`right`* . Если `unordered_map::get_allocator() == right.get_allocator()` значение равно, то оно [`unordered_map::get_allocator`](#get_allocator) делает это в константном времени, оно создает исключение только в результате копирования сохраненного объекта признаков типа `Tr` и не делает недействительными ссылки, указатели или итераторы, обозначающие элементы в двух управляемых последовательностях. В противном случае она выполняет ряд назначений элементов и вызовов конструктора, пропорционально количеству элементов в двух управляемых последовательностях.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

// display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapunordered_map"></a><a name="unordered_map"></a> `unordered_map::unordered_map`

Создает объект контейнера.

```cpp
unordered_map(const unordered_map& Right);

explicit unordered_map(
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Allocator());

unordered_map(unordered_map&& Right);
unordered_map(initializer_list<Type> IList);
unordered_map(initializer_list<Type> IList, size_type Bucket_count);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& equal);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& Equal
    const Allocator& Al);

template <class InIt>
unordered_map(
    InputIterator First,
    InputIterator Last,
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>Параметры

*`Al`*\
Объект распределителя для сохранения.

*`Comp`*\
Объект функции сравнения для сохранения.

*`Hash`*\
Объект хэш-функции для сохранения.

*`Bucket_count`*\
Минимальное количество блоков.

*`Right`*\
Контейнер для копирования.

*`First`*\
Позиция первого элемента, который следует скопировать.

*`Last`*\
Позиция непосредственно перед последним элементом, который следует скопировать.

*`IList`*\
Список initializer_list с элементами, которые необходимо скопировать.

### <a name="remarks"></a>Замечания

Первый конструктор определяет копию последовательности, управляемой `right`. Второй конструктор определяет управляемую пустую последовательность. Третий конструктор добавляет последовательность значений элементов `[first, last)`. Четвертый конструктор задает копию последовательности путем перемещения `right`.

Все конструкторы также инициализируют ряд сохраненных значений. Для конструктора копии значения извлекаются из *`Right`* . В противном случае:

минимальное число контейнеров — это аргумент *`Bucket_count`* , если он есть; в противном случае это значение по умолчанию, описываемое здесь как значение, определяемое реализацией `N0` .

объект хэш-функции — это аргумент *`Hash`* , если он есть; в противном случае — значение `Hash()` .

Объект функции сравнения — это аргумент *`Comp`* , если он есть; в противном случае — значение `Pred()` .

Объект распределителя — это аргумент *`Al`* , если он есть; в противном случае — значение `Alloc()` .

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_construct.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <initializer_list>

using namespace std;

using Mymap = unordered_map<char, int>;

int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c2(8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    // display contents " [f 6] [e 5] [d 4]"
    for (const auto& c : c2) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c3(c1.begin(),
        c1.end(),
        8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c3) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c4(move(c3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c4) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Construct with an initializer_list
    unordered_map<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });
    for (const auto& c : c5) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size
    unordered_map<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Initializer_list plus size and hash
    unordered_map<int, char, hash<char>> c7(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, and key_equal
    unordered_map<int, char, hash<char>, equal_to<char>> c8(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, key_equal, and allocator
    unordered_map<int, char, hash<char>, equal_to<char>> c9(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
}
```

```Output
[a, 1] [b, 2] [c, 3]
[d, 4] [e, 5] [f, 6]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]

[5, g] [6, h] [7, i] [8, j]
[a, 1] [b, 2] [c, 3]

[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
```

## <a name="unordered_mapvalue_type"></a><a name="value_type"></a> `unordered_map::value_type`

Тип элемента.

```cpp
typedef std::pair<const Key, Ty> value_type;
```

### <a name="remarks"></a>Замечания

Тип описывает элемент управляемой последовательности.

### <a name="example"></a>Пример

```cpp
// std__unordered_map__unordered_map_value_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="see-also"></a>См. также раздел

[`<unordered_map>`](../standard-library/unordered-map.md)\
[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
