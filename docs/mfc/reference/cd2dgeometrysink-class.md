---
title: Класс CD2DGeometrySink
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
ms.openlocfilehash: 48c88f0b837b2e49e4c87f07a9aa28c16a66c1e3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271207"
---
# <a name="cd2dgeometrysink-class"></a>Класс CD2DGeometrySink

Оболочка для ID2D1GeometrySink.

## <a name="syntax"></a>Синтаксис

```
class CD2DGeometrySink;
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Создает объект CD2DGeometrySink из CD2DPathGeometry объекта.|
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|Деструктор Вызывается при уничтожении объекта D2D геометрии в качестве приемника.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|Добавляет один дуги по геометрическому пути|
|[CD2DGeometrySink::AddBezier](#addbezier)|Создает кривую Безье третьего порядка между текущей и заданной конечной точками.|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Создает набор кривых Безье третьего порядка и добавляет их в приемник geometry.|
|[CD2DGeometrySink::AddLine](#addline)|Создает сегмент линии между текущей точкой и заданной конечной точкой и добавляет его в приемник geometry.|
|[CD2DGeometrySink::AddLines](#addlines)|Создает последовательность строк, используя указанные точки и добавляет их в приемник geometry.|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Создает кривую Безье второго порядка между текущей и заданной конечной точками.|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Добавляет последовательность сегментов кривых Безье второго как массив в одном вызове.|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Открывает новую фигуру в указанной точке.|
|[CD2DGeometrySink::Close](#close)|Закрывает приемника geometry|
|[CD2DGeometrySink::EndFigure](#endfigure)|Заканчивает текущую фигуру; При необходимости закрывает его.|
|[CD2DGeometrySink::Get](#get)|Возвращает интерфейс ID2D1GeometrySink|
|[CD2DGeometrySink::IsValid](#isvalid)|Проверяет допустимость геометрии в качестве приемника|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Указывает метод, используемый для определения, какие точки находятся внутри геометрического объекта, описываемого этим приемником geometry, а какие точки находятся за пределами.|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Указывает параметры обводки и соединения для применения к новые сегменты, добавляемый в приемник geometry.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание|
|----------|-----------------|
|[CD2DGeometrySink::operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|Возвращает интерфейс ID2D1GeometrySink|

### <a name="protected-data-members"></a>Защищенные члены данных

|name|Описание:|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|Указатель на ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`CD2DGeometrySink`

## <a name="requirements"></a>Требования

**Заголовок:** afxrendertarget.h

##  <a name="_dtorcd2dgeometrysink"></a>  CD2DGeometrySink:: ~ CD2DGeometrySink

Деструктор Вызывается при уничтожении объекта D2D геометрии в качестве приемника.

```
virtual ~CD2DGeometrySink();
```

##  <a name="addarc"></a>  CD2DGeometrySink::AddArc

Добавляет один дуги по геометрическому пути

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Параметры

*Дуги*<br/>
Чтобы добавить к рисунку, сегмент дуги

##  <a name="addbezier"></a>  CD2DGeometrySink::AddBezier

Создает кривую Безье третьего порядка между текущей и заданной конечной точками.

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Параметры

*Безье*<br/>
Структура, описывающая контрольные точки и конечной точки кривой Безье для добавления.

##  <a name="addbeziers"></a>  CD2DGeometrySink::AddBeziers

Создает набор кривых Безье третьего порядка и добавляет их в приемник geometry.

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Параметры

*кривые Безье*<br/>
Массив сегментов Безье, описывающий кривых Безье, для создания. Кривую извлекается из текущей точки в приемник геометрии (конечная точка рисуется последнего сегмента или расположении, заданном параметром BeginFigure) в конечную точку из первого сегмента в массиве. Если массив содержит дополнительные сегменты Безье, каждый последующий сегмент Безье использует конечную точку предыдущего сегмента в качестве начальной точки.

##  <a name="addline"></a>  CD2DGeometrySink::AddLine

Создает сегмент линии между текущей точкой и заданной конечной точкой и добавляет его в приемник geometry.

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Параметры

*point*<br/>
Конечная точка линии для рисования.

##  <a name="addlines"></a>  CD2DGeometrySink::AddLines

Создает последовательность строк, используя указанные точки и добавляет их в приемник geometry.

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Параметры

*Точки*<br/>
Массив из одной или нескольких точек, которые описывают строки для рисования. Линия с текущего места в приемник геометрии (конечная точка рисуется последнего сегмента или расположении, заданном параметром BeginFigure) точки в массиве. Если массив содержит дополнительные точки, линия с первой точки для второй точки в массиве, из второй точки третья точка и т. д. Массив из последовательности из конечных точек для рисования линий.

##  <a name="addquadraticbezier"></a>  CD2DGeometrySink::AddQuadraticBezier

Создает кривую Безье второго порядка между текущей и заданной конечной точками.

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Параметры

*Безье*<br/>
Структура, описывающая контрольная точка и кривая Безье второго порядка, чтобы добавить конечную точку.

##  <a name="addquadraticbeziers"></a>  CD2DGeometrySink::AddQuadraticBeziers

Добавляет последовательность сегментов кривых Безье второго как массив в одном вызове.

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Параметры

*кривые Безье*<br/>
Массив из последовательности сегментов кривых Безье второго.

##  <a name="beginfigure"></a>  CD2DGeometrySink::BeginFigure

Открывает новую фигуру в указанной точке.

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Параметры

*startPoint*<br/>
Точка, с которого начинается новый рисунок.

*figureBegin*<br/>
Новой фигуры должны ли пустой или заполнены.

##  <a name="cd2dgeometrysink"></a>  CD2DGeometrySink::CD2DGeometrySink

Создает объект CD2DGeometrySink из CD2DPathGeometry объекта.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Параметры

*pathGeometry*<br/>
Существующий объект CD2DPathGeometry.

##  <a name="close"></a>  CD2DGeometrySink::Close

Закрывает приемника geometry

```
BOOL Close();
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если выполнение прошло успешно; в противном случае — значение FALSE.

