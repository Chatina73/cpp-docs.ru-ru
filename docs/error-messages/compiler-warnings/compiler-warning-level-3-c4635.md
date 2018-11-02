---
title: Предупреждение компилятора (уровень 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: 21873a883b19924ce3ef41511d65f8ae640875f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479240"
---
# <a name="compiler-warning-level-3-c4635"></a>Предупреждение компилятора (уровень 3) C4635

Цель комментария XML-документа: неправильно сформированный XML: причина

Компилятор обнаружил проблему с XML-тегами.  Устраните проблему и выполните повторную компиляцию.

Следующий пример приводит к возникновению ошибки C4635:

```
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

Обратите внимание, что в результате для данного примера говорится: **Закрывающий тег member не соответствует открывающему тегу summary.**

Проблема в этом примере это закрывающего тега для \<summary > сформирован неправильно, и компилятор не распознает его как \<summary > закрывающего тега.  \<Член > тег внедряется в XDC-файл компилятором в каждой компиляции/doc.  Таким образом, проблема здесь в том, закрывающий тег \</member >, не соответствует предыдущему открывающему тегу, обработанному компилятором (\<summary >.