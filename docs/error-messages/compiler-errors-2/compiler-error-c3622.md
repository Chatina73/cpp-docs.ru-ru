---
title: Ошибка компилятора C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 69565a1a2d159623bca927a94543834d18c13299
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518096"
---
# <a name="compiler-error-c3622"></a>Ошибка компилятора C3622

«класс»: класс, объявленный как «ключевое_слово» не может быть создан

Была предпринята попытка создать экземпляр класса, помеченного как [абстрактный](../../windows/abstract-cpp-component-extensions.md). Класс, помеченный как `abstract` может быть базовым классом, но он не может быть создан.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3622.

```
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
