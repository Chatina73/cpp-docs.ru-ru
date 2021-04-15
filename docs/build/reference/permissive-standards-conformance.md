---
title: /permissive- (соответствие стандартам)
description: Справочное руководство по параметру компилятора Microsoft C++/permissive-(соответствие стандартам).
ms.date: 10/28/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: ab6f1a088ae45e1098a02d2ab0bdf18d6bc8047c
ms.sourcegitcommit: aaab04df80e2d00389c13b075cfac59afc7f4681
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107467643"
---
# <a name="permissive--standards-conformance"></a>/permissive- (соответствие стандартам)

Укажите режим соответствия стандартам для компилятора. Используйте этот параметр, чтобы определить и исправить проблемы соответствия в коде, чтобы сделать его более правильным и переносимым.

## <a name="syntax"></a>Синтаксис

> **`/permissive-`**\
> **`/permissive`**

## <a name="remarks"></a>Remarks

Этот **`/permissive-`** параметр поддерживается в Visual Studio 2017 и более поздних версиях. **`/permissive`** поддерживается в Visual Studio 2019 версии 16,8 и более поздних версиях.

Параметр компилятора можно использовать **`/permissive-`** для указания стандартных стандартов поведения компилятора. Этот параметр отключает разрешающее поведение и задает [`/Zc`](zc-conformance.md) параметры компилятора для более строгего соответствия. В интегрированной среде разработки этот параметр также делает подчеркивание подсистемой IntelliSense несогласованным кодом.

**`/permissive-`** Параметр использует поддержку соответствия в текущей версии компилятора, чтобы определить, какие языковые конструкции не являются согласованными. Параметр не определяет, соответствует ли код определенной версии стандарта C++. Чтобы включить поддержку всех реализованных компиляторов для последнего чернового стандарта, используйте [`/std:c++latest`](std-specify-language-standard-version.md) параметр. Чтобы ограничить поддержку компилятора на текущий реализованный стандарт C++ 17, используйте [`/std:c++17`](std-specify-language-standard-version.md) параметр. Чтобы обеспечить более точное соответствие поддержки компилятора стандарту C++ 14, используйте [`/std:c++14`](std-specify-language-standard-version.md) параметр, который является значением по умолчанию.

Начиная с Visual Studio 2019 версии 16,8, **`/std:c++latest`** параметр неявно задает **`/permissive-`** параметр. Он необходим для поддержки модулей C++ 20. Возможно, ваш код не нуждается в поддержке модулей, но для него требуется включить другие функции **`/std:c++latest`** . Можно явно включить поддержку расширений Майкрософт, используя **`/permissive`** параметр без дефиса в конце.

По умолчанию этот **`/permissive-`** параметр задается в новых проектах, созданных Visual Studio 2017 версии 15,5 и более поздних версий. В более ранних версиях он не задан по умолчанию. Если задан параметр, компилятор создает диагностические ошибки или предупреждения при обнаружении нестандартных языковых конструкций в коде. Эти конструкции включают в себя некоторые распространенные ошибки в коде pre-C + + 11.

