---
description: 'Дополнительные сведения о: Ошибка компилятора C2178'
title: Ошибка компилятора C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 7a93293fdb87f30827b8b9c3c6d38066b0c76798
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322166"
---
# <a name="compiler-error-c2178"></a>Ошибка компилятора C2178

"*идентификатор*" не может быть объявлен с описателем "*спецификатор*"

В **`mutable`** объявлении использовался спецификатор, но в данном контексте спецификатор не разрешен.

**`mutable`** Спецификатор может применяться только к именам элементов данных класса и не может применяться к именам, объявленным **`const`** или **`static`** , и не может применяться к ссылочным элементам.

## <a name="example"></a>Пример

В следующем примере показано, как может произойти C2178, и как устранить эту проблему.

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
