---
title: Ревале Справочник Декларатор:&amp;&amp;
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 53729cca7c259bc2d3b792ddc3509d5fc3bd255a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749830"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Ревале Справочник Декларатор:&amp;&amp;

Содержит ссылку на выражение rvalue.

## <a name="syntax"></a>Синтаксис

```
type-id && cast-expression
```

## <a name="remarks"></a>Remarks

Ссылки rvalue позволяют различать значения lvalue и rvalue. Ссылки lvalue и rvalue синтаксически и семантически аналогичны, однако они подчиняются несколько различающимся правилам. Для получения дополнительной информации о lvalues и rvalues, [см. Lvalues и Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md). Для получения дополнительной информации о lvalue ссылки, см [Lvalue Справочник Декларатор: &](../cpp/lvalue-reference-declarator-amp.md).

В следующих разделах описывается, как ссылки на rvalue поддерживают реализацию *семантики хода* и *совершенную пересылку.*

## <a name="move-semantics"></a>Семантика перемещения

Ссылки Rvalue поддерживают реализацию *семантики*перемещений, что может значительно повысить производительность ваших приложений. Семантика перемещения позволяет создавать код, который переносит ресурсы (например, динамически выделяемую память) из одного объекта в другой. Семантика перемещения работает, поскольку она позволяет переносить ресурсы из временных объектов, на которые невозможно ссылаться из других мест в программе.

Для реализации семантики перемещения обычно предоставляется *конструктор перемещения и,* по желанию, оператор назначения перемещения **(оператор)** для вашего класса. Операции копирования и присваивания, источниками которых являются значения rvalue, затем автоматически используют семантику перемещения. В отличие от конструктора копирования по умолчанию, компилятор не предоставляет конструктор перемещения по умолчанию. Для получения более подробной информации о том, как написать конструктор хода и как использовать его в приложении, [см.](../cpp/move-constructors-and-move-assignment-operators-cpp.md)

Можно также перегрузить обычные функции и операторы, чтобы воспользоваться преимуществами семантики перемещения. Visual Studio 2010 вводит семантику перемещения в Стандартную библиотеку СЗ. Например, класс `string` реализует операции, использующие семантику перемещения. Рассмотрим следующий пример, в котором объединяются несколько строк и выводится результат:

```cpp
// string_concatenation.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

int main()
{
   string s = string("h") + "e" + "ll" + "o";
   cout << s << endl;
}
```

Перед Visual Studio 2010 каждый вызов **оператору** выделяет `string` и возвращает новый временный объект (rvalue). **оператор не** может придатить одну строку к другой, потому что он не знает, являются ли строки источника lvalues или rvalues. Если обе исходные строки являются значениями lvalue, на них могут указывать ссылки из какого-либо другого места программы, поэтому их не следует изменять. Используя ссылки на rvalue, **оператор** может быть изменен, чтобы взять rvalues, которые не могут быть упомянуты в другом месте программы. Таким образом, **оператор может** теперь придатить одну строку к другой. Это может значительно снизить количество операций динамического выделения памяти, которые должен выполнять класс `string`. Для получения дополнительной `string` информации о классе, см [basic_string.](../standard-library/basic-string-class.md)

Семантика перемещения также помогает, когда компилятор не может использовать оптимизацию возвращаемого значения (RVO) или оптимизацию именованного возвращаемого значения (NRVO). В таких случаях компилятор вызывает конструктор перемещения, если он определен в типе.

Для лучшего понимания семантики перемещения рассмотрим пример вставки элемента в объект `vector`. Если ресурсы объекта `vector` превышены, объект `vector` должен заново выделить память для своих элементов, а затем скопировать каждый элемент в другое расположение в памяти, чтобы освободить место для добавленного элемента. Когда операция вставки копирует элемент, она создает новый элемент, вызывает конструктор копирования для копирования данных из предыдущего элемента в новый элемент, а затем уничтожает предыдущий элемент. Семантика перемещения позволяет перемещать объекты напрямую, не выполняя ресурсоемкие операции выделения памяти и копирования.

