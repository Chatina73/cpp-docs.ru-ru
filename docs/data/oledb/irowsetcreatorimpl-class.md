---
description: 'Дополнительные сведения о: IRowsetCreatorImpl Class'
title: Класс IRowsetCreatorImpl
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
ms.openlocfilehash: 6a478e86bdb09851afed091c99ed0d0931a9115e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317406"
---
# <a name="irowsetcreatorimpl-class"></a>Класс IRowsetCreatorImpl

Выполняет те же функции, что и, `IObjectWithSite` но также включает свойства OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` .

## <a name="syntax"></a>Синтаксис

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Параметры

*T*<br/>
Класс, производный от `IRowsetCreator` .

## <a name="requirements"></a>Требования

**Заголовок:** atldb.h

## <a name="members"></a>Элементы

### <a name="methods"></a>Методы

| Имя | Описание |
|-|-|
|[SetSite](#setsite)|Задает сайт, содержащий объект набора строк.|

## <a name="remarks"></a>Комментарии

Этот класс наследует от [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) и переопределяет [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Когда команда поставщика или объект сеанса создает набор строк, он вызывает `QueryInterface` объект набора строк для поиска `IObjectWithSite` и вызывает `SetSite` передачу интерфейса объекта набора строк в `IUnkown` качестве интерфейса сайта.

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a> IRowsetCreatorImpl:: SetSite

Задает сайт, содержащий объект набора строк. Дополнительные сведения см. в разделе [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Синтаксис

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Параметры

*пкреатор*<br/>
окне Указатель на `IUnknown` указатель интерфейса сайта, управляющего объектом набора строк.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Кроме того, `IRowsetCreatorImpl::SetSite` включает свойства OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` .

## <a name="see-also"></a>См. также раздел

[Шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
