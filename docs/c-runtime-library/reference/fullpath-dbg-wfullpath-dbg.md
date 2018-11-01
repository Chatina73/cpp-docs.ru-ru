---
title: _fullpath_dbg, _wfullpath_dbg
ms.date: 11/04/2016
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
ms.openlocfilehash: b84c5b77d0a9bfb298d4c597e372cd39a92441f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488014"
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg, _wfullpath_dbg

Версии [_fullpath, _wfullpath](fullpath-wfullpath.md) , которые используют отладочную версию **malloc** для выделения памяти.

## <a name="syntax"></a>Синтаксис

```C
char *_fullpath_dbg(
   char *absPath,
   const char *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wfullpath_dbg(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Параметры

*absPath*<br/>
Указатель на буфер, содержащий абсолютный или полный путь, или **NULL**.

*relPath*<br/>
Относительный путь.

*MaxLength*<br/>
Максимальная длина буфера абсолютного пути имя (*absPath*). Длина указывается в байтах для **_fullpath** и в расширенных символах (**wchar_t**) для **_wfullpath**.

*blockType*<br/>
Запрошенный тип блока памяти: **_CLIENT_BLOCK** или **_NORMAL_BLOCK**.

*filename*<br/>
Указатель на имя исходного файла, который запросил операцию выделения или **NULL**.

*linenumber*<br/>
Номер строки в файле источника, в которой была запрошена операция выделения или **NULL**.

## <a name="return-value"></a>Возвращаемое значение

Каждая функция возвращает указатель на буфер, содержащий абсолютный путь (*absPath*). Если возникает ошибка (например, в том случае, если значение, переданное в *relPath* содержит букву диска, который является недопустимым или не найден, или если длина имени создаваемого абсолютного пути (*absPath*) больше, чем *maxLength*) функция возвращает **NULL**.

## <a name="remarks"></a>Примечания

**_Fullpath_dbg** и **_wfullpath_dbg** функции аналогичны **_fullpath** и **_wfullpath** за исключением того, что, когда **_DEBUG** будет определен, эти функции используют отладочную версию **malloc**, **_malloc_dbg**для выделения памяти в том случае, если **NULL** передается как первый параметр. Сведения о компонентах отладки **_malloc_dbg**, см. в разделе [_malloc_dbg](malloc-dbg.md).

Как правило, явно вызывать эти функции не требуется. Вместо этого можно определить **_CRTDBG_MAP_ALLOC** флаг. Когда **_CRTDBG_MAP_ALLOC** определен, вызовы функций **_fullpath** и **_wfullpath** сопоставляются **_fullpath_dbg** и **_wfullpath_dbg**, соответственно, с помощью *blockType* присвоено **_NORMAL_BLOCK**. Таким образом, не нужно явно вызывать эти функции, если вы не хотите пометить блоки кучи как **_CLIENT_BLOCK**. Дополнительные сведения см. в разделе [Типы блоков в отладочной куче](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста

|Подпрограмма Tchar.h|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>Требования

|Функция|Обязательный заголовок|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[Обработка файлов](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[Версии отладки функций выделения кучи](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
