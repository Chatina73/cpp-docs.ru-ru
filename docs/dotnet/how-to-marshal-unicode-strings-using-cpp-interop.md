---
description: См. Дополнительные сведения о маршалинге строк Юникода с помощью взаимодействия C++.
title: Практическое руководство. Маршалирование строк Юникода с использованием взаимодействия C++
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: 7aa21acc912aafec7d3fccd78f7e9f1ab216ea86
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302521"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Практическое руководство. Маршалирование строк Юникода с использованием взаимодействия C++

В этом разделе демонстрируется один аспект взаимодействия Visual C++. Дополнительные сведения см. [в разделе Использование взаимодействия C++ (неявный PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

В следующих примерах кода используются [управляемые, неуправляемые](../preprocessor/managed-unmanaged.md) директивы #pragma для реализации управляемых и неуправляемых функций в одном и том же файле, но эти функции взаимодействуют одинаково, если они определены в отдельных файлах. Файлы, содержащие только неуправляемые функции, не должны компилироваться с [параметром/CLR (компиляция CLR)](../build/reference/clr-common-language-runtime-compilation.md).

В этом разделе показано, как можно передавать строки Юникода из управляемой функции в неуправляемую, и наоборот. Сведения о взаимодействии с другими типами строк см. в следующих разделах:

- [Инструкции. маршалинг строк ANSI с помощью взаимодействия C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Инструкции. маршалинг строк COM с помощью взаимодействия C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example-pass-unicode-string-from-managed-to-unmanaged-function"></a>Пример. Передача строки в Юникоде из управляемой функции в неуправляемую

Чтобы передать строку Юникода из управляемой функции в неуправляемую, функцию Птртострингчарс (объявленную в Вкклр. h) можно использовать для доступа к памяти, где хранится управляемая строка. Поскольку этот адрес передается в собственную функцию, важно, чтобы память была закреплена с [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) , чтобы предотвратить повторное размещение строковых данных, если выполняется цикл сборки мусора во время выполнения неуправляемой функции.

```cpp
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example-data-marshaling-required-to-access-unicode-string"></a>Пример. для доступа к строке в Юникоде требуется маршалирование данных

В следующем примере показана упаковка данных, необходимая для доступа к строке Юникода в управляемой функции, вызываемой неуправляемой функцией. Управляемая функция, получающая собственную строку в Юникоде, преобразует ее в управляемую строку с помощью <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> метода.

```cpp
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>См. также раздел

[Использование взаимодействия C++ (неявный PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
