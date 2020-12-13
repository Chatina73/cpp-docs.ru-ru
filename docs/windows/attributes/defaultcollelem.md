---
description: 'Дополнительные сведения о: дефаултколлелем'
title: defaultcollelem
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultcollelem
helpviewer_keywords:
- defaultcollelem attribute
ms.assetid: 3dbbd293-8b83-4f70-a36b-64cc1d0b6713
ms.openlocfilehash: 6d1d3bb77a9951fc82cd19a3dc9d6f42ee54b6c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333022"
---
# <a name="defaultcollelem"></a>defaultcollelem

Используется для Visual Basic оптимизации кода.

## <a name="syntax"></a>Синтаксис

```cpp
[defaultcollelem]
```

## <a name="remarks"></a>Remarks

Атрибут **дефаултколлелем** C++ имеет те же функциональные возможности, что и атрибут [дефаултколлелем](/windows/win32/Midl/defaultcollelem) MIDL.

## <a name="example"></a>Пример

В следующем коде показан метод интерфейса с использованием атрибута **дефаултколлелем** :

```cpp
// cpp_attr_ref_defaultcollelem.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyForm
{
   [propget, id(1), bindable, defaultcollelem, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);
   [propput, id(1), bindable, defaultcollelem, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);
};
```

## <a name="requirements"></a>Требования

| Контекст атрибута | Значение |
|-|-|
|**Относится к**|Метод интерфейса|
|**REPEATABLE**|Нет|
|**Требуемые атрибуты**|Нет|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также раздел

[Атрибуты IDL](idl-attributes.md)<br/>
[Атрибуты метода](method-attributes.md)
