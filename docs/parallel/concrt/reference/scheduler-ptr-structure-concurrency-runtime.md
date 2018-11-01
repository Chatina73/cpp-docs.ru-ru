---
title: Структура scheduler_ptr
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 7fd81a1ccf6702c74a013c5772d59f01121b61a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479226"
---
# <a name="schedulerptr-structure"></a>Структура scheduler_ptr

Представляет указатель на планировщик. Этот класс существует в том, чтобы разрешить в спецификации общего времени жизни путем применения shared_ptr или простой ссылки с помощью необработанного указателя.

## <a name="syntax"></a>Синтаксис

```
struct scheduler_ptr;
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|Перегружен. Создает указатель планировщика из shared_ptr планировщику|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[scheduler_ptr::get](#get)|Возвращает необработанный указатель планировщику|

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание|
|----------|-----------------|
|[scheduler_ptr::operator bool](#operator_bool)|Проверьте, является ли указатель планировщика отличным от null|
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Поведение, как у указателя|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`scheduler_ptr`

## <a name="requirements"></a>Требования

**Заголовок:** pplinterface.h

**Пространство имен:** concurrency

##  <a name="get"></a>  Метод scheduler_ptr::Get

Возвращает необработанный указатель планировщику

```
scheduler_interface* get() const;
```

### <a name="return-value"></a>Возвращаемое значение

##  <a name="operator_bool"></a>  scheduler_ptr::operator bool

Проверьте, является ли указатель планировщика отличным от null

'''operator bool() const;
```

##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;

Behave like a pointer

```
scheduler_interface * operator -> () const;
```

### Return Value

##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor

Creates a scheduler pointer from shared_ptr to scheduler

```
явные scheduler_ptr (планировщика std::shared_ptr < scheduler_interface >);

явные scheduler_ptr (_In_opt_ scheduler_interface * pScheduler);
```

### Parameters

*scheduler*<br/>
The scheduler to convert.

*pScheduler*<br/>
The scheduler pointer to convert.

## See Also

[concurrency Namespace](concurrency-namespace.md)
