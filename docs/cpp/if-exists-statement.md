---
description: 'Дополнительные сведения о инструкции: __if_exists'
title: Оператор __if_exists
ms.date: 11/04/2016
f1_keywords:
- __if_exists_cpp
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
ms.openlocfilehash: d2edfc11d70e50d2e393938c108db9c425468003
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113965"
---
# <a name="__if_exists-statement"></a>Оператор __if_exists

**`__if_exists`** Оператор проверяет, существует ли указанный идентификатор. Если идентификатор существует, выполняется определенный блок операторов.

## <a name="syntax"></a>Синтаксис

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Параметры

*identifier*\
Идентификатор, наличие которого требуется проверить.

*инструкции*\
Одна или несколько инструкций для выполнения, если *идентификатор* существует.

## <a name="remarks"></a>Комментарии

> [!CAUTION]
> Для достижения наиболее достоверных результатов используйте **`__if_exists`** инструкцию под следующими ограничениями.

- Примените **`__if_exists`** инструкцию только к простым типам, а не к шаблонам.

- Примените **`__if_exists`** инструкцию к идентификаторам как внутри, так и вне класса. Не применяйте **`__if_exists`** инструкцию к локальным переменным.

- Используйте **`__if_exists`** оператор только в теле функции. За пределами тела функции **`__if_exists`** инструкция может проверять только полностью определенные типы.

- При проверке перегруженных функций невозможно выполнить проверку определенной формы перегрузки.

Дополнение к **`__if_exists`** оператору является оператором [__if_not_exists](../cpp/if-not-exists-statement.md) .

## <a name="example"></a>Пример

Обратите внимание, что в этом примере используются шаблоны, что не рекомендуется.

```cpp
// the__if_exists_statement.cpp
// compile with: /EHsc
#include <iostream>

template<typename T>
class X : public T {
public:
   void Dump() {
      std::cout << "In X<T>::Dump()" << std::endl;

      __if_exists(T::Dump) {
         T::Dump();
      }

      __if_not_exists(T::Dump) {
         std::cout << "T::Dump does not exist" << std::endl;
      }
   }
};

class A {
public:
   void Dump() {
      std::cout << "In A::Dump()" << std::endl;
   }
};

class B {};

bool g_bFlag = true;

class C {
public:
   void f(int);
   void f(double);
};

int main() {
   X<A> x1;
   X<B> x2;

   x1.Dump();
   x2.Dump();

   __if_exists(::g_bFlag) {
      std::cout << "g_bFlag = " << g_bFlag << std::endl;
   }

   __if_exists(C::f) {
      std::cout << "C::f exists" << std::endl;
   }

   return 0;
}
```

## <a name="output"></a>Вывод

```Output
In X<T>::Dump()
In A::Dump()
In X<T>::Dump()
T::Dump does not exist
g_bFlag = 1
C::f exists
```

## <a name="see-also"></a>См. также

[Инструкции выбора](../cpp/selection-statements-cpp.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)<br/>
[__if_not_exists, инструкция](../cpp/if-not-exists-statement.md)
