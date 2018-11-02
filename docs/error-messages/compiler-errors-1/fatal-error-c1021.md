---
title: Неустранимая ошибка C1021
ms.date: 11/04/2016
f1_keywords:
- C1021
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
ms.openlocfilehash: 35b94e6cea177121c38d06706b42437ec610c38a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587111"
---
# <a name="fatal-error-c1021"></a>Неустранимая ошибка C1021

недопустимая команда препроцессора "строка"

`string` не является допустимой [директивой препроцессора](../../preprocessor/preprocessor-directives.md). Чтобы устранить эту ошибку, используйте допустимое имя директивы препроцессора для `string`.

Следующий пример приводит к возникновению ошибки C1021:

```
// C1021.cpp
#BadPreProcName    // C1021 delete line
```