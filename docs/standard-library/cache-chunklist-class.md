---
description: 'Дополнительные сведения о: cache_chunklist классе'
title: Класс cache_chunklist
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: 264713ed12727d45928f40f2bc6a790e0e3b1db1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325402"
---
# <a name="cache_chunklist-class"></a>Класс cache_chunklist

Задает [распределитель блоков](../standard-library/allocators-header.md), который выделяет и освобождает блоки памяти одного размера.

## <a name="syntax"></a>Синтаксис

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Параметры

*SZ*\
Число выделяемых элементов в массиве.

## <a name="remarks"></a>Комментарии

Этот шаблон класса использует **оператор New** для выделения блоков необработанной памяти, блоков подвыделения для выделения хранилища для блока памяти, когда это необходимо. Он хранит освобожденные блоки памяти в отдельном свободном списке для каждого фрагмента и использует **оператор DELETE** для освобождения блока, если ни один из его блоков памяти не используется.

Каждый блок памяти содержит *SZ* байты доступной памяти и указатель на блок, к которому он принадлежит. Каждый блок содержит `Nelts` блоки памяти, три указателя, int и данные, необходимые **операторам New** и **Delete** .

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[cache_chunklist](#cache_chunklist)|Создает объект типа `cache_chunklist`.|

### <a name="member-functions"></a>Функции элементов

|Функция-член|Описание|
|-|-|
|[памяти](#allocate)|Выделяет блок памяти.|
|[deallocate](#deallocate)|Освобождает указанное число объектов из памяти, начиная с заданной позиции.|

## <a name="requirements"></a>Требования

**Заголовок:**\<allocators>

**Пространство имен:** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a> cache_chunklist:: allocate

Выделяет блок памяти.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Параметры

*расчета*\
Число выделяемых элементов в массиве.

### <a name="return-value"></a>Возвращаемое значение

Указатель на выделяемый объект.

### <a name="remarks"></a>Комментарии

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a> cache_chunklist:: cache_chunklist

Создает объект типа `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Комментарии

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a> cache_chunklist::d еаллокате

Освобождает указанное число объектов из памяти, начиная с заданной позиции.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Параметры

*указатель*\
Указатель на первый объект, который должен быть освобожден из хранилища.

*расчета*\
Количество объектов для освобождения из хранилища.

### <a name="remarks"></a>Комментарии

## <a name="see-also"></a>См. также раздел

[\<allocators>](../standard-library/allocators-header.md)
