---
description: 'Дополнительные сведения о: CD2DRectF Class'
title: Класс CD2DRectF
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 273a3d07f152f8b24a24175c0f466c8969830ebd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136023"
---
# <a name="cd2drectf-class"></a>Класс CD2DRectF

Программа-оболочка для `D2D1_RECT_F`.

## <a name="syntax"></a>Синтаксис

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|Перегружен. Конструирует `CD2DRectF` объект из `D2D1_RECT_F` объекта.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CD2DRectF:: IsNull](#isnull)|Возвращает **логическое** значение, указывающее, содержит ли выражение допустимые данные (null).|

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание|
|----------|-----------------|
|[CD2DRectF:: operator Крект](#operator_crect)|Преобразует `CD2DRectF` в `CRect` объект.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Требования

**Заголовок:** афксрендертаржет. h

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a> CD2DRectF::CD2DRectF

Конструирует объект CD2DRectF из объекта Крект.

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>Параметры

*rect*<br/>
Исходный прямоугольник

*флефт*<br/>
Координата слева источника

*фтоп*<br/>
Координата вершины источника

*фригхт*<br/>
Координата справа источника

*фботтом*<br/>
координата нижней части источника

## <a name="cd2drectfisnull"></a><a name="isnull"></a> CD2DRectF:: IsNull

Возвращает логическое значение, указывающее, содержит ли выражение допустимые данные (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Возвращаемое значение

TRUE, если значения верхнего, левого, нижнего и правого прямоугольника равны 0; в противном случае — FALSE.

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a> CD2DRectF:: operator Крект

Преобразует CD2DRectF в объект Крект.

```
operator CRect();
```

### <a name="return-value"></a>Возвращаемое значение

Текущее значение прямоугольника D2D.

## <a name="see-also"></a>См. также раздел

[Классы](../../mfc/reference/mfc-classes.md)
