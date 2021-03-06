---
description: Дополнительные сведения о функции IID_PPV_ARGS_Helper
title: IID_PPV_ARGS_Helper - функция
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 7003a3270a6fdb2070055e0059b106f55324c63e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229149"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper - функция

Проверяет, что тип заданного аргумента является производным от интерфейса `IUnknown`.

> [!IMPORTANT]
> Данная специализация шаблона поддерживает инфраструктуру WRL и не предназначена для использования непосредственно из кода. Вместо этого используйте [IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) .

## <a name="syntax"></a>Синтаксис

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Параметры

*T*<br/>
Тип аргумента *PP*.

*PP*<br/>
Двойной косвенный указатель.

## <a name="return-value"></a>Возвращаемое значение

*PP* аргумента приведение указателя к указателю на **`void`** .

## <a name="remarks"></a>Комментарии

Если параметр шаблона *T* не является производным от, создается ошибка времени компиляции `IUnknown` .

## <a name="requirements"></a>Требования

**Заголовок:** client.h
