---
title: _cabs
ms.date: 11/04/2016
apiname:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cabsl
- _cabs
- _cabsl
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 3e95b6f568ce66b8e9e5483bd1dcbcfaa7af3d28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341071"
---
# <a name="cabs"></a>_cabs

Вычисляет абсолютное значение комплексного числа.

## <a name="syntax"></a>Синтаксис

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Параметры

*z*<br/>
Комплексное число.

## <a name="return-value"></a>Возвращаемое значение

**_cabs** возвращает абсолютное значение своего аргумента, при успешном выполнении. В случае переполнения **_cabs** возвращает **HUGE_VAL** и задает **errno** для **ERANGE**. Изменить обработку ошибок можно с помощью функции [_matherr](matherr.md).

## <a name="remarks"></a>Примечания

**_Cabs** функция вычисляет абсолютное значение комплексного числа, которое должно быть структурой типа [_complex](../../c-runtime-library/standard-types.md). Структура *z* состоит из вещественной *x* а мнимая часть *y*. Вызов **_cabs** возвращает значение, эквивалентное значению выражения `sqrt( z.x * z.x + z.y * z.y )`.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_cabs**|\<math.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>См. также

[Поддержка чисел с плавающей запятой](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)