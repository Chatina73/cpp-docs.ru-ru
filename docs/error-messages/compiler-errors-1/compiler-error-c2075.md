---
description: 'Дополнительные сведения о: Ошибка компилятора C2075'
title: Ошибка компилятора C2075
ms.date: 11/04/2016
f1_keywords:
- C2075
helpviewer_keywords:
- C2075
ms.assetid: 8b1865d2-540b-4117-b982-e7a58a0b6cf7
ms.openlocfilehash: f08f92725cbd78e54fb0fa86c6d70b4629eb99f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151348"
---
# <a name="compiler-error-c2075"></a>Ошибка компилятора C2075

"идентификатор": для инициализации массива требуются фигурные скобки

Указанный инициализатор массива не заключен в фигурные скобки.

В следующем примере возникает ошибка C2075.

```c
// C2075.c
int main() {
   int i[] = 1, 2, 3 };   // C2075
}
```

Возможное решение:

```c
// C2075b.c
int main() {
   int j[] = { 1, 2, 3 };
}
```
