---
title: Макросы точки подключения
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: cb8d6f696980ef91d7b43c960dc50289ea8500a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278206"
---
# <a name="connection-point-macros"></a>Макросы точки подключения

Эти макросы определяют схемы точки подключения и записи.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Отмечает начало карты записей точки подключения.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Вводит точки подключения в схеме.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017 г.) Но, похоже на CONNECTION_POINT_ENTRY принимает указатель на iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Помечает конец записи подключения точки карты.|

## <a name="requirements"></a>Требования

**Заголовок:** atlcom.h

##  <a name="begin_connection_point_map"></a>  BEGIN_CONNECTION_POINT_MAP

Отмечает начало карты записей точки подключения.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Параметры

*x*<br/>
[in] Имя класса, содержащего точки подключения.

### <a name="remarks"></a>Примечания

Запустите на сопоставление точки подключения с помощью макроса BEGIN_CONNECTION_POINT_MAP, добавьте записи для каждого из вашей точки подключения с [CONNECTION_POINT_ENTRY](#connection_point_entry) макрос и выполнить сопоставление с [END_CONNECTION_ POINT_MAP](#end_connection_point_map) макрос.

Дополнительные сведения о точках подключения библиотеки ATL, см. в статье [точек подключения](../../atl/atl-connection-points.md).

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

##  <a name="connection_point_entry"></a>  CONNECTION_POINT_ENTRY и CONNECTION_POINT_ENTRY_P

Вводит точку подключения для указанного интерфейса в сопоставление точки подключения, чтобы он был доступен.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Параметры

*IID*<br/>
[in] Идентификатор GUID интерфейса, добавляемое сопоставление точки подключения.

*piid*<br/>
[in] Указатель на идентификатор GUID интерфейса, добавить.

### <a name="remarks"></a>Примечания

Записи точки подключения в схеме используются [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). Класс, содержащий сопоставление точки подключения должен наследовать из `IConnectionPointContainerImpl`.

Запуск на сопоставление точки подключения с [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) макрос, добавьте записи для каждого из вашей точки подключения с помощью макроса CONNECTION_POINT_ENTRY и выполнить сопоставление с [END_CONNECTION_ POINT_MAP](#end_connection_point_map) макрос.

Дополнительные сведения о точках подключения библиотеки ATL, см. в статье [точек подключения](../../atl/atl-connection-points.md).

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

##  <a name="end_connection_point_map"></a>  END_CONNECTION_POINT_MAP

Помечает конец записи подключения точки карты.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Примечания

Запуск на сопоставление точки подключения с [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) макрос, добавьте записи для каждого из вашей точки подключения с [CONNECTION_POINT_ENTRY](#connection_point_entry) макрос и выполнить сопоставление с END_ Макрос CONNECTION_POINT_MAP.

Дополнительные сведения о точках подключения библиотеки ATL, см. в статье [точек подключения](../../atl/atl-connection-points.md).

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>См. также

[Макросы](../../atl/reference/atl-macros.md)<br/>
[Глобальные функции точек подключения](../../atl/reference/connection-point-global-functions.md)
