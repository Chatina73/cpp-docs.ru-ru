---
title: Предупреждение компилятора (уровень 1) C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: 1afb29b10352150cac2969849979fb5b5e2b8719
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378483"
---
# <a name="compiler-warning-level-1-c4829"></a>Предупреждение компилятора (уровень 1) C4829

Возможно, неверные параметры для функции main. Рассмотрите возможность "intmain (Platform::Array\<Platform::String ^ > ^ argv)"

Некоторые функции, например main, не могут принимать параметры ссылочного типа. Хотя компиляция будет успешной, полученный в результате образ, возможно, не будет выполняться.

Следующий пример приводит к возникновению ошибки C4829.

```
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829
```