---
title: Ошибка компилятора C3861
ms.date: 03/23/2018
f1_keywords:
- C3861
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
ms.openlocfilehash: 4ebfd3b0129e25cf543cac803a3b33fb074f3d70
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302417"
---
# <a name="compiler-error-c3861"></a>Ошибка компилятора C3861

> "*идентификатор*": идентификатор не найден

Компилятору не удалось разрешить ссылку на идентификатор даже при поиске с зависимостью от аргументов.

## <a name="remarks"></a>Примечания

Чтобы устранить эту ошибку, сравните использование *идентификатор* на написание и регистр объявления идентификатора. Убедитесь, что [операторов разрешения области](../../cpp/scope-resolution-operator.md) и пространство имен [директив using](../../cpp/namespaces-cpp.md#using_directives) используются правильно. Если идентификатор объявлен в файле заголовка, убедитесь, что заголовок включен до ссылки на идентификатор. Если идентификатор должен быть видимый извне, убедитесь, что он объявлен в все файлы исходного кода, который его использует. Также проверьте, что идентификатор объявления или определения не исключен с [директивы условной компиляции](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

Изменения, чтобы удалить устаревшие функции из библиотеки времени выполнения C в Visual Studio 2015 может привести к C3861. Чтобы устранить эту ошибку, удалите ссылки на эти функции или замените их безопасных альтернатив, если таковые имеются. Дополнительные сведения см. в разделе [устаревшие функции](../../c-runtime-library/obsolete-functions.md).

При появлении ошибки C3861 после миграции проекта из более старой версии компилятора, возможно, возникли проблемы, связанные с поддерживаемыми версиями Windows. Visual C++ больше не поддерживает создание программ для Windows 95, Windows 98, Windows ME, Windows NT и Windows 2000. Если ваши макросы **WINVER** или **_WIN32_WINNT** предназначены для одной из этих версий Windows, необходимо изменить такие макросы. Дополнительные сведения см. в разделе [изменение WINVER и _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

## <a name="examples"></a>Примеры

### <a name="undefined-identifier"></a>Неопределенный идентификатор

Следующий пример приводит к возникновению ошибки C3861, так как идентификатор не определен.

```cpp
// C3861.cpp
void f2(){}
int main() {
   f();    // C3861
   f2();   // OK
}
```

### <a name="identifier-not-in-scope"></a>Идентификатор не находится в области

Следующий пример приводит к возникновению ошибки C3861, так как идентификатор отображается в области видимости файла его определения, только в том случае, если она не объявлена в других исходных файлах, которые ее используют.

```cpp
// C3861_a1.cpp
// Compile with: cl /EHsc /W4 C3861_a1.cpp C3861_a2.cpp
#include <iostream>
// Uncomment the following line to fix:
// int f();  // declaration makes external function visible
int main() {
   std::cout << f() << std::endl;    // C3861
}
```

```cpp
// C3861_a2.cpp
int f() {  // declared and defined here
   return 42;
}
```

### <a name="namespace-qualification-required"></a>Требуется квалификации пространства имен

Классы исключений в стандартной библиотеке C++ требует `std` пространства имен.

```cpp
// C3861_b.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   try {
      throw exception("Exception");   // C3861
      // try the following line instead
      // throw std::exception("Exception");
   }
   catch (...) {
      std::cout << "caught an exception" << std::endl;
   }
}
```

### <a name="obsolete-function-called"></a>Устаревшие функции с именем

Устаревшие функции были удалены из библиотеки CRT.

```cpp
// C3861_c.cpp
#include <stdio.h>
int main() {
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C3861
   // Use gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

### <a name="adl-and-friend-functions"></a>ADL и дружественные функции

В следующем примере возникает C3767, так как компилятор не может использовать поиск по аргументам для `FriendFunc`:

```cpp
namespace N {
   class C {
      friend void FriendFunc() {}
      friend void AnotherFriendFunc(C* c) {}
   };
}

int main() {
   using namespace N;
   FriendFunc();   // C3861 error
   C* pC = new C();
   AnotherFriendFunc(pC);   // found via argument-dependent lookup
}
```

Чтобы устранить эту ошибку, объявите friend в области видимости класса и определите его в области видимости пространства имен:

```cpp
class MyClass {
   int m_private;
   friend void func();
};

void func() {
   MyClass s;
   s.m_private = 0;
}

int main() {
   func();
}
```
