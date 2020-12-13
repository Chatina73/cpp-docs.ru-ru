---
description: Дополнительные сведения см. в статье основы COM-объектов ATL.
title: Основы COM-объектов ATL
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 0a94d57701770b00eb2c2d5aed675b8cc19e9e58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152940"
---
# <a name="fundamentals-of-atl-com-objects"></a>Основы COM-объектов ATL

На следующем рисунке показана связь между классами и интерфейсами, которые используются для определения COM-объекта ATL.

![Структура ATL](../atl/media/vc307y1.gif "Структура ATL")

> [!NOTE]
> На этой схеме показано, что `CComObject` является производным от, `CYourClass` `CComAggObject` а и `CComPolyObject` включается в `CYourClass` качестве переменной-члена.

Существует три способа определения COM-объекта ATL. Стандартным вариантом является использование `CComObject` класса, производного от `CYourClass` . Второй вариант — создать агрегированный объект с помощью `CComAggObject` класса. Третий вариант — использовать `CComPolyObject` класс. `CComPolyObject` выступает в качестве гибридного: он может функционировать как `CComObject` класс или как `CComAggObject` класс в зависимости от того, как он был создан впервые. Дополнительные сведения об использовании `CComPolyObject` класса см. в разделе [класс CComPolyObject](../atl/reference/ccompolyobject-class.md).

При использовании стандартной модели COM ATL используются два объекта: внешний объект и внутренний объект. Внешние клиенты обращаются к функциональным возможностям внутреннего объекта через функции-оболочки, определенные во внешнем объекте. Внешний объект имеет тип `CComObject` .

При использовании агрегированного объекта внешний объект не предоставляет оболочки для функциональности внутреннего объекта. Вместо этого внешний объект предоставляет указатель, к которому напрямую обращаются внешние клиенты. В этом сценарии внешний объект имеет тип `CComAggObject` . Внутренний объект является переменной-членом внешнего объекта и имеет тип `CYourClass` .

Поскольку клиенту не нужно проходить через внешний объект для взаимодействия с внутренним объектом, агрегированные объекты обычно более эффективны. Кроме того, внешнему объекту не требуется знание функциональных возможностей агрегированного объекта, учитывая, что интерфейс агрегированного объекта напрямую доступен клиенту. Однако не все объекты могут быть объединены. Для агрегирования объекта его необходимо разработать с учетом статистической обработки.

ATL реализует [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) в два этапа:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)или [CComPolyObject](../atl/reference/ccompolyobject-class.md) реализует `IUnknown` методы.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) или [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) управляет счетчиком ссылок и внешними указателями `IUnknown` .

Другие аспекты COM-объекта ATL обрабатываются другими классами:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) определяет фабрику класса по умолчанию и статистическую модель объекта.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) предоставляет реализацию по умолчанию `IDispatch Interface` части любых сдвоенных интерфейсов объекта.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) реализует `ISupportErrorInfo` интерфейс, который гарантирует, что сведения об ошибках могут быть распространены в цепочке вызовов правильно.

## <a name="in-this-section"></a>в этом разделе

[Реализация CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Показывать примеры записей карт COM для реализации `CComObjectRootEx` .

[Реализация CComObject, CComAggObject и CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
Описывает, как **DECLARE_ \* _AGGREGATABLE** макросы влияют на использование `CComObject` , `CComAggObject` и `CComPolyObject` .

[Поддержка IDispatch и IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Список классов реализации ATL, используемых для поддержки `IDispatch` `IErrorInfo` интерфейсов и.

[Поддержка IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
Описание действий по реализации точки подключения для класса.

[Изменение фабрики классов по умолчанию и статистической модели](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Показывает, какие макросы следует использовать для изменения фабрики класса по умолчанию и модели агрегирования.

[Создание агрегированного объекта](../atl/creating-an-aggregated-object.md)<br/>
Содержит инструкции по созданию агрегированного объекта.

## <a name="related-sections"></a>Связанные разделы

[Создание проекта ATL](../atl/reference/creating-an-atl-project.md)<br/>
Содержит сведения о создании COM-объекта ATL.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Ссылки на разделы о программировании с использованием библиотеки ATL.

## <a name="see-also"></a>См. также раздел

[Основные понятия](../atl/active-template-library-atl-concepts.md)
