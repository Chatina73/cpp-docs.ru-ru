---
description: Дополнительные сведения о классе EventSource
title: EventSource - класс
ms.date: 09/12/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
ms.openlocfilehash: 2553d82a0fc16cd759f43ef2e4ae9527884cab10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272816"
---
# <a name="eventsource-class"></a>EventSource - класс

Представляет событие, не являющееся гибким. Функции-члены `EventSource` добавляют, удаляют и вызывают обработчики событий. Для гибких событий используйте [агиливентсаурце](agileeventsource-class.md).

## <a name="syntax"></a>Синтаксис

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Параметры

*тделегатеинтерфаце*<br/>
Интерфейс к делегату, который представляет обработчик событий.

## <a name="members"></a>Элементы

### <a name="public-constructors"></a>Открытые конструкторы

| name                                     | Описание                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource:: EventSource](#eventsource) | Инициализирует новый экземпляр класса `EventSource`. |

### <a name="public-methods"></a>Открытые методы

| name                                 | Описание                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: Add](#add)             | Добавляет обработчик событий, представленный указанным интерфейсом делегата, к набору обработчиков событий для текущего `EventSource` объекта.                     |
| [EventSource:: DataSize](#getsize)     | Возвращает число обработчиков событий, связанных с текущим `EventSource` объектом.                                                                         |
| [EventSource:: InvokeAll](#invokeall) | Вызывает каждый обработчик событий, связанный с текущим `EventSource` объектом, используя указанные типы аргументов и аргументы.                                      |
| [EventSource:: Remove](#remove)       | Удаляет обработчик событий, представленный указанным токеном регистрации событий, из набора обработчиков событий, связанного с текущим `EventSource` объектом. |

### <a name="protected-data-members"></a>Защищенные члены данных

| Имя                                                    | Описание                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: addRemoveLock_](#addremovelock)           | Синхронизирует доступ к [targets_](#targets) массиву при добавлении, удалении или вызове обработчиков событий.                          |
| [EventSource:: targets_](#targets)                       | Массив из одного или нескольких обработчиков событий.                                                                                           |
| [EventSource:: targetsPointerLock_](#targetspointerlock) | Синхронизирует доступ к внутренним элементам данных, даже пока обработчики событий для этой EventSource добавляются, удаляются или вызываются. |

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`EventSource`

## <a name="requirements"></a>Требования

**Заголовок:** Event. h

**Пространство имен:** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a> EventSource:: Add

Добавляет обработчик событий, представленный указанным интерфейсом делегата, к набору обработчиков событий для текущего `EventSource` объекта.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Параметры

*делегатеинтерфаце*<br/>
Интерфейс для объекта делегата, который представляет обработчик событий.

*token*<br/>
После завершения операции представляет дескриптор события. Используйте этот токен в качестве параметра метода [Remove ()](#remove) для отмены обработчика событий.

### <a name="return-value"></a>Возвращаемое значение

Значение S_OK, если операция завершилась успешно; в противном случае — значение HRESULT, указывающее на ошибку.

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a> EventSource:: addRemoveLock_

Синхронизирует доступ к [targets_](#targets) массиву при добавлении, удалении или вызове обработчиков событий.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a> EventSource:: EventSource

Инициализирует новый экземпляр класса `EventSource`.

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a> EventSource:: DataSize

Возвращает число обработчиков событий, связанных с текущим `EventSource` объектом.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Возвращаемое значение

Число обработчиков событий в [targets_](#targets).

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a> EventSource:: InvokeAll

Вызывает каждый обработчик событий, связанный с текущим `EventSource` объектом, используя указанные типы аргументов и аргументы.

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>Параметры

*T0*<br/>
Тип нулевого аргумента обработчика событий.

*T1*<br/>
Тип первого аргумента обработчика событий.

*T2*<br/>
Тип второго аргумента обработчика событий.

*T3*<br/>
Тип третьего аргумента обработчика событий.

*T4*<br/>
Тип четвертого аргумента обработчика событий.

*T5*<br/>
Тип пятого аргумента обработчика событий.

*T6*<br/>
Тип шестого аргумента обработчика событий.

*T7*<br/>
Тип седьмого аргумента обработчика событий.

*T8*<br/>
Тип аргумента восьмого обработчика событий.

*T9*<br/>
Тип девятого аргумента обработчика событий.

*arg0*<br/>
Нулевой аргумент обработчика событий.

*arg1*<br/>
Первый аргумент обработчика событий.

*arg2*<br/>
Второй аргумент обработчика событий.

*arg3*<br/>
Третий аргумент обработчика событий.

*arg4*<br/>
Четвертый аргумент обработчика событий.

*arg5*<br/>
Пятый аргумент обработчика событий.

*arg6*<br/>
Шестой аргумент обработчика событий.

*arg7*<br/>
Седьмой аргумент обработчика событий.

*arg8*<br/>
Восьмой аргумент обработчика событий.

*arg9*<br/>
Девятый аргумент обработчика событий.

## <a name="eventsourceremove"></a><a name="remove"></a> EventSource:: Remove

Удаляет обработчик событий, представленный указанным токеном регистрации событий, из набора обработчиков событий, связанного с текущим `EventSource` объектом.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Параметры

*token*<br/>
Дескриптор, представляющий обработчик событий. Этот токен был возвращен, когда обработчик событий был зарегистрирован методом [Add ()](#add) .

### <a name="return-value"></a>Возвращаемое значение

Значение S_OK, если операция завершилась успешно; в противном случае — значение HRESULT, указывающее на ошибку.

### <a name="remarks"></a>Комментарии

Дополнительные сведения о `EventRegistrationToken` структуре см. в разделе **Windows:: Foundation:: EventRegistrationToken Structure** в справочной документации по **Среда выполнения Windows** .

## <a name="eventsourcetargets_"></a><a name="targets"></a> EventSource:: targets_

Массив из одного или нескольких обработчиков событий.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Комментарии

При возникновении события, представленного текущим `EventSource` объектом, вызываются обработчики событий.

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a> EventSource:: targetsPointerLock_

Синхронизирует доступ к внутренним элементам данных даже при `EventSource` добавлении, удалении или вызове обработчиков событий для этого элемента.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
