---
title: 'Оператор разрешения области: ::'
ms.date: 11/04/2016
f1_keywords:
- '::'
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
ms.openlocfilehash: e601bed976009a72a43545d8d38a38d75e93a137
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267398"
---
# <a name="scope-resolution-operator-"></a>Оператор разрешения области: ::

Оператор разрешения области **::** используется для выявления и устранения неоднозначности идентификаторов, которые используются в разных областях. Дополнительные сведения об области см. в разделе [область](../cpp/scope-visual-cpp.md).

## <a name="syntax"></a>Синтаксис

```
:: identifier
class-name :: identifier
namespace :: identifier
enum class :: identifier
enum struct :: identifier
```

## <a name="remarks"></a>Примечания

`identifier` может быть переменной, функцией или значением перечисления.

## <a name="with-classes-and-namespaces"></a>С классами и пространствами имен

В следующем примере показано, каким образом оператор разрешения области используется с пространствами имен и классами:

```cpp
namespace NamespaceA{
    int x;
    class ClassA {
    public:
        int x;
    };
}

int main() {

    // A namespace name used to disambiguate
    NamespaceA::x = 1;

    // A class name used to disambiguate
    NamespaceA::ClassA a1;
    a1.x = 2;
}
```

Оператор разрешения области без квалификатора области применяется к глобальному пространству имен.

```cpp
namespace NamespaceA{
    int x;
}

int x;

int main() {
    int x;

    // the x in main()
    x = 0;
    // The x in the global namespace
    ::x = 1;

    // The x in the A namespace
    NamespaceA::x = 2;
}
```

Оператор разрешения области можно использовать для идентификации члена пространства имен или пространства имен, которое определяет пространство имен члена в директиве using. В примере ниже `NamespaceC` можно использовать для указания `ClassB`, даже если `ClassB` был объявлен в пространстве имен `NamespaceB`, поскольку `NamespaceB` было определено в `NamespaceC` с помощью директивы using.

```cpp
namespace NamespaceB {
    class ClassB {
    public:
        int x;
    };
}

namespace NamespaceC{
    using namespace B;
}
int main() {
    NamespaceB::ClassB c_b;
    NamespaceC::ClassB c_c;

    c_b.x = 3;
    c_c.x = 4;
}
```

Можно использовать цепочки операторов разрешения области. В следующем примере `NamespaceD::NamespaceD1` определяет вложенное пространство имен `NamespaceD1`, а `NamespaceE::ClassE::ClassE1` определяет вложенный класс `ClassE1`.

```cpp
namespace NamespaceD{
    namespace NamespaceD1{
        int x;
    }
}

namespace NamespaceE{
    class ClassE{
    public:
        class ClassE1{
        public:
            int x;
        };
    };
}

int main() {
    NamespaceD:: NamespaceD1::x = 6;
    NamespaceE::ClassE::ClassE1 e1;
    e1.x = 7  ;
}
```

## <a name="with-static-members"></a>Со статическими членами

Оператор разрешения области необходимо использовать для вызова статических членов класса.

```cpp
class ClassG {
public:
    static int get_x() { return x;}
    static int x;
};

int ClassG::x = 6;

int main() {

    int gx1 = ClassG::x;
    int gx2 = ClassG::get_x();
}
```

## <a name="with-scoped-enumerations"></a>С ограниченными перечислениями

Оператор разрешения области также используется со значениями ограниченного перечисления [объявления перечислений](../cpp/enumerations-cpp.md), как показано в следующем примере:

```cpp
enum class EnumA{
    First,
    Second,
    Third
};

int main() {
    EnumA enum_value = EnumA::First;
}
```

## <a name="see-also"></a>См. также

[Встроенные операторы C++, приоритет и ассоциативность](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Пространства имен](../cpp/namespaces-cpp.md)