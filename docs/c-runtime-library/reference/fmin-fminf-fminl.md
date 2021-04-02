---
title: fmin, fminf, fminl
description: Справочник по API для фмин, фминф и фминл; , который определяет меньшее из двух значений.
ms.date: 9/1/2020
api_name:
- fmin
- fminf
- fminl
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: 007eae82ca60796d7a81b34e6419d21585c708d0
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099720"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Определяет наименьшее из двух указанных значений.

## <a name="syntax"></a>Синтаксис

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);

#define fmin(x) // Requires C11 or higher
```

### <a name="parameters"></a>Параметры

*x*\
Первое сравниваемое значение.

*&*\
Второе сравниваемое значение.

## <a name="return-value"></a>Возвращаемое значение

В случае успеха возвращает меньшее значение *x* или *y*.

|Входные данные|Результат|
|-----------|------------|
|*x* является NaN|*y*|
|*y* — NaN|*x*|
|*x* и *y* — это NaN|не число|

Функция не вызывает [_matherr](matherr.md) вызываться, приводит к исключениям с плавающей запятой или изменению **значения параметра «значение».**

## <a name="remarks"></a>Комментарии

Поскольку C++ допускает перегрузку, можно вызывать перегрузки **фмин** , которые принимают и возвращают **`float`** **`long double`** типы и. В программе на языке C, если только вы не используете \<tgmath.h> макрос для вызова этой функции, **фмин** всегда принимает и возвращает **`double`** .

При использовании \<tgmath.h> `fmin()` макроса тип аргумента определяет, какая версия функции выбрана. Подробные сведения см. в разделе [Type-Generic Math](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**фмин**, **фминф**, **фминл**|Ц \<math.h><br />C++: \<math.h> или \<cmath>|
|макрос **фмин** | \<tgmath.h> |

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также раздел

[Алфавитный справочник по функциям](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
