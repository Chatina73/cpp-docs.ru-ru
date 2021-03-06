---
description: 'Дополнительные сведения: Ошибка средств компоновщика LNK2020'
title: Ошибка средств компоновщика LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 61e999b2f451359e3a806bc2da5f2beb431e6fab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275858"
---
# <a name="linker-tools-error-lnk2020"></a>Ошибка средств компоновщика LNK2020

неразрешенный токен "токен"

Аналогично неопределенной внешней ошибке, за исключением того, что ссылка осуществляется через метаданные. В метаданных должны быть определены все функции и данные.

Чтобы устранить проблему, сделайте следующее:

- Определите недостающую функцию или данные или

- Включите объектный файл или библиотеку, в которых уже определена отсутствующая функция или данные.

## <a name="examples"></a>Примеры

Следующий пример приводит к возникновению ошибки LNK2020.

```cpp
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

LNK2020 также произойдет при создании переменной типа управляемого шаблона, но не создает экземпляр типа.

Следующий пример приводит к возникновению ошибки LNK2020.

```cpp
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```
