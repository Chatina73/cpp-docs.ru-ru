---
title: Структура short_vector_traits
ms.date: 11/04/2016
f1_keywords:
- short_vector_traits
- AMP_SHORT_VECTORS/short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::size Constant
ms.assetid: cd9492da-9e02-4a6e-9d50-b61252cdb460
ms.openlocfilehash: fd86228417234f705d3f765624cd942c982df875
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456190"
---
# <a name="shortvectortraits-structure"></a>Структура short_vector_traits

Получение базовых Длина вектора и скалярный тип типа короткого вектора или скалярного типа позволяет short_vector_traits

## <a name="syntax"></a>Синтаксис

```
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

#### <a name="parameters"></a>Параметры

`T`

## <a name="members"></a>Участники

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Описание|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[Конструктор short_vector_traits::short_vector_traits](#ctor)||

### <a name="public-constants"></a>Открытые константы

|name|Описание|
|----------|-----------------|
|[Константа short_vector_traits::size](#size)||

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`short_vector_traits`

## <a name="requirements"></a>Требования

**Заголовок:** amp_short_vectors.h

**Пространство имен:** Concurrency::graphics

##  <a name="ctor"></a>  Конструктор short_vector_traits::short_vector_traits

```
short_vector_traits();
```

##  <a name="size"></a>  Константа short_vector_traits::size

```
static int const size = 1;
```

## <a name="see-also"></a>См. также

[Пространство имен Concurrency::graphics](concurrency-graphics-namespace.md)
