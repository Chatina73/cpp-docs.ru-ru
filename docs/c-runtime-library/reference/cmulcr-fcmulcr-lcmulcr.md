---
description: 'Дополнительные сведения: _Cmulcr, _FCmulcr, _LCmulcr'
title: _Cmulcr, _FCmulcr, _LCmulcr
ms.date: 03/30/2018
api_name:
- _Cmulcr
- _FCmulcr
- _LCmulcr
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
- _Cmulcr
- _FCmulcr
- _LCmulcr
- complex/_Cmulcr
- complex/_FCmulcr
- complex/_LCmulcr
helpviewer_keywords:
- _Cmulcr function
- _FCmulcr function
- _LCmulcr function
ms.openlocfilehash: ea1dbbcea6890246b1e318da238fb8cc2ee3abb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260726"
---
# <a name="_cmulcr-_fcmulcr-_lcmulcr"></a>_Cmulcr, _FCmulcr, _LCmulcr

Умножает комплексное число на число с плавающей запятой.

## <a name="syntax"></a>Синтаксис

```C
_Dcomplex _Cmulcr( _Dcomplex x, double y );
_Fcomplex _FCmulcr( _Fcomplex x, float y );
_Lcomplex _LCmulcr( _Lcomplex x, long double y );
```

### <a name="parameters"></a>Параметры

*x*<br/>
Один из сложных операндов для умножения.

*y*<br/>
Операнд с плавающей запятой, который необходимо умножить.

## <a name="return-value"></a>Возвращаемое значение

Структура **_Dcomplex**, **_Fcomplex** или **_Lcomplex** , представляющая комплексное произведение комплексного числа *x* и флаотинг-Point с номером *y*.

## <a name="remarks"></a>Комментарии

Поскольку встроенные арифметические операторы не работают в реализации сложных типов Майкрософт, функции **_Cmulcr**, **_FCmulcr** и **_LCmulcr** упрощают умножение сложных типов на типы с плавающей запятой.

## <a name="requirements"></a>Требования

|Подпрограмма|Заголовок C|Заголовок C++|
|-------------|--------------|------------------|
|**_Cmulcr**, **_FCmulcr** **_LCmulcr**|\<complex.h>|\<complex.h>|

Эти функции относятся только к Microsoft. Типы **_Dcomplex**, **_Fcomplex** и **_Lcomplex** являются эквивалентами, специфичными для Microsoft, для нереализованных C99 машинных типов **Double _Complex**, **float _Complex** и **long double _Complex** соответственно. Дополнительные сведения о совместимости см. в разделе [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также раздел

[Алфавитный справочник по функциям](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
