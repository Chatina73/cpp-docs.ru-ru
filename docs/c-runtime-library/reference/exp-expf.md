---
title: exp, expf, expl
description: Справочник по API для EXP, експф и експл; который Вычисляет экспоненту.
ms.date: 1/15/2021
api_name:
- expf
- expl
- exp
- _o_exp
- _o_expf
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
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.openlocfilehash: 20a22600d068569468b764ff07519d4292afbfea
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577209"
---
# <a name="exp-expf-expl"></a>`exp`, `expf`, `expl`

Вычисляет экспоненту.

## <a name="syntax"></a>Синтаксис

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
#define exp(z) // Requires C11 or higher
```

### <a name="parameters"></a>Параметры

*`x`*\
Значение с плавающей запятой, експонентиате основание натурального логарифма по адресу *e* .

## <a name="return-value"></a>Возвращаемое значение

**`exp`** Функции возвращают экспоненциальное значение параметра с плавающей запятой, в *`x`* случае успеха. То есть результатом является *e* <sup>*`x`*</sup> , где *e* — основание натурального логарифма. При переполнении функция возвращает значение `INF` 0 (бесконечность) и в случае потери точности **`exp`** .

|Входные данные|Исключение SEH|`Matherr` об|
|-----------|-------------------|-----------------------|
|± Скрытого NaN, неопределенного|None|`_DOMAIN`|
|± Бесконечности|`INVALID`|`_DOMAIN`|
|x ≥ 7.097827e+002|`INEXACT+OVERFLOW`|`OVERFLOW`|
|X ≤ -7.083964e+002|`INEXACT+UNDERFLOW`|`UNDERFLOW`|

**`exp`** Функция имеет реализацию, использующую Streaming SIMD Extensions 2 (SSE2). [`_set_SSE2_enable`](set-sse2-enable.md)Сведения и ограничения по использованию реализации SSE2 см. в разделе.

## <a name="remarks"></a>Замечания

C++ допускает перегрузку, поэтому можно вызывать перегрузки **`exp`** , принимающие **`float`** аргумент или **`long double`** . В программе на языке C, если только вы не используете `<tgmath.h>` макрос для вызова этой функции, **`exp`** всегда принимает и возвращает **`double`** .

При использовании `<tgmath.h>` `exp()` макроса тип аргумента определяет, какая версия функции выбрана. Подробные сведения см. в разделе [Type-Generic Math](../../c-runtime-library/tgmath.md) .

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

## <a name="requirements"></a>Требования

|Функция|Обязательный заголовок C|Обязательный заголовок C++|
|--------------|---------------------|---|
|**`exp`**, **`expf`**, **`expl`**|`<math.h>`|`<cmath>` или `<math.h>`|
|**`exp`** макровирусах| `<tgmath.h>` ||

Дополнительные сведения о совместимости см. в разделе [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>См. также раздел

[Поддержка операций с плавающей запятой](../../c-runtime-library/floating-point-support.md)\
[`log, logf, log10, log10f`](log-logf-log10-log10f.md)\
[`_CIexp`](../../c-runtime-library/ciexp.md)
