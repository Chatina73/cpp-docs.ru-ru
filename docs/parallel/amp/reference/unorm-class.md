---
description: 'Дополнительные сведения о: unorm Class'
title: Класс unorm
ms.date: 11/04/2016
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
ms.openlocfilehash: 947660d046ea41025e70aa4e6521e3c8f34c0a94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314532"
---
# <a name="unorm-class"></a>Класс unorm

Представляет unorm число. Каждый элемент является числом с плавающей запятой в диапазоне [0,0 f, 1,0 f].

## <a name="syntax"></a>Синтаксис

```cpp
class unorm;
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Конструктор unorm](#ctor)|Перегружен. Конструктор по умолчанию. Инициализируйте до 0,0 f.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание|
|----------|-----------------|
|unorm:: operator--||
|unorm:: operator float|Оператор преобразования. Преобразуйте номер unorm в значение с плавающей запятой.|
|unorm:: operator * =||
|unorm:: operator/=||
|unorm:: operator + +||
|unorm:: operator + =||
|unorm:: operator =||
|unorm:: operator-=||

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`unorm`

## <a name="requirements"></a>Требования

**Заголовок:** amp_short_vectors. h

**Пространство имен:** Concurrency:: Graphics

## <a name="unorm"></a><a name="ctor"></a> unorm

Конструктор по умолчанию. Инициализируйте до 0,0 f.

```cpp
unorm(
    void) restrict(amp,
    cpu);

explicit unorm(
    float _V) restrict(amp,
    cpu);

explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

explicit unorm(
    int _V) restrict(amp,
    cpu);

explicit unorm(
    double _V) restrict(amp,
    cpu);

unorm(
    const unorm& _Other) restrict(amp,
    cpu);

inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Параметры

*_V*<br/>
Значение, используемое для инициализации.

*_Other*<br/>
Объект нормы, используемый для инициализации.

## <a name="see-also"></a>См. также раздел

[Пространство имен Concurrency::graphics](concurrency-graphics-namespace.md)
