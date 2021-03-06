---
description: 'Дополнительные сведения о: HelpContext'
title: HelpContext (атрибут COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: cfedec2f7650490dd266331e6853ba47265aa4ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335723"
---
# <a name="helpcontext"></a>helpcontext

Указывает идентификатор контекста, позволяющий пользователю просматривать сведения об этом элементе в файле **справки** .

## <a name="syntax"></a>Синтаксис

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Параметры

*id*<br/>
Идентификатор контекста раздела справки. Дополнительные сведения об идентификаторах контекста см. в [справке HTML: Context-Sensitive справку для своих программ](../../mfc/html-help-context-sensitive-help-for-your-programs.md) .

## <a name="remarks"></a>Комментарии

Атрибут **HelpContext** C++ имеет те же функциональные возможности, что и атрибут MIDL для [HelpContext](/windows/win32/Midl/helpcontext) .

## <a name="example"></a>Пример

Пример использования **HelpContext** см. в примере для [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Требования

| Контекст атрибута | Значение |
|-|-|
|**Относится к**|**интерфейс**, **`typedef`** , **`class`** , метод, свойство|
|**REPEATABLE**|Нет|
|**Требуемые атрибуты**|Нет|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также раздел

[Атрибуты IDL](idl-attributes.md)<br/>
[Атрибуты интерфейса](interface-attributes.md)<br/>
[Атрибуты класса](class-attributes.md)<br/>
[Атрибуты метода](method-attributes.md)<br/>
[Атрибуты typedef, enum, Union и struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
