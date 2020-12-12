---
description: 'Дополнительные сведения о: класс варианта'
title: Класс Variant
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
helpviewer_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
ms.openlocfilehash: 0fc2887def147b458e63bc316f211e62a5eba879
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305108"
---
# <a name="variant-class"></a>Класс Variant

Любой экземпляр Variant в любой момент времени либо содержит значение одного из альтернативных типов, либо не содержит значения.

## <a name="syntax"></a>Синтаксис

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>Члены

### <a name="constructors"></a>Конструкторы

|Имя|Описание|
|-|-|
|[variant](#variant)|Создает объект типа `variant`.|

### <a name="functions"></a>Функции

|Имя|Описание|
|-|-|
|[emplace](#emplace)|Создает новое вложенное значение.|
|[index](#index)|Возвращает индекс содержащегося значения.|
|[позиции](#swap)||
|[valueless_by_exception](#emplace)|Возвращает **`false`** , если вариант содержит значение.|

### <a name="operators"></a>Операторы

|Имя|Описание|
|-|-|
|[Оператор =](#op_eq)|Заменяет вариант копией другого варианта.|

## <a name="emplace"></a><a name="emplace"></a> emplace

Создает новое вложенное значение.

```cpp
template <class T, class... Args>
    T& emplace(Args&&...);
template <class T, class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(Args&&...);
template <size_t I, class U, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(initializer_list<U>, Args&&...);
```

## <a name="index"></a><a name="index"></a> номер

Возвращает индекс содержащегося значения.

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a><a name="variant"></a> значение

Создает объект типа `variant`. Также включает деструктор.

```cpp
constexpr variant() noexcept(see below);
variant(const variant&);
variant(variant&&) noexcept(see below);
template <class T>
    constexpr variant(T&&) noexcept(see below);
template <class T, class... Args>
    constexpr explicit variant(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    constexpr explicit variant(in_place_type_t<T>, initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    constexpr explicit variant(in_place_index_t<I>, Args&&...);
template <size_t I, class U, class... Args>
    constexpr explicit variant(in_place_index_t<I>, initializer_list<U>, Args&&...);

template <class Alloc>
    variant(allocator_arg_t, const Al&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, const variant&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, variant&&);
template <class Alloc, class T>
    variant(allocator_arg_t, const Al&, T&&);
template <class Alloc, class T, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, Args&&...);
template <class Alloc, class T, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, initializer_list<U>, Args&&...);
template <class Alloc, size_t I, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, Args&&...);
template <class Alloc, size_t I, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, initializer_list<U>, Args&&...);

~variant();
```

### <a name="parameters"></a>Параметры

*Al*\
Класс распределителя для использования с данным объектом.

## <a name="operator"></a><a name="op_eq"></a> Оператор =

Заменяет вариант копией другого варианта.

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a><a name="swap"></a> позиции

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless_by_exception"></a><a name="valueless"></a> valueless_by_exception

Возвращает **`false`** , если вариант содержит значение.

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
