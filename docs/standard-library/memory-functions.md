---
description: Дополнительные сведения о &lt; &gt; функциях памяти
title: Функции &lt;memory&gt;
ms.date: 08/05/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.openlocfilehash: fe5aedffe76bb613d0f042d1aa521d4c43943b8b
ms.sourcegitcommit: a89eac9acdbd54a181e3bd5d5bc71a3ef3c1abca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106506056"
---
# <a name="memory-functions"></a>Функции`<memory>`

## <a name="addressof"></a><a name="addressof"></a> `addressof`

Получает истинный адрес объекта.

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>Параметры

*`value`*\
Объект или функция, для которой необходимо получить истинный адрес.

### <a name="return-value"></a>Возвращаемое значение

Фактический адрес объекта или функции, на который ссылается *`value`* , даже если существует перегруженный объект `operator&()` .

### <a name="remarks"></a>Remarks

## <a name="align"></a><a name="align"></a> `align`

Замещает хранилище заданного размера, выровненное по заданной спецификации выравнивания, в первый возможный адрес данного хранилища.

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>Параметры

*`alignment`*\
Граница выравнивания для выполнения попытки.

*`size`*\
Размер в байтах для выровненного хранилища.

*`ptr`*\
Начальный адрес доступного смежного пула хранилища для использования. Этот параметр также является выходным параметром и устанавливается для включения нового начального адреса, если выравнивание выполнено успешно. Если `align()` операция не выполнена, этот параметр не изменяется.

*`space`*\
Полный размер пространства, доступного `align()`, для использования при создании выровненного хранилища. Этот параметр также является параметром вывода и содержит откорректированное пространство, оставшееся в хранилище после вычитания выровненного хранилища и всей связанной с ним дополнительной нагрузки.

Если `align()` операция не выполнена, этот параметр не изменяется.

### <a name="return-value"></a>Возвращаемое значение

`NULL`Указатель, если запрошенный выравниваемая буфер не умещается в доступное пространство; в противном случае — новое значение *`ptr`* .

### <a name="remarks"></a>Remarks

Измененные *`ptr`* *`space`* Параметры и позволяют `align()` многократно вызывать один и тот же буфер, возможно, с разными значениями параметров *`alignment`* и *`size`* . В следующем фрагменте кода показан один из способов использования `align()`.

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a><a name="allocate_shared"></a> `allocate_shared`

Создает объект [`shared_ptr`](shared-ptr-class.md) для объектов, которые выделяются и формируются для данного типа с помощью указанного распределителя. Возвращает `shared_ptr`.

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>Параметры

*`alloc`*\
Распределитель используется для создания объектов.

*`args`*\
Ноль или более аргументов, которые будут объектами.

### <a name="remarks"></a>Remarks

Функция создает объект `shared_ptr<T>` , указатель на который `T(args...)` выделяется и создается с помощью *`alloc`* .

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a> `atomic_compare_exchange_strong`

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a> `atomic_compare_exchange_weak`

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a> `atomic_compare_exchange_strong_explicit`

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a> `atomic_compare_exchange_weak_explicit`

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a> `atomic_exchange`

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a> `atomic_exchange_explicit`

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a> `atomic_is_lock_free`

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a><a name="atomic_load"></a> `atomic_load`

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a> `atomic_load_explicit`

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a><a name="atomic_store"></a> `atomic_store`

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a> `atomic_store_explicit`

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a><a name="const_pointer_cast"></a> `const_pointer_cast`

Приведение const к типу [`shared_ptr`](shared-ptr-class.md) .

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Параметры

*`T`*\
Тип, управляемый возвращаемым общим указателем.

*`Other`*\
Тип, управляемый общим указателем на аргумент.

*`sp`*\
Общий указатель на аргумент.

### <a name="remarks"></a>Remarks

Функция-шаблон возвращает пустой `shared_ptr` объект, если `const_cast<T*>(sp.get())` возвращает указатель null; в противном случае возвращается `shared_ptr<T>` объект, владеющий ресурсом, владельцем которого является *`sp`* . Выражение `const_cast<T*>(sp.get())` должно быть допустимым.

### <a name="example"></a>Пример

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

    *sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a><a name="declare_no_pointers"></a> `declare_no_pointers`

Сообщает сборщику мусора, что символы в блоке памяти, определенном указателем на базовый адрес и размером блока, не содержат трассируемых указателей.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Параметры

