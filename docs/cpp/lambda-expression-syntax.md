---
title: Синтаксис лямбда-выражений
ms.date: 11/04/2016
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
ms.openlocfilehash: 030960cf8a301575396231cec1a37ff7bed2667f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577480"
---
# <a name="lambda-expression-syntax"></a>Синтаксис лямбда-выражений

В этой статье демонстрируется синтаксис и структурные элементы лямбда-выражений. Описание лямбда-выражения, см. в разделе [лямбда-выражения](../cpp/lambda-expressions-in-cpp.md).

## <a name="function-objects-vs-lambdas"></a>Объекты-функции и Лямбда-выражения

При написании кода, вы, возможно, использовать указатели на функции и объекты-функции для решения проблем и выполнения вычислений, особенно в том случае, если вы используете [алгоритмы стандартной библиотеки C++](../cpp/algorithms-modern-cpp.md). У объектов-функций и указателей на функции есть как преимущества, так и недостатки. Например, указатели на функции отличаются минимальными требованиями к синтаксису, но не сохраняют состояние в области видимости. Объекты-функции, в свою очередь, могут сохранять состояние, но требуют дополнительного синтаксиса в определении класса.

Лямбда-выражение сочетает преимущества указателей на функции и объектов-функций, избегая их недостатков. Как и объекты-функции, лямбда-выражения гибки и могут сохранять состояние. Однако в отличие от объектов-функций, их компактный синтаксис не требует явного определения класса. С помощью лямбда-выражений можно написать код, более простой и менее подверженный появлению ошибок, чем код для соответствующего объекта-функции.

В следующих примерах сравнивается использование лямбда-выражения и объекта-функции. В первом примере лямбда-выражение используется для вывода на консоль сообщения о четности или нечетности каждого из элементов в объекте `vector`. Во втором примере для выполнения той же задачи используется объект-функция.

## <a name="example-1-using-a-lambda"></a>Пример 1: использование лямбда-выражения

В этом примере передается лямбда-выражения и **for_each** функции. Лямбда-выражение выводит сообщение о четности или нечетности каждого из элементов объекта `vector`.

### <a name="code"></a>Код

```cpp
// even_lambda.cpp
// compile with: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

int main()
{
   // Create a vector object that contains 10 elements.
   vector<int> v;
   for (int i = 1; i < 10; ++i) {
      v.push_back(i);
   }

   // Count the number of even numbers in the vector by
   // using the for_each function and a lambda.
   int evenCount = 0;
   for_each(v.begin(), v.end(), [&evenCount] (int n) {
      cout << n;
      if (n % 2 == 0) {
         cout << " is even " << endl;
         ++evenCount;
      } else {
         cout << " is odd " << endl;
      }
   });

   // Print the count of even numbers to the console.
   cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

### <a name="output"></a>Вывод

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

### <a name="comments"></a>Комментарии

В примере третий аргумент **for_each** функция является лямбда-выражение. Часть `[&evenCount]` указывает предложение захвата выражения, `(int n)` определяет список параметров, а оставшаяся часть определяет тело выражения.

## <a name="example-2-using-a-function-object"></a>Пример 2: использование объекта-функции

Иногда лямбда-выражение может быть слишком громоздким для значительного расширения из состояния, показанного в предыдущем примере. В следующем примере используется объект функции, а не лямбда-выражение, вместе с **for_each** функции, чтобы получить те же результаты, что в примере 1. Оба примера хранят количество четных чисел в объекте `vector`. Для поддержания состояния операции класс `FunctorClass` хранит переменную `m_evenCount` по ссылке как переменную-член. Для выполнения операции, `FunctorClass` реализует оператор вызова функции, **operator()**. Компилятор Visual C++ создает код, который сопоставим по размеру и производительности коду лямбда-выражения в примере 1. Для несложной проблемы, такой как в этом примере, более простая конструкция лямбда-выражения, возможно, лучше, чем конструкция объекта-функции. Однако если вы считаете, что в будущем потребуется значительно расширить функциональность, используйте конструкцию объекта-функции, чтобы упростить обслуживание кода.

Дополнительные сведения о **operator()**, см. в разделе [вызовов функций](../cpp/function-call-cpp.md). Дополнительные сведения о **for_each** функции, см. в разделе [for_each](../standard-library/algorithm-functions.md#for_each).

### <a name="code"></a>Код

```cpp
// even_functor.cpp
// compile with: /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

class FunctorClass
{
public:
    // The required constructor for this example.
    explicit FunctorClass(int& evenCount)
        : m_evenCount(evenCount) { }

    // The function-call operator prints whether the number is
    // even or odd. If the number is even, this method updates
    // the counter.
    void operator()(int n) const {
        cout << n;

        if (n % 2 == 0) {
            cout << " is even " << endl;
            ++m_evenCount;
        } else {
            cout << " is odd " << endl;
        }
    }

private:
    // Default assignment operator to silence warning C4512.
    FunctorClass& operator=(const FunctorClass&);

    int& m_evenCount; // the number of even variables in the vector.
};

int main()
{
    // Create a vector object that contains 10 elements.
    vector<int> v;
    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }

    // Count the number of even numbers in the vector by
    // using the for_each function and a function object.
    int evenCount = 0;
    for_each(v.begin(), v.end(), FunctorClass(evenCount));

    // Print the count of even numbers to the console.
    cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

## <a name="output"></a>Вывод

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

## <a name="see-also"></a>См. также

[Лямбда-выражения](../cpp/lambda-expressions-in-cpp.md)<br/>
[Примеры лямбда-выражений](../cpp/examples-of-lambda-expressions.md)<br/>
[generate](../standard-library/algorithm-functions.md#generate)<br/>
[generate_n](../standard-library/algorithm-functions.md#generate_n)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)<br/>
[Спецификации исключений (throw)](../cpp/exception-specifications-throw-cpp.md)<br/>
[Предупреждение компилятора (уровень 1) C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)<br/>
[Модификаторы, используемые в системах Майкрософт](../cpp/microsoft-specific-modifiers.md)