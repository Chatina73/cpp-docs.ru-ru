---
description: Дополнительные сведения о классе Mutex (стандартная библиотека C++)
title: Класс mutex (Стандартная библиотека C++ ) | Документы Майкрософт
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 528fe0698fb7815be9b678d72055c54bad5ce2bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338282"
---
# <a name="mutex-class-c-standard-library"></a>Класс mutex (Стандартная библиотека C++)

Представляет *тип мьютекса*. Используйте объекты этого типа для принудительного взаимного исключения в программе.

## <a name="syntax"></a>Синтаксис

```cpp
class mutex;
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[принадлежащ](#mutex)|Формирует объект `mutex`.|
|[Деструктор mutex::~mutex](#dtormutex_destructor)|Освобождает ресурсы, используемые объектом `mutex`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[lock](#lock)|Блокирует вызывающий поток до тех пор, пока этот поток не получит права владельца объекта `mutex`.|
|[native_handle](#native_handle)|Возвращает тип реализации, представляющий дескриптор мьютекса.|
|[try_lock](#try_lock)|Попытки получить права владельца объекта `mutex` без блокировки.|
|[блокирован](#unlock)|Освобождает права владения объектом `mutex`.|

## <a name="requirements"></a>Требования

**Заголовок:**\<mutex>

**Пространство имен:** std

## <a name="mutexlock"></a><a name="lock"></a> мьютекс:: Lock

Блокирует вызывающий поток до тех пор, пока этот поток не получит права владельца объекта `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Комментарии

Если вызывающий поток уже является владельцем `mutex`, поведение не определено.

## <a name="mutexmutex-constructor"></a><a name="mutex"></a> Конструктор Mutex:: Mutex

Создает объект `mutex`, который не заблокирован.

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a> Деструктор Mutex:: ~ Mutex

Освобождает все ресурсы, используемые объектом `mutex`.

```cpp
~mutex();
```

### <a name="remarks"></a>Комментарии

Если при выполнении деструктора объект заблокирован, поведение не определено.

## <a name="mutexnative_handle"></a><a name="native_handle"></a> мьютекс:: native_handle

Возвращает тип реализации, представляющий дескриптор мьютекса. Дескриптор мьютекса может использоваться разными способами в зависимости от реализации.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Возвращаемое значение

`native_handle_type`определяется как `Concurrency::critical_section *`, которое приводится к `void *`.

## <a name="mutextry_lock"></a><a name="try_lock"></a> мьютекс:: try_lock

Попытки получить права владельца объекта `mutex` без блокировки.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если метод успешно получает владение `mutex` ; в противном случае — **`false`** .

### <a name="remarks"></a>Комментарии

Если вызывающий поток уже является владельцем `mutex`, поведение не определено.

## <a name="mutexunlock"></a><a name="unlock"></a> мьютекс:: Unlock

Освобождает права владения объектом `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Комментарии

Если вызывающий поток не является владельцем `mutex`, поведение не определено.

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
