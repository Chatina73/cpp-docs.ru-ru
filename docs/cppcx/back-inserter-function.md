---
description: Дополнительные сведения о функции back_inserter
title: back_inserter - функция
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
ms.openlocfilehash: d2483c9947fbf3a7bc04024221ec6e582e416f84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223585"
---
# <a name="back_inserter-function"></a>back_inserter - функция

Возвращает итератор, используемый для вставки элементов в конце указанной коллекции.

## <a name="syntax"></a>Синтаксис

```

template <typename T>
Platform::BackInsertIterator<T>
    back_inserter(IVector<T>^ v);

template<typename T>
Platform::BackInsertIterator<T>
   back_inserter(IObservableVector<T>^ v);
```

#### <a name="parameters"></a>Параметры

*T*<br/>
Параметр типа шаблона.

*v*<br/>
Указатель интерфейса, предоставляющий доступ к базовой коллекции.

### <a name="return-value"></a>Возвращаемое значение

Итератор.

### <a name="requirements"></a>Требования

**Заголовок:** collection.h

**Пространство имен:** Windows::Foundation::Collections

## <a name="see-also"></a>См. также раздел

[Пространство имен Windows:: Foundation:: Collections](../cppcx/windows-foundation-collections-namespace-c-cx.md)
