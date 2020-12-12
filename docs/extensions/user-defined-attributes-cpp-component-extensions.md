---
description: 'Дополнительные сведения: атрибуты User-Defined (C++/CLI и C++/CX)'
title: Пользовательские атрибуты (C++/CLI и C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: 2fab2cc1317522b43cd4bddbb56ae174907607d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327896"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>Пользовательские атрибуты (C++/CLI и C++/CX)

C++/CLI и C++/CX позволяют вам создать специфические для платформы атрибуты, которые расширяют метаданные интерфейса, класса или структуры, метода, параметра или перечисления. Эти атрибуты отличаются от [стандартных атрибутов C++](../cpp/attributes.md).

## <a name="windows-runtime"></a>Среда выполнения Windows

Вы можете применить атрибуты C++/CX к свойствам, но не к конструкторам или методам.

### <a name="requirements"></a>Требования

Параметр компилятора: `/ZW`

## <a name="common-language-runtime"></a>Среда CLR

Сведения и синтаксис, представленные в этом разделе, заменяют сведения, приведенные в статье [attribute](../windows/attributes/attribute.md).

Настраиваемый атрибут можно определить, указав тип и создав для него базовый класс <xref:System.Attribute>, а также при необходимости применив атрибут <xref:System.AttributeUsageAttribute>.

Дополнительные сведения см. в разделе:

- [Целевые объекты атрибутов](attribute-targets-cpp-component-extensions.md)

- [Типы параметров атрибутов](attribute-parameter-types-cpp-component-extensions.md)

Сведения о подписывании сборок в проектах Visual C++ см. в статье [Strong Name Assemblies (Assembly Signing) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) (Сборки со строгими именами (подписывание сборок) (C++/CLI)).

### <a name="requirements"></a>Требования

Параметр компилятора: `/clr`

### <a name="examples"></a>Примеры

В следующем примере показано определение настраиваемого атрибута.

```cpp
// user_defined_attributes.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};
```

В приведенном ниже примере продемонстрированы некоторые важные функции настраиваемых атрибутов. Например, в нем показано общее использование настраиваемых атрибутов: создание экземпляра сервера, который может полностью представлять свои характеристики клиентам.

```cpp
// extending_metadata_b.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

public enum class Access { Read, Write, Execute };

// Defining the Job attribute:
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]
public ref class Job : Attribute {
public:
   property int Priority {
      void set( int value ) { m_Priority = value; }
      int get() { return m_Priority; }
   }

   // You can overload constructors to specify Job attribute in different ways
   Job() { m_Access = Access::Read; }
   Job( Access a ) { m_Access = a; }
   Access m_Access;

protected:
   int m_Priority;
};

interface struct IService {
   void Run();
};

   // Using the Job attribute:
   // Here we specify that QueryService is to be read only with a priority of 2.
   // To prevent namespace collisions, all custom attributes implicitly
   // end with "Attribute".

[Job( Access::Read, Priority=2 )]
ref struct QueryService : public IService {
   virtual void Run() {}
};

// Because we said AllowMultiple=true, we can add multiple attributes
[Job(Access::Read, Priority=1)]
[Job(Access::Write, Priority=3)]
ref struct StatsGenerator : public IService {
   virtual void Run( ) {}
};

int main() {
   IService ^ pIS;
   QueryService ^ pQS = gcnew QueryService;
   StatsGenerator ^ pSG = gcnew StatsGenerator;

   //  use QueryService
   pIS = safe_cast<IService ^>( pQS );

   // use StatsGenerator
   pIS = safe_cast<IService ^>( pSG );

   // Reflection
   MemberInfo ^ pMI = pIS->GetType();
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);

   // We can now quickly and easily view custom attributes for an
   // Object through Reflection */
   for( int i = 0; i < pObjs->Length; i++ ) {
      Console::Write("Service Priority = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);
      Console::Write("Service Access = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);
   }
}
```

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

Тип `Object^` заменяет тип данных variant. В следующем примере определяется настраиваемый атрибут, который принимает массив `Object^` в качестве параметров.

Аргументы атрибута должны быть константами времени компиляции; в большинстве случаев они должны быть константными литералами.

Сведения о возврате значения типа System::Type из блока настраиваемых атрибутов см. в статье [typeid (C++/CLI and C++/CX)](typeid-cpp-component-extensions.md).

```cpp
// extending_metadata_e.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]
public ref class AnotherAttr : public Attribute {
public:
   AnotherAttr(array<Object^>^) {}
   array<Object^>^ var1;
};

// applying the attribute
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]
public ref class SomeClass {};
```

Среда выполнения требует, чтобы открытая часть класса настраиваемого атрибута была сериализуемой.  При создании настраиваемых атрибутов их именованные аргументы ограничены константами времени компиляции.  (Можно сказать, что к макету класса в метаданных добавляется последовательность битов.)

```cpp
// extending_metadata_f.cpp
// compile with: /clr /c
using namespace System;
ref struct abc {};

[AttributeUsage( AttributeTargets::All )]
ref struct A : Attribute {
   A( Type^ ) {}
   A( String ^ ) {}
   A( int ) {}
};

[A( abc::typeid )]
ref struct B {};
```

## <a name="see-also"></a>См. также раздел

[Расширения компонентов для .NET и UWP](component-extensions-for-runtime-platforms.md)
