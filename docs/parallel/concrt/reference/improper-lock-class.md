---
title: Класс improper_lock
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: de7393c9186a1572040acd18854b5b3046b239f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552793"
---
# <a name="improperlock-class"></a>Класс improper_lock

Этот класс описывает исключение, создаваемое, когда блокировка получена неправильно.

## <a name="syntax"></a>Синтаксис

```
class improper_lock : public std::exception;
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[improper_lock](#ctor)|Перегружен. Создает элемент `improper_lock exception`.|

## <a name="remarks"></a>Примечания

Как правило это исключение возникает при попытке получить блокировку не допускающий повторные входы рекурсивно на том же контексте.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`exception`

`improper_lock`

## <a name="requirements"></a>Требования

**Заголовок:** concrt.h

**Пространство имен:** concurrency

##  <a name="ctor"></a> improper_lock

Создает элемент `improper_lock exception`.

```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>Параметры

*_Message*<br/>
Описательное сообщение об ошибке.

## <a name="see-also"></a>См. также

[Пространство имен concurrency](concurrency-namespace.md)<br/>
[Класс critical_section](critical-section-class.md)<br/>
[Класс reader_writer_lock](reader-writer-lock-class.md)
