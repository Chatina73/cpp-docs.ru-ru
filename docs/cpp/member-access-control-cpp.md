---
description: 'Дополнительные сведения: Управление доступом к членам (C++)'
title: Управление доступом к членам (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: 2cce7cb98e76098f3c20a6c2404f91ccf40db1cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206881"
---
# <a name="member-access-control-c"></a>Управление доступом к членам (C++)

Элементы управления доступом позволяют разделять [открытый](../cpp/public-cpp.md) интерфейс класса от [закрытых](../cpp/private-cpp.md) деталей реализации и [защищенных](../cpp/protected-cpp.md) членов, которые используются только производными классами. Спецификатор доступа действует для всех членов, объявленных после него, пока не будет объявлен следующий спецификатор доступа.

```cpp
class Point
{
public:
    Point( int, int ) // Declare public constructor.;
    Point();// Declare public default constructor.
    int &x( int ); // Declare public accessor.
    int &y( int ); // Declare public accessor.

private:                 // Declare private state variables.
    int _x;
    int _y;

protected:      // Declare protected function for derived classes only.
    Point ToWindowCoords();
};
```

По умолчанию доступ осуществляется **`private`** в классе, **`public`** в структуре или объединении. Спецификаторы доступа класса могут использоваться любое количество раз и в любом порядке. Выделение хранилища для объектов типов классов зависит от реализации, но членам гарантировано присваиваются старшие адреса памяти, расположенные подряд между описателями доступа.

## <a name="member-access-control"></a>Управление доступом к членам

|Тип доступа|Значение|
|--------------------|-------------|
|[private](../cpp/private-cpp.md)|Члены класса, объявленные как, **`private`** могут использоваться только функциями-членами и друзьями (классами или функциями) класса.|
|[protected](../cpp/protected-cpp.md)|Члены класса, объявленные как, **`protected`** могут использоваться функциями-членами и друзьями (классами или функциями) класса. Кроме того, они могут использоваться производными классами данного класса.|
|[public](../cpp/public-cpp.md)|Члены класса, объявленные как, **`public`** могут использоваться любой функцией.|

Управление доступом помогает предотвратить использование объектов в неправомерных целях. Такая защита теряется при выполнении явных преобразований типов (приведении типов).

> [!NOTE]
> Управление доступом одинаково применимо ко всем именам: функциям-членам, данным члена, вложенным классам и перечислителям.

## <a name="access-control-in-derived-classes"></a>Управление доступом в производном классе

Доступность в производном классе членов базового класса и унаследованных членов определяется двумя следующими факторами.

- Объявляет ли производный класс базовый класс с помощью **`public`** описателя доступа.

- Какой доступ к членам предоставляется в базовом классе.

В следующей таблице показана взаимосвязь между этими факторами и определен доступ к членам в базовом классе.

### <a name="member-access-in-base-class"></a>Доступ к членам в базовом классе

|private|protected|Открытый|
|-------------|---------------|------------|
|Всегда отсутствует независимо от доступа при наследовании|Закрытый в производном классе при использовании закрытого наследования|Закрытый в производном классе при использовании закрытого наследования|
||Защищенный в производном классе при использовании защищенного наследования|Защищенный в производном классе при использовании защищенного наследования|
||Защищенный в производном классе при использовании открытого наследования|Открытый в производном классе при использовании открытого наследования|

Проиллюстрируем это на примере.

```cpp
// access_specifiers_for_base_classes.cpp
class BaseClass
{
public:
    int PublicFunc(); // Declare a public member.
protected:
    int ProtectedFunc(); // Declare a protected member.
private:
    int PrivateFunc(); // Declare a private member.
};

// Declare two classes derived from BaseClass.
class DerivedClass1 : public BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

class DerivedClass2 : private BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

int main()
{
    DerivedClass1 derived_class1;
    DerivedClass2 derived_class2;
    derived_class1.PublicFunc();
    derived_class2.PublicFunc(); // function is inaccessible
}
```

В классе `DerivedClass1` функция-член `PublicFunc` является открытым членом, а функция `ProtectedFunc` — защищенным членом, поскольку `BaseClass` — открытый базовый класс. Функция `PrivateFunc` закрыта для класса `BaseClass` и не доступна всем производным классам.

В классе `DerivedClass2` функции `PublicFunc` и `ProtectedFunc` считаются закрытыми членами, поскольку `BaseClass` — закрытый базовый класс. Функция `PrivateFunc` снова закрыта для класса `BaseClass` и не доступна всем производным классам.

Производный класс можно объявить без спецификатора доступа базового класса. В этом случае наследование считается закрытым, если в объявлении производного класса используется **`class`** ключевое слово. Наследование считается открытым, если в объявлении производного класса используется **`struct`** ключевое слово. Например, приведенный ниже код

```cpp
class Derived : Base
...
```

эквивалентно правилу

```cpp
class Derived : private Base
...
```

Аналогично код

```cpp
struct Derived : Base
...
```

эквивалентно правилу

```cpp
struct Derived : public Base
...
```

Обратите внимание, что члены, объявленные как имеющие закрытый доступ, недоступны для функций или производных классов, если эти функции или классы не объявлены с помощью **`friend`** объявления в базовом классе.

**`union`** Тип не может иметь базовый класс.

> [!NOTE]
> При указании закрытого базового класса рекомендуется явно использовать **`private`** ключевое слово, чтобы пользователи производного класса могли понимать доступ к членам.

## <a name="access-control-and-static-members"></a>Управление доступом и статические члены

Если базовый класс указан как **`private`** , он влияет только на нестатические члены. Открытые статические члены по-прежнему доступны в производных классах. Однако доступ к членам базового класса с помощью указателей, ссылок и объектов может потребовать преобразования, а во время выполнения управление доступом применяется снова. Рассмотрим следующий пример.

```cpp
// access_control.cpp
class Base
{
public:
    int Print();             // Nonstatic member.
    static int CountOf();    // Static member.
};

// Derived1 declares Base as a private base class.
class Derived1 : private Base
{
};
// Derived2 declares Derived1 as a public base class.
class Derived2 : public Derived1
{
    int ShowCount();    // Nonstatic member.
};
// Define ShowCount function for Derived2.
int Derived2::ShowCount()
{
   // Call static member function CountOf explicitly.
    int cCount = Base::CountOf();     // OK.

   // Call static member function CountOf using pointer.
    cCount = this->CountOf();  // C2247. Conversion of
                               //  Derived2 * to Base * not
                               //  permitted.
    return cCount;
}
```

В предыдущем примере кода управление доступом запрещает преобразование указателя на `Derived2` к указателю на `Base`. **`this`** Указатель неявно имеет тип `Derived2 *` . Чтобы выбрать `CountOf` функцию, **`this`** необходимо преобразовать ее в тип `Base *` . Такое преобразование не поддерживается, поскольку `Base` — это закрытый косвенный базовый класс в `Derived2`. Преобразование к типу закрытого базового класса применимо только для указателей на непосредственные производные классы. Поэтому указатели типа `Derived1 *` можно преобразовать к типу `Base *`.

Обратите внимание, что при явном вызове функции `CountOf` без использования указателя, ссылки или объекта для выделения этой функции, преобразование не выполняется. Поэтому вызов разрешен.

Члены и дружественные функции производного класса, `T`, могут преобразовать указатель на `T` в указатель на частный прямой базовый класс `T`.

## <a name="access-to-virtual-functions"></a>Доступ к виртуальным функциям

Управление доступом к [виртуальным](../cpp/virtual-cpp.md) функциям определяется типом, используемым для выполнения вызова функции. Переопределение объявлений функции не влияет на управление доступом для данного типа. Пример:

```cpp
// access_to_virtual_functions.cpp
class VFuncBase
{
public:
    virtual int GetState() { return _state; }
protected:
    int _state;
};

class VFuncDerived : public VFuncBase
{
private:
    int GetState() { return _state; }
};

int main()
{
   VFuncDerived vfd;             // Object of derived type.
   VFuncBase *pvfb = &vfd;       // Pointer to base type.
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.
   int State;

   State = pvfb->GetState();     // GetState is public.
   State = pvfd->GetState();     // C2248 error expected; GetState is private;
}
```

В приведенном выше примере вызов виртуальной функции `GetState` с помощью указателя на тип `VFuncBase` приводит к вызову функции `VFuncDerived::GetState`, и функция `GetState` обрабатывается как открытая. Однако вызов `GetState` с помощью указателя на тип `VFuncDerived` нарушает правила управления доступом, поскольку функция `GetState` в классе `VFuncDerived` объявляется закрытой.

> [!CAUTION]
> Виртуальную функцию `GetState` можно вызвать с помощью указателя на базовый класс `VFuncBase`. Это не означает, что вызываемая функция является версией базового класса данной функции.

## <a name="access-control-with-multiple-inheritance"></a>Управление доступом с множественным наследованием

В решетках множественного наследования, в которых используются виртуальные базовые классы, к конкретным именам можно обращаться несколькими путями. Поскольку в разных путях могут применяться разные средства управления доступом, компилятор выбирает тот путь, который позволяет получить наиболее широкий доступ. См. следующий рисунок.

![Доступ вдоль линий графа наследования](../cpp/media/vc38v91.gif "Доступ вдоль линий графа наследования") <br/>
Доступ вдоль линий графа наследования

На этом рисунке обращение к имени, которое было объявлено в классе `VBase`, всегда будет выполняться через класс `RightPath`. Путь справа дает более широкий доступ, поскольку в `RightPath` класс `VBase` объявлен как общедоступный базовый, а в `LeftPath` класс `VBase` объявлен как закрытый.

## <a name="see-also"></a>См. также

[Справочник по языку C++](../cpp/cpp-language-reference.md)