**`/permissive-`** Параметр совместим с практически всеми файлами заголовков из последних комплектов Windows, таких как пакет средств разработки программного обеспечения (SDK) или Windows Driver Kit (WDK), начиная с пакета SDK для дизайнеров Windows (10.0.16299.0). Более старые версии пакета SDK могут не компилироваться в соответствии с **`/permissive-`** различными причинами соответствия исходного кода. Компилятор и пакеты SDK поставляются на разных временных шкалах выпуска, поэтому существуют некоторые другие проблемы. Конкретные проблемы с файлами заголовков см. ниже в разделе [проблемы с заголовком Windows](#windows-header-issues) .

**`/permissive-`** Параметр задает [`/Zc:referenceBinding`](zc-referencebinding-enforce-reference-binding-rules.md) [`/Zc:strictStrings`](zc-strictstrings-disable-string-literal-type-conversion.md) Параметры, и [`/Zc:rvalueCast`](zc-rvaluecast-enforce-type-conversion-rules.md) для согласования поведения. Эти параметры по умолчанию имеют несогласованное поведение. **`/Zc`** Чтобы переопределить это поведение, можно передать определенные параметры после **`/permissive-`** в командной строке.

В версиях компилятора, начиная с Visual Studio 2017 версии 15,3, **`/permissive-`** параметр задает [`/Zc:ternary`](zc-ternary.md) параметр. Компилятор также реализует больше требований к состановке имен с двумя этапами. Если **`/permissive-`** задан параметр, компилятор анализирует определения шаблонов функций и классов и определяет зависимые и независимые имена, используемые в шаблонах. В этом выпуске выполняется только анализ зависимостей имен.

Расширения и языковые области, зависящие от среды, которые не затрагиваются стандартом **`/permissive-`** . Например, ключевые слова, связанные с корпорацией Майкрософт **`__declspec`** , соглашением о вызовах и структурированной обработкой исключений, а также директивы pragma или атрибуты, относящиеся к компилятору, не помечаются компилятором в **`/permissive-`** режиме.

Не все стандарты C++ 11, C++ 14 или C++ 17 поддерживаются компилятором КОМПИЛЯТОРОМ MSVC во всех версиях Visual Studio 2017. В зависимости от версии Visual Studio **`/permissive-`** параметр может не обнаруживать проблемы в некоторых аспектах поиска имен с двумя этапами, привязывая неконстантную ссылку на временную, рассматривая копию в качестве прямой инициализации, что позволяет использовать несколько пользовательских преобразований в инициализации или альтернативные маркеры для логических операторов, а также другие неподдерживаемые области соответствия. Дополнительные сведения о вопросах соответствия в Visual C++ см. в статье [Nonstandard Behavior](../../cpp/nonstandard-behavior.md). Чтобы максимально эффективно воспользоваться **`/permissive-`** , обновите Visual Studio до последней версии.

### <a name="how-to-fix-your-code"></a>Как исправить код

Ниже приведены примеры кода, который определяется как несогласованный при использовании **`/permissive-`** , а также предлагаются способы устранения проблем.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Использовать значение по умолчанию в качестве идентификатора в машинном коде

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Поиск элементов в зависимом базовом

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>Использование полных имен в объявлениях членов

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Инициализация нескольких членов Union в инициализаторе члена

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>Правила поиска скрытых дружественных имен

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(p); // Hidden friend now found via argument-dependent lookup.
}
```

Вы можете включить правила поиска скрытых дружественных имен независимо от с **`/permissive`** помощью [`/Zc:hiddenFriend`](./zc-hiddenfriend.md) . Если вы хотите использовать устаревшее поведение для поиска скрытого дружественного имени, но в ином случае требуется **`/permissive-`** поведение, используйте **`/Zc:hiddenFriend-`** параметр.

#### <a name="use-scoped-enums-in-array-bounds"></a>Использование перечислений с областью действия в границах массива

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Использование for each в машинном коде

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>Использование атрибутов ATL

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be
// used to automatically obtain a *.idl file for the interfaces with
// annotation. Second, add a midl step to your build system to make
// sure that the C++ interface definitions are outputted.
// Last, adjust your existing code to use ATL directly as shown in
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>Неоднозначные аргументы условного оператора

В версиях компилятора перед Visual Studio 2017 версии 15,3 компилятор принимает аргументы в условный оператор (или оператор ternary) `?:` , который считается неоднозначным по стандарту. В **`/permissive-`** режиме компилятора теперь выдается одна или несколько диагностических сведений в случаях, скомпилированных без диагностики в более ранних версиях.

Ниже перечислены распространенные ошибки, которые могут быть результатом этого изменения.

- `error C2593: 'operator ?' is ambiguous`

- `error C2679: binary '?': no operator found which takes a right-hand operand of type 'B' (or there is no acceptable conversion)`

- `error C2678: binary '?': no operator found which takes a left-hand operand of type 'A' (or there is no acceptable conversion)`

- `error C2446: ':': no conversion from 'B' to 'A'`

Типичный шаблон кода, который может вызвать эту неполадку, заключается в том, что некоторый класс C предоставляет как неявный конструктор из другого типа T, так и оператор неявного преобразования для типа T. В этом случае преобразование второго аргумента в тип третьего аргумента и преобразование третьего аргумента в тип второго аргумента являются допустимыми преобразованиями. Так как оба значения являются допустимыми, они являются неоднозначными в соответствии со стандартом.

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

Существует важное исключение для этого общего шаблона, когда T представляет один из строковых типов, завершающихся нулем (например,, `const char *` `const char16_t *` и т. д.), а фактический аргумент `?:` — это строковый литерал соответствующего типа. В c++ 17 была изменена семантика с C++ 14. В результате код в примере 2 принимается **`/std:c++14`** и отклоняется **`/std:c++17`** при **`/Zc:ternary`** **`/permissive-`** использовании или.

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s;
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

Другой случай, когда ошибки могут возникнуть в условных операторах с одним аргументом типа **`void`** . Этот вариант может быть распространен в макросах, подобных УТВЕРЖДЕНию.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Вы также можете увидеть ошибки в шаблоне метапрограммирование, где типы результата условного оператора могут измениться в **`/Zc:ternary`** и **`/permissive-`** . Одним из способов устранения этой проблемы является использование [`std::remove_reference`](../../standard-library/remove-reference-class.md) в результирующем типе.

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Два этапа поиска имен

Если **`/permissive-`** задан параметр, компилятор анализирует определения шаблонов функций и классов, определяя зависимые и независимые имена, используемые в шаблонах в соответствии с требованиями для поиска имен с двумя этапами. В Visual Studio 2017 версии 15,3 выполняется анализ зависимостей имен. В частности, независимые имена, не объявленные в контексте определения шаблона, вызывают диагностическое сообщение согласно требованиям стандартов ISO C++. В Visual Studio 2017 версии 15,7 привязка независимых имен, требующих от аргумента поиска в контексте определения, также выполняется.

```cpp
// dependent base
struct B {
    void g() {}
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

Если требуется использовать устаревшее поведение для двухэтапного поиска, но в противном случае необходимо **`/permissive-`** Добавить **`/Zc:twoPhase-`** параметр.

### <a name="windows-header-issues"></a>Проблемы с заголовком Windows

**`/permissive-`** Параметр слишком велик для версий комплектов Windows, предшествующих пакету SDK обновления Windows (10.0.16299.0) или Windows Driver Kit (WDK) версии 1709. Мы рекомендуем выполнить обновление до последних версий комплектов Windows для использования **`/permissive-`** в коде драйвера Windows или устройства.

Некоторые файлы заголовков в пакете SDK для Windows от апреля 2018 с обновлением (10.0.17134.0), пакет SDK для дизайнеров Windows (10.0.16299.0) или набор драйверов Windows (WDK) 1709, по-прежнему имеют проблемы, которые делают их несовместимыми с использованием **`/permissive-`** . Чтобы обойти эти проблемы, рекомендуется ограничить использование этих заголовков только теми файлами исходного кода, которые им требуются, и удалить **`/permissive-`** параметр при компиляции этих файлов исходного кода.

Эти заголовки WRL WinRT, выпущенные в пакете SDK для обновлений Windows от апреля 2018 (10.0.17134.0), не удаляются вместе с **`/permissive-`** . Чтобы обойти эти проблемы, либо не используйте **`/permissive-`** , либо используйте **`/permissive-`** WITH **`/Zc:twoPhase-`** при работе с этими заголовками:

- Проблемы в WinRT/WRL/Async. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Проблемы в WinRT/WRL/Implements. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Эти заголовки пользовательского режима, выпущенные в пакете SDK для обновления Windows от апреля 2018 (10.0.17134.0), не удаляются вместе с **`/permissive-`** . Чтобы обойти эти проблемы, не используйте **`/permissive-`** при работе с этими заголовками:

- Проблемы в UM/настройке. h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Проблемы в UM/спддкхлп. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Проблемы в UM/рефптрко. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Эти проблемы относятся к заголовкам пользовательского режима в пакете SDK обновления Windows для дизайнеров (10.0.16299.0):

- Проблемы в UM/Query. h