Чтобы воспользоваться преимуществами семантики перемещения в примере `vector`, можно создать конструктор перемещения для перемещения данных из одного объекта в другой.

Для получения более подробной информации о введении семантики перемещения в [C++ Standard Library](../standard-library/cpp-standard-library-reference.md)Стандартную библиотеку СЗ в Visual Studio 2010, см.

## <a name="perfect-forwarding"></a>Точная пересылка

Точная пересылка уменьшает необходимость в использовании перегруженных функций и позволяет избежать проблем пересылки. *Проблема пересылки* может возникнуть, когда вы пишете общую функцию, которая принимает ссылки в качестве своих параметров, и она передает (или *перенаправляет)* эти параметры к другой функции. Например, если универсальная функция принимает параметр типа `const T&`, вызываемая функция не может изменять значение этого параметра. Если универсальная функция принимает параметр типа `T&`, эта функция не может вызываться с использованием значения rvalue (такого как временный объект или целочисленный литерал).

Обычно для решения этой проблемы необходимо предоставить перегруженные версии универсальной функции, принимающие для каждого из своих параметров значения `T&` и `const T&`. В результате число перегруженных функций экспоненциально возрастает по мере увеличения числа параметров. Ссылки rvalue позволяют создать одну версию функции, принимающую произвольные аргументы и пересылающую их в другую функцию, как если бы эта другая функция вызывалась напрямую.

Рассмотрим следующий пример, в котором определяются четыре типа: `W`, `X`, `Y` и `Z`. Конструктор для каждого типа принимает различное сочетание **const** и**non-const** ссылки lvalue как свои параметры.

```cpp
struct W
{
   W(int&, int&) {}
};

struct X
{
   X(const int&, int&) {}
};

struct Y
{
   Y(int&, const int&) {}
};

struct Z
{
   Z(const int&, const int&) {}
};
```

Предположим, требуется написать универсальную функцию, которая создает объекты. В следующем примере показан один из возможных способов написания этой функции:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

В следующем примере показан допустимый вызов функции `factory`:

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

Однако следующий пример содержит недопустимый вызов функции `factory`, поскольку функция `factory` принимает в качестве параметров ссылки lvalue, допускающие изменения, но вызывается с использованием значений rvalue:

```cpp
Z* pz = factory<Z>(2, 2);
```

Обычно для решения этой проблемы необходимо создать перегруженные версии функции `factory` для каждого сочетания параметров `A&` и `const A&`. Ссылки rvalue позволяют создать одну версию функции `factory`, как показано в следующем примере:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

