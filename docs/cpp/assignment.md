---
title: Назначение
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: 1e6d715011cfaab7e250e23a9a31bb3f0c83f36a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603443"
---
# <a name="assignment"></a>Назначение

Оператор присваивания (**=**) является, строго говоря, бинарным оператором. Его объявление идентично объявлению любого другого бинарного оператора, со следующими исключениями:

- Он должен быть нестатической функцией-членом. Не **оператор =** могут быть объявлены как функции недопустимы.
- Он не наследуется производными классами.
- По умолчанию **оператор =** функция может быть создана компилятором для типов классов, если он не существует.

В следующем примере показано, как объявить оператор присваивания:

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

Предоставленный аргумент является правой части выражения. Оператор возвращает объект для сохранения поведения оператора присваивания, который после завершения присваивания возвращает значение левой части. Это позволяет цепочки назначений, таких как:

```cpp
pt1 = pt2 = pt3;
```

Оператор присваивания копии является не следует путать с помощью конструктора копии. Последний вызывается во время создания объекта из существующей структуры:

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> Рекомендуется следовать [правило из трех](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) , что класс, определяющий оператор присваивания копии следует явным образом определить конструктор копии, чтобы конструктор и перемещения присваивание перемещением деструктор и, начиная с C ++ 11, оператор.

## <a name="see-also"></a>См. также

- [Перегрузка операторов](../cpp/operator-overloading.md)
- [Конструкторы копий и операторы присваивания копий (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)