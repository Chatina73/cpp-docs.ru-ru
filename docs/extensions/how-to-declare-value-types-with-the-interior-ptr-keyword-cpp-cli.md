---
description: Дополнительные сведения см. в статье как объявлять типы значений с помощью ключевого слова interior_ptr (C++/CLI).
title: Практическое руководство. Объявление типов значений с использованием ключевого слова interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: b8d5c554f212a9536b0ad063d67e044c08194015
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119178"
---
# <a name="how-to-declare-value-types-with-the-interior_ptr-keyword-ccli"></a>Практическое руководство. Объявление типов значений с использованием ключевого слова interior_ptr (C++/CLI)

**interior_ptr** можно использовать с типом значения.

> [!IMPORTANT]
> Эта возможность языка поддерживается параметром компилятора `/clr`, а параметром компилятора `/ZW` не поддерживается.

## <a name="example-interior_ptr-with-value-type"></a>Пример: interior_ptr с типом значения

### <a name="description"></a>Описание

В следующем примере C++/CLI показано использование **interior_ptr** с типом значения.

### <a name="code"></a>Код

```cpp
// interior_ptr_value_types.cpp
// compile with: /clr
value struct V {
   V(int i) : data(i){}
   int data;
};

int main() {
   V v(1);
   System::Console::WriteLine(v.data);

   // pointing to a value type
   interior_ptr<V> pv = &v;
   pv->data = 2;

   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);

   // pointing into a value type
   interior_ptr<int> pi = &v.data;
   *pi = 3;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);
}
```

```Output
1
2
2
3
3
3
```

## <a name="example-this-pointer"></a>Пример: этот указатель

### <a name="description"></a>Описание

В типе значения **`this`** указатель принимает значение interior_ptr.

В теле нестатической функции-члена типа значения `V` **`this`** — это выражение типа, `interior_ptr<V>` значение которого является адресом объекта, для которого вызывается функция.

### <a name="code"></a>Код

```cpp
// interior_ptr_value_types_this.cpp
// compile with: /clr /LD
value struct V {
   int data;
   void f() {
      interior_ptr<V> pv1 = this;
      // V* pv2 = this;   error
   }
};
```

## <a name="example-address-of-operator"></a>Пример: оператор взятия адреса

### <a name="description"></a>Описание

В следующем примере показано использование оператора взятия адреса со статическими членами.

Адрес статического члена типа Visual C++ создает собственный указатель.  Адрес статического члена типа значения является управляемым указателем, так как член типа значения выделяется в куче среды выполнения и может быть перемещен сборщиком мусора.

### <a name="code"></a>Код

```cpp
// interior_ptr_value_static.cpp
// compile with: /clr
using namespace System;
value struct V { int i; };

ref struct G {
   static V v = {22};
   static int i = 23;
   static String^ pS = "hello";
};

int main() {
   interior_ptr<int> p1 = &G::v.i;
   Console::WriteLine(*p1);

   interior_ptr<int> p2 = &G::i;
   Console::WriteLine(*p2);

   interior_ptr<String^> p3 = &G::pS;
   Console::WriteLine(*p3);
}
```

```Output
22
23
hello
```

## <a name="see-also"></a>См. также

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)
