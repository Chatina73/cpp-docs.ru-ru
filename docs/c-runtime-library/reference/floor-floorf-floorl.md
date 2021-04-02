---
title: floor, floorf, floorl
description: Справочник по API для Floor, флурф и Floor; , который вычисляет этаж значения.
ms.date: 9/1/2020
api_name:
- floorf
- floorl
- floor
- _o_floor
- _o_floorf
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- floor
- floorl
- _floorl
- floorf
helpviewer_keywords:
- floor function
- floorf function
- calculating floors of values
- floorl function
ms.assetid: e9955f70-d659-414f-8050-132e13c8ff36
ms.openlocfilehash: f2fa789d780b624ab0e680afa0631793d7eed162
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099566"
---
# <a name="floor-floorf-floorl"></a>floor, floorf, floorl

Округляет значение вниз до целого числа.

## <a name="syntax"></a>Синтаксис

```C
double floor(
   double x
);
float floor(
   float x
); // C++ only
long double floor(
   long double x
); // C++ only
float floorf(
   float x
);
long double floorl(
   long double x
);
#define floor(X) // Requires C11 or higher
```

### <a name="parameters"></a>Параметры

*x*\
Значение с плавающей запятой.

## <a name="return-value"></a>Возвращаемое значение

Функции **Floor** возвращают значение с плавающей запятой, представляющее максимальное целое число, которое меньше или равно *x*. Ошибки не возвращаются.

|Входные данные|Исключение SEH|Исключение Matherr|
|-----------|-------------------|-----------------------|
|± КНАН, С|нет|_DOMAIN|

у **этажа** есть реализация, использующая Streaming SIMD Extensions 2 (SSE2). Сведения о реализации SSE2 и ограничениях на ее использование см. в разделе [_set_SSE2_enable](set-sse2-enable.md).

## <a name="remarks"></a>Комментарии

C++ допускает перегрузку, поэтому можно вызывать перегрузки **Floor** , которые принимают и возвращают **`float`** **`long double`** значения и. В программе на языке C, если только вы не используете \<tgmath.h> макрос для вызова этой функции, **Floor** всегда принимает и возвращает **`double`** .

При использовании \<tgmath.h> `floor()` макроса тип аргумента определяет, какая версия функции выбрана. Подробные сведения см. в разделе [Type-Generic Math](../../c-runtime-library/tgmath.md) .

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

## <a name="requirements"></a>Требования

|Функция|Обязательный заголовок|
|--------------|---------------------|
|**Floor**, **флурф**, **этаж**|\<math.h>|
|макрос **Floor** | \<tgmath.h> |

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_floor.c
// This example displays the largest integers
// less than or equal to the floating-point values 2.8
// and -2.8. It then shows the smallest integers greater
// than or equal to 2.8 and -2.8.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double y;

   y = floor( 2.8 );
   printf( "The floor of 2.8 is %f\n", y );
   y = floor( -2.8 );
   printf( "The floor of -2.8 is %f\n", y );

   y = ceil( 2.8 );
   printf( "The ceil of 2.8 is %f\n", y );
   y = ceil( -2.8 );
   printf( "The ceil of -2.8 is %f\n", y );
}
```

```Output
The floor of 2.8 is 2.000000
The floor of -2.8 is -3.000000
The ceil of 2.8 is 3.000000
The ceil of -2.8 is -2.000000
```

## <a name="see-also"></a>См. также раздел

[Поддержка операций с плавающей запятой](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
