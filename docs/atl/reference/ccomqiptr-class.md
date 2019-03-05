---
title: Класс CComQIPtr
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: 64716d945ffbc6802ec23fb47523464246065192
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298819"
---
# <a name="ccomqiptr-class"></a>Класс CComQIPtr

Класс смарт-указатель для управления указателей интерфейса СОМ.

## <a name="syntax"></a>Синтаксис

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Параметры

*T*<br/>
COM-интерфейс, указав тип указателя для сохранения.

*piid*<br/>
Указатель на идентификатор IID *T*.

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание:|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Конструктор.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание:|
|----------|-----------------|
|[CComQIPtr::operator =](#operator_eq)|Присваивает указатель на указатель элемента.|

## <a name="remarks"></a>Примечания

Использует ATL `CComQIPtr` и [CComPtr](../../atl/reference/ccomptr-class.md) для управления указателей интерфейса СОМ, оба из которых являются производными от [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Оба класса выполните подсчет через вызовы к автоматической ссылок `AddRef` и `Release`. Перегруженные операторы будут выполнять операции с указателем.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Требования

**Заголовок:** atlcomcli.h

##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr

Конструктор.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Параметры

*к пулу журналов*<br/>
Позволяет инициализировать указатель интерфейса.

*T*<br/>
COM-интерфейса.

*piid*<br/>
Указатель на идентификатор IID *T*.

##  <a name="operator_eq"></a>  CComQIPtr::operator =

Оператор присваивания.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Параметры

*к пулу журналов*<br/>
Позволяет инициализировать указатель интерфейса.

*T*<br/>
COM-интерфейса.

*piid*<br/>
Указатель на идентификатор IID *T*.

### <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на обновленный `CComQIPtr` объекта.

## <a name="see-also"></a>См. также

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[Класс CComPtrBase](../../atl/reference/ccomptrbase-class.md)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)<br/>
[Класс CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)
