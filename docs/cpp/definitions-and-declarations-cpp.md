---
description: 'Дополнительные сведения: определения и объявления (C++)'
title: Определения и объявления (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: c22274534193011c1c5ec26aedbece339a9302b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339440"
---
# <a name="definitions-and-declarations-c"></a>Определения и объявления (C++)

**Блок, относящийся только к системам Microsoft**

Интерфейс DLL ссылается на все элементы (функции и данные), которые могут быть экспортированы какой-либо программой в системе; то есть все элементы, объявленные как **`dllimport`** или **`dllexport`** . Все объявления, входящие в интерфейс DLL, должны указывать либо **`dllimport`** атрибут, либо **`dllexport`** . Однако определение должно указывать только **`dllexport`** атрибут. Например, следующее определение функции вызовет ошибку компилятора.

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;
}
```

Показанный ниже код также вызовет ошибку.

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

Однако следующий синтаксис правильный.

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

Использование класса **`dllexport`** подразумевает определение, а **`dllimport`** подразумевает объявление. **`extern`** Для принудительного объявления необходимо использовать ключевое слово WITH **`dllexport`** . в противном случае подразумевается определение. Таким образом, приведенные ниже примеры правильны.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

В следующих примерах поясняются предшествующие.

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
