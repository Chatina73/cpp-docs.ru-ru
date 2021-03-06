---
description: 'Дополнительные сведения: Директива #using (C++/CLI)'
title: '#Директива using (C++/CLI)'
ms.date: 08/29/2019
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: 5903e3b5af4cd6ee40e0b087d52d1bd0115b1c6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167530"
---
# <a name="using-directive-ccli"></a>Директива #using (C++/CLI)

Импортирует метаданные в программу, скомпилированную с [параметром/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Синтаксис

> **`#using`***File* [ **`as_friend`** ]

### <a name="parameters"></a>Параметры

*File*\
*`.dll`* Файл MSIL, *`.exe`* , *`.netmodule`* или *`.obj`* . например следующие.

`#using <MyComponent.dll>`

**`as_friend`**\
Указывает, что все типы в *файле* доступны. Дополнительные сведения см. в разделе [дружественные сборки (C++)](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Комментарии

*файл* может представлять собой файл MSIL, который импортируется для управляемых данных и управляемых конструкций. Если библиотека DLL содержит манифест сборки, то импортируются все библиотеки DLL, на которые имеются ссылки в манифесте. Сборка, которую вы собираетесь создать, будет содержать *файл* в метаданных как ссылку на сборку.

Возможно, *файл* не содержит сборку (*файл* является модулем), и вы не собираетесь использовать информацию о типах из модуля в текущем приложении (сборка). Можно указать, что модуль является частью сборки с помощью [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). После этого типы из этого модуля будут доступны любому приложению, ссылки на которые содержатся в этой сборке.

Альтернативой для использования **`#using`** является параметр компилятора [/Fu](../build/reference/fu-name-forced-hash-using-file.md) .

сборки. exe, передаваемые в, **`#using`** должны быть скомпилированы с помощью одного из компиляторов .NET Visual Studio (например, Visual Basic или Visual C#).  Попытка импортировать метаданные из exe-сборки, скомпилированной с помощью **`/clr`** , приведет к возникновению исключения загрузки файла.

> [!NOTE]
> Компонент, на который имеется ссылка, **`#using`** может быть запущен с другой версией файла, импортированного во время компиляции, что приводит к непредсказуемым результатам в клиентском приложении.

Чтобы компилятор распознал тип в сборке (а не в модуле), необходимо принудительно разрешить тип. Например, можно принудительно определить экземпляр типа. Существуют и другие способы разрешения имен типов в сборке для компилятора. Например, при наследовании от типа в сборке имя типа будет называться компилятором.

При импорте метаданных, построенных на основе исходного кода, [`__declspec(thread)`](../cpp/thread.md) семантика потока не сохраняется в метаданных. Например, переменная, объявленная с **`__declspec(thread)`** , скомпилирована в программе, созданной для .NET Framework среды CLR, а затем импортирована с помощью **`#using`** , не будет иметь **`__declspec(thread)`** семантику для переменной.

Все импортированные типы (управляемые и собственные) в файле, на который ссылается, **`#using`** доступны, но компилятор обрабатывает собственные типы как объявления, а не определения.

На mscorlib.dll автоматически создается ссылка при компиляции с помощью **`/clr`** .

Переменная среды LIBPATH указывает каталоги для поиска, когда компилятор разрешает имена файлов, переданных в **`#using`** .

Компилятор ищет ссылки по следующему пути:

- Путь, указанный в **`#using`** инструкции.

- Текущий каталог.

- Системный каталог .NET Framework.

- Каталоги, добавленные с помощью [`/AI`](../build/reference/ai-specify-metadata-directories.md) параметра компилятора.

- Каталоги, указанные в переменной среды LIBPATH.

## <a name="examples"></a>Примеры

Можно создать сборку, которая ссылается на вторую сборку, которая сама ссылается на третью сборку. Необходимо явно ссылаться на третью сборку из первой, если вы явно используете один из ее типов.

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

```cpp
// using_assembly_B.cpp
// compile with: /clr /LD
#using "using_assembly_A.dll"
public ref class B {
public:
   void Test(A a) {}
   void Test() {}
};
```

В следующем примере компилятор не сообщает об ошибке, ссылающейся на *using_assembly_A.dll*, поскольку программа не использует типы, определенные в *using_assembly_A. cpp*.

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>См. также раздел

[Директивы препроцессора](../preprocessor/preprocessor-directives.md)
