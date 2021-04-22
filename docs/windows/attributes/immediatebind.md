---
description: 'Дополнительные сведения о: иммедиатебинд (атрибут C++ COM)'
title: иммедиатебинд (атрибут COM C++)
ms.date: 04/15/2021
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: b4bd8ddd61de7bc249fef2e6b0a140f4ee5cff95
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539755"
---
# `immediatebind`

Указывает, что база данных будет уведомлена сразу обо всех изменениях свойства объекта, привязанного к данным.

## <a name="syntax"></a>Синтаксис

```cpp
[immediatebind]
```

## <a name="remarks"></a>Remarks

**`immediatebind`** Атрибут C++ имеет те же функциональные возможности, что и [`immediatebind`](/windows/win32/Midl/immediatebind) атрибут MIDL.

## <a name="example"></a>Пример

[`bindable`](bindable.md)Пример использования **иммедиатебинд** см. в разделе.

## <a name="requirements"></a>Требования

| Контекст атрибута | Значение |
|-|-|
|**Относится к**|Метод интерфейса|
|**Повторяемый**|Нет|
|**Требуемые атрибуты**|Нет|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также раздел

[Атрибуты IDL](idl-attributes.md)<br/>
[Атрибуты метода](method-attributes.md)<br/>
[`defaultbind`](defaultbind.md)<br/>
[`displaybind`](displaybind.md)<br/>
[`requestedit`](requestedit.md)
