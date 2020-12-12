---
description: 'Дополнительные сведения: подстрочные сценарии'
title: Индексация ;
ms.date: 11/04/2016
helpviewer_keywords:
- subscript operator [C++], overloaded
- arrays [C++], subscripting
- subscripting [C++]
- operators [C++], overloading
- operator overloading [C++], examples
- subscript operator
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
ms.openlocfilehash: 77230045e66336e9989f49dd54557fa92d2ab001
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178203"
---
# <a name="subscripting"></a>Индексация ;

Оператор подстрочного индекса (**[]**), как и оператор вызова функции, считается бинарным оператором. Оператор индекса должен быть нестатической функцией-членом, которая принимает один аргумент. Этот аргумент может быть любого типа и определяет требуемый индекс массива.

## <a name="example"></a>Пример

В следующем примере показано, как создать вектор типа **`int`** , который реализует проверку границ:

```cpp
// subscripting.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class IntVector {
public:
   IntVector( int cElements );
   ~IntVector() { delete [] _iElements; }
   int& operator[](int nSubscript);
private:
   int *_iElements;
   int _iUpperBound;
};

// Construct an IntVector.
IntVector::IntVector( int cElements ) {
   _iElements = new int[cElements];
   _iUpperBound = cElements;
}

// Subscript operator for IntVector.
int& IntVector::operator[](int nSubscript) {
   static int iErr = -1;

   if( nSubscript >= 0 && nSubscript < _iUpperBound )
      return _iElements[nSubscript];
   else {
      clog << "Array bounds violation." << endl;
      return iErr;
   }
}

// Test the IntVector class.
int main() {
   IntVector v( 10 );
   int i;

   for( i = 0; i <= 10; ++i )
      v[i] = i;

   v[3] = v[9];

   for ( i = 0; i <= 10; ++i )
      cout << "Element: [" << i << "] = " << v[i] << endl;
}
```

```Output
Array bounds violation.
Element: [0] = 0
Element: [1] = 1
Element: [2] = 2
Element: [3] = 9
Element: [4] = 4
Element: [5] = 5
Element: [6] = 6
Element: [7] = 7
Element: [8] = 8
Element: [9] = 9
Array bounds violation.
Element: [10] = 10
```

## <a name="comments"></a>Комментарии

При `i` достижении 10 в предыдущей программе **оператор []** обнаруживает, что индекс вне границ используется и выдает сообщение об ошибке.

Обратите внимание, что **оператор Function []** возвращает ссылочный тип. В результате она является значением l-value, что позволяет использовать выражения с индексами с любой стороны операторов присваивания.

## <a name="see-also"></a>См. также раздел

[Перегрузка операторов](../cpp/operator-overloading.md)
