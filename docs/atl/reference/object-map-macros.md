---
description: 'Дополнительные сведения: макросы для карт объектов'
title: Макросы схемы объектов
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: accd1fdaebaab3a5c71730dcfd5db83fc2b320de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139039"
---
# <a name="object-map-macros"></a>Макросы схемы объектов

Эти макросы определяют сопоставления объектов и записи.

|Имя|Описание|
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Позволяет указать текстовое описание объекта класса, которое будет введено в карту объектов.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Вводит объект ATL в карту объектов, обновляет реестр и создает экземпляр объекта.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Позволяет указать, что объект должен быть зарегистрирован и инициализирован, но не должен создаваться внешне через `CoCreateInstance`.|

## <a name="requirements"></a>Требования

**Заголовок:** атлком. h

## <a name="declare_object_description"></a><a name="declare_object_description"></a> DECLARE_OBJECT_DESCRIPTION

Позволяет указать текстовое описание для объекта класса.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Параметры

*x*<br/>
окне Описание объекта класса.

### <a name="remarks"></a>Комментарии

ATL вводит это описание в карту объектов с помощью макроса [OBJECT_ENTRY_AUTO](#object_entry_auto) .

DECLARE_OBJECT_DESCRIPTION реализует `GetObjectDescription` функцию, которую можно использовать для переопределения метода [CComCoClass:: жетобжектдескриптион](ccomcoclass-class.md#getobjectdescription) .

`GetObjectDescription`Функция вызывается методом `IComponentRegistrar::GetComponents` . `IComponentRegistrar` — Это интерфейс автоматизации, позволяющий регистрировать и отменять регистрацию отдельных компонентов в библиотеке DLL. При создании объекта регистратора компонентов с помощью мастера проектов ATL мастер автоматически реализует `IComponentRegistrar` интерфейс. `IComponentRegistrar` обычно используется сервером транзакций Microsoft Transaction Server.

Дополнительные сведения о мастере проектов ATL см. в статье [Создание проекта ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a> OBJECT_ENTRY_AUTO

Вводит объект ATL в карту объектов, обновляет реестр и создает экземпляр объекта.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Параметры

*этому*<br/>
окне Идентификатор CLSID класса COM, реализуемого классом C++ с именем *Class*.

*class*<br/>
окне Имя класса C++, реализующего класс COM, представленный *CLSID*.

### <a name="remarks"></a>Комментарии

Макросы записи объекта помещаются в глобальной области видимости в проекте для поддержки регистрации, инициализации и создания класса.

OBJECT_ENTRY_AUTO вводит указатели функций класса Creator и класса Creator фабрики классов `CreateInstance` для этого объекта в автоматически созданную карту объектов ATL. При вызове [катлкоммодуле:: регистерсервер](catlcommodule-class.md#registerserver) он обновляет системный реестр для каждого объекта в сопоставлении объектов.

В следующей таблице описывается получение сведений, добавляемых в карту объектов, из класса, заданного вторым параметром для этого макроса.

|Сведения для|Получено из|
|---------------------|-------------------|
|Регистрация COM|[Макросы реестра](../../atl/reference/registry-macros.md)|
|Создание фабрики класса|[Макросы фабрики класса](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Создание экземпляра|[Статистические макросы](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Регистрация категории компонентов|[Макросы категорий](../../atl/reference/category-macros.md)|
|Инициализация и очистка на уровне класса|[обжектмаин](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a> OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Позволяет указать, что объект должен быть зарегистрирован и инициализирован, но не должен создаваться внешне через `CoCreateInstance`.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Параметры

*этому*<br/>
окне Идентификатор CLSID класса COM, реализуемого классом C++ с именем *Class*.

*class*<br/>
окне Имя класса C++, реализующего класс COM, представленный *CLSID*.

### <a name="remarks"></a>Комментарии

Макросы записи объекта помещаются в глобальной области видимости в проекте для поддержки регистрации, инициализации и создания класса.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO позволяет указать, что объект должен быть зарегистрирован и инициализирован (Дополнительные сведения см. в [OBJECT_ENTRY_AUTO](#object_entry_auto) ), но его нельзя создавать с помощью `CoCreateInstance` .

## <a name="see-also"></a>См. также раздел

[Макросы](../../atl/reference/atl-macros.md)
