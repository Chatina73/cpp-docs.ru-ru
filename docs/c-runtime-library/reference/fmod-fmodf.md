---
title: fmod, fmodf, fmodl
description: Справочник по API для FMOD, фмодф и фмодл; для вычисления остатка с плавающей запятой.
ms.date: 1/15/2021
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
- _o_fmodf
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.openlocfilehash: 02089e44f1eca66ef5452b73144bfe670e20cd94
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577369"
---
# <a name="fmod-fmodf-fmodl"></a>`fmod`, `fmodf`, `fmodl`

Вычисляет остаток с плавающей запятой.

## <a name="syntax"></a>Синтаксис

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);

#define fmod(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Параметры

*`x`*, *`y`*\
Значения с плавающей запятой.

## <a name="return-value"></a>Возвращаемое значение

**`fmod`** Возвращает остаток от деления с плавающей запятой *`x`*  /  *`y`* . Если значение *`y`* равно 0,0, **`fmod`** возвращает нетихом NaN. Сведения о том, как семейство не является беспоконым **`printf`** , см. в разделе [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Замечания

**`fmod`** Функция вычисляет значение *f* остатка с плавающей запятой *`x`*  /  *`y`* таким образом, что *`x`*  =  *i* \* *`y`*  +  *`f`* , где *`i`* является целым числом, *`f`* имеет тот же знак, что *`x`* и абсолютное значение, *`f`* меньше абсолютного значения *`y`* .

C++ допускает перегрузку, поэтому можно вызывать перегрузки **`fmod`** , которые принимают и возвращают **`float`** **`long double`** значения и. В программе на языке C, если только вы не используете `<tgmath.h>` макрос для вызова этой функции, **`fmod`** всегда принимает два **`double`** аргумента и возвращает **`double`** .

При использовании `<tgmath.h>` `fmod()` макроса тип аргумента определяет, какая версия функции выбрана. Подробные сведения см. в разделе [Type-Generic Math](../../c-runtime-library/tgmath.md) .

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

## <a name="requirements"></a>Требования

|Функция|Обязательный заголовок|
|--------------|---------------------|
|**`fmod`**, **`fmodf`**, **`fmodl`**|`<math.h>`|
|**`fmod`** макровирусах | `<tgmath.h>` |

Дополнительные сведения о совместимости см. в разделе [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>См. также раздел

[Поддержка операций с плавающей запятой](../../c-runtime-library/floating-point-support.md)\
[`ceil, ceilf, ceill`](ceil-ceilf-ceill.md)\
[`fabs, fabsf, fabsl`](fabs-fabsf-fabsl.md)\
[`floor, floorf, floorl`](floor-floorf-floorl.md)\
[`_CIfmod`](../../c-runtime-library/cifmod.md)
