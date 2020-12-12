---
description: 'Дополнительные сведения: String (C++)'
title: String (атрибут COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: fadfd0b12a8054dedb275e9e2c33c23206856102
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329582"
---
# <a name="string-c"></a>string (C++)

Указывает, что одномерный **`char`** массив, **`wchar_t`** `byte` (эквивалентный) или указатель на такой массив должен рассматриваться как строка.

## <a name="syntax"></a>Синтаксис

```cpp
[string]
```

## <a name="remarks"></a>Remarks

Атрибут **String** C++ имеет те же функциональные возможности, что и атрибут [String](/windows/win32/Midl/string) MIDL.

## <a name="example"></a>Пример

В следующем коде показано, как использовать **строку** в интерфейсе и в определении типа:

```cpp
// cpp_attr_ref_string.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, string] typedef char a[21];
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1)] HRESULT Method3([in, string] char *pC);
};
```

## <a name="requirements"></a>Требования

| Контекст атрибута | Значение |
|-|-|
|**Относится к**|Массив или указатель на массив, параметр интерфейса, метод интерфейса|
|**REPEATABLE**|Нет|
|**Требуемые атрибуты**|Нет|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения о контекстах атрибутов см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также раздел

[Атрибуты IDL](idl-attributes.md)<br/>
[Атрибуты массива](array-attributes.md)<br/>
[программе](export.md)
