---
title: Поиск имен функций с зависимостью от аргументов (поиск Koenig)
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: d979b79c0f712ed35a42a44047dd1091010c72bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184483"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Поиск имен функций с зависимостью от аргументов (поиск Koenig)

Компилятор может использовать поиск имени с зависимостью от аргументов для поиска определения неопределенного вызова функции. Поиск имени с зависимостью от аргументов также называется поиском Koenig. Тип каждого аргумента в вызове функции определяется в иерархии пространств имен, классов, структур, объединений или шаблонов. При указании неопределенного [постфиксные](../cpp/postfix-expressions.md) вызов функции, компилятор выполняет поиск для определения функции в иерархии, связанной с каждым типом аргумента.

## <a name="example"></a>Пример

В образце компилятор замечает, что функция `f()` принимает аргумент `x`. Аргумент `x` принадлежит типу `A::X`, определенному в пространстве имен `A`. Компилятор выполняет поиск пространства имен `A` и обнаруживает определение функции `f()`, принимающей аргумент типа `A::X`.

```cpp
// argument_dependent_name_koenig_lookup_on_functions.cpp
namespace A
{
   struct X
   {
   };
   void f(const X&)
   {
   }
}
int main()
{
// The compiler finds A::f() in namespace A, which is where
// the type of argument x is defined. The type of x is A::X.
   A::X x;
   f(x);
}
```