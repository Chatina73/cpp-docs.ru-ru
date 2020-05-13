---
title: Класс integer_sequence
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
ms.openlocfilehash: 3de64f7855b5158f1565580d305e2a6eeaf3e76f
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031476"
---
# <a name="integer_sequence-class"></a>Класс integer_sequence

Представляет последовательность целых чисел. Может использоваться для извлечения и развертывания пакетов параметров в типах с переменным числом аргументов, например std::tuple\<T.... >, которые передаются в функцию в качестве аргументов.

## <a name="syntax"></a>Синтаксис

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Параметры

*T*\
Тип значений. Это должен быть целочисленный тип: bool, char, char16_t, char32_t, wchar_t или целочисленный тип со знаком или без знака.

*Вальс*\
Пакет параметров, не являющихся типами, представляющий последовательность значений целочисленного типа T.

## <a name="members"></a>Участники

|||
|-|-|
|`static size_t size() noexcept`|Число элементов в последовательности.|
|`typedef T value_type`|Тип каждого элемента последовательности. Должен быть целочисленным типом.|

## <a name="remarks"></a>Remarks

Пакет параметров, который передается непосредственно в функцию, может быть распакован без использования специальных вспомогательных методов библиотеки. Когда пакет параметров входит в тип, передаваемый в функцию, и вам необходимы индексы для доступа к элементам, то самым простым способом распаковать его будет использование `integer_sequence` и связанных с ним псевдонимов типа `make_integer_sequence`, `index_sequence`, `make_index_sequence` и `index_sequence_for`.

## <a name="example"></a>Пример

Следующий пример основан на исходном предложении [N3658](https://wg21.link/n3658). В нем продемонстрирован способ использования `integer_sequence` для создания `std::tuple` из `std::array<T,N>`, и способ использования `integer_sequence` для получения элементов кортежа.

В функции `a2t``index_sequence` является псевдонимом `integer_sequence` на основе целочисленного типа `size_t`. `make_index_sequence` — это псевдоним, который во время компиляции создает `index_sequence`, отсчитываемый от нуля, с тем же количеством элементов, как у массива, переданного вызывающим объектом. `a2t` передает `index_sequence` по значению в `a2t_`, где выражение `a[I]...` распаковывает `I`, а затем элементы передаются в `make_tuple`, который использует их как отдельные аргументы. Например, если последовательность содержит три элемента, то `make_tuple` вызывается как make_tuple(a[0], a[1], a[2]). Сами элементы массива, конечно, могут быть любого типа.

Функция применения принимает [std::tuple](../standard-library/tuple-class.md), и `integer_sequence` производит `tuple_size` с помощью класса помощника. Обратите внимание, что [std::decay't](../standard-library/decay-class.md) необходимо, потому что [tuple_size](../standard-library/tuple-size-class-tuple.md) не работает с типами ссылок. Функция `apply_` распаковывает элементы кортежа и пересылает их как отдельные аргументы при вызове функции. В этом примере функция представляет из себя простое лямбда-выражение, которое выводит значения.

```cpp
#include <stddef.h>
#include <iostream>
#include <tuple>
#include <utility>
#include <array>
#include <string>

using namespace std;

// Create a tuple from the array and the index_sequence
template<typename Array, size_t... I>
auto a2t_(const Array& a, index_sequence<I...>)
{
    return make_tuple(a[I]...);
}

// Create an index sequence for the array, and pass it to the
// implementation function a2t_
template<typename T, size_t N>
auto a2t(const array<T, N>& a)
{
    return a2t_(a, make_index_sequence<N>());
}

// Call function F with the tuple members as separate arguments.
template<typename F, typename Tuple = tuple<T...>, size_t... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);
}

// Create an index_sequence for the tuple, and pass it with the
// function object and the tuple to the implementation function apply_
template<typename F, typename Tuple = tuple<T...>>
decltype(auto) apply(F&& f, Tuple&& args)
{
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());
}

int main()
{
    const array<string, 3> arr { "Hello", "from", "C++14" };

    //Create a tuple given a array
    auto tup = a2t(arr);

    // Extract the tuple elements
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);

    char c;
    cin >> c;
}
```

Чтобы подготовить `index_sequence` для пакета параметров, используйте `index_sequence_for`\<T...>, который является псевдонимом для `make_index_sequence`\<sizeof...(T)>.

## <a name="requirements"></a>Требования

Заголовок: \<type_traits\>

Пространство имен: std

## <a name="see-also"></a>См. также раздел

[Эллипсис и вариадские шаблоны](../cpp/ellipses-and-variadic-templates.md)
