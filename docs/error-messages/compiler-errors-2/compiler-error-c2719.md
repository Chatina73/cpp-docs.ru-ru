---
description: 'Дополнительные сведения о: Ошибка компилятора C2719'
title: Ошибка компилятора C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: 61e01107d5681c4bab39b06b00293ecdbeb9fc9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320726"
---
# <a name="compiler-error-c2719"></a>Ошибка компилятора C2719

parameter: формальный параметр с __declspec(align('#')) не будет выровнен

Использование [](../../cpp/align-cpp.md) **`__declspec`** модификатора aligned в параметрах функции не допускается. Выравнивание параметров функции контролируется используемым соглашением о вызовах. Дополнительные сведения см. в разделе [соглашения о вызовах](../../cpp/calling-conventions.md).

В следующем примере показано возникновение ошибки C2719 и приводятся сведения по ее устранению.

```cpp
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```
