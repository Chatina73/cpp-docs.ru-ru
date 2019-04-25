---
title: imaxdiv
ms.date: 04/05/2018
apiname:
- imaxdiv
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- imaxdiv
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
ms.openlocfilehash: 23067b2028fc11193fae707e25165fb0ce754515
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157335"
---
# <a name="imaxdiv"></a>imaxdiv

Вычисляет частное и остаток от деления двух целочисленных значений любого размера в рамках одной операции.

## <a name="syntax"></a>Синтаксис

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>Параметры

*Число добавлений*<br/>
Числитель.

*denom*<br/>
Знаменатель.

## <a name="return-value"></a>Возвращаемое значение

**imaxdiv** вызван с аргументами типа [intmax_t](../../c-runtime-library/standard-types.md) возвращает структуру типа [imaxdiv_t](../../c-runtime-library/standard-types.md) , которая содержит частное и остаток.

## <a name="remarks"></a>Примечания

**Imaxdiv** функция делит *числа* по *denom* и тем самым Вычисляет частное и остаток. **Imaxdiv_t** структура содержит частное, **intmax_t** **quot**и остаток, **intmax_t** **rem**. Знак частного совпадает со знаком математического частного. Его абсолютное значение представляет собой наибольшее целое число, которое меньше абсолютного значения математического частного. Если знаменатель равен 0, выполнение программы прекратится и появится сообщение об ошибке.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_imaxdiv.c
// Build using: cl /W3 /Tc crt_imaxdiv.c
// This example takes two integers as command-line
// arguments and calls imaxdiv to divide the first
// argument by the second, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x,y;
   imaxdiv_t div_result;

   x = atoll(argv[1]);
   y = atoll(argv[2]);

   printf("The call to imaxdiv(%lld, %lld)\n", x, y);
   div_result = imaxdiv(x, y);
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",
          div_result.quot, div_result.rem);
}
```

При построении и последующем вызове с параметрами командной строки `9460730470000000 8766` код генерирует следующие выходные данные:

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>См. также

[Поддержка чисел с плавающей запятой](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
