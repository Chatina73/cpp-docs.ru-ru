---
description: 'Дополнительные сведения о: Ошибка компилятора C2975'
title: Ошибка компилятора C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 9f9108d1dc4e0fe61b6dd2135fb69bbaedfaedf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210352"
---
# <a name="compiler-error-c2975"></a>Ошибка компилятора C2975

> "*аргумент*": недопустимый аргумент шаблона для "*тип*", требуется константное выражение времени компиляции

Аргумент шаблона не соответствует объявлению шаблона. константное выражение должно находиться в угловых скобках. Переменные не допускаются в качестве фактических аргументов шаблона. Проверьте определение шаблона, чтобы найти правильные типы.

## <a name="example"></a>Пример

В следующем примере показано создание C2975, а также правильное использование:

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 также возникает при использовании &#95;&#95;LINE&#95;&#95; в качестве константы времени компиляции с [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md). Одним из решений может быть компиляция с параметром [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) вместо **/Zi**.

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```