*`ptr`*\
Адрес первого символа, который больше не содержит трассируемых указателей.

*`size`*\
Размер блока, который начинается с *`ptr`* , не содержит отслеживаемых указателей.

### <a name="remarks"></a>Remarks

Функция информирует любой сборщик мусора о том, что адреса в диапазоне `[ptr, ptr + size)` больше не содержат отслеживаемых указателей. (Все указатели на выделенное хранилище не должны быть разыменованы, если только они не были доступны.)

## <a name="declare_reachable"></a><a name="declare_reachable"></a> `declare_reachable`

Уведомляет сборщик мусора, что указанный адрес относится к выделенной памяти и является доступным.

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>Параметры

*`ptr`*\
Указатель на доступную, выделенную, допустимую область хранения.

### <a name="remarks"></a>Remarks

Если *`ptr`* параметр не равен null, функция информирует любой сборщик мусора, который *`ptr`* теперь доступен, то есть он указывает на допустимое выделенное хранилище.

## <a name="default_delete"></a><a name="default_delete"></a> `default_delete`

Удаляет объекты, выделенные с помощью **`operator new`** . Подходит для использования с [`unique_ptr`](unique-ptr-class.md) .

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>Параметры

*`ptr`*\
Указатель на объект, который нужно удалить.

*`Other`*\
Тип представленных в массиве элементов, который нужно удалить.

### <a name="remarks"></a>Remarks

Шаблон класса описывает удаление, которое удаляет скалярные объекты, выделенные с помощью **`operator new`** , которые подходят для использования с шаблоном класса `unique_ptr` . Также имеет явную специализацию `default_delete<T[]>`.

## <a name="destroy_at"></a><a name="destroy_at"></a> `destroy_at`

```cpp
template <class T>
void destroy_at(
    T* location);
```

Эквивалентно `location->~T()`.

## <a name="destroy"></a><a name="destroy"></a> `destroy`

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

То же, что:

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a><a name="destroy_n"></a> `destroy_n`

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

То же, что:

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a><a name="dynamic_pointer_cast"></a> `dynamic_pointer_cast`

Динамическое приведение к [`shared_ptr`](shared-ptr-class.md) .

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Параметры

*`T`*\
Тип, управляемый возвращаемым общим указателем.

*`Other`*\
Тип, управляемый общим указателем на аргумент.

*`sp`*\
Общий указатель на аргумент.

### <a name="remarks"></a>Remarks

Функция-шаблон возвращает пустой `shared_ptr` объект, если `dynamic_cast<T*>(sp.get())` возвращает указатель null; в противном случае возвращается `shared_ptr<T>` объект, владеющий ресурсом, владельцем которого является *`sp`* . Выражение `dynamic_cast<T*>(sp.get())` должно быть допустимым.

### <a name="example"></a>Пример

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a><a name="get_deleter"></a> `get_deleter`

Получение удаления из [`shared_ptr`](shared-ptr-class.md) .

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>Параметры

*`Deleter`*\
Тип метода удаления.

*`T`*\
Тип, управляемый общим указателем.

*`sp`*\
Общий указатель.

### <a name="remarks"></a>Remarks

Функция шаблона возвращает указатель на метод удаления типа *`Deleter`* , который принадлежит `shared_ptr` объекту *`sp`* . Если не *`sp`* имеет функции удаления или если его тип удаления не относится *`Deleter`* к типу, функция возвращает 0.

### <a name="example"></a>Пример

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a><a name="get_pointer_safety"></a> `get_pointer_safety`

Возвращает тип безопасности указателя, подразумеваемый любым сборщиком мусора.

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>Remarks

Функция возвращает тип безопасности указателя, предполагаемый любым автоматическим сборщиком мусора.

## <a name="get_temporary_buffer"></a><a name="get_temporary_buffer"></a> `get_temporary_buffer`

Выделяет временное хранилище для последовательности элементов, которая не превышает заданное число элементов.

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>Параметры

*расчета*\
Максимальное количество запрошенных элементов, для которых нужно выделить память.

### <a name="return-value"></a>Возвращаемое значение

`pair`, первый компонент которого — это указатель на память, которая была выделена, а второй компонент — размер буфера (наибольшее количество элементов, которые он может сохранить).

### <a name="remarks"></a>Remarks

Функция делает запрос на выделение памяти, и она может не завершиться успешно. Если буфер не выделен, функция возвращает пару, второй компонент которой равен нулю, а первый компонент — пустой указатель.

