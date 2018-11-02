---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: 24cc4dd3cd7e0c893664339e7ad83383839b0b11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600376"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>Синтаксис

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Примечания

Когда располагается перед списком членов класса, **открытый** ключевое слово указывает, что эти члены доступны из любой функции. Это применяется ко всем членам, объявленным до следующего описателя доступа или до конца класса.

Если перед именем базового класса, **открытый** ключевое слово указывает, что открытые и защищенные члены базового класса являются открытыми и защищенные члены, соответственно, производного класса.

Доступ членов в классе по умолчанию является закрытым. Доступ членов в структуре или объединении по умолчанию является открытым.

Доступ базового класса по умолчанию является закрытым для классов и открытым для структур. Объединения не могут иметь базовые классы.

Дополнительные сведения см. в разделе [частного](../cpp/private-cpp.md), [защищенные](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md)и в таблице членского доступа в [управление доступом к членам класса](member-access-control-cpp.md) .

## <a name="clr-specific"></a>Специально для /clr

В CLR-типах ключевые слова описателя доступа C++ (**открытый**, **частного**, и **защищенные**) может повлиять на видимость типов и методов с точки зрения сборок. Дополнительные сведения см. в разделе [управление доступом к членам](member-access-control-cpp.md).

> [!NOTE]
>  Файлы, скомпилированные с помощью [/LN](../build/reference/ln-create-msil-module.md) не затрагиваются этим поведением. В этом случае все управляемые классы (открытые или закрытые) будут видны.

## <a name="end-clr-specific"></a>КОНЕЦ специально для /clr

## <a name="example"></a>Пример

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>См. также

[Управление доступом к членам классов](member-access-control-cpp.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)