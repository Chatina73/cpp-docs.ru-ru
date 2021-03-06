---
description: 'Дополнительные сведения: карты подключений'
title: Схемы подключения
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 61d2e7023ab97aa00952aee4786b34e60ba57af7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345255"
---
# <a name="connection-maps"></a>Схемы подключения

Элементы управления OLE могут предоставлять интерфейсы другим приложениям. Эти интерфейсы разрешают доступ только из контейнера в этот элемент управления. Если элементу управления OLE требуется доступ к внешним интерфейсам других объектов OLE, необходимо установить точку соединения. Эта точка подключения позволяет управлять исходящим доступом к внешним картам диспетчеризации, таким как схемы событий или функции уведомления.

Библиотека Microsoft Foundation Class предлагает модель программирования, поддерживающую точки подключения. В этой модели "карты соединения" используются для обозначения интерфейсов или точек соединения для элемента управления OLE. Карты соединений содержат по одному макросу для каждой точки подключения. Дополнительные сведения о картах соединений см. в разделе класс [кконнектионпоинт](../../mfc/reference/cconnectionpoint-class.md) .

Как правило, элемент управления будет поддерживать только две точки соединения: один для событий и один для уведомлений о свойствах. Они реализуются `COleControl` базовым классом и не нуждаются в дополнительной работе с помощью модуля записи управления. Все дополнительные точки подключения, которые необходимо реализовать в классе, необходимо добавить вручную. Для поддержки карт соединений и точек MFC предоставляет следующие макросы:

### <a name="connection-map-declaration-and-demarcation"></a>Объявление и разделительной схемы подключения

