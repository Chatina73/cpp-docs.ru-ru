---
title: Идентификатор ProgID (атрибут COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: 5b0c688ad4d9b607cc1f5fb6b1c6d536a1c7888e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407436"
---
# <a name="progid"></a>progid

Указывает идентификатор ProgID для COM-объекта.

## <a name="syntax"></a>Синтаксис

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Параметры

*name*<br/>
Идентификатор ProgID, представляющий объект.

Идентификаторы ProgID представляют удобное для восприятия версию идентификатор класса (CLSID), используемый для идентификации объектов COM/ActiveX.

## <a name="remarks"></a>Примечания

**Progid** C++ атрибут позволяет указать идентификатор ProgID для COM-объекта. Идентификатор ProgID имеет форму *name1.name2.version*. Если вы не укажете *версии* для ProgID, версия по умолчанию — 1. Если вы не укажете *name1.name2*, имя по умолчанию — *classname.classname*. Если вы не укажете **progid** и указать `vi_progid`, *name1.name2* берутся из `vi_progid` и (порядковый номер) версии добавляется.

Если в блоке атрибута, который использует **progid** также не используйте **uuid**, тогда компилятор проверит реестр ли **uuid** существует для указанного **progid** . Если **progid** не указан, версии (и имя компонентного класса, если создание компонентного класса) будет использоваться для создания **progid**.

**Идентификатор ProgID** подразумевает `coclass` атрибута, то есть, если указать **progid**, это то же самое, что и указание `coclass` и **progid** атрибуты.

**Progid** атрибут заставляет класс автоматически регистрироваться под указанным именем. Созданного IDL-файла не отобразит **progid** значение.

Если этот атрибут используется в проекте, где применяется ATL, поведение атрибута изменяется. Помимо описанного выше поведения, сведений, указанных с помощью этого атрибута используется в `GetProgID` функции, введенному `coclass` атрибута. Дополнительные сведения см. в разделе [coclass](coclass.md) атрибута.

## <a name="example"></a>Пример

См. в примере [coclass](coclass.md) использовать образец **progid**.

## <a name="requirements"></a>Требования

### <a name="attribute-context"></a>Контекст атрибута

|||
|-|-|
|**Применение**|**Класс**, **структуры**|
|**Повторяемый**|Нет|
|**Обязательные атрибуты**|Нет|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения о контекстах атрибутов см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также

[Атрибуты IDL](idl-attributes.md)<br/>
[Атрибуты классов](class-attributes.md)<br/>
[Атрибуты Typedef, Enum, Union и Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Идентификатор progID ключ](/windows/desktop/com/-progid--key)
