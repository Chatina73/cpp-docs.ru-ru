---
description: 'Дополнительные сведения о: discrete_distribution классе'
title: Класс discrete_distribution
ms.date: 11/04/2016
f1_keywords:
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
helpviewer_keywords:
- std::discrete_distribution [C++]
- std::discrete_distribution [C++], reset
- std::discrete_distribution [C++], probabilities
- std::discrete_distribution [C++], param
- std::discrete_distribution [C++], min
- std::discrete_distribution [C++], max
- std::discrete_distribution [C++], param_type
- std::discrete_distribution [C++], param_type
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
ms.openlocfilehash: b84d174a653efdeba47fb0356c903b8c7dd2a8d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232763"
---
# <a name="discrete_distribution-class"></a>Класс discrete_distribution

Формирует дискретное распределение целых чисел с равномерными интервалами ширины и одинаковой вероятностью в каждом интервале.

## <a name="syntax"></a>Синтаксис

```cpp
template<class IntType = int>
class discrete_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructor and reset functions
   discrete_distribution();
   template <class InputIterator>
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Параметры

*инттипе*\
Целочисленный тип результата, по умолчанию — **`int`** . Возможные типы см. в разделе [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Комментарии

Выборочное распределение использует равномерные интервалы ширины с одинаковой вероятностью в каждом интервале. Сведения о других выборочных распределениях см. в разделах [piecewise_linear_distribution Class](../standard-library/piecewise-linear-distribution-class.md) и [piecewise_constant_distribution Class](../standard-library/piecewise-constant-distribution-class.md).

В следующей таблице представлены ссылки на статьи об отдельных членах.

[discrete_distribution](#discrete_distribution)\
[param_type](#param_type)

Функция свойства `vector<double> probabilities()` возвращает отдельные вероятности для каждого полученного целого числа.

Дополнительные сведения о классах распределения и их членах см [\<random>](../standard-library/random.md) . в разделе.

## <a name="example"></a>Пример

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "probabilities (value: probability):" << endl;
    vector<double> p = distr.probabilities();
    int counter = 0;
    for (const auto& n : p) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 4
probabilities (value: probability):
          0:   0.0666666667
          1:   0.1333333333
          2:   0.2000000000
          3:   0.2666666667
          4:   0.3333333333

Distribution for 100 samples:
    0 :::
    1 ::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::::::::::::::::
    4 ::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Требования

**Заголовок:**\<random>

**Пространство имен:** std

## <a name="discrete_distributiondiscrete_distribution"></a><a name="discrete_distribution"></a> discrete_distribution::d iscrete_distribution

Формирует распределение.

```cpp
// default constructor
discrete_distribution();

// construct using a range of weights, [firstW, lastW)
template <class InputIterator>
discrete_distribution(InputIterator firstW, InputIterator lastW);

// construct using an initializer list for range of weights
discrete_distribution(initializer_list<double> weightlist);

// construct using unary operation function
template <class UnaryOperation>
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);

// construct from an existing param_type structure
explicit discrete_distribution(const param_type& parm);
```

### <a name="parameters"></a>Параметры

*firstW*\
Первый итератор в списке, на основе которого формируется распределение.

*lastW*\
Последний итератор в списке, на основе которого формируется распределение (неинклюзивный список, так как итераторы используют пустой элемент в качестве последнего элемента).

*weightlist*\
Объект [initializer_list](../cpp/initializers.md), из которого формируется распределение.

*расчета*\
Количество элементов в диапазоне распределения. Если `count==0`, то эквивалентно конструктору по умолчанию (всегда формируется 0).

*низшую*\
Минимальное значение в диапазоне распределения.

*высоком*\
Максимальное значение в диапазоне распределения.

*веигхтфунк*\
Объект, представляющий функцию вероятности распределения. Параметр и возвращаемое значение должны быть преобразованы в **`double`** .

*ParM*\
Структура `param_type`, используемая для формирования распределения.

### <a name="remarks"></a>Комментарии

Конструктор по умолчанию создает объект, значение вероятности которого содержит один элемент со значением 1. Это приводит к получению распределения, которое всегда возвращает 0.

Конструктор диапазона итератора с параметрами *firstW* и *lastW* создает объект распределения с помощью значений веса из итераторов в пределах последовательности интервала [*firstW*, *lastW*).

Конструктор списка инициализаторов с параметром *weightlist* конструирует объект распределения с весовыми коэффициентами из списка инициализаторов *weightlist*.

Конструктор с параметрами *число*, *низкий*, *высокий* и *weightfunc* формирует объект распределения, инициализируемый на основе следующих правил:

- Если *число* < 1, **n** = 1, то эквивалентно конструктору по умолчанию (всегда формируется 0).
- Если *число* > 0, **n** = *число*. Предоставленный **d** = (*High*  -  *Low*) **/n** больше нуля с использованием **d** однородных поддиапазонов, каждый вес назначается следующим образом: `weight[k] = weightfunc(x)` , где **x**  =  *Low*  +  **k**  *  **d**  +   /2, для **k** = 0,..., **n** -1.

Конструктор, имеющий `param_type` параметр *parm*, создает объект распределения, используя *parm* как сохраненную структуру параметров.

## <a name="discrete_distributionparam_type"></a><a name="param_type"></a> discrete_distribution::p aram_type

Сохраняет все параметры распределения.

```cpp
struct param_type {
   typedef discrete_distribution<result_type> distribution_type;
   param_type();

   // construct using a range of weights, [firstW, lastW)
   template <class InputIterator>
   param_type(InputIterator firstW, InputIterator lastW);

   // construct using an initializer list for range of weights
   param_type(initializer_list<double> weightlist);

   // construct using unary operation function
   template <class UnaryOperation>
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Параметры

*firstW*\
Первый итератор в списке, на основе которого формируется распределение.

*lastW*\
Последний итератор в списке, на основе которого формируется распределение (неинклюзивный список, так как итераторы используют пустой элемент в качестве последнего элемента).

*weightlist*\
Объект [initializer_list](../cpp/initializers.md), из которого формируется распределение.

*расчета*\
Количество элементов в диапазоне распределения. Если *число* равно 0, это эквивалентно конструктору по умолчанию (всегда формируется 0).

*низшую*\
Минимальное значение в диапазоне распределения.

*высоком*\
Максимальное значение в диапазоне распределения.

*веигхтфунк*\
Объект, представляющий функцию вероятности распределения. Параметр и возвращаемое значение должны быть преобразованы в **`double`** .

*Правильно*\
Объект `param_type`, который требуется сравнить с данным объектом.

### <a name="remarks"></a>Комментарии

Этот пакет параметров можно передать в `operator()` для получения возвращаемого значения.

## <a name="see-also"></a>См. также раздел

[\<random>](../standard-library/random.md)
