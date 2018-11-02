---
title: _aligned_offset_realloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_offset_realloc_dbg
apilocation:
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
apitype: DLLExport
f1_keywords:
- aligned_offset_realloc_dbg
- _aligned_offset_realloc_dbg
helpviewer_keywords:
- aligned_offset_realloc_dbg function
- _aligned_offset_realloc_dbg function
ms.assetid: 64e30a12-887e-453b-aea8-aed793fca9d8
ms.openlocfilehash: e5ffb37227e1e20f32e065290056da05e7dcd065
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625866"
---
# <a name="alignedoffsetreallocdbg"></a>_aligned_offset_realloc_dbg

Изменяет размер блока памяти, который был выделен с помощью функции [_aligned_malloc](aligned-malloc.md) или [_aligned_offset_malloc](aligned-offset-malloc.md) (только отладочная версия).

## <a name="syntax"></a>Синтаксис

```C
void * _aligned_offset_realloc_dbg(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Параметры

*memblock*<br/>
Указатель текущего блока памяти.

*size*<br/>
Размер выделения памяти.

*Выравнивание*<br/>
Значение выравнивания, которое должно быть целой степенью числа 2.

*offset*<br/>
Смещение в выделение памяти для принудительного выполнения выравнивания.

*filename*<br/>
Указатель на имя исходного файла, который запросил **aligned_offset_realloc** операции или **NULL**.

*linenumber*<br/>
Номер строки в исходном файле где **aligned_offset_realloc** была запрошена операция или **NULL**.

## <a name="return-value"></a>Возвращаемое значение

**_aligned_offset_realloc_dbg** возвращает указатель void на блок памяти перераспределенном (и, возможно, перемещенном). Возвращает значение **NULL** Если размер равен нулю и аргумент буфера не **NULL**, или если не хватает доступной памяти для увеличения блока до заданного размера. В первом случае исходный блок освобождается. Во втором случае исходный блок не изменяется. Возвращаемое значение указывает на пространство хранилища, которое гарантированно будет соответственно выровнено для хранения объектов любого типа. Чтобы получить указатель на тип, отличающийся от void, используйте приведение типа для возвращаемого значения.

## <a name="remarks"></a>Примечания

**_aligned_offset_realloc_dbg** является отладочной версией [_aligned_offset_realloc](aligned-offset-realloc.md) функции. Когда [_DEBUG](../../c-runtime-library/debug.md) не определен, каждый вызов **_aligned_offset_realloc_dbg** сокращается до вызова **_aligned_offset_realloc**. Оба **_aligned_offset_realloc** и **_aligned_offset_realloc_dbg** выполняют перераспределение блока памяти в основной куче, но **_aligned_offset_realloc_dbg** разместить различные возможности отладки: буферы на обеих сторонах пользовательской части блока для тестирования утечек, параметр типа блока для отслеживания конкретных типов выделения, и *filename*/*linenumber*  сведения для определения источника запросов на выделение.

Как и [_aligned_offset_malloc](aligned-offset-malloc.md), **_aligned_offset_realloc_dbg** позволяет структуры выравниваться со смещением в структуре.

**_realloc_dbg** перераспределяет указанный блок памяти с немного больше пространства, чем запрошено *newSize*. *newSize* может быть больше или меньше размера первоначально выделенного блока памяти. Дополнительное пространство используется диспетчером кучи отладки, чтобы связать блоки памяти отладки и предоставить приложению сведения о заголовке отладки и буферы перезаписи. Перераспределение может привести к перемещению исходного блока памяти в другое расположение в куче, а также к изменению размера блока памяти. Если блок памяти перемещен, содержимое исходного блока перезаписывается.

Эта функция задает **errno** для **ENOMEM** случае сбоя выделения памяти, или если запрошенный размер был больше, чем **_HEAP_MAXREQ**. Дополнительные сведения о **errno**, см. в разделе [errno, _doserrno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Кроме того **_aligned_offset_realloc_dbg** проверяет свои параметры. Если *выравнивание* не является степенью числа 2 или, если *смещение* больше или равно *размер* и не равно нулю, эта функция вызывает обработчик недопустимого параметра, как описано в [ Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эта функция возвращает **NULL** и задает **errno** для **EINVAL**.

Сведения о выделении, инициализации и управлении блоками памяти в отладочной версии базовой кучи, см. в статье [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Сведения о типах блоков выделения и способах их использования см. в разделе [Типы блоков в отладочной куче](/visualstudio/debugger/crt-debug-heap-details). Сведения о различиях между вызовом стандартной функции кучи и ее отладочной версии в сборке отладки приложения см. в разделе [Версии отладки функций выделения кучи](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_aligned_offset_realloc_dbg**|\<crtdbg.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Библиотеки

Только отладочные версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>См. также

[Процедуры отладки](../../c-runtime-library/debug-routines.md)<br/>
