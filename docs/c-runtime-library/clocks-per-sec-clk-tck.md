---
description: 'Дополнительные сведения: CLOCKS_PER_SEC, CLK_TCK'
title: CLOCKS_PER_SEC, CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: 43c59932a3026919435516fc0bfe88ef1e1e45ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322676"
---
# <a name="clocks_per_sec-clk_tck"></a>CLOCKS_PER_SEC, CLK_TCK

## <a name="syntax"></a>Синтаксис

```
#include <time.h>
```

## <a name="remarks"></a>Remarks

Время в секундах — значение, возвращаемое функцией `clock`, разделенное на `CLOCKS_PER_SEC`. `CLK_TCK` эквивалентно, но считается устаревшим.

## <a name="see-also"></a>См. также раздел

[регистрация](../c-runtime-library/reference/clock.md)<br/>
[Глобальные константы](../c-runtime-library/global-constants.md)
