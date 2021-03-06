---
description: 'Дополнительные сведения о: uint_2 классе'
title: Класс uint_2
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::uint_2::set_xy
- amp_short_vectors/Concurrency::graphics::uint_2::y
- amp_short_vectors/Concurrency::graphics::uint_2::gr
- amp_short_vectors/Concurrency::graphics::uint_2::operator-
- amp_short_vectors/Concurrency::graphics::uint_2::get_x
- amp_short_vectors/Concurrency::graphics::uint_2::operator-=
- amp_short_vectors/Concurrency::graphics::uint_2::r
- amp_short_vectors/Concurrency::graphics::uint_2::yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator--
- amp_short_vectors/Concurrency::graphics::uint_2::set_yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator=
- amp_short_vectors/Concurrency::graphics::uint_2::set_x
- amp_short_vectors/Concurrency::graphics::uint_2::operator+=
- amp_short_vectors/Concurrency::graphics::uint_2::get_y
- amp_short_vectors/Concurrency::graphics::uint_2::xy
- amp_short_vectors/Concurrency::graphics::uint_2::x
- amp_short_vectors/Concurrency::graphics::uint_2::get_xy
- amp_short_vectors/Concurrency::graphics::uint_2::set_y
- amp_short_vectors/Concurrency::graphics::uint_2
- amp_short_vectors/Concurrency::graphics::uint_2::operator*=
- amp_short_vectors/Concurrency::graphics::uint_2::get_yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator/=
- amp_short_vectors/Concurrency::graphics::uint_2::g
- amp_short_vectors/Concurrency::graphics::uint_2::operator++
- amp_short_vectors/Concurrency::graphics::uint_2::rg
ms.assetid: 9fcc9129-72b1-4da7-9012-4d3be15f1c52
ms.openlocfilehash: 6cf10e10baad6cedb06cef4358feebb11e6ce076
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325814"
---
# <a name="uint_2-class"></a>Класс uint_2

Представляет короткий вектор двух целых чисел без знака.

## <a name="syntax"></a>Синтаксис

```cpp
class uint_2;
```

## <a name="members"></a>Члены

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Описание|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Конструктор uint_2](#ctor)|Перегружен. Конструктор по умолчанию инициализирует все элементы значением 0.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|uint_2:: get_x||
|uint_2:: get_xy||
|uint_2:: get_y||
|uint_2:: get_yx||
|uint_2:: ref_g_Method||
|uint_2:: ref_r_Method||
|uint_2:: ref_x_Method||
|uint_2:: ref_y_Method||
|uint_2:: set_x||
|uint_2:: set_xy||
|uint_2:: set_y||
|uint_2:: set_yx||

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание|
|----------|-----------------|
|uint_2:: operator--||
|uint_2:: operator% =||
|uint_2:: operator&=||
|uint_2:: operator * =||
|uint_2:: operator/=||
|uint_2:: operator ^ =||
|uint_2:: operator&#124;=||
|uint_2:: operator ~||
|uint_2:: operator + +||
|uint_2:: operator + =||
|uint_2:: operator<\<=||
|uint_2:: operator =||
|uint_2:: operator-=||
|uint_2:: operator>>=||

### <a name="public-constants"></a>Открытые константы

|Имя|Описание|
|----------|-----------------|
|[Константа размера](#uint_2__size)||

### <a name="public-data-members"></a>Открытые члены данных

|Имя|Описание|
|----------|-----------------|
|uint_2:: g||
|uint_2:: GR||
|uint_2:: r||
|uint_2:: RG||
|uint_2:: x||
|uint_2:: XY||
|uint_2:: y||
|uint_2:: Икс||

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`uint_2`

## <a name="requirements"></a>Требования

**Заголовок:** amp_short_vectors. h

**Пространство имен:** Concurrency:: Graphics

## <a name="uint_2"></a><a name="ctor"></a> uint_2

Конструктор по умолчанию инициализирует все элементы значением 0.

```cpp
uint_2() restrict(amp,
    cpu);

uint_2(
    unsigned int _V0,
    unsigned int _V1) restrict(amp,
    cpu);

uint_2(
    unsigned int _V) restrict(amp,
    cpu);

uint_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Параметры

*_V0*<br/>
Значение для инициализации элемента 0.

*_V1*<br/>
Значение для инициализации элемента 1.

*_V*<br/>
Значение для инициализации.

*_Other*<br/>
Объект, используемый для инициализации.

## <a name="size"></a><a name="uint_2__size"></a> изменять

```cpp
static const int size = 2;
```

## <a name="see-also"></a>См. также раздел

[Пространство имен Concurrency::graphics](concurrency-graphics-namespace.md)