   При использовании **`/permissive-`**  параметра компилятора `tagRESTRICTION` структура не компилируется из-за варианта (рТор) члена или.

   ```cpp
   struct tagRESTRICTION
   {
       ULONG rt;
       ULONG weight;
       /* [switch_is][switch_type] */ union _URes
       {
           /* [case()] */ NODERESTRICTION ar;
           /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
           /* [case()] */ NODERESTRICTION pxr;
           /* [case()] */ VECTORRESTRICTION vr;
           /* [case()] */ NOTRESTRICTION nr;
           /* [case()] */ CONTENTRESTRICTION cr;
           /* [case()] */ NATLANGUAGERESTRICTION nlr;
           /* [case()] */ PROPERTYRESTRICTION pr;
           /* [default] */  /* Empty union arm */
       } res;
   };
   ```

   Чтобы устранить эту ошибку, Скомпилируйте файлы, содержащие Query. h, без **`/permissive-`** параметра.

- Проблемы в UM/cellularapi_oem. h

   При использовании **`/permissive-`**  параметра компилятора прямая декларация `enum UICCDATASTOREACCESSMODE` вызывает предупреждение:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   Прямым объявлением неограниченного перечисления является расширение Майкрософт. Чтобы устранить эту ошибку, Скомпилируйте файлы, содержащие cellularapi_oem. h, без **`/permissive-`** параметра или используйте [`/wd`](compiler-option-warning-level.md) параметр для бездействия предупреждения C4471.

- Проблемы в UM/омскрипт. h

   В C++ 03 преобразование строкового литерала в BSTR (typedef для "wchar_t *") является нерекомендуемым, но допустимым. В C++ 11 преобразование больше не разрешено.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Чтобы устранить эту ошибку, Скомпилируйте файлы, содержащие омскрипт. h, без **`/permissive-`** параметра или используйте **`/Zc:strictStrings-`** вместо него.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

В Visual Studio 2017 версии 15,5 и более поздних версиях используйте следующую процедуру:

1. Откройте диалоговое окно **страницы свойств** проекта.

1. Перейдите на   >  страницу свойств языка **C/C++**  >  **Language** .

1. Измените значение свойства **режим соответствия** на **Да (/permissive-)**. Нажмите кнопку **ОК** или **Применить** , чтобы сохранить изменения.

В версиях до Visual Studio 2017 версии 15,5 Используйте следующую процедуру:

1. Откройте диалоговое окно **страницы свойств** проекта.

1. Выберите страницу свойств **Свойства конфигурации**  >  **C/C++**  >  **Командная строка** .

1. В поле **Дополнительные параметры** введите параметр компилятора **/permissive-** . Нажмите кнопку **ОК** или **Применить** , чтобы сохранить изменения.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора MSVC](compiler-options.md)\
[Синтаксис командной строки компилятора MSVC](compiler-command-line-syntax.md)
