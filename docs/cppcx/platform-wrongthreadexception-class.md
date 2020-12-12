---
description: 'Дополнительные сведения о классе Platform:: WrongThreadException'
title: Класс Platform::WrongThreadException
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WrongThreadException
- VCCORLIB/Platform::WrongThreadException::WrongThreadException
helpviewer_keywords:
- Platform::WrongThreadException
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
ms.openlocfilehash: a7fbaed7766a3928ca24d56f5233c38d9298d466
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307734"
---
# <a name="platformwrongthreadexception-class"></a>Класс Platform::WrongThreadException

Вызывается, если поток выполняет вызов посредством указателя на интерфейс для прокси-объекта, который не принадлежит подразделению потока.

## <a name="syntax"></a>Синтаксис

```cpp
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Remarks

Дополнительные сведения см. в описании класса [COMException](../cppcx/platform-comexception-class.md).

### <a name="requirements"></a>Требования

**Минимальный поддерживаемый клиент:** Windows 8

**Минимальный поддерживаемый сервер:** Windows Server 2012

**Пространство имен:** Platform

**Метаданные:** Platform. winmd

## <a name="see-also"></a>См. также раздел

[Класс Platform:: COMException](../cppcx/platform-comexception-class.md)
