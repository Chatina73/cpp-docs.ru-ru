---
description: 'Дополнительные сведения о: Ошибка компилятора Ошибка c3484'
title: Ошибка компилятора C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: 6d3e72ef89ad33333c840b549cfc5c7c40495130
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315690"
---
# <a name="compiler-error-c3484"></a>Ошибка компилятора C3484

требуется "->" перед типом возврата

Необходимо указать `->` перед типом возврата лямбда-выражения.

### <a name="to-correct-this-error"></a>Исправление ошибки

- Укажите `->` перед типом возврата.

## <a name="examples"></a>Примеры

В следующем примере возникает ошибка C3484:

```cpp
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

В следующем примере устраняется ошибка C3484 путем предоставления `->` перед типом возврата лямбда-выражения:

```cpp
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>См. также

[Лямбда-выражения](../../cpp/lambda-expressions-in-cpp.md)
