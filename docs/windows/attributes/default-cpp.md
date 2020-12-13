---
description: 'Дополнительные сведения о: Default (C++)'
title: Default (атрибут COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: 83c4a17f513db755395ed978d57c9c6f01f84ca3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333014"
---
# <a name="default-c"></a>default (C++)

Указывает, что настраиваемый или disp-интерфейс, определенный в коклассе, представляет интерфейс программирования по умолчанию.

## <a name="syntax"></a>Синтаксис

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Параметры

*interface1*<br/>
Интерфейс по умолчанию, который будет предоставляться в средах сценариев, которые создают объект на основе класса, определенного с помощью **`default`** атрибута.

Если исходный интерфейс по умолчанию не указан, в качестве интерфейса по умолчанию используется первое вхождение неисходного интерфейса.

*интерфейс2*<br/>
Используемых Исходный интерфейс по умолчанию. Этот интерфейс также необходимо указать с помощью атрибута [source](source-cpp.md) .

Если исходный интерфейс по умолчанию не указан, в качестве интерфейса по умолчанию используется первый исходный интерфейс.

## <a name="remarks"></a>Комментарии

**`default`** Атрибут C++ имеет те же функциональные возможности, что и атрибут MIDL [по умолчанию](/windows/win32/Midl/default) . **`default`** Атрибут также используется с атрибутом [case](case-cpp.md) .

## <a name="example"></a>Пример

В следующем коде показано, как **`default`** используется в определении кокласса для указания `ICustomDispatch` в качестве интерфейса программирования по умолчанию:

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

[Исходный](source-cpp.md) атрибут также содержит пример использования **`default`** .

## <a name="requirements"></a>Требования

| Контекст атрибута | Значение |
|-|-|
|**Относится к**|**`class`**, **`struct`** , элемент данных|
|**REPEATABLE**|Нет|
|**Требуемые атрибуты**|**coclass** (при применении к **`class`** или **`struct`** )|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также раздел

[Атрибуты IDL](idl-attributes.md)<br/>
[Атрибуты класса](class-attributes.md)<br/>
[кокласс](coclass.md)
