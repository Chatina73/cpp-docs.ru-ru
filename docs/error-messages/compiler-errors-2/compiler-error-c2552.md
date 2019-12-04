---
title: Ошибка компилятора C2552
ms.date: 11/04/2016
f1_keywords:
- C2552
helpviewer_keywords:
- C2552
ms.assetid: 0e0ab759-788a-4faf-9337-80d4b9e2e8c9
ms.openlocfilehash: 7f3e4cfc46655c5201e7a79a9333f532a8fcab9c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740810"
---
# <a name="compiler-error-c2552"></a>Ошибка компилятора C2552

"идентификатор": инициализация не агрегированных данных с помощью списка инициализации не допускается

Идентификатор агрегата был неверно инициализирован.

[Статистические выражения](../../c-language/initializing-aggregate-types.md) определяются следующим образом:

- Массивы

- классы, структуры и объединения, у которых нет:

   - Конструкторы

   - закрытых или защищенных членов;

   - базовых классов;

   - Виртуальные функции

Кроме того, в Visual C++ в агрегатах не допускаются типы данных, содержащие конструкторы.

Ниже приведены причины, из-за которых при попытке инициализации агрегата для типа может возникнуть ошибка C2552:

- Тип имеет один или несколько пользовательских конструкторов.

- Тип имеет один или несколько нестатических, закрытых данных-членов.

- Тип имеет одну или несколько виртуальных функций.

- Тип имеет базовый класс.

- Тип является классом ссылки или интерфейсом среды CLR.

- Тим включает массив нефиксированного размера (нулевой массив), элементы которого имеют деструкторы.

Следующий пример приводит к возникновению ошибки C2552:

```cpp
// C2552.cpp
// compile with: /clr
#include <string>
using namespace std;

struct Pair_Incorrect {
private:
   string m_name;
   double m_val;
};

struct Pair_Correct1 {
public:
   Pair_Correct1(string name, double val)
      : m_name(name), m_val(val) {}

private:
   string m_name;
   double m_val;
};

struct Pair_Correct2 {
public:
   string m_name;
   double m_val;
};

int main() {
   // To fix, add a constructor to this class and use it for
   // initializing the data members, see Pair_Correct1 (below)
   // or
   // Do not have any private or protected non-static data members,
   // see Pair_Correct2 (below).  Pair_Correct2 is not recommended in
   // case your object model requires some non-static data members to
   // be private or protected

   string name("John");
   Pair_Incorrect pair1 = { name, 0.0 };   // C2552

   // initialize a CLR immutable value type that has a constructor
   System::DateTime dt = {2001, 4, 12, 22, 16, 49, 844};   // C2552

   Pair_Correct1 pair2( name, 0.0 );
   Pair_Correct1 pair3 = Pair_Correct1( name, 0.0 );
   Pair_Correct2 pair4 = { name, 0.0 };
   System::DateTime dt2(2001, 4, 12, 22, 16, 49, 844);
}
```
