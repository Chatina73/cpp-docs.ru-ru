---
title: Распределители
ms.date: 11/04/2016
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
ms.openlocfilehash: 5aee23f72c5b0fb955b4dcc76a3f8c51eca7be70
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204239"
---
# <a name="allocators"></a>Распределители

Распределители используются стандартной библиотекой C++ для управления распределением и отменой распределения элементов, содержащихся в контейнерах. Все контейнеры стандартной библиотеки C++, кроме std::array, имеют параметр шаблона типа `allocator<Type>`, где `Type` представляет тип элемента контейнера. Например, класс vector объявляется следующим образом:

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

Стандартная библиотека C++ предоставляет реализацию распределителя, используемую по умолчанию. В C++ 11 и более поздних версиях распределитель по умолчанию обновлен с целью предоставления меньшего по размеру интерфейса. Новый распределитель называется *минимальным распределителем*. В частности, член `construct()` минимального распределителя поддерживает семантику перемещения, которая может значительно повысить производительность. В большинстве случаев возможностей этого распределителя по умолчанию должно быть достаточно. В C++ 11 все типы и функции стандартной библиотеки, которые принимают параметр типа распределителя, поддерживают интерфейс минимального распределителя, включая `std::function`, `shared_ptr, allocate_shared()` и `basic_string`.  Дополнительные сведения о распределителе по умолчанию см. в разделе [Класс allocator](allocator-class.md).

## <a name="writing-your-own-allocator-c11"></a>Написание собственного распределителя (C++ 11)

Распределитель по умолчанию использует **`new`** и **`delete`** для выделения и освобождения памяти. Если вы хотите использовать другой метод выделения памяти, например, при использовании общей памяти, необходимо создать собственный распределитель. Если вы используете C++ 11 и вам нужно написать новый пользовательский распределитель, сделайте его минимальным распределителем, если это возможно. Даже если вы уже реализовали распределитель старого стиля, рассмотрите возможность его преобразования в *минимальный распределитель*, чтобы воспользоваться преимуществами более эффективного метода `construct()`, который будет предоставлен автоматически.

Минимальный распределитель требует гораздо меньше стандартных действий и позволяет сосредоточиться на функциях-членах `allocate` и `deallocate`, которые выполняют всю работу. При создании минимального распределителя не реализуйте никакие другие элементы кроме тех, которые показаны в следующем примере.

1. Преобразующий конструктор копии (см. пример)

1. оператор ==

1. operator!=

1. allocate

1. deallocate

Член `construct()`, предоставляемый в C++ 11 по умолчанию, выполняет идеальную пересылку и обеспечивает семантику перемещения. Он гораздо более эффективен во многих случаях, чем старая версия.

> [!WARNING]
> Во время компиляции стандартная библиотека C++ использует класс allocator_traits для определения членов, предоставленных явно, и обеспечивает стандартную реализацию для всех отсутствующих членов. Не нарушайте работу этого механизма — не делайте специализацию allocator_traits для своего распределителя!

Следующий пример демонстрирует минимальную реализацию распределителя, который использует `malloc` и `free`. Обратите внимание на использование нового типа исключения `std::bad_array_new_length`, которое возникает, если размер массива оказывается меньше нуля или больше, чем максимально допустимый размер.

```cpp
#pragma once
#include <stdlib.h> //size_t, malloc, free
#include <new> // bad_alloc, bad_array_new_length
#include <memory>
template <class T>
struct Mallocator
{
    typedef T value_type;
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library

    // A converting copy constructor:
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}
    template<class U> bool operator==(const Mallocator<U>&) const noexcept
    {
        return true;
    }
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept
    {
        return false;
    }
    T* allocate(const size_t n) const;
    void deallocate(T* const p, size_t) const noexcept;
};

template <class T>
T* Mallocator<T>::allocate(const size_t n) const
{
    if (n == 0)
    {
        return nullptr;
    }
    if (n > static_cast<size_t>(-1) / sizeof(T))
    {
        throw std::bad_array_new_length();
    }
    void* const pv = malloc(n * sizeof(T));
    if (!pv) { throw std::bad_alloc(); }
    return static_cast<T*>(pv);
}

template<class T>
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept
{
    free(p);
}
```

## <a name="writing-your-own-allocator-c03"></a>Написание собственного распределителя (C++ 03)

В C++03 все распределители, используемые с контейнерами стандартной библиотеки C++, должны реализовывать следующие определения типа:

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

Кроме того, все распределители, используемые с контейнерами стандартной библиотеки C++, должны реализовывать следующие методы:

|||
|-|-|
|Конструктор|`deallocate`|
|Конструктор копии|`destroy`|
|Деструктор|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

Дополнительные сведения об этих определениях типов и методах см. в разделе [Класс allocator](allocator-class.md).

## <a name="see-also"></a>См. также раздел

[Справочник по стандартной библиотеке C++](cpp-standard-library-reference.md)