##  <a name="endfigure"></a>  CD2DGeometrySink::EndFigure

Заканчивает текущую фигуру; При необходимости закрывает его.

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Параметры

*figureEnd*<br/>
Значение, указывающее, закрыт ли текущую фигуру. Если замкнутой, линия проводится между текущей точкой и заданные BeginFigure начальную точку.

##  <a name="get"></a>  CD2DGeometrySink::Get

Возвращает интерфейс ID2D1GeometrySink

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на интерфейс ID2D1GeometrySink или значение NULL, если объект еще не инициализирован.

##  <a name="isvalid"></a>  CD2DGeometrySink::IsValid

Проверяет допустимость геометрии в качестве приемника

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если приемник geometry является допустимым; в противном случае — значение FALSE.

##  <a name="m_psink"></a>  CD2DGeometrySink::m_pSink

Указатель на ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

##  <a name="operator_id2d1geometrysink_star"></a>  CD2DGeometrySink::operator ID2D1GeometrySink *

Возвращает интерфейс ID2D1GeometrySink

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на интерфейс ID2D1GeometrySink или значение NULL, если объект еще не инициализирован.

##  <a name="setfillmode"></a>  CD2DGeometrySink::SetFillMode

Указывает метод, используемый для определения, какие точки находятся внутри геометрического объекта, описываемого этим приемником geometry, а какие точки находятся за пределами.

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Параметры

*fillMode*<br/>
Метод, используемый для определения, является ли заданная точка частью геометрии.

##  <a name="setsegmentflags"></a>  CD2DGeometrySink::SetSegmentFlags

Указывает параметры обводки и соединения для применения к новые сегменты, добавляемый в приемник geometry.

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Параметры

*vertexFlags*<br/>
Приемник параметры обводки и соединения для применения к новые сегменты, добавить к данной геометрии.

## <a name="see-also"></a>См. также

[Классы](../../mfc/reference/mfc-classes.md)
