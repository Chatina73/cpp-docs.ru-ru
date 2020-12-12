---
description: Дополнительные сведения о платформах, пространствах имен по умолчанию и интерфейсах CLI (C++/CLI и C++/CX)
title: Пространства имен Platform, default и cli (C++/CLI и C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: 1b4b47a1568b1a137bc49a09b8b50feb8ec3a76b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185678"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>Пространства имен Platform, default и cli (C++/CLI и C++/CX)

Пространство имен определяет имена языковых элементов таким образом, чтобы они не конфликтовали с именами в других частях исходного кода, которые в противном случае считались бы идентичными. Например, конфликты имен могут не дать компилятору распознать [контекстно-зависимые ключевые слова](context-sensitive-keywords-cpp-component-extensions.md). Пространства имен используются компилятором, но не сохраняются в скомпилированной сборке.

## <a name="all-runtimes"></a>Все среды выполнения

При создании проекта Visual Studio предоставляет для него пространство имен по умолчанию. Вы можете вручную переименовать пространство имен, хотя в C++/CX имя WINMD-файла должно соответствовать имени корневого пространства имен.

## <a name="windows-runtime"></a>Среда выполнения Windows

Подробные сведения см. в статье [Namespaces and type visibility (C++/CX)](../cppcx/namespaces-and-type-visibility-c-cx.md) (Пространства имен и видимость типов (C++/CX )).

### <a name="requirements"></a>Требования

Параметр компилятора: `/ZW`

## <a name="common-language-runtime"></a>Среда CLR

### <a name="syntax"></a>Синтаксис

```cpp
using namespace cli;
```

### <a name="remarks"></a>Remarks

C++/CLI поддерживает пространство имен **cli**. При компиляции с `/clr` **`using`** инструкция подразумевается в разделе синтаксиса.

Следующие возможности языка находятся в пространстве имен **cli**:

- [Массивы](arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Требования

Параметр компилятора: `/clr`

### <a name="examples"></a>Примеры

В следующем примере кода показано, что можно использовать символ в пространстве имен **cli** в качестве определяемого пользователем символа в коде.  Однако после этого необходимо будет явно или неявно определить ссылки на языковой элемент **cli** с таким же именем.

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>См. также раздел

[Расширения компонентов для .NET и UWP](component-extensions-for-runtime-platforms.md)
