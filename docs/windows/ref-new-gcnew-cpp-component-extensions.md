---
title: ref new, gcnew (C + +/ CLI и C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
ms.openlocfilehash: dd78bcb7283cb08f4971192274686710fe22181f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641772"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new, gcnew (C + +/ CLI и C + +/ CX)

**Ref новый** агрегатное ключевое слово выделяет экземпляр типа, который является сбор мусора, когда объект становится недоступным, и возвращает дескриптор ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) на выделенный объект.

## <a name="all-runtimes"></a>Все среды выполнения

Память для экземпляра типа, который выделяется средой **ref новый** освобождается автоматически.

Объект **ref новый** вызывает операцию `OutOfMemoryException` Если не удается выделить память.

Дополнительные сведения о том, как выделении и освобождении памяти для собственных типов C++, см. в разделе [новых и удаленных операторах](../cpp/new-and-delete-operators.md).

## <a name="windows-runtime"></a>Среда выполнения Windows

Используйте **ref новый** выделить память для объектов среды выполнения Windows, время существования которых требуется администрировать автоматически. Объект автоматически освобождается, когда число ссылок становится равным нулю, что происходит после выхода последней копии ссылки за пределы области. Дополнительные сведения см. в разделе [классы и структуры ссылки](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Требования

Параметр компилятора: `/ZW`

## <a name="common-language-runtime"></a>Среда CLR

Выделена память для управляемого типа (ссылку или тип значения) **gcnew**и освобождается с помощью сбора мусора.

### <a name="requirements"></a>Требования

Параметр компилятора: `/clr`

### <a name="examples"></a>Примеры

В следующем примере используется **gcnew** выделить объект сообщения.

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

В следующем примере используется **gcnew** Создание упакованного типа значения для использования как ссылочному типу.

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>См. также

[Расширения компонентов для .NET и UWP](../windows/component-extensions-for-runtime-platforms.md)