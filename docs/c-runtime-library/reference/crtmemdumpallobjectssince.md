---
description: 'Дополнительные сведения: _CrtMemDumpAllObjectsSince'
title: _CrtMemDumpAllObjectsSince
ms.date: 11/04/2016
api_name:
- _CrtMemDumpAllObjectsSince
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
ms.openlocfilehash: e833543d3119b39a21b596af412a97f6991e4ef0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319642"
---
# <a name="_crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Записывает в дамп сведения об объектах в куче с начала выполнения программы или перехода в указанное состояние кучи (только в отладочной версии).

## <a name="syntax"></a>Синтаксис

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Параметры

*state*<br/>
Указатель на состояние кучи, при наступлении которого должен начинаться дамп, или **NULL**.

## <a name="remarks"></a>Комментарии

Функция **_CrtMemDumpAllObjectsSince** выводит данные заголовка отладки объектов, выделенных в куче, в форме, доступной для чтения пользователем. Данные дампа могут использоваться приложением для отслеживания операций выделения памяти и выявления проблем с памятью. Если [_DEBUG](../../c-runtime-library/debug.md) не определено, вызовы **_CrtMemDumpAllObjectsSince** удаляются во время предварительной обработки.

**_CrtMemDumpAllObjectsSince** использует значение параметра *State* для определения места инициации операции дампа. Чтобы начать выгрузку из указанного состояния кучи, параметр *State* должен быть указателем на **_CrtMemState** структуру, заполненную [_CrtMemCheckpoint](crtmemcheckpoint.md) перед вызовом **_CrtMemDumpAllObjectsSince** . Если *State* имеет **значение NULL**, функция начинает дамп с начала выполнения программы.

Если приложение установило функцию-обработчик дампа путем вызова [_CrtSetDumpClient](crtsetdumpclient.md), то каждый раз, **_CrtMemDumpAllObjectsSince** выводит сведения о **_CLIENT_BLOCK** типе блока, он также вызывает функцию дампа, предоставляемую приложением. По умолчанию внутренние блоки времени выполнения C (**_CRT_BLOCK**) не включаются в операции дампа памяти. Функцию [_CrtSetDbgFlag](crtsetdbgflag.md) можно использовать, чтобы включить **_CRTDBG_CHECK_CRT_DF** бит **_crtDbgFlag** , чтобы включить эти блоки. Кроме того, блоки, помеченные как освобожденные или игнорируемые (**_FREE_BLOCK**, **_IGNORE_BLOCK**), в дамп памяти не включаются.

Дополнительные сведения о функциях состояния кучи и структуре **_CrtMemState** см. в разделе [функции создания отчетов о состоянии кучи](/visualstudio/debugger/crt-debug-heap-details). Дополнительные сведения о выделении, инициализации и управлении блоками памяти в отладочной версии основной кучи см. в разделе [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_CrtMemDumpAll Обжектссинце**|\<crtdbg.h>|

Дополнительные сведения о совместимости см. в разделе [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Библиотеки

Только отладочные версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Пример

Пример использования **_CrtMemDumpAllObjectsSince** см. в разделе [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>См. также раздел

[Отладочные подпрограммы](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
