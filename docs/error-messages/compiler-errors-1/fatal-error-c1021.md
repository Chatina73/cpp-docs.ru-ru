---
description: 'Дополнительные сведения о: Неустранимая ошибка C1021'
title: Неустранимая ошибка C1021
ms.date: 11/04/2016
f1_keywords:
- C1021
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
ms.openlocfilehash: 74998b7b745ab2c0404ecea3392750b71cd40c6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316353"
---
# <a name="fatal-error-c1021"></a>Неустранимая ошибка C1021

недопустимая команда препроцессора "строка"

`string` не является допустимой [директивой препроцессора](../../preprocessor/preprocessor-directives.md). Чтобы устранить эту ошибку, используйте допустимое имя директивы препроцессора для `string`.

Следующий пример приводит к возникновению ошибки C1021:

```cpp
// C1021.cpp
#BadPreProcName    // C1021 delete line
```
