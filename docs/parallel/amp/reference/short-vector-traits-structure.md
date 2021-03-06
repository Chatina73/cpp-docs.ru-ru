---
description: 'Дополнительные сведения: структура short_vector_traits'
title: Структура short_vector_traits
ms.date: 11/04/2016
f1_keywords:
- short_vector_traits
- AMP_SHORT_VECTORS/short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::size Constant
ms.assetid: cd9492da-9e02-4a6e-9d50-b61252cdb460
ms.openlocfilehash: dc211c8e66cbd31c57655afce22376909cf77530
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329893"
---
# <a name="short_vector_traits-structure"></a>Структура short_vector_traits

short_vector_traits позволяет получать базовую длину вектора и скалярный тип для короткого векторного типа или скалярного типа.

## <a name="syntax"></a>Синтаксис

```cpp
template<
    typename T
>
struct short_vector_traits;
template<>
struct short_vector_traits<unsigned int>;
template<>
struct short_vector_traits<uint_2>;
template<>
struct short_vector_traits<uint_3>;
template<>
struct short_vector_traits<uint_4>;
template<>
struct short_vector_traits<int>;
template<>
struct short_vector_traits<int_2>;
template<>
struct short_vector_traits<int_3>;
template<>
struct short_vector_traits<int_4>;
template<>
struct short_vector_traits<float>;
template<>
struct short_vector_traits<float_2>;
template<>
struct short_vector_traits<float_3>;
template<>
struct short_vector_traits<float_4>;
template<>
struct short_vector_traits<unorm>;
template<>
struct short_vector_traits<unorm_2>;
template<>
struct short_vector_traits<unorm_3>;
template<>
struct short_vector_traits<unorm_4>;
template<>
struct short_vector_traits<norm>;
template<>
struct short_vector_traits<norm_2>;
template<>
struct short_vector_traits<norm_3>;
template<>
struct short_vector_traits<norm_4>;
template<>
struct short_vector_traits<double>;
template<>
struct short_vector_traits<double_2>;
template<>
struct short_vector_traits<double_3>;
template<>
struct short_vector_traits<double_4>;
```

### <a name="parameters"></a>Параметры

`T`

## <a name="members"></a>Элементы

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Описание|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Конструктор short_vector_traits::short_vector_traits](#ctor)||

### <a name="public-constants"></a>Открытые константы

|Имя|Описание|
|----------|-----------------|
|[Константа short_vector_traits::size](#size)||

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`short_vector_traits`

## <a name="requirements"></a>Требования

**Заголовок:** amp_short_vectors. h

**Пространство имен:** Concurrency:: Graphics

## <a name="short_vector_traitsshort_vector_traits-constructor"></a><a name="ctor"></a> Конструктор short_vector_traits:: short_vector_traits

```cpp
short_vector_traits();
```

## <a name="short_vector_traitssize-constant"></a><a name="size"></a> Константа short_vector_traits:: size

```cpp
static int const size = 1;
```

## <a name="see-also"></a>См. также раздел

[Пространство имен Concurrency::graphics](concurrency-graphics-namespace.md)
