---
title: Оператор continue (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 6fbc4af6a9a56f3406582ea9ba59f4d5759b88a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154637"
---
# <a name="continue-statement-c"></a>Оператор continue (C++)

Принудительно вызывает передачу управления управляющему выражению наименьшего внешнего [сделать](../cpp/do-while-statement-cpp.md), [для](../cpp/for-statement-cpp.md), или [хотя](../cpp/while-statement-cpp.md) цикла.

## <a name="syntax"></a>Синтаксис

```
continue;
```

## <a name="remarks"></a>Примечания

Все остальные операторы текущей итерации не выполняются. Следующая итерация цикла определяется следующим образом.

- В **сделать** или **хотя** цикл, следующая итерация начинается путем повторного вычисления управляющее выражение оператора **сделать** или **хотя** инструкции.

- В **для** цикла (с использованием синтаксиса `for`(`init-expr`; `cond-expr`; `loop-expr`)), `loop-expr` предложение выполняется. Затем повторно выполняется предложение `cond-expr` и, в зависимости от результата, цикл завершается или начинается другая итерация.

В следующем примере показан как **по-прежнему** инструкция может использоваться для обхода фрагментов кода и начала выполнения следующей итерации цикла.

## <a name="example"></a>Пример

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>См. также

[Операторы перехода](../cpp/jump-statements-cpp.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)