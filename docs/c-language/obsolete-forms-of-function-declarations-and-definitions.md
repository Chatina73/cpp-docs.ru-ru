---
description: 'Подробнее о следующем: Устаревшие формы объявлений и определений функций'
title: Устаревшие формы объявлений и определений функций
ms.date: 11/04/2016
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
ms.openlocfilehash: 7cd66ba1600d4a5fd381819f4b1d3f0beeb30f0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256917"
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>Устаревшие формы объявлений и определений функций

В объявлениях и определениях функций по старому стилю используют несколько иные правила объявления параметров, нежели рекомендовано стандартом ANSI C. Во-первых, объявления по старому стилю не имеют списка параметров. Во-вторых, в определении функции перечислены параметры, однако их типы не объявлены в списке параметров. Объявления типов предшествуют составной инструкции, образующей тело функции. Прежний синтаксис является устаревшим, его не следует использовать в новом коде. Однако код, составленный с использованием синтаксиса старого стиля, до сих пор поддерживается. В этом примере показаны устаревшие формы объявлений и определений.

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

Функции, возвращающие целое число или указатель того же размера, что и **`int`** , не обязательно должны иметь объявление, хотя это рекомендуется.

В целях соответствия стандарту ANSI C объявления функций по старому стилю, выполненные с использованием многоточия, теперь выдают ошибку при выполнении компиляции с параметром /Za и предупреждение четвертого уровня при выполнении компиляции с параметром /Ze. Пример:

```cpp
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

Необходимо переписать это объявление в качестве прототипа.

```cpp
void funct1( int a, ... )
{
}
```

Объявления функций по старому стилю также создают предупреждения, если впоследствии та же функция объявляется или определяется с помощью многоточия или параметра с типом, отличным от соответствующего типа повышенного уровня.

В следующей статье ([Определения функций на языке C](../c-language/c-function-definitions.md)) описан синтаксис для определения функций, в том числе устаревший синтаксис. Нетерминал *identifier-list* обозначает список параметров для синтаксиса устаревшего стиля.

## <a name="see-also"></a>См. также

[Общие сведения о функциях](../c-language/overview-of-functions.md)
