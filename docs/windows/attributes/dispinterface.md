---
description: 'Подробнее о: DISP'
title: диспетчерский интерфейс (атрибут COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: fe39e537ccbc350f3733653a710dfd0f0d817339
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122139"
---
# <a name="dispinterface"></a>dispinterface

Помещает интерфейс в IDL-файл в качестве интерфейса диспетчеризации.

## <a name="syntax"></a>Синтаксис

```cpp
[dispinterface]
```

## <a name="remarks"></a>Remarks

Если интерфейсу предшествует атрибут **dispinterface** языка C++, это вызывает помещение интерфейса в блок library созданного IDL-файла.

Если не указать базовый класс, интерфейс диспетчеризации будет производным от `IDispatch`. Необходимо указать [идентификатор](id.md) для членов интерфейса диспетчеризации.

Пример использования [dispinterface](/windows/win32/Midl/dispinterface) в документации MIDL:

```cpp
dispinterface helloPro
   { interface hello; };
```

не является допустимым для атрибута **dispinterface** .

## <a name="example"></a>Пример

Просмотрите пример с [bindable](bindable.md) , чтобы увидеть, как можно использовать **dispinterface**.

## <a name="requirements"></a>Требования

| Контекст атрибута | Значение |
|-|-|
|**Относится к**|**interface**|
|**REPEATABLE**|Нет|
|**Требуемые атрибуты**|Нет|
|**Недопустимые атрибуты**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Дополнительные сведения см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также раздел

[Атрибуты IDL](idl-attributes.md)<br/>
[Атрибуты по использованию](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[двойной](dual.md)<br/>
[настройки](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