|Имя|Описание|
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Объявляет внедренный класс, реализующий дополнительную точку соединения (необходимо использовать в объявлении класса).|
|[END_CONNECTION_PART](#end_connection_part)|Завершает объявление точки соединения (должно использоваться в объявлении класса).|
|[CONNECTION_IID](#connection_iid)|Указывает идентификатор интерфейса точки соединения элемента управления.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Объявляет, что схема соединения будет использоваться в классе (должен использоваться в объявлении класса).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Начинает определение схемы соединения (необходимо использовать в реализации класса).|
|[END_CONNECTION_MAP](#end_connection_map)|Завершает определение схемы соединения (необходимо использовать в реализации класса).|
|[CONNECTION_PART](#connection_part)|Задает точку соединения в сопоставлении соединения элемента управления.|

Следующие функции помогают приемнику устанавливать и отключать подключение с помощью точек подключения:

### <a name="initializationtermination-of-connection-points"></a>Инициализация и завершение точек соединения

|Имя|Описание|
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Устанавливает соединение между источником и приемником.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Прерывает соединение между источником и приемником.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a> BEGIN_CONNECTION_PART

Используйте макрос BEGIN_CONNECTION_PART, чтобы начать определение дополнительных точек соединения за пределами точек подключения уведомлений о событиях и свойствах.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Параметры

*секласс*<br/>
Указывает имя класса элемента управления, точка соединения которого имеет значение.

*локалкласс*<br/>
Указывает имя локального класса, реализующего точку подключения.

### <a name="remarks"></a>Комментарии

В файле объявления (. h), который определяет функции-члены для класса, запустите точку подключения с помощью макроса BEGIN_CONNECTION_PART, добавьте CONNECTION_IID макрос и другие функции-члены, которые требуется реализовать, и завершите карту точек подключения с помощью макроса END_CONNECTION_PART.

### <a name="requirements"></a>Требования

  **Заголовок** афксдисп. h

## <a name="end_connection_part"></a><a name="end_connection_part"></a> END_CONNECTION_PART

Завершает объявление точки подключения.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Параметры

*локалкласс*<br/>
Указывает имя локального класса, реализующего точку подключения.

### <a name="requirements"></a>Требования

  **Заголовок** афксдисп. h

## <a name="connection_iid"></a><a name="connection_iid"></a> CONNECTION_IID

Используйте макросы BEGIN_CONNECTION_PART и END_CONNECTION_PART, чтобы определить идентификатор интерфейса для точки подключения, поддерживаемой элементом управления OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Параметры

*IID*<br/>
Идентификатор интерфейса, вызываемого точкой соединения.

### <a name="remarks"></a>Комментарии

Аргумент *IID* — это идентификатор интерфейса, используемый для идентификации интерфейса, который точка подключения будет вызывать для подключенных к нему приемников. Пример:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

Указывает точку соединения, которая вызывает `ISinkInterface` интерфейс.

### <a name="requirements"></a>Требования

  **Заголовок** афксдисп. h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a> DECLARE_CONNECTION_MAP

Каждый `COleControl` производный класс в программе может предоставить карту соединения для указания дополнительных точек подключения, поддерживаемых элементом управления.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Комментарии

Если элемент управления поддерживает дополнительные точки, используйте макрос DECLARE_CONNECTION_MAP в конце объявления класса. Затем в cpp – файле, который определяет функции элементов для класса, используйте макрос BEGIN_CONNECTION_MAP, CONNECTION_PART макросы для каждой точки соединения элемента управления и макрос END_CONNECTION_MAP для объявления конца схемы соединения.

### <a name="requirements"></a>Требования

  **Заголовок** афксдисп. h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a> BEGIN_CONNECTION_MAP

Каждый `COleControl` производный класс в программе может предоставить карту соединения для указания точек соединения, которые будет поддерживать элемент управления.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Параметры

*секласс*<br/>
Указывает имя класса элемента управления, для которого сопоставлена связь.

*себасе*<br/>
Задает имя базового класса *секласс*.

### <a name="remarks"></a>Комментарии

В реализации (. CPP), который определяет функции-члены для класса, запускает схему подключения с помощью макроса BEGIN_CONNECTION_MAP, а затем добавляет записи макросов для каждой точки подключения с помощью макроса [CONNECTION_PART](#connection_part) . Наконец, завершите схему подключения с помощью макроса [END_CONNECTION_MAP](#end_connection_map) .

### <a name="requirements"></a>Требования

  **Заголовок** афксдисп. h

## <a name="end_connection_map"></a><a name="end_connection_map"></a> END_CONNECTION_MAP

Завершает определение схемы подключения.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Требования

  **Заголовок** афксдисп. h

## <a name="connection_part"></a><a name="connection_part"></a> CONNECTION_PART

Сопоставляет точку подключения для элемента управления OLE с заданным ИДЕНТИФИКАТОРом интерфейса.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Параметры

*секласс*<br/>
Указывает имя класса элемента управления, точка соединения которого имеет значение.

*IID*<br/>
Идентификатор интерфейса, вызываемого точкой соединения.

*локалкласс*<br/>
Указывает имя локального класса, реализующего точку подключения.

### <a name="remarks"></a>Комментарии

Пример:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

реализует карту соединения с точкой соединения, которая вызывает `IID_ISinkInterface` интерфейс.

### <a name="requirements"></a>Требования

  **Заголовок** афксдисп. h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a> афксконнектионадвисе

Вызовите эту функцию, чтобы установить соединение между источником, заданным параметром *пунксрк*, и приемником, заданным параметром *пунксинк*.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>Параметры

*пунксрк*<br/>
Указатель на объект, который вызывает интерфейс.

*пунксинк*<br/>
Указатель на объект, реализующий интерфейс.

*IID*<br/>
Идентификатор интерфейса соединения.

*брефкаунт*<br/>
Значение TRUE указывает, что создание соединения должно приводить к увеличению счетчика ссылок *пунксинк* . Значение FALSE указывает, что счетчик ссылок не должен увеличиваться.

*пдвкукие*<br/>
Указатель на DWORD, где возвращается идентификатор соединения. Это значение должно быть передано в качестве параметра *двкукие* при отключении `AfxConnectionUnadvise` соединения.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если соединение установлено; в противном случае — 0.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Требования

**Заголовок:** afxctl. h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a> афксконнектионунадвисе

Вызовите эту функцию, чтобы отключить соединение между источником, заданным параметром *пунксрк*, и приемником, заданным параметром *пунксинк*.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>Параметры

*пунксрк*<br/>
Указатель на объект, который вызывает интерфейс.

*пунксинк*<br/>
Указатель на объект, реализующий интерфейс.

*IID*<br/>
Идентификатор интерфейса точки подключения.

*брефкаунт*<br/>
Значение TRUE указывает, что отключение соединения должно привести к уменьшению числа ссылок *пунксинк* . Значение FALSE указывает, что счетчик ссылок не следует уменьшать.

*двкукие*<br/>
Идентификатор соединения, возвращенный `AfxConnectionAdvise` .

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если соединение было разорвано; в противном случае — 0.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Требования

**Заголовок:** afxctl. h

## <a name="see-also"></a>См. также раздел

[Макросы и глобальные объекты](../../mfc/reference/mfc-macros-and-globals.md)
