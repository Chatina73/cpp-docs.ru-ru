---
description: 'Дополнительные сведения о: &lt; Мьютексные &gt; функции и переменные'
title: Функции и переменные &lt;мьютексов&gt;
ms.date: 11/04/2016
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: e06fe09c78d8b79f5dd804e64ef11e84c558ba24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338269"
---
# <a name="ltmutexgt-functions-and-variables"></a>Функции и переменные &lt;мьютексов&gt;

## <a name="adopt_lock"></a><a name="adopt_lock"></a> adopt_lock

Представляет объект, который можно передать в конструкторы для [lock_guard](../standard-library/lock-guard-class.md) и [unique_lock](../standard-library/unique-lock-class.md), чтобы указать на блокировку объекта мьютекса, также передаваемого в конструктор.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a><a name="call_once"></a> call_once

Предоставляет механизм для однократного вызова указанного объекта во время выполнения.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Параметры

*RAS*\
Объект [once_flag](../standard-library/once-flag-structure.md), который гарантирует, что вызываемый объект вызывается только один раз.

*Ж*\
Вызываемый объект.

*Конкретного*\
Список аргументов.

### <a name="remarks"></a>Комментарии

Если *флаг* является недопустимым, функция создает [system_error](../standard-library/system-error-class.md) , код ошибки `invalid_argument` . В противном случае функция шаблона использует свой аргумент *флага* , чтобы убедиться, что она вызывается `F(A...)` успешно только один раз, независимо от того, сколько раз вызывается функция шаблона. Если `F(A...)` завершает работу, создавая исключение, вызов считается неуспешным.

## <a name="defer_lock"></a><a name="defer_lock"></a> defer_lock

Представляет объект, который может быть передан в конструктор для [unique_lock](../standard-library/unique-lock-class.md). Это означает, что конструктор не должен блокировать объект мьютекса, который также ему передается.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a><a name="lock"></a> скрыть

Пытается заблокировать все аргументы без взаимоблокировки.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Комментарии

Аргументы функции-шаблона должны быть типа *мьютекс*, за исключением того, что при вызове `try_lock` могут вызываться исключения.

Функция блокирует все свои аргументы без взаимоблокировки путем вызовов `lock`, `try_lock`, и `unlock`. Если вызов `lock` или `try_lock` приводит к исключению, функция вызывает `unlock` для любых объектов-мьютексов, которые были успешно заблокированы до повторного создания исключения.

## <a name="swap"></a><a name="swap"></a> позиции

```cpp
template <class Mutex>
void swap(unique_lock<Mutex>& x, unique_lock<Mutex>& y) noexcept;
```

## <a name="try_lock"></a><a name="try_lock"></a> try_lock

```cpp
template <class L1, class L2, class... L3> int try_lock(L1&, L2&, L3&...);
```

## <a name="try_to_lock"></a><a name="try_to_lock"></a> try_to_lock

Представляет объект, который можно передать в конструктор для [unique_lock](../standard-library/unique-lock-class.md), чтобы указать, что конструктор должен попытаться разблокировать объект `mutex`, который также передается в него, без блокировки.

```cpp
const try_to_lock_t try_to_lock;
```
