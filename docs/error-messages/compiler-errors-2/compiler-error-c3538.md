---
description: 'Дополнительные сведения о: Ошибка компилятора C3538'
title: Ошибка компилятора C3538
ms.date: 11/04/2016
f1_keywords:
- C3538
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
ms.openlocfilehash: 6fbfbc59bb52d4603fc734e69f2f7ccc88942f7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112470"
---
# <a name="compiler-error-c3538"></a>Ошибка компилятора C3538

в списке объявлений спецификатор "auto" должен всегда выводить тот же самый тип

Все переменные в списке объявлений не были разрешены в один тип.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Убедитесь, что все объявления в списке выводятся на **`auto`** один и тот же тип.

## <a name="example"></a>Пример

Следующие выражения вызывают ошибку C3538. Каждый оператор объявляет несколько переменных, но каждое использование **`auto`** ключевого слова не приводит к одному и тому же типу.

```cpp
// C3538.cpp
// Compile with /Zc:auto
// C3538 expected
int main()
{
// Variable x1 is a pointer to char, but y1 is a double.
   auto * x1 = "a", y1 = 3.14;
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;
// Variable x2 is an int, but y2 is a double and z is a char.
   auto x2(1), y2(0.0), z = 'a';
// Variable a is a pointer to int, but b is a pointer to double.
   auto *a = new auto(1), *b = new auto(2.0);
   return 0;
}
```

## <a name="see-also"></a>См. также

[Ключевое слово auto](../../cpp/auto-cpp.md)
