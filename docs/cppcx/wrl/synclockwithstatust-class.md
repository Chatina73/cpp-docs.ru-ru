---
title: Класс SyncLockWithStatusT
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 1c9c0805834a59d10a559bfc2b6da0f10e2fe160
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786037"
---
# <a name="synclockwithstatust-class"></a>Класс SyncLockWithStatusT

Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.

## <a name="syntax"></a>Синтаксис

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Параметры

*SyncTraits*<br/>
Тип, который может принимать монопольного или общее владение ресурсом.

## <a name="remarks"></a>Примечания

Представляет тип, который может занять монопольного или общее владение ресурсом.

`SyncLockWithStatusT` Класс используется для реализации [мьютекс](mutex-class.md) и [семафора](semaphore-class.md) классы.

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

name                                                             | Описание
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Инициализирует новый экземпляр класса `SyncLockWithStatusT`.

### <a name="protected-constructors"></a>Защищенные конструкторы

name                                                             | Описание
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Инициализирует новый экземпляр класса `SyncLockWithStatusT`.

### <a name="public-methods"></a>Открытые методы

name                                         | Описание
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::GetStatus](#getstatus) | Получает сведения о состоянии ожидания текущего `SyncLockWithStatusT` объекта.
[SyncLockWithStatusT::IsLocked](#islocked)   | Указывает ли текущий `SyncLockWithStatusT` объекта, которому принадлежит ресурс, то есть, `SyncLockWithStatusT` объект *заблокирован*.

### <a name="protected-data-members"></a>Защищенные члены данных

name                                    | Описание
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | Содержит результат базовой операции ожидания после операции блокирования объекта на основе текущего `SyncLockWithStatusT` объекта.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Требования

**Заголовок:** corewrappers.h

**Пространство имен:** Microsoft::WRL::Wrappers::Details

## <a name="getstatus"></a>SyncLockWithStatusT::GetStatus

Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Возвращаемое значение

Результат операции ожидания на объект, который основан на `SyncLockWithStatusT` класс, например [мьютекс](mutex-class.md) или [семафора](semaphore-class.md). Ноль (0) указывает, что операция ожидания возвращается в сигнальном состоянии; в противном случае — другой возникло состояние, такие как прошедшее значение времени ожидания.

### <a name="remarks"></a>Примечания

Получает сведения о состоянии ожидания текущего `SyncLockWithStatusT` объекта.

Функция GetStatus() извлекает значение базового [status_](#status) данные-член. Если создан на основе объекта `SyncLockWithStatusT` класс выполняет операцию блокировки, объект сначала ожидает объект станет доступным. Результат этой операции ожидания сохраняется в `status_` элемент данных. Возможные значения `status_` элемент данных являются возвращаемыми значениями для операции ожидания. Дополнительные сведения см. в разделе возвращаемые значения `WaitForSingleObjectEx()` функция в библиотеке MSDN.

## <a name="islocked"></a>SyncLockWithStatusT::IsLocked

Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Примечания

Указывает ли текущий `SyncLockWithStatusT` объекта, которому принадлежит ресурс, то есть, `SyncLockWithStatusT` объект *заблокирован*.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если `SyncLockWithStatusT` объектов заблокирован; в противном случае — значение **false**.

## <a name="status"></a>SyncLockWithStatusT::status_

Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Примечания

Содержит результат базовой операции ожидания после операции блокирования объекта на основе текущего `SyncLockWithStatusT` объекта.

## <a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>Параметры

*other*<br/>
Ссылка rvalue на другой `SyncLockWithStatusT` объекта.

*sync*<br/>
Ссылка на другой `SyncLockWithStatusT` объекта.

*status*<br/>
Значение [status_](#status) данными-членом *других* параметр или *синхронизации* параметра.

### <a name="remarks"></a>Примечания

Инициализирует новый экземпляр класса `SyncLockWithStatusT`.

Первый конструктор инициализирует текущий `SyncLockWithStatusT` из другого объекта `SyncLockWithStatusT` заданный параметром *других*и затем недействительными другой `SyncLockWithStatusT` объекта. Второй конструктор является `protected`и инициализирует текущий `SyncLockWithStatusT` объекта в недопустимом состоянии.