Эта функция используется только для временной памяти.

### <a name="example"></a>Пример

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
        << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a><a name="make_shared"></a> `make_shared`

Создает и возвращает объект [`shared_ptr`](shared-ptr-class.md) , указывающий на выделенные объекты, созданные из нуля или более аргументов с помощью распределителя по умолчанию. Выделяет и создает объект указанного типа и `shared_ptr` для управления общим владением объекта и возвращает `shared_ptr`.

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>Параметры

*`args`*\
Без аргументов или несколько аргументов конструктора. Функция определяет перегрузку конструктора, которую нужно вызвать, на основе переданных аргументов.

### <a name="remarks"></a>Remarks

Используйте одновременно `make_shared` как простой и эффективный способ создания объекта и `shared_ptr` для управления общим доступом к объекту. Семантически следующие два оператора эквивалентны:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Однако первый оператор назначает два выделения, и при сбое выделения `shared_ptr` после успешного выделения объекта `Example` происходит утечка неименованного объекта `Example`. Оператор с `make_shared` проще, поскольку используется только один вызов функции. Он более эффективен, так как библиотека может создать одно и то же выделение для объекта и интеллектуального указателя. Эта функция выполняется быстрее и приводит к уменьшению фрагментации памяти, и существует вероятность возникновения исключения в одном выделении, но не в другом. Благодаря более оптимальному расположению кода, указывающего на объект и обновляющего счетчики в интеллектуальном указателе, повышается производительность.

