---
title: Класс CAutoPtr
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: 7f4f446aa97f2bf3843b830bd7fb4c4a5d74ffdb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260166"
---
# <a name="cautoptr-class"></a>Класс CAutoPtr

Этот класс представляет объект интеллектуального указателя.

> [!IMPORTANT]
>  Этот класс и его члены не может использоваться в приложениях, выполняемых в среде выполнения Windows.

## <a name="syntax"></a>Синтаксис

```
template <typename T>
class CAutoPtr
```

#### <a name="parameters"></a>Параметры

*T*<br/>
Тип указателя.

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|Конструктор.|
|[CAutoPtr:: ~ CAutoPtr](#dtor)|Деструктор|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CAutoPtr::Attach](#attach)|Вызовите этот метод, чтобы стать владельцем существующего указателя.|
|[CAutoPtr::Detach](#detach)|Вызовите этот метод для освобождения владения указатель.|
|[CAutoPtr::Free](#free)|Вызовите этот метод, чтобы удалить объект, на которые указывают `CAutoPtr`.|

### <a name="public-operators"></a>Открытые операторы

|name|Описание|
|----------|-----------------|
|[CAutoPtr::operator T *](#operator_t_star)|Оператор приведения типов.|
|[CAutoPtr::operator =](#operator_eq)|Оператор присваивания.|
|[CAutoPtr::operator "->"](#operator_ptr)|Оператор указателя на член.|

### <a name="public-data-members"></a>Открытые члены данных

|name|Описание|
|----------|-----------------|
|[CAutoPtr::m_p](#m_p)|Указатель данных переменная-член.|

## <a name="remarks"></a>Примечания

Этот класс предоставляет методы для создания и управления смарт-указатель, который поможет защититься от утечки памяти, автоматически освобождение ресурсов, когда оно выпадает из области.

Кроме того, `CAutoPtr`конструктор копирования и присваивания оператора передачи владения указателя, копирование исходного указателя на указатель назначения и задав для исходного указателя NULL. Таким образом, это может быть два `CAutoPtr` объектов друг хранения тот же указатель; это снижает вероятность удаления тот же указатель дважды.

`CAutoPtr` также упрощает создание коллекций указателей. Вместо создания производного класса коллекции и при переопределении деструктора, проще сделать из коллекции `CAutoPtr` объектов. При удалении коллекции `CAutoPtr` объекты будут выходить за область применения и автоматически удалить себя.

[CHeapPtr](../../atl/reference/cheapptr-class.md) и варианты работы в так же, как `CAutoPtr`, за исключением того, что они выделяют и освобождают память, с помощью функции другую кучу вместо C++ **новый** и **удалить** операторы. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) аналогичен `CAutoPtr`, единственное отличие — что он использует **vector new []** и **вектор delete []** для выделения и освобождения памяти.

См. также [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) и [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) когда необходимы массивов или списков смарт-указателей.

## <a name="requirements"></a>Требования

**Заголовок:** atlbase.h

## <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

##  <a name="attach"></a>  CAutoPtr::Attach

Вызовите этот метод, чтобы стать владельцем существующего указателя.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Параметры

*p*<br/>
`CAutoPtr` Объект будет стать владельцем этого указателя.

### <a name="remarks"></a>Примечания

Когда `CAutoPtr` объект принимает владение указатель, оно автоматически удалит указатель и все выделенные данные при его выходит за пределы области. Если [CAutoPtr::Detach](#detach) — вызывается, программист еще раз данный ответственность за освобождение любой выделяются ресурсы.

В отладочных сборках, произойдет сбой утверждения, если [CAutoPtr::m_p](#m_p) данные-член в текущий момент направлен к существующему значению; то есть не равно NULL.

### <a name="example"></a>Пример

Ознакомьтесь с примером в [CAutoPtr Обзор](../../atl/reference/cautoptr-class.md).

##  <a name="cautoptr"></a>  CAutoPtr::CAutoPtr

Конструктор.

```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Параметры

*p*<br/>
Существующего указателя.

*TSrc*<br/>
Под управлением другой тип `CAutoPtr`, которое используется для инициализации текущего объекта.

### <a name="remarks"></a>Примечания

`CAutoPtr` Объект может быть создан с помощью существующего указателя, в этом случае он передает право владения указателем.

### <a name="example"></a>Пример

Ознакомьтесь с примером в [CAutoPtr Обзор](../../atl/reference/cautoptr-class.md).

##  <a name="dtor"></a>  CAutoPtr:: ~ CAutoPtr

Деструктор

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>Примечания

Освобождает все выделенные ресурсы. Вызовы [CAutoPtr::Free](#free).

##  <a name="detach"></a>  CAutoPtr::Detach

Вызовите этот метод для освобождения владения указатель.

```
T* Detach() throw();
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает копию указателя.

### <a name="remarks"></a>Примечания

Освобождает права владения указателем, задает [CAutoPtr::m_p](#m_p) переменной-члена данных значение NULL и возвращает копию указателя. После вызова метода `Detach`, он на программиста, чтобы освободить все выделяется ресурсы по которому `CAutoPtr` объект ранее предполагается reponsibility.

### <a name="example"></a>Пример

Ознакомьтесь с примером в [CAutoPtr Обзор](../../atl/reference/cautoptr-class.md).

##  <a name="free"></a>  CAutoPtr::Free

Вызовите этот метод, чтобы удалить объект, на которые указывают `CAutoPtr`.

```
void Free() throw();
```

### <a name="remarks"></a>Примечания

Объект, на который указывает `CAutoPtr` освобождается и [CAutoPtr::m_p](#m_p) переменной-члена данных задано значение NULL.

##  <a name="m_p"></a>  CAutoPtr::m_p

Указатель данных переменная-член.

```
T* m_p;
```

### <a name="remarks"></a>Примечания

Эта переменная-член содержит информацию об указателях.

##  <a name="operator_eq"></a>  CAutoPtr::operator =

Оператор присваивания.

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Параметры

*p*<br/>
Указатель.

*TSrc*<br/>
Тип класса.

### <a name="return-value"></a>Возвращаемое значение

Возвращает ссылку на **CAutoPtr\< T >**.

### <a name="remarks"></a>Примечания

Оператор присваивания отсоединяет `CAutoPtr` объект из любой текущий указатель и присоединяет новый указатель, *p*, вместо него.

### <a name="example"></a>Пример

Ознакомьтесь с примером в [CAutoPtr Обзор](../../atl/reference/cautoptr-class.md).

##  <a name="operator_ptr"></a>  CAutoPtr::operator-&gt;

Оператор указателя на член.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение [CAutoPtr::m_p](#m_p) переменной-члена данных.

### <a name="remarks"></a>Примечания

Этот оператор используется для вызова метода в классе, на которые указывают `CAutoPtr` объекта. В отладочных сборках, произойдет сбой утверждения, если `CAutoPtr` указывает на значение NULL.

### <a name="example"></a>Пример

Ознакомьтесь с примером в [CAutoPtr Обзор](../../atl/reference/cautoptr-class.md).

##  <a name="operator_t_star"></a>  CAutoPtr::operator T *

Оператор приведения типов.

```
operator T* () const throw();
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на тип данных объекта, определенный в шаблоне класса.

### <a name="example"></a>Пример

Ознакомьтесь с примером в [CAutoPtr Обзор](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>См. также

[Класс CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Класс CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
