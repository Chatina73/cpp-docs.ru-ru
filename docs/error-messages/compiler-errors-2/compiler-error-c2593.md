---
description: 'Дополнительные сведения о: Ошибка компилятора C2593'
title: Ошибка компилятора C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 849cd79b1d469d957cf1bde499ce66bd54a64074
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120169"
---
# <a name="compiler-error-c2593"></a>Ошибка компилятора C2593

неоднозначный "идентификатор оператора"

Для перегруженного оператора определено более одного возможного оператора.

Эту ошибку можно исправить, если использовать явное приведение для одного или нескольких фактических параметров.

Следующий пример приводит к возникновению ошибки C2593:

```cpp
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

Эта ошибка может быть вызвана сериализацией переменной с плавающей запятой с помощью `CArchive` объекта. Компилятор идентифицирует `<<` оператор как неоднозначный. Единственные примитивные типы C++, которые `CArchive` могут быть сериализованы, — это типы фиксированного размера `BYTE` ,, `WORD` `DWORD` и `LONG` . Для сериализации все целочисленные типы должны быть приведены к одному из этих типов. Типы с плавающей запятой должны быть архивированы с помощью `CArchive::Write()` функции-члена.

В следующем примере показано, как архивировать переменную с плавающей запятой ( `f` ) в архив `ar` :

```
ar.Write(&f, sizeof( float ));
```
