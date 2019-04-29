---
title: _heapchk
ms.date: 11/04/2016
apiname:
- _heapchk
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _heapchk
- heapchk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
ms.openlocfilehash: bdc0137761664a668d6ef95d739f09501e8290e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331718"
---
# <a name="heapchk"></a>_heapchk

Выполняет проверки согласованности в куче.

## <a name="syntax"></a>Синтаксис

```C
int _heapchk( void );
```

## <a name="return-value"></a>Возвращаемое значение

**_heapchk** возвращает одно из следующих целочисленных констант манифеста определенных в файле Malloc.h.

|Возвращаемое значение|Условие|
|-|-|
| **_HEAPBADBEGIN** | Начальные сведения о заголовке повреждены или не найдены. |
| **_HEAPBADNODE** | Обнаружен недопустимый узел или куча повреждена. |
| **_HEAPBADPTR** | Недопустимый указатель на кучу. |
| **_HEAPEMPTY** | Куча не инициализирована. |
| **_HEAPOK** | Вероятно, куча согласована. |

Кроме того, если возникает ошибка **_heapchk** задает **errno** для **ENOSYS**.

## <a name="remarks"></a>Примечания

**_Heapchk** функция помогает при отладке проблем с кучей путем проверки на предмет минимальной согласованности кучи. Если операционная система не поддерживает **_heapchk**(например, Windows 98), функция возвращает **_HEAPOK** и задает **errno** для **ENOSYS**.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|Необязательный заголовок|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>См. также

[Выделение памяти](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
