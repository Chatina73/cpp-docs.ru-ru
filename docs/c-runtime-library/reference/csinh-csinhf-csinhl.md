---
description: 'Дополнительные сведения о: ксинх, ксинхф, ксинхл'
title: csinh, csinhf, csinhl
ms.date: 11/04/2016
api_name:
- csinh
- csinhf
- csinhl
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
- csinh
- csinhf
- csinhl
- complex/csinh
- complex/csinhf
- complex/csinhl
helpviewer_keywords:
- csinh function
- csinhf function
- csinhl function
ms.assetid: cc616e55-d14d-4cd3-91f0-fbee03ce5edf
ms.openlocfilehash: 1c34e403fa4fb023ee7ddbb707f7af789034559b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178775"
---
# <a name="csinh-csinhf-csinhl"></a>csinh, csinhf, csinhl

Извлекает гиперболический синус комплексного числа.

## <a name="syntax"></a>Синтаксис

```C
_Dcomplex csinh(
   _Dcomplex z
);
_Fcomplex csinh(
   _Fcomplex z
);  // C++ only
_Lcomplex csinh(
   _Lcomplex z
);  // C++ only
_Fcomplex csinhf(
   _Fcomplex z
);
_Lcomplex csinhl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Параметры

*з*<br/>
Комплексное число, указывающее угол в радианах.

## <a name="return-value"></a>Возвращаемое значение

Гиперболический синус *z*, в радианах.

## <a name="remarks"></a>Комментарии

Поскольку C++ допускает перегрузку, можно вызывать перегрузки **ксинх** , которые принимают и возвращают **_Fcomplex** и **_Lcomplex** значения. В программе на языке C **ксинх** всегда принимает и возвращает значение **_Dcomplex** .

## <a name="requirements"></a>Требования

|Подпрограмма|Заголовок C|Заголовок C++|
|-------------|--------------|------------------|
|**ксинх**,               **ксинхф**, **ксинхл**|\<complex.h>|\<ccomplex>|

Дополнительные сведения о совместимости см. в разделе [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также раздел

[Алфавитный справочник по функциям](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
