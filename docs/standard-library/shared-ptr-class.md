---
description: 'Дополнительные сведения о: shared_ptr классе'
title: Класс shared_ptr
ms.date: 07/29/2019
f1_keywords:
- memory/std::shared_ptr
- memory/std::shared_ptr::element_type
- memory/std::shared_ptr::get
- memory/std::shared_ptr::owner_before
- memory/std::shared_ptr::reset
- memory/std::shared_ptr::swap
- memory/std::shared_ptr::unique
- memory/std::shared_ptr::use_count
- memory/std::shared_ptr::operator boolean-type
- memory/std::shared_ptr::operator*
- memory/std::shared_ptr::operator=
- memory/std::shared_ptr::operator->
helpviewer_keywords:
- std::shared_ptr [C++]
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
ms.openlocfilehash: 8f809c4cf10c57e86f207090bd86cdbfeb31f226
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721541"
---
# <a name="shared_ptr-class"></a>Класс `shared_ptr`

Помещает объект с динамическим выделением памяти в оболочку интеллектуального указателя с подсчитанными ссылками.

## <a name="syntax"></a>Синтаксис

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>Remarks

`shared_ptr`Класс описывает объект, использующий подсчет ссылок для управления ресурсами. Объект `shared_ptr` фактически содержит указатель на ресурс, которым он владеет, или содержит пустой указатель (NULL). Обладать ресурсом могут несколько объектов `shared_ptr`; при удалении последнего объекта `shared_ptr`, обладающего тем или иным ресурсом, данный ресурс освобождается.

`shared_ptr`Останавливает приостановку ресурса при его переназначении или сбросе.

Аргумент шаблона `T` может быть неполным типом, за исключением случаев, особо отмеченных для определенных функций-членов.

При создании объекта `shared_ptr<T>` из указателя ресурса типа `G*` или из `shared_ptr<G>` тип указателя `G*` должен допускать преобразование в `T*`. Если это не преобразуемое, код не будет компилироваться. Пример:

```cpp
#include <memory>
using namespace std;

class F {};
class G : public F {};

shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>
shared_ptr<int> sp5(new G); // error, G* not convertible to int*
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>
```

Объект `shared_ptr` владеет ресурсом:

- если он был создан с использованием указателя на этот ресурс;

- если он был создан из объекта `shared_ptr`, владеющего этим ресурсом;

- Если он был создан из [`weak_ptr`](weak-ptr-class.md) объекта, указывающего на этот ресурс, или

