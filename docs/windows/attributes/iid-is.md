---
title: iid_is (атрибут COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 176ab83bfae18ff7f43fe0860591f2d1ac50d7eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535334"
---
# <a name="iidis"></a>iid_is

Указывает идентификатор IID интерфейса COM, на которые указывает указатель интерфейса.

## <a name="syntax"></a>Синтаксис

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Параметры

*Выражение*<br/>
Выражение языка C, которое указывает IID COM-интерфейса, на который указывает указатель интерфейса.

## <a name="remarks"></a>Примечания

**Iid_is** атрибут C++ имеет ту же функциональность, что [iid_is](/windows/desktop/Midl/iid-is) описании атрибута MIDL.

## <a name="example"></a>Пример

В следующем коде показано использование **iid_is**:

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Требования

### <a name="attribute-context"></a>Контекст атрибута

|||
|-|-|
|**Применение**|Параметр интерфейса, элемент данных|
|**Повторяемый**|Нет|
|**Обязательные атрибуты**|Нет|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также

[Атрибуты IDL](idl-attributes.md)<br/>
[Атрибуты параметра](parameter-attributes.md)