В этом примере в качестве параметров функции `factory` используются ссылки rvalue. Цель [std::forward](../standard-library/utility-functions.md#forward) функция заключается в том, чтобы направить параметры заводской функции конструктору класса шаблона.

В следующем примере показана функция `main`, использующая измененную функцию `factory` для создания экземпляров классов `W`, `X`, `Y` и `Z`. Измененная функция `factory` пересылает свои параметры (значения lvalue или rvalue) в конструктор соответствующего класса.

```cpp
int main()
{
   int a = 4, b = 5;
   W* pw = factory<W>(a, b);
   X* px = factory<X>(2, b);
   Y* py = factory<Y>(a, 2);
   Z* pz = factory<Z>(2, 2);

   delete pw;
   delete px;
   delete py;
   delete pz;
}
```

## <a name="additional-properties-of-rvalue-references"></a>Дополнительные свойства ссылок rvalue

**Можно перегрузить функцию, чтобы она принимала ссылки lvalue и rvalue.**

Перегрузив функцию, чтобы взять ссылку **на конст-lvalue** или ссылку на rvalue, можно написать код, который различает неизменяемые объекты (lvalues) и изменяемые временные значения (rvalues). Вы можете передать объект функции, которая принимает ссылку на rvalue, если объект не помечен как **const.** В следующем примере показана перегруженная функция `f`, принимающая ссылки lvalue и rvalue. Функция `main` вызывает функцию `f` как со значениями lvalue, так и со значениями rvalue.

```cpp
// reference-overload.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void f(const MemoryBlock&)
{
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;
}

void f(MemoryBlock&&)
{
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;
}

int main()
{
   MemoryBlock block;
   f(block);
   f(MemoryBlock());
}
```

В этом примере выводятся следующие данные:

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

В этом примере при первом вызове функции `f` в качестве аргумента передается локальная переменная (значение lvalue). При втором вызове функции `f` в качестве аргумента передается временный объект. Поскольку на временный объект невозможно ссылаться из какого-либо другого места в программе, вызов привязывается к перегруженной версии функции `f`, которая принимает ссылку rvalue и может свободно изменять этот объект.

**Компилятор обрабатывает именованную ссылку rvalue как значение lvalue, а безымянную ссылку rvalue как значение rvalue.**

При создании функции, которая принимает в качестве параметра ссылку rvalue, в теле функции этот параметр обрабатывается как значение lvalue. Компилятор обрабатывает именованную ссылку rvalue как значение lvalue, поскольку на именованный объект возможны ссылки из нескольких частей программы; было бы опасно разрешить нескольким частям программы изменять или удалять ресурсы из этого объекта. Например, если несколько частей программы попытаются переместить ресурсы из одного и того же объекта, только первая часть сможет успешно переместить ресурс.

В следующем примере показана перегруженная функция `g`, принимающая ссылки lvalue и rvalue. Функция `f` принимает ссылку rvalue в качестве своего параметра (именованная ссылка rvalue) и возвращает ссылку rvalue (безымянная ссылка rvalue). При вызове функции `g` из функции `f` механизм разрешения перегрузок выбирает версию `g`, которая принимает ссылку lvalue, так как в теле функции `f` ее параметр рассматривается как значение lvalue. При вызове функции `g` из функции `main` механизм разрешения перегрузок выбирает версию `g`, которая принимает ссылку rvalue, так как функция `f` возвращает ссылку rvalue.

```cpp
// named-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

MemoryBlock&& f(MemoryBlock&& block)
{
   g(block);
   return move(block);
}

int main()
{
   g(f(MemoryBlock()));
}
```

В этом примере выводятся следующие данные:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

В этом примере функция `main` передает значение rvalue в функцию `f`. В теле функции `f` ее именованный параметр рассматривается как значение lvalue. При вызове функции `f` из функции `g` параметр связывается со ссылкой lvalue (первая перегруженная версия функции `g`).

- **Можно привести значение lvalue к ссылке rvalue.**

Функция [стандартной](../standard-library/utility-functions.md#move) библиотеки C's Standard Library позволяет преобразовать объект в ссылку на этот объект. Кроме того, можно использовать ключевое слово **static_cast,** чтобы отбросить lvalue в ссылку на rvalue, как показано в следующем примере:

```cpp
// cast-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

int main()
{
   MemoryBlock block;
   g(block);
   g(static_cast<MemoryBlock&&>(block));
}
```

В этом примере выводятся следующие данные:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**В шаблонах функций выводятся свои типы аргументов шаблона, а затем используются правила сворачивания ссылок.**

Обычно используется шаблон функции, который передает (или *перенаправляет)* свои параметры другой функции. Важно понимать, как работает вывод типа шаблона для шаблонов функций, принимающих ссылки rvalue.

Если аргумент функции является значением rvalue, компилятор считает, что аргумент является ссылкой rvalue. Например, при передаче ссылки rvalue на объект типа `X` в шаблон функции, который принимает в качестве параметра тип `T&&`, логика выведения аргумента шаблона определит, что `T` — это `X`. Поэтому параметр имеет тип `X&&`. Если аргумент функции является lvalue или **const** lvalue, компилятор выводит свой тип как ссылка lvalue или **ссылка на констовую** lvalue этого типа.

В следующем примере объявляется один шаблон структуры, который затем специализируется для различных ссылочных типов. Функция `print_type_and_value` принимает в качестве параметра ссылку rvalue и пересылает ее в соответствующую специализированную версию метода `S::print`. Функция `main` показывает различные способы вызова метода `S::print`.

```cpp
// template-type-deduction.cpp
// Compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

template<typename T> struct S;

// The following structures specialize S by
// lvalue reference (T&), const lvalue reference (const T&),
// rvalue reference (T&&), and const rvalue reference (const T&&).
// Each structure provides a print method that prints the type of
// the structure and its parameter.

template<typename T> struct S<T&> {
   static void print(T& t)
   {
      cout << "print<T&>: " << t << endl;
   }
};

template<typename T> struct S<const T&> {
   static void print(const T& t)
   {
      cout << "print<const T&>: " << t << endl;
   }
};

template<typename T> struct S<T&&> {
   static void print(T&& t)
   {
      cout << "print<T&&>: " << t << endl;
   }
};

template<typename T> struct S<const T&&> {
   static void print(const T&& t)
   {
      cout << "print<const T&&>: " << t << endl;
   }
};

// This function forwards its parameter to a specialized
// version of the S type.
template <typename T> void print_type_and_value(T&& t)
{
   S<T&&>::print(std::forward<T>(t));
}

// This function returns the constant string "fourth".
const string fourth() { return string("fourth"); }

int main()
{
   // The following call resolves to:
   // print_type_and_value<string&>(string& && t)
   // Which collapses to:
   // print_type_and_value<string&>(string& t)
   string s1("first");
   print_type_and_value(s1);

   // The following call resolves to:
   // print_type_and_value<const string&>(const string& && t)
   // Which collapses to:
   // print_type_and_value<const string&>(const string& t)
   const string s2("second");
   print_type_and_value(s2);

   // The following call resolves to:
   // print_type_and_value<string&&>(string&& t)
   print_type_and_value(string("third"));

   // The following call resolves to:
   // print_type_and_value<const string&&>(const string&& t)
   print_type_and_value(fourth());
}
```

В этом примере выводятся следующие данные:

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

Чтобы разрешить каждый вызов функции `print_type_and_value`, компилятор сначала выполняет выведение аргументов шаблона. Затем при подстановке аргументов шаблона, выведенных для типов параметра, компилятор применяет правила сворачивания ссылок. Например, при передаче локальной переменной `s1` в функцию `print_type_and_value` компилятор создает следующую сигнатуру функции:

```cpp
print_type_and_value<string&>(string& && t)
```

Используя правила сворачивания ссылок, компилятор уменьшает сигнатуру до следующей:

```cpp
print_type_and_value<string&>(string& t)
```

Затем эта версия функции `print_type_and_value` пересылает свой параметр в требуемую специализированную версию метода `S::print`.

В следующей таблице приведены правила сворачивания ссылок для выведения типа аргументов шаблонов:

|||
|-|-|
|Развернутый тип|Свернутый тип|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

Вывод аргументов шаблонов — это важный элемент реализации точной пересылки. Более подробно точная пересылка рассматривается выше в подразделе "Точная пересылка" этого раздела.

## <a name="summary"></a>Сводка

Ссылки rvalue различают значения lvalue и rvalue. Они помогают повысить производительность приложений, устраняя необходимость в ненужных операциях выделения памяти и копирования. Они также позволяют создавать одну версию функции, принимающую произвольные аргументы и пересылающую их в другую функцию, как если бы эта другая функция вызывалась напрямую.

## <a name="see-also"></a>См. также раздел

[Выражения с унарными операторами](../cpp/expressions-with-unary-operators.md)<br/>
[Декларатор ссылки Lvalue: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Lvalues и Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Конструкторы перемещения и операторы присваивания перемещением (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Стандартная библиотека СЗ](../standard-library/cpp-standard-library-reference.md)
