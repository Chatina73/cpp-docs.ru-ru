---
title: atan, atanf, atanl, atan2, atan2f, atan2l
description: Справочник по API для Atan, атанф, атанл, atan2, atan2f и atan2l; который Вычисляет арктангенс значения с плавающей запятой.
ms.date: 1/15/2021
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
- _o_atan2f
- _o_atanf
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.openlocfilehash: bbfc08507bd48e1b9eb0b91350b2b39948d19a5f
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564073"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>`atan`, `atanf`, `atanl`, `atan2`, `atan2f`, `atan2l`

Вычисляет арктангенс ( **`x`** **`atan`** , **`atanf`** и **`atanl`** ) или арктангенс **`y`** / **`x`** ( **`atan2`** , **`atan2f`** и **`atan2l`** ).

## <a name="syntax"></a>Синтаксис

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );
#define atan(X) // Requires C11 or higher

float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
#define atan2(Y, X) // Requires C11 or higher

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>Параметры

*`x`*, *`y`*\
Все числа.

## <a name="return-value"></a>Возвращаемое значение

**`atan`** Возвращает арктангенс *`x`* в диапазоне от-π/2 до π/2 радиан. **`atan2`** Возвращает арктангенс *`y`* / *`x`* в диапазоне от-π до π радиан. Если *`x`* значение равно 0, **`atan`** возвращает 0. Если оба параметра **`atan2`** равны 0, функция возвращает 0. Все результаты даются в радианах.

**`atan2`** использует знаки обоих параметров для определения квадранта возвращаемого значения.

|Входные данные|Исключение SEH|Исключение Matherr|
|-----------|-------------------|-----------------------|
|± **`QNAN`**, **`IND`**|нет|**`_DOMAIN`**|

## <a name="remarks"></a>Комментарии

**`atan`** Функция вычисляет арктангенс (обратную функцию тангенса) *`x`* . **`atan2`** Вычисляет арктангенс *`y`* / *`x`* (если *`x`* равно 0, **`atan2`** возвращает π/2, если *`y`* является положительным,-π/2, если *`y`* имеет отрицательное значение, или 0, если *`y`* равен 0).

При использовании `<tgmath.h>` `atan()` `atan2()` макроса или тип аргумента определяет, какая версия функции выбрана. Подробные сведения см. в разделе [Type-Generic Math](../../c-runtime-library/tgmath.md) .

**`atan`** имеет реализацию, использующую Streaming SIMD Extensions 2 (SSE2). Сведения и ограничения по использованию реализации SSE2 см. в разделе [`_set_SSE2_enable`](set-sse2-enable.md) .

Поскольку C++ допускает перегрузку, можно вызывать перегрузки **`atan`** и **`atan2`** , которые принимают **`float`** аргументы и **`long double`** . В программе на языке C, если только вы не используете `<tgmath.h>` макрос для вызова этой функции **`atan`** и **`atan2`** всегда принимаете **`double`** аргументы и возвращает **`double`** .

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок (C)|Обязательный заголовок (C++)|
|-------------|---------------------|-|
|**`atan`**, **`atan2`**, **`atanf`**, **`atan2f`**, **`atanl`**, **`atan2l`**|`<math.h>`|`<cmath>` или `<math.h>`|
|**`atan()`**, **`atan2`** макросы | `<tgmath.h>` ||

## <a name="example"></a>Пример

```C
// crt_atan.c
// arguments: 5 0.5
#include <math.h>
#include <stdio.h>
#include <errno.h>

int main( int ac, char* av[] )
{
   double x, y, theta;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );
      return 1;
   }
   x = atof( av[1] );
   theta = atan( x );
   printf( "Arctangent of %f: %f\n", x, theta );
   y = atof( av[2] );
   theta = atan2( y, x );
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );
   return 0;
}
```

```Output
Arctangent of 5.000000: 1.373401
Arctangent of 0.500000 / 5.000000: 0.099669
```

## <a name="see-also"></a>См. также

[Поддержка операций с плавающей запятой](../../c-runtime-library/floating-point-support.md)\
[`acos`, `acosf`, `acosl`](acos-acosf-acosl.md)\
[`asin`, `asinf`, `asinl`](asin-asinf-asinl.md)\
[`cos`, `cosf`, `cosl`](cos-cosf-cosl.md)\
[`_matherr`](matherr.md)\
[`sin`, `sinf`, `sinl`](sin-sinf-sinl.md)\
[`tan`, `tanf`, `tanl`](tan-tanf-tanl.md)\
[`_CIatan`](../../c-runtime-library/ciatan.md)\
[`_CIatan2`](../../c-runtime-library/ciatan2.md)