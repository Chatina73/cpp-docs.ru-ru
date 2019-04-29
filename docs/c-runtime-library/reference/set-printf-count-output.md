---
title: _set_printf_count_output
ms.date: 11/04/2016
apiname:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 0d4847d850b39c7c03ea92a98499715b1e6a4913
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356528"
---
# <a name="setprintfcountoutput"></a>_set_printf_count_output

Включить или отключить поддержку **%n** формат в [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-функциями семейства.

## <a name="syntax"></a>Синтаксис

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>Параметры

*Включить*<br/>
Ненулевое значение, чтобы включить **%n** поддерживает, 0, чтобы отключить **%n** поддержки.

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Состояние **%n** поддержки перед вызовом этой функции: ненулевое значение, если **%n** была включена поддержка, 0, если оно было отключено.

## <a name="remarks"></a>Примечания

В целях безопасности поддержка **%n** описатель формата отключен по умолчанию в **printf** и всех ее вариантах. Если **%n** встречается в **printf** является вызывают обработчик недопустимого параметра, как описано в спецификации формата, поведение по умолчанию [проверка параметров](../../c-runtime-library/parameter-validation.md). Вызов **_set_printf_count_output** с ненулевым аргументом приведет к **printf**-функциями семейства для интерпретации **%n** как описано в разделе [формат Синтаксис описания: функции printf и wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_set_printf_count_output.c
#include <stdio.h>

int main()
{
   int e;
   int i;
   e = _set_printf_count_output( 1 );
   printf( "%%n support was %sabled.\n",
        e ? "en" : "dis" );
   printf( "%%n support is now %sabled.\n",
        _get_printf_count_output() ? "en" : "dis" );
   printf( "12345%n6789\n", &i ); // %n format should set i to 5
   printf( "i = %d\n", i );
}
```

```Output
%n support was disabled.
%n support is now enabled.
123456789
i = 5
```

## <a name="see-also"></a>См. также

[_get_printf_count_output](get-printf-count-output.md)<br/>
