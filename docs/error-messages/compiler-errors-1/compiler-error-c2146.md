---
title: Ошибка компилятора C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: 3a0fd9c49a71f6f53d1a109378e3a6894bb68723
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175432"
---
# <a name="compiler-error-c2146"></a>Ошибка компилятора C2146

Синтаксическая ошибка: отсутствует «токен» перед идентификатором «идентификатор»

Компилятор ожидал `token` и найти `identifier` вместо этого.  Возможные причины:

1. Ошибка проверки орфографии или регистр букв.

1. Отсутствует спецификатор типа в объявлении идентификатора.

Эта ошибка может быть вызвана опечатка. Ошибка [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) обычно предшествует эту ошибку.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C2146.

```
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

## <a name="example"></a>Пример

Эта ошибка также может возникать в результате действий по обеспечению совместимости компилятора с Visual Studio .NET 2003: отсутствует `typename` ключевое слово.

Следующий пример компилируется в Visual Studio .NET 2002, но завершается неудачей в Visual Studio .NET 2003:

```
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

## <a name="example"></a>Пример

Вы также увидите эту ошибку, в результате действий по обеспечению совместимости компилятора с Visual Studio .NET 2003: явные специализации больше не находят параметры шаблона из первичного шаблона.

Использование `T` из первичного шаблона не допускается в явной специализации. Код функционировал в версии Visual C++ в Visual Studio .NET 2003 и Visual Studio .NET замените все вхождения параметра шаблона в специализации явно специализированный тип.

Следующий пример компилируется в Visual Studio .NET, но завершается неудачей в Visual Studio .NET 2003:

```
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```