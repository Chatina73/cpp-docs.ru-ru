---
description: Дополнительные сведения о инструкции Continue (C++)
title: Оператор continue (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 6899e5cd249ab5a7a3b786e4b82c9890c08a7183
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344644"
---
# <a name="continue-statement-c"></a>Оператор continue (C++)

Принудительно передает управление управляющему выражению наименьшего включающего цикла [Do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)или [while](../cpp/while-statement-cpp.md) .

## <a name="syntax"></a>Синтаксис

```
continue;
```

## <a name="remarks"></a>Remarks

Все остальные операторы текущей итерации не выполняются. Следующая итерация цикла определяется следующим образом.

- В **`do`** **`while`** цикле или Следующая итерация начинается с переоценки управляющего выражения **`do`** **`while`** оператора или.

- В **`for`** цикле (с использованием синтаксиса `for( <init-expr> ; <cond-expr> ; <loop-expr> )` ) `<loop-expr>` выполняется предложение. Затем повторно выполняется предложение `<cond-expr>` и, в зависимости от результата, цикл завершается или начинается другая итерация.

В следующем примере показано, как **`continue`** можно использовать инструкцию для обхода частей кода и начать следующую итерацию цикла.

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

## <a name="see-also"></a>См. также раздел

[Операторы перехода](../cpp/jump-statements-cpp.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)
