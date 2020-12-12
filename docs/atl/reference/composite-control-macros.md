---
description: 'Дополнительные сведения: макросы составного элемента управления'
title: Макросы составного элемента управления
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 0107f91350516bd0f7e35cf82a49f79ff3c5797e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141197"
---
# <a name="composite-control-macros"></a>Макросы составного элемента управления

Эти макросы определяют карты приемников событий и записи.

|Макрос|Описание|
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Помечает начало схемы приемника событий для составного элемента управления.|
|[END_SINK_MAP](#end_sink_map)|Помечает конец схемы приемника событий для составного элемента управления.|
|[SINK_ENTRY](#sink_entry)|Запись на карту приемника событий.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Запись в карту приемника событий с дополнительным параметром.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Аналогично SINK_ENTRY_EX за исключением того, что он принимает указатель на IID.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Запись на карту приемника событий с информацией о типе, предоставляемой вручную, для использования с [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Аналогично SINK_ENTRY_INFO за исключением того, что он принимает указатель на IID.|

## <a name="requirements"></a>Требования

**Заголовок:** атлком. h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a> BEGIN_SINK_MAP

Объявляет начало схемы приемника событий для составного элемента управления.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Параметры

*_class*<br/>
окне Задает элемент управления.

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Комментарии

Реализация приемников событий ActiveX в CE ATL поддерживает только возвращаемые значения типа HRESULT или void из методов обработчика событий. любое другое возвращаемое значение не поддерживается, и его поведение не определено.

## <a name="end_sink_map"></a><a name="end_sink_map"></a> END_SINK_MAP

Объявляет конец схемы приемника событий для составного элемента управления.

```
END_SINK_MAP()
```

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Комментарии

Реализация приемников событий ActiveX в CE ATL поддерживает только возвращаемые значения типа HRESULT или void из методов обработчика событий. любое другое возвращаемое значение не поддерживается, и его поведение не определено.

## <a name="sink_entry"></a><a name="sink_entry"></a> SINK_ENTRY

Объявляет функцию обработчика (*fn*) для указанного события (*DISPID*) элемента управления, идентифицируемого по *идентификатору*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Параметры

*id*<br/>
окне Определяет элемент управления.

*DISPID*<br/>
окне Идентифицирует указанное событие.

*FN*<br/>
окне Имя функции обработчика событий. Эта функция должна использовать `_stdcall` соглашение о вызовах и иметь соответствующую сигнатуру в стиле disp-интерфейса.

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Комментарии

Реализация приемников событий ActiveX в CE ATL поддерживает только возвращаемые значения типа HRESULT или void из методов обработчика событий. любое другое возвращаемое значение не поддерживается, и его поведение не определено.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a> SINK_ENTRY_EX и SINK_ENTRY_EX_P

Объявляет функцию обработчика (*fn*) для указанного события (*DISPID*) интерфейса диспетчеризации (*IID*) для элемента управления, идентифицируемого по *идентификатору*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Параметры

*id*<br/>
окне Определяет элемент управления.

*IID*<br/>
окне Определяет интерфейс диспетчеризации.

*пиид*<br/>
окне Указатель на интерфейс диспетчеризации.

*DISPID*<br/>
окне Идентифицирует указанное событие.

*FN*<br/>
окне Имя функции обработчика событий. Эта функция должна использовать `_stdcall` соглашение о вызовах и иметь соответствующую сигнатуру в стиле disp-интерфейса.

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Комментарии

Реализация приемников событий ActiveX в CE ATL поддерживает только возвращаемые значения типа HRESULT или void из методов обработчика событий. любое другое возвращаемое значение не поддерживается, и его поведение не определено.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a> SINK_ENTRY_INFO и SINK_ENTRY_INFO_P

Используйте макрос SINK_ENTRY_INFO в карте приемника событий, чтобы предоставить сведения, необходимые [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) для маршрутизации событий в соответствующую функцию обработчика.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Параметры

*id*<br/>
окне Целое число без знака, определяющее источник события. Это значение должно соответствовать параметру шаблона *NID* , используемому в связанном базовом классе [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) .

*IID*<br/>
окне Идентификатор IID, определяющий интерфейс диспетчеризации.

*пиид*<br/>
окне Указатель на IID, определяющий интерфейс диспетчеризации.

*DISPID*<br/>
окне Идентификатор DISPID, идентифицирующий указанное событие.

*FN*<br/>
окне Имя функции обработчика событий. Эта функция должна использовать `_stdcall` соглашение о вызовах и иметь соответствующую сигнатуру в стиле disp-интерфейса.

*контактные*<br/>
окне Сведения о типе для функции обработчика событий. Эти сведения о типе предоставляются в виде указателя на `_ATL_FUNC_INFO` структуру. CC_CDECL является единственным вариантом, поддерживаемым в Windows CE для поля КАЛЛКОНВ `_ATL_FUNC_INFO` структуры. Любое другое значение не поддерживается, поэтому его поведение не определено.

### <a name="remarks"></a>Комментарии

Первые четыре параметра макроса те же, что и для макроса [SINK_ENTRY_EX](#sink_entry_ex) . Последний параметр предоставляет сведения о типе для события. Реализация приемников событий ActiveX в CE ATL поддерживает только возвращаемые значения типа HRESULT или void из методов обработчика событий. любое другое возвращаемое значение не поддерживается, и его поведение не определено.

## <a name="see-also"></a>См. также раздел

[Макросы](../../atl/reference/atl-macros.md)<br/>
[Глобальные функции составного элемента управления](../../atl/reference/composite-control-global-functions.md)
