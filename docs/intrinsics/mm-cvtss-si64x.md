---
title: _mm_cvtss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: 7948348e0bbc0ea5c0eb1536d79d9eaad08b1087
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330701"
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x

**Блок, относящийся только к системам Microsoft**

Создает x64 расширенной версии преобразовать скаляр единый точности с плавающей запятой 64-битовое целое число (`cvtss2si`) инструкции.

## <a name="syntax"></a>Синтаксис

```
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

#### <a name="parameters"></a>Параметры

*значение*<br/>
[in] `__m128` Структуру, содержащую значения с плавающей точкой.

## <a name="return-value"></a>Возвращаемое значение

64-разрядное целое число, результат преобразования первого значения с плавающей запятой в целое число.

## <a name="requirements"></a>Требования

|Встроенная функция|Архитектура|
|---------------|------------------|
|`_mm_cvtss_si64x`|X64|

**Файл заголовка** \<intrin.h >

## <a name="remarks"></a>Примечания

Первый элемент структуры значение преобразуется в целое число и возвращается. Округления управляющие биты в регистре MXCSR используются для определения поведения округления. Режим округления по умолчанию — с округлением к ближайшему, округление до четного числа, если десятичная часть является 0,5. Так как `__m128` структуры представляет регистр XMM, а это функция принимает значение регистр XMM и записывает его в оперативную память.

Эта процедура доступна только как встроенная функция.

## <a name="example"></a>Пример

```
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[__m128d](../cpp/m128d.md)<br/>
[Встроенные инструкции компилятора](../intrinsics/compiler-intrinsics.md)