- значение, если владение этим ресурсом было назначено с помощью [`shared_ptr::operator=`](#op_eq) или путем вызова функции члена [`shared_ptr::reset`](#reset) .

Владеющие ресурсом объекты `shared_ptr` совместно используют один блок управления. Блок управления содержит следующее:

- количество объектов `shared_ptr`, владеющих ресурсом;

- количество объектов `weak_ptr`, указывающих на ресурс;

- метод удаления для этого ресурса, если он есть;

- пользовательский распределитель для блока управления, если он есть.

Объект `shared_ptr`, инициализируемый при помощи пустого указателя, имеет блок управления и не является пустым. После того как объект `shared_ptr` освобождает ресурс, он перестает быть его владельцем. После того как объект `weak_ptr` освобождает ресурс, он перестает указывать на него.

Если количество объектов `shared_ptr`, владеющих ресурсом, становится равным нулю, ресурс освобождается путем удаления или передачи его адреса в метод удаления в зависимости от того, как изначально был создан владелец ресурса. Если количество объектов `shared_ptr`, владеющих ресурсом, как и число объектов `weak_ptr`, которые указывают на ресурс, становится равным нулю, освобождается блок управления с использованием пользовательского распределителя этого блока управления при его наличии.

Пустой объект `shared_ptr` не владеет какими-либо ресурсами и не имеет блока управления.

Метод удаления является объектом функции, имеющим функцию-член `operator()`. Его тип должен быть конструируемым по копии, а его конструктор копии и деструктор не должны выдавать исключения. Он принимает один параметр — удаляемый объект.

Некоторые функции принимают список аргументов, определяющий свойства результирующего объекта `shared_ptr<T>` или `weak_ptr<T>`. Такой список аргументов можно задать несколькими способами.

Нет аргументов — результирующий объект является пустым объектом `shared_ptr` или `weak_ptr`.

`ptr` — указатель типа `Other*` на ресурс, которым требуется управлять. `T` должен быть полным типом. Если функция завершается ошибкой (поскольку блок управления не может быть выделен), вычисляется выражение `delete ptr` .

`ptr, deleter` — указатель типа `Other*` на ресурс, которым требуется управлять, и метод удаления для данного ресурса. Если функция завершается ошибкой (поскольку блок управления не может быть выделен), он вызывает `deleter(ptr)` , который должен быть четко определен.

`ptr, deleter, alloc` — указатель типа `Other*` на ресурс, которым требуется управлять, для управления, метод удаления для данного ресурса и распределитель для управления выделяемым и освобождаемым местом в хранилище. Если функция завершается ошибкой (поскольку блок управления не может быть выделен), он вызывает `deleter(ptr)` , который должен быть четко определен.

`sp` — объект `shared_ptr<Other>`, владеющий ресурсом, которым требуется управлять.

`wp` — объект `weak_ptr<Other>`, указывающий на ресурс, которым требуется управлять.

`ap` — объект `auto_ptr<Other>`, содержащий указатель на ресурс, которым требуется управлять. Если функция завершается с ошибкой, вызывается `ap.release()` ; в противном случае она остается `ap` неизменной.

Во всех случаях тип указателя типа `Other*` должен допускать преобразование в `T*`.

## <a name="thread-safety"></a>Потокобезопасность

Несколько потоков могут одновременно считывать и записывать разные объекты `shared_ptr`, даже если они являются копиями с общим владельцем.

## <a name="members"></a>Члены

|Имя|Описание|
|-|-|
| **Конструкторы** | |
|[`shared_ptr`](#shared_ptr)|Создает документ `shared_ptr`.|
|[`~shared_ptr`](#dtorshared_ptr)|Удаляет `shared_ptr`.|
| **Определения типов** | |
|[`element_type`](#element_type)|Тип элемента.|
|[`weak_type`](#weak_type)|Тип слабого указателя на элемент.|
| **Функции элементов** | |
|[`get`](#get)|Возвращает адрес принадлежащего ресурса.|
|[`owner_before`](#owner_before)|Возвращает значение true, если `shared_ptr` упорядочен до (меньше) предоставленного указателя.|
|[`reset`](#reset)|Заменяет принадлежащий ресурс.|
|[`swap`](#swap)|Меняет местами два объекта `shared_ptr`.|
|[`unique`](#unique)|Проверяет, является ли принадлежащий ресурс уникальным.|
|[`use_count`](#use_count)|Подсчитывает количество владельцев ресурса.|
| **Операторы** | |
|[`operator bool`](#op_bool)|Проверяет существование принадлежащего ресурса.|
|[`operator*`](#op_star)|Возвращает указанное значение.|
|[`operator=`](#op_eq)|Заменяет принадлежащий ресурс.|
|[`operator->`](#op_arrow)|Получает указатель на указанное значение.|

## <a name="element_type"></a><a name="element_type"></a> `element_type`

Тип элемента.

```cpp
typedef T element_type;                  // before C++17
using element_type = remove_extent_t<T>; // C++17
```

### <a name="remarks"></a>Замечания

`element_type`Тип является синонимом для параметра-шаблона `T` .

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::shared_ptr<int>::element_type val = *sp0;

    std::cout << "*sp0 == " << val << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="get"></a><a name="get"></a> `get`

Возвращает адрес принадлежащего ресурса.

```cpp
element_type* get() const noexcept;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает адрес контролируемого ресурса. Если объект не владеет ресурсом, он возвращает 0.

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "sp0.get() == 0 == " << std::boolalpha
        << (sp0.get() == 0) << std::endl;
    std::cout << "*sp1.get() == " << *sp1.get() << std::endl;

    return (0);
}
```

```Output
sp0.get() == 0 == true
*sp1.get() == 5
```

## <a name="operator-bool"></a><a name="op_bool"></a> `operator bool`

Проверяет существование принадлежащего ресурса.

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>Замечания

Оператор возвращает значение **`true`** `get() != nullptr` , если, в противном случае **`false`** .

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_operator_bool.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;
    std::cout << "(bool)sp1 == " << std::boolalpha
        << (bool)sp1 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
(bool)sp1 == true
```

## <a name="operator"></a><a name="op_star"></a> `operator*`

Возвращает указанное значение.

```cpp
T& operator*() const noexcept;
```

### <a name="remarks"></a>Замечания

Оператор косвенного обращения возвращает `*get()`. Следовательно, сохраненный указатель не должен быть пустым.

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_operator_st.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

Заменяет принадлежащий ресурс.

```cpp
shared_ptr& operator=(const shared_ptr& sp) noexcept;

shared_ptr& operator=(shared_ptr&& sp) noexcept;

template <class Other>
shared_ptr& operator=(const shared_ptr<Other>& sp) noexcept;

template <class Other>
shared_ptr& operator=(shared_ptr<Other>&& sp) noexcept;

template <class Other>
shared_ptr& operator=(auto_ptr<Other>&& ap);    // deprecated in C++11, removed in C++17

template <class Other, class Deleter>
shared_ptr& operator=(unique_ptr<Other, Deleter>&& up);
```

### <a name="parameters"></a>Параметры

*`sp`*\
Общий указатель для копирования или перемещения.

*`ap`*\
Автоматический указатель для перемещения. `auto_ptr`Перегрузка является устаревшей в c++ 11 и удалена в c++ 17.

*`up`*\
Уникальный указатель на объект, для которого необходимо принять владение. *`up`* не владеет объектом после вызова.

*`Other`*\
Тип объекта, на который указывает *`sp`* , *`ap`* или *`up`* .

*`Deleter`*\
Тип удаления принадлежащего объекта, который сохраняется для последующего удаления объекта.

### <a name="remarks"></a>Замечания

Все операторы уменьшают счетчик ссылок для ресурса, который в настоящее время принадлежит, **`*this`** и назначает владение ресурсом с именем, указанным в последовательности операндов **`*this`** . Если число ссылок на ресурс становится равным нулю, ресурс освобождается (delete). Если оператор завершается с ошибкой, он остается **`*this`** неизменным.

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));
    std::unique_ptr<int> up(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = up;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
*sp0 == 10
```

## <a name="operator-"></a><a name="op_arrow"></a> `operator->`

Получает указатель на указанное значение.

```cpp
T* operator->() const noexcept;
```

### <a name="remarks"></a>Замечания

Оператор выбора возвращает `get()`, так что выражение `sp->member` ведет себя так же, как `(sp.get())->member`, где `sp` — это объект класса `shared_ptr<T>`. Следовательно, сохраненный указатель не должен быть пустым, и `T` должен быть классом, структурой или типом объединения с членом `member`.

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_operator_ar.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

typedef std::pair<int, int> Mypair;
int main()
{
    std::shared_ptr<Mypair> sp0(new Mypair(1, 2));

    std::cout << "sp0->first == " << sp0->first << std::endl;
    std::cout << "sp0->second == " << sp0->second << std::endl;

    return (0);
}
```

```Output
sp0->first == 1
sp0->second == 2
```

## <a name="owner_before"></a><a name="owner_before"></a> `owner_before`

Возвращает значение true, если `shared_ptr` упорядочен до (меньше) предоставленного указателя.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>Параметры

*`ptr`*\
Ссылка lvalue на `shared_ptr` или `weak_ptr` .

### <a name="remarks"></a>Замечания

Функция-член шаблона возвращает значение true **`*this`** , если упорядочено до `ptr` .

## <a name="reset"></a><a name="reset"></a> `reset`

Заменяет принадлежащий ресурс.

```cpp
void reset() noexcept;

template <class Other>
void reset(Other *ptr);

template <class Other, class Deleter>
void reset(
    Other *ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
void reset(
    Other *ptr,
    Deleter deleter,
    Allocator alloc);
```

### <a name="parameters"></a>Параметры

*`Other`*\
Тип, управляемый указателем аргумента.

*`Deleter`*\
Тип метода удаления.

*`ptr`*\
Копируемый указатель.

*`deleter`*\
Метод удаления для копирования.

*`Allocator`*\
Тип распределителя.

*`alloc`*\
Распределитель для копирования.

### <a name="remarks"></a>Замечания

Все операторы уменьшают счетчик ссылок для ресурса, который в настоящее время принадлежит, **`*this`** и назначает владение ресурсом с именем, указанным в последовательности операндов **`*this`** . Если число ссылок на ресурс становится равным нулю, ресурс освобождается (delete). Если оператор завершается с ошибкой, он остается **`*this`** неизменным.

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp(new int(5));

    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset();
    std::cout << "(bool)sp == " << std::boolalpha
        << (bool)sp << std::endl;

    sp.reset(new int(10));
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset(new int(15), deleter());
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    return (0);
}
```

```Output
*sp == 5
(bool)sp == false
*sp == 10
*sp == 15
```

## <a name="shared_ptr"></a><a name="shared_ptr"></a> `shared_ptr`

Создает документ `shared_ptr`.

```cpp
constexpr shared_ptr() noexcept;

constexpr shared_ptr(nullptr_t) noexcept : shared_ptr() {}

shared_ptr(const shared_ptr& sp) noexcept;

shared_ptr(shared_ptr&& sp) noexcept;

template <class Other>
explicit shared_ptr(Other* ptr);

template <class Other, class Deleter>
shared_ptr(
    Other* ptr,
    Deleter deleter);

template <class Deleter>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
shared_ptr(
    Other* ptr,
    Deleter deleter,
    Allocator alloc);

template <class Deleter, class Allocator>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter,
    Allocator alloc);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp) noexcept;

template <class Other>
explicit shared_ptr(
    const weak_ptr<Other>& wp);

template <class &>
shared_ptr(
    std::auto_ptr<Other>& ap);

template <class &>
shared_ptr(
    std::auto_ptr<Other>&& ap);

template <class Other, class Deleter>
shared_ptr(
    unique_ptr<Other, Deleter>&& up);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp,
    element_type* ptr) noexcept;

template <class Other>
shared_ptr(
    shared_ptr<Other>&& sp,
    element_type* ptr) noexcept;

template <class Other, class Deleter>
shared_ptr(
    const unique_ptr<Other, Deleter>& up) = delete;
```

### <a name="parameters"></a>Параметры

*`Other`*\
Тип, управляемый указателем аргумента.

*`ptr`*\
Копируемый указатель.

*`Deleter`*\
Тип метода удаления.

*`Allocator`*\
Тип распределителя.

*`deleter`*\
Метод удаления.

*`alloc`*\
Распределитель.

*`sp`*\
Интеллектуальный указатель для копирования

*`wp`*\
Слабый указатель.

*`ap`*\
"Автоматический" указатель ( auto_ptr ) для копирования

### <a name="remarks"></a>Замечания

Каждый из конструкторов создает объект для контроля над ресурсом, указанным в качестве операнда. Конструктор `shared_ptr(const weak_ptr<Other>& wp)` создает объект исключения типа [`bad_weak_ptr`](bad-weak-ptr-class.md) if `wp.expired()` .

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp0;
    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    std::shared_ptr<int> sp2(new int(10), deleter());
    std::cout << "*sp2 == " << *sp2 << std::endl;

    std::shared_ptr<int> sp3(sp2);
    std::cout << "*sp3 == " << *sp3 << std::endl;

    std::weak_ptr<int> wp(sp3);
    std::shared_ptr<int> sp4(wp);
    std::cout << "*sp4 == " << *sp4 << std::endl;

    std::auto_ptr<int> ap(new int(15));
    std::shared_ptr<int> sp5(ap);
    std::cout << "*sp5 == " << *sp5 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
*sp1 == 5
*sp2 == 10
*sp3 == 10
*sp4 == 10
*sp5 == 15
```

## <a name="shared_ptr"></a><a name="dtorshared_ptr"></a> `~shared_ptr`

Удаляет `shared_ptr`.

```cpp
~shared_ptr();
```

### <a name="remarks"></a>Замечания

Деструктор уменьшает счетчик ссылок для ресурса, который в настоящее время принадлежит **`*this`** . Если число ссылок на ресурс становится равным нулю, ресурс освобождается (delete).

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << "use count == " << sp1.use_count() << std::endl;

    {
        std::shared_ptr<int> sp2(sp1);
        std::cout << "*sp2 == " << *sp2 << std::endl;
        std::cout << "use count == " << sp1.use_count() << std::endl;
    }

    // check use count after sp2 is destroyed
    std::cout << "use count == " << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
use count == 1
*sp2 == 5
use count == 2
use count == 1
```

## <a name="swap"></a><a name="swap"></a> `swap`

Меняет местами два объекта `shared_ptr`.

```cpp
void swap(shared_ptr& sp) noexcept;
```

### <a name="parameters"></a>Параметры

*`sp`*\
Разделяемый указатель (shared_ptr), с которым требуется произвести обмен контролируемыми объектами.

### <a name="remarks"></a>Замечания

Функция члена оставляет ресурс, изначально принадлежащий, владельцем ресурса **`*this`** *`sp`* , а затем ресурс, изначально принадлежащий *`sp`* **`*this`** . Функция не изменяет подсчет ссылок для двух ресурсов и не создает исключений.

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5
*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="unique"></a><a name="unique"></a> `unique`

Проверяет, является ли принадлежащий ресурс уникальным. Эта функция была признана устаревшей в C++ 17 и удалена в C++ 20.

```cpp
bool unique() const noexcept;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает **`true`** , если другой `shared_ptr` объект не владеет ресурсом, владельцем которого является **`*this`** , в противном случае — **`false`** .

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_unique.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    return (0);
}
```

```Output
sp1.unique() == true
sp1.unique() == false
```

## <a name="use_count"></a><a name="use_count"></a> `use_count`

Подсчитывает количество владельцев ресурса.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Замечания

Функция-член возвращает количество `shared_ptr` объектов, владеющих ресурсом, владельцем которого является **`*this`** .

### <a name="example"></a>Пример

```cpp
// std__memory__shared_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
sp1.use_count() == 1
sp1.use_count() == 2
```

## <a name="weak_type"></a><a name="weak_type"></a> `weak_type`

Тип слабого указателя на элемент.

```cpp
using weak_type = weak_ptr<T>; // C++17
```

### <a name="remarks"></a>Замечания

`weak_type`Определение Добавлено в c++ 17.

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](cpp-standard-library-header-files.md)\
[`<memory>`](memory.md)\
[`unique_ptr`](unique-ptr-class.md)\
[Класс `weak_ptr`](weak-ptr-class.md)
