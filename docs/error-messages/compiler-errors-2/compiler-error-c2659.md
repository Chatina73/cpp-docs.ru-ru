---
description: 'Дополнительные сведения о: Ошибка компилятора C2659'
title: Ошибка компилятора C2659
ms.date: 11/04/2016
f1_keywords:
- C2659
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
ms.openlocfilehash: 6a0f6c84e6bc279d9db75c423fdfc0d99b5ea769
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249676"
---
# <a name="compiler-error-c2659"></a>Ошибка компилятора C2659

оператор: функция в качестве левого операнда

Функция находится слева от указанного оператора. Наиболее частая причина этой ошибки состоит в том, что в результате синтаксического анализа компилятор воспринял идентификатор в левой части оператора как функцию, хотя по замыслу разработчика это должна быть переменная. Дополнительные сведения см. в статье Википедии [досадной Parse](https://en.wikipedia.org/wiki/Most_vexing_parse). В этом примере показаны объявление функции и определение переменной, которые легко перепутать.

```cpp
// C2659a.cpp
// Compile using: cl /W4 /EHsc C2659a.cpp
#include <string>
using namespace std;

int main()
{
   string string1(); // string1 is a function returning string
   string string2{}; // string2 is a string initialized to empty

   string1 = "String 1"; // C2659
   string2 = "String 2";
}
```

Для разрешения этой проблемы измените объявление идентификатора таким образом, чтобы он не воспринимался как объявление функции.

Ошибка C2659 также может возникать, если функция имеет тип, который не может использоваться в выражениях с левой стороны указанного оператора. Этот пример приводит к возникновению ошибки C2659, когда код присваивает функции указатель на функцию:

```cpp
// C2659b.cpp
// Compile using: cl /W4 /EHsc C2659b.cpp
int func0(void) { return 42; }
int (*func1)(void);

int main()
{
   func1 = func0;
   func0 = func1; // C2659
}
```
