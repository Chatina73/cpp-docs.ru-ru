---
title: Явные переопределения (C + +/ CLI и C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: 54f3d50b3a47890e6f3dd68c41832fa3d1e13e59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459830"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>Явные переопределения (C + +/ CLI и C + +/ CX)

В этом разделе описывается явно переопределить член базового класса или интерфейса. Именованное переопределение (явно) должен использоваться только для переопределения одного метода производном методе отличается от имени.

## <a name="all-runtimes"></a>Все среды выполнения

### <a name="syntax"></a>Синтаксис

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Параметры

*Переопределение функция декларатор*<br/>
Возвращаемый тип, имя и аргумент список переопределяющая функция.  Обратите внимание, что переопределяющая функция не обязательно иметь имя, совпадающее с именем переопределяемой функции.

*type*<br/>
Базовый тип, содержащий функцию для переопределения.

*function*<br/>
Разделенный запятыми список один или несколько имен функций для переопределения.

*Переопределение function-definition*<br/>
Операторы тело функции, которые определяют переопределяющая функция.

### <a name="remarks"></a>Примечания

Чтобы создать псевдоним для сигнатуры метода, или можно определить разные реализации для методов witht такой же сигнатурой следует использовать явные переопределения.

Сведения об изменении поведение унаследованных типов и наследуемые члены типа, см. в разделе [спецификаторы переопределения](../windows/override-specifiers-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Среда выполнения Windows

### <a name="requirements"></a>Требования

Параметр компилятора: `/ZW`

## <a name="common-language-runtime"></a>Среда CLR

### <a name="remarks"></a>Примечания

Сведения о явных переопределений в машинный код или код компилируется с `/clr:oldSyntax`, см. в разделе [явное переопределение](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Требования

Параметр компилятора: `/clr`

### <a name="examples"></a>Примеры

В следующем примере кода показан простой, неявное override и реализацию члена в базовый интерфейс, неиспользование явного переопределения.

```cpp
// explicit_override_1.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
}
```

```Output
X::f override of I1::f
```

В следующем примере кода показано, как реализовать все элементы интерфейса распространенных подписью, используя синтаксис явного переопределения.

```cpp
// explicit_override_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

interface struct I2 {
   virtual void f();
};

ref struct X : public I1, I2 {
   virtual void f() = I1::f, I2::f {
      System::Console::WriteLine("X::f override of I1::f and I2::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   I2 ^ MyI2 = gcnew X;
   MyI -> f();
   MyI2 -> f();
}
```

```Output
X::f override of I1::f and I2::f
X::f override of I1::f and I2::f
```

В следующем примере кода показано, как переопределения функции могут иметь другое имя из функции, которое он реализует.

```cpp
// explicit_override_3.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void g() = I1::f {
      System::Console::WriteLine("X::g");
   }
};

int main() {
   I1 ^ a = gcnew X;
   a->f();
}
```

```Output
X::g
```

В следующем примере кода показана реализация явный интерфейс, реализующий безопасный тип коллекции.

```cpp
// explicit_override_4.cpp
// compile with: /clr /LD
using namespace System;
ref class R : ICloneable {
   int X;

   virtual Object^ C() sealed = ICloneable::Clone {
      return this->Clone();
   }

public:
   R() : X(0) {}
   R(int x) : X(x) {}

   virtual R^ Clone() {
      R^ r = gcnew R;
      r->X = this->X;
      return r;
   }
};
```

## <a name="see-also"></a>См. также

[Расширения компонентов для .NET и UWP](../windows/component-extensions-for-runtime-platforms.md)