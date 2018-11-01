---
title: Класс CComObjectGlobal
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: ebaec439393a67331293cbf47abd08a5e7e416af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485570"
---
# <a name="ccomobjectglobal-class"></a>Класс CComObjectGlobal

Этот класс управляет значение счетчика ссылок на модуль, содержащий ваш `Base` объекта.

## <a name="syntax"></a>Синтаксис

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>Параметры

*Base*<br/>
Ваш класс, производный от [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) или [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), а также как и из любого другого интерфейса, которые должны поддерживаться в объекте.

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Конструктор.|
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|Деструктор|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|Реализует глобальную `AddRef`.|
|[CComObjectGlobal::QueryInterface](#queryinterface)|Реализует глобальную `QueryInterface`.|
|[CComObjectGlobal::Release](#release)|Реализует глобальную `Release`.|

### <a name="public-data-members"></a>Открытые члены данных

|Имя|Описание|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Содержит значение HRESULT, возвращенное во время создания `CComObjectGlobal` объекта.|

## <a name="remarks"></a>Примечания

`CComObjectGlobal` Управляет значение счетчика ссылок на модуль, содержащий ваш `Base` объекта. `CComObjectGlobal` гарантирует, что объект не будут удалены до тех пор, пока модуль не освобождается. Объект будет удален только в том случае, когда счетчик ссылок на весь модуль становится равен нулю.

Например, с помощью `CComObjectGlobal`, фабрику класса может содержать общие глобальный объект, который является общим для всех своих клиентов.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Требования

**Заголовок:** atlcom.h

##  <a name="addref"></a>  CComObjectGlobal::AddRef

Увеличивает счетчик ссылок объекта на 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Возвращаемое значение

Значение, которое может быть полезно для диагностики и тестирования.

### <a name="remarks"></a>Примечания

По умолчанию `AddRef` вызовы `_Module::Lock`, где `_Module` — это глобальный экземпляр [CComModule](../../atl/reference/ccommodule-class.md) или класс, производный от него.

##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal

Конструктор. Вызовы `FinalConstruct` и затем задает [m_hResFinalConstruct](#m_hresfinalconstruct) для `HRESULT` возвращаемый `FinalConstruct`.

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Примечания

Если не производного базового класса из [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), необходимо создать собственные `FinalConstruct` метод. Деструктор вызывает `FinalRelease`.

##  <a name="dtor"></a>  CComObjectGlobal:: ~ CComObjectGlobal

Деструктор

```
CComObjectGlobal();
```

### <a name="remarks"></a>Примечания

Освобождает все выделенные ресурсы и вызовы [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct

Содержит значение HRESULT из вызова метода `FinalConstruct` во время создания `CComObjectGlobal` объекта.

```
HRESULT m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface

Извлекает указатель на запрошенный указатель интерфейса.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Параметры

*IID*<br/>
[in] Идентификатор GUID запрашиваемого интерфейса.

*ppvObject*<br/>
[out] Указатель на указатель интерфейса, идентифицируемый iid, или значение NULL, если интерфейс не найден.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Примечания

`QueryInterface` обрабатывает интерфейсы только в таблице сопоставлений COM.

##  <a name="release"></a>  CComObjectGlobal::Release

Уменьшает счетчик ссылок объекта на 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Возвращаемое значение

В отладочных сборках `Release` возвращает значение, которое может быть полезно для диагностики и тестирования. В неотладочных сборках `Release` всегда возвращает значение 0.

### <a name="remarks"></a>Примечания

По умолчанию `Release` вызовы `_Module::Unlock`, где `_Module` — это глобальный экземпляр [CComModule](../../atl/reference/ccommodule-class.md) или класс, производный от него.

## <a name="see-also"></a>См. также

[Класс CComObjectStack](../../atl/reference/ccomobjectstack-class.md)<br/>
[Класс CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Класс CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