[`make_unique`](memory-functions.md#make_unique)Если общий доступ к объекту не нужен, рассмотрите возможность использования. Используйте [`allocate_shared`](memory-functions.md#allocate_shared) , если необходимо указать пользовательский распределитель для объекта. Нельзя использовать `make_shared` , если объекту требуется пользовательский метод удаления, так как в качестве аргумента нельзя передать средство удаления.

В приведенном ниже примере показано, как можно создавать общие указатели на тип, задавая определенные перегрузки конструктора.

### <a name="example"></a>Пример

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
    std::wstring title_;
    std::wstring artist_;

    Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
    Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers()
{
    // Okay, but less efficient to have separate allocations for
    // Song object and shared_ptr control block.
    auto song = new Song(L"Ode to Joy", L"Beethoven");
    std::shared_ptr<Song> sp0(song);

    // Use make_shared function when possible. Memory for control block
    // and Song object are allocated in the same call:
    auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
    auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

    // make_shared infers which constructor to use based on the arguments.
    auto sp3 = std::make_shared<Song>(L"Greensleeves");

    // The playlist vector makes copies of the shared_ptr pointers.
    std::vector<std::shared_ptr<Song>> playlist;
    playlist.push_back(sp0);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    playlist.push_back(sp3);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

В примере получается следующий результат.

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a><a name="make_unique"></a> `make_unique`

Создает и возвращает [`unique_ptr`](unique-ptr-class.md) объект для указанного типа, который создается с помощью указанных аргументов.

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>Параметры

*`T`*\
Тип объекта, на который будет указывать `unique_ptr`.

*`Args`*\
Типы аргументов конструктора, заданные параметром *`args`* .

*`args`*\
Аргументы, передаваемые конструктору объекта типа *`T`* .

*`elements`*\
Массив элементов типа *`T`* .

*`size`*\
Количество элементов, для которых нужно выделить место в новом массиве.

### <a name="remarks"></a>Remarks

Первая перегрузка используется для отдельных объектов. Вторая перегрузка вызывается для массивов. Третья перегрузка не позволяет указать размер массива в аргументе типа ( `make_unique<T[N]>` ); Эта конструкция не поддерживается текущим стандартом. При использовании `make_unique` для создания `unique_ptr` в массив требуется инициализировать элементы массива отдельно. Вместо использования этой перегрузки, вероятно, лучше использовать [`std::vector`](vector-class.md) .

Так как `make_unique` тщательно реализована для безопасности исключений, рекомендуется использовать `make_unique` вместо прямого вызова конструкторов `unique_ptr`.

### <a name="example"></a>Пример

В следующем примере показано, как использовать `make_unique`. Дополнительные примеры см. в разделе [Примеры: создание и использование экземпляров unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

При появлении ошибки C2280 в связи с `unique_ptr`, это почти наверняка связано с тем, что вы пытаетесь вызвать его конструктор копированием, который является удаленной функцией.

## <a name="owner_less"></a><a name="owner_less"></a> `owner_less`

Разрешает смешанные сравнения общих и слабых указателей на основе собственности. Возвращает, **`true`** если левый параметр упорядочивается до правого параметра функцией-членом `owner_before` .

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>Параметры

*`left`*\
Общий или слабый указатель.

*`right`*\
Общий или слабый указатель.

### <a name="remarks"></a>Remarks

Шаблоны классов определяют все их операторы членов как возвращаемые `left.owner_before(right)` .

## <a name="reinterpret_pointer_cast"></a><a name="reinterpret_pointer_cast"></a> `reinterpret_pointer_cast`

Создает новый объект `shared_ptr` из существующего общего указателя с помощью приведения.

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>Параметры

*`ptr`*\
Ссылка на `shared_ptr<U>` .

### <a name="remarks"></a>Remarks

Если *`ptr`* параметр пуст, новый параметр `shared_ptr` также будет пустым, в противном случае — на *`ptr`* . Новый общий указатель является результатом вычисления `reinterpret_cast<Y*>(ptr.get())` , где `Y` имеет значение `typename std::shared_ptr<T>::element_type` . Если `reinterpret_cast<T*>((U*)nullptr)` параметр не имеет правильного формата, поведение не определено.

Функция шаблона, которая принимает ссылку lvalue, является новой в C++ 17. Функция шаблона, которая принимает ссылку rvalue, является новой в C++ 20.

## <a name="return_temporary_buffer"></a><a name="return_temporary_buffer"></a> `return_temporary_buffer`

Отменяет выделение временной памяти, выделенной с помощью функции шаблона `get_temporary_buffer`.

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>Параметры

*`buffer`*\
Указатель на память, которую нужно освободить.

### <a name="remarks"></a>Remarks

Эта функция используется только для временной памяти.

### <a name="example"></a>Пример

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
         << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

    int* tempBuffer = resultPair.first;

    // Deallocates memory allocated with get_temporary_buffer
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a><a name="static_pointer_cast"></a> `static_pointer_cast`

Статическое приведение к [`shared_ptr`](shared-ptr-class.md) .

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Параметры

*`T`*\
Тип, управляемый возвращаемым общим указателем.

*`Other`*\
Тип, управляемый общим указателем на аргумент.

*`sp`*\
Общий указатель на аргумент.

### <a name="remarks"></a>Remarks

Функция-шаблон возвращает пустой `shared_ptr` объект, если *`sp`* является пустым `shared_ptr` объектом; в противном случае возвращается `shared_ptr<T>` объект, владеющий ресурсом, владельцем которого является *`sp`* . Выражение `static_cast<T*>(sp.get())` должно быть допустимым.

### <a name="example"></a>Пример

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a><a name="swap"></a> `swap`

Переключение двух [`shared_ptr`](shared-ptr-class.md) [`unique_ptr`](unique-ptr-class.md) объектов, или [`weak_ptr`](weak-ptr-class.md) .

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>Параметры

*`T`*\
Тип, управляемый указателем аргумента.

*`Deleter`*\
Удаление уникального типа указателя.

*`left`*\
Левый указатель.

*`right`*\
Правый указатель.

### <a name="remarks"></a>Remarks

Функция шаблона вызывает `left.swap(right)`.

### <a name="example"></a>Пример

```cpp
// std__memory__swap.cpp
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

## <a name="undeclare_no_pointers"></a><a name="undeclare_no_pointers"></a> `undeclare_no_pointers`

Сообщает сборщику мусора, что символы в блоке памяти, определенном указателем на базовый адрес и размером блока, теперь могут содержать трассируемые указатели.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Параметры

*`ptr`*\
Указатель на адрес памяти, ранее помеченный с помощью [`declare_no_pointers`](#declare_no_pointers) .

*`size`*\
Число байтов в диапазоне памяти. Это значение должно равняться числу, используемому в `declare_no_pointers` вызове.

### <a name="remarks"></a>Remarks

Функция информирует любой сборщик мусора о том, что диапазон адресов `[ptr, ptr + size)` теперь может содержать отслеживаемые указатели.

## <a name="undeclare_reachable"></a><a name="undeclare_reachable"></a> `undeclare_reachable`

Отменяет объявление достижимости для указанного расположения в памяти.

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>Параметры

*`ptr`*\
Указатель на адрес памяти, ранее помеченный с помощью [`declare_reachable`](#declare_reachable) .

### <a name="remarks"></a>Remarks

Если *`ptr`* параметр не имеет значение **`nullptr`** , функция информирует все сборщики мусора, которые *`ptr`* больше не доступны. Он возвращает безопасный производный указатель, который сравнивается со значением *`ptr`* .

## <a name="uninitialized_copy"></a><a name="uninitialized_copy"></a> `uninitialized_copy`

Копирует объекты из указанного исходного диапазона в неинициализированный конечный диапазон.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Итератор ввода, обращающийся к первому элементу в исходном диапазоне.

*`last`*\
Итератор ввода, обращающийся к последнему элементу в исходном диапазоне.

*`dest`*\
Прямой оператор, обращающийся к первому элементу в диапазоне назначения.

### <a name="return-value"></a>Возвращаемое значение

Прямой итератор, обращающийся к первой позиции за пределами целевого диапазона, если исходный диапазон не был пустым.

### <a name="remarks"></a>Remarks

Этот алгоритм позволяет отделить выделение памяти от создания объекта.

Шаблонная функция фактически выполняется.

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

если код не создает исключение. В этом случае все созданные объекты уничтожаются, и создается исключение.

Перегрузка с политикой выполнения — это новая версия C++ 17.

### <a name="example"></a>Пример

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a><a name="uninitialized_copy_n"></a> `uninitialized_copy_n`

Создает копию заданного числа элементов из итератора ввода. Копии помещаются в прямой итератор.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Итератор ввода, который ссылается на объект, подлежащий копированию.

*`count`*\
Целочисленный тип со знаком или без знака, указывающий количество операций копирования объекта.

*`dest`*\
Прямой итератор, ссылающийся на место размещения новых копий.

### <a name="return-value"></a>Возвращаемое значение

Прямой итератор, обращающийся к первой позиции после места назначения. Если исходный диапазон был пустым, итератор обращается к *`first`* .

### <a name="remarks"></a>Remarks

Функция шаблона фактически выполняет следующий код:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

если код не создает исключение. В этом случае все созданные объекты уничтожаются, и создается исключение.

Перегрузка с политикой выполнения — это новая версия C++ 17.

## <a name="uninitialized_default_construct"></a><a name="uninitialized_default_construct"></a> `uninitialized_default_construct`

По умолчанию конструирует объекты итераторов `value_type` в указанном диапазоне.

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Итератор, обращающийся к первому элементу в диапазоне для создания.

*`last`*\
Итератор, указывающий на одну после последнего элемента в диапазоне для создания.

### <a name="remarks"></a>Remarks

Версия без политики выполнения фактически аналогична:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

При возникновении исключения ранее созданные объекты уничтожаются в неопределенном порядке.

Версия с политикой выполнения имеет тот же результат, но выполняется в соответствии с указанным *`policy`* .

Эти функции появились в C++ 17.

## <a name="uninitialized_default_construct_n"></a><a name="uninitialized_default_construct_n"></a> `uninitialized_default_construct_n`

По умолчанию конструирует указанное число объектов итератора `value_type` , начиная с указанного расположения.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Итератор, обращающийся к первому элементу в диапазоне назначения для создания.

*`count`*\
Число элементов в диапазоне назначения для создания.

### <a name="return-value"></a>Возвращаемое значение

Прямой итератор, обращающийся к первой позиции за пределами целевого диапазона, если исходный диапазон не был пустым.

### <a name="remarks"></a>Remarks

Версия без политики выполнения фактически аналогична:

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

При возникновении исключения ранее созданные объекты уничтожаются в неопределенном порядке.

Версия с политикой выполнения имеет тот же результат, но выполняется в соответствии с указанным *`policy`* .

Эти функции появились в C++ 17.

## <a name="uninitialized_fill"></a><a name="uninitialized_fill"></a> `uninitialized_fill`

Копирует объекты с указанным значением в неинициализированный конечный диапазон.

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Прямой итератор, обращающийся к первому элементу в диапазоне назначения для инициализации.

*`last`*\
Прямой итератор, обращающийся к последнему элементу в диапазоне назначения для инициализации.

*`value`*\
Значение, используемое для инициализации диапазона назначения.

### <a name="remarks"></a>Remarks

Этот алгоритм позволяет отделить выделение памяти от создания объекта.

Шаблонная функция фактически выполняется.

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

если код не создает исключение. В этом случае все созданные объекты уничтожаются, и создается исключение.

Перегрузка с политикой выполнения — это новая версия C++ 17.

### <a name="example"></a>Пример

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a><a name="uninitialized_fill_n"></a> `uninitialized_fill_n`

Копирует объекты указанного значения в указанное число элементов неинициализированного диапазона назначения.

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Прямой итератор, обращающийся к первому элементу в диапазоне назначения для инициализации.

*`count`*\
Число элементов для инициализации.

*`value`*\
Значение, используемое для инициализации диапазона назначения.

### <a name="remarks"></a>Remarks

Этот алгоритм позволяет отделить выделение памяти от создания объекта.

Шаблонная функция фактически выполняется.

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

если код не создает исключение. В этом случае все созданные объекты уничтожаются, и создается исключение.

Перегрузка с политикой выполнения — это новая версия C++ 17.

### <a name="example"></a>Пример

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a><a name="uninitialized_move"></a> `uninitialized_move`

Перемещает элементы из исходного диапазона в область неинициализированной целевой памяти.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Входной итератор, обращающийся к первому элементу в исходном диапазоне для перемещения.

*`last`*\
Входной итератор, указывающий на один за последним элементом в исходном диапазоне для перемещения.

*`dest`*\
Начало диапазона назначения.

### <a name="remarks"></a>Remarks

Версия без политики выполнения фактически аналогична:

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

При возникновении исключения некоторые объекты в исходном диапазоне могут остаться в допустимом, но неопределенном состоянии. Ранее созданные объекты уничтожаются в неопределенном порядке.

Версия с политикой выполнения имеет тот же результат, но выполняется в соответствии с указанным *`policy`* .

Эти функции появились в C++ 17.

## <a name="uninitialized_move_n"></a><a name="uninitialized_move_n"></a> `uninitialized_move_n`

Перемещает указанное число элементов из исходного диапазона в область неинициализированной целевой памяти.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Входной итератор, обращающийся к первому элементу в исходном диапазоне для перемещения.

*`count`*\
Количество элементов в исходном диапазоне для перемещения.

*`dest`*\
Начало диапазона назначения.

### <a name="remarks"></a>Remarks

Версия без политики выполнения фактически аналогична:

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

При возникновении исключения некоторые объекты в исходном диапазоне могут остаться в допустимом, но неопределенном состоянии. Ранее созданные объекты уничтожаются в неопределенном порядке.

Версия с политикой выполнения имеет тот же результат, но выполняется в соответствии с указанным *`policy`* .

Эти функции появились в C++ 17.

## <a name="uninitialized_value_construct"></a><a name="uninitialized_value_construct"></a> `uninitialized_value_construct`

Конструирует объекты итераторов `value_type` по инициализации значений в указанном диапазоне.

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Итератор, обращающийся к первому элементу в конструкции диапазона к значению.

*`last`*\
Итератор, обращающийся к одному из последних элементов в конструкции Range to Value.

### <a name="remarks"></a>Remarks

Версия без политики выполнения фактически аналогична:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

При возникновении исключения ранее созданные объекты уничтожаются в неопределенном порядке.

Версия с политикой выполнения имеет тот же результат, но выполняется в соответствии с указанным *`policy`* .

При сбое выделения памяти `std::bad_alloc` возникает исключение.

Эти функции появились в C++ 17.

## <a name="uninitialized_value_construct_n"></a><a name="uninitialized_value_construct_n"></a> `uninitialized_value_construct_n`

Конструирует заданное количество объектов `value_type` с помощью инициализации значения итератора, начиная с указанного расположения.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Параметры

*`policy`*\
Используемая политика выполнения.

*`first`*\
Итератор, обращающийся к первому элементу в диапазоне назначения для создания.

*`count`*\
Число элементов в диапазоне назначения для создания.

### <a name="remarks"></a>Remarks

Версия без политики выполнения фактически аналогична:

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

При возникновении исключения ранее созданные объекты уничтожаются в неопределенном порядке.

Версия с политикой выполнения имеет тот же результат, но выполняется в соответствии с указанным *`policy`* .

При сбое выделения памяти `std::bad_alloc` возникает исключение.

Эти функции появились в C++ 17.

## <a name="uses_allocator_v"></a><a name="uses_allocator_v"></a> `uses_allocator_v`

Шаблон вспомогательной переменной для доступа к значению `uses_allocator` шаблона.

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>См. также раздел

[`<memory>`](memory.md)
