---
description: 'Дополнительные сведения: __movsq'
title: __movsq
ms.date: 09/02/2019
f1_keywords:
- __movsq
helpviewer_keywords:
- __movsq intrinsic
- rep movsq instruction
- movsq instruction
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
ms.openlocfilehash: 8b1713cc17353640904b6593149a73ebce52475d
ms.sourcegitcommit: 977b5151e7dae7584112328bab515fb15622a6cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104883874"
---
# <a name="__movsq"></a>__movsq

**Блок, относящийся только к системам Microsoft**

Формирует повторяющуюся инструкцию перемещения строки ( `rep movsq` ).

## <a name="syntax"></a>Синтаксис

```C
void __movsq(
   unsigned long long* Destination,
   unsigned long long const* Source,
   size_t Count
);
```

### <a name="parameters"></a>Параметры

*Местоназначение*\
заполняет Назначение операции.

*Источника*\
окне Источник операции.

*Расчета*\
окне Число куадвордс для копирования.

## <a name="requirements"></a>Требования

|Intrinsic|Architecture|
|---------------|------------------|
|`__movsq`|X64|

**Файл заголовка** \<intrin.h>

## <a name="remarks"></a>Remarks

В результате первый *Счетчик* куадвордс, на который указывает *источник* , копируется в *целевую* строку.

Эта процедура доступна только как встроенная функция.

## <a name="example"></a>Пример

```cpp
// movsq.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsq)

int main()
{
    unsigned __int64 a1[10];
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,
                               150, 50};
    __movsq(a1, a2, 10);

    for (int i = 0; i < 10; i++)
       printf_s("%d ", a1[i]);
    printf_s("\n");
}
```

```Output
950 850 750 650 550 450 350 250 150 50
```

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Встроенные функции компилятора](../intrinsics/compiler-intrinsics.md)
