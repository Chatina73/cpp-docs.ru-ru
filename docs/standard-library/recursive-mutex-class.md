---
description: 'Дополнительные сведения о: recursive_mutex классе'
title: Класс recursive_mutex
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: f8a9c9322407871984c83135eecd2e26ac475d2b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337888"
---
# <a name="recursive_mutex-class"></a>Класс recursive_mutex

Представляет *тип мьютекса*. В отличие от класса [mutex](../standard-library/mutex-class-stl.md), поведение вызовов методов блокировки для объектов, которые уже заблокированы, четко определено.

## <a name="syntax"></a>Синтаксис

```cpp
class recursive_mutex;
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Формирует объект `recursive_mutex`.|
|[Деструктор ~recursive_mutex](#dtorrecursive_mutex_destructor)|Освобождает все ресурсы, используемые объектом `recursive_mutex`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[lock](#lock)|Блокирует вызывающий поток до тех пор, пока этот поток не получит права владельца мьютекса.|
|[try_lock](#try_lock)|Попытки получить права владельца мьютекса без блокировки.|
|[блокирован](#unlock)|Освобождает права владения мьютексом.|

## <a name="requirements"></a>Требования

**Заголовок:**\<mutex>

**Пространство имен:** std

## <a name="lock"></a><a name="lock"></a> скрыть

Блокирует вызывающий поток до тех пор, пока этот поток не получит права владельца объекта `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Комментарии

Если вызывающий поток уже владеет `mutex`, метод немедленно возвращает значение и предыдущая блокировка остается в силе.

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a> recursive_mutex

Создает объект `recursive_mutex`, который не заблокирован.

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a>  ~recursive_mutex

Освобождает все ресурсы, используемые объектом.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Комментарии

Если при выполнении деструктора объект заблокирован, поведение не определено.

## <a name="try_lock"></a><a name="try_lock"></a> try_lock

Попытки получить права владельца объекта `mutex` без блокировки.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Возвращаемое значение

**`true`** Если метод успешно получает владение `mutex` или, если вызывающий поток уже владеет `mutex**; otherwise, **false` .

### <a name="remarks"></a>Комментарии

Если вызывающий поток уже владеет `mutex` , функция немедленно возвращает значение **`true`** , а предыдущая блокировка остается в силе.

## <a name="unlock"></a><a name="unlock"></a> блокирован

Освобождает права владения мьютексом.

```cpp
void unlock();
```

### <a name="remarks"></a>Комментарии

Этот метод освобождает владение `mutex` только после его вызова столько раз, сколько [lock](#lock) и [try_lock](#try_lock) были успешно вызваны для объекта`recursive_mutex`.

Если вызывающий поток не является владельцем `mutex`, поведение не определено.

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
