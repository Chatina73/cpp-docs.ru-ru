---
title: Предупреждение компилятора (уровень 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: bcadf31eda079ebb8ea7a496efe4c945e16b1ab7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622850"
---
# <a name="compiler-warning-level-1-c4532"></a>Предупреждение компилятора (уровень 1) C4532

«continue»: перехода из блока __finally/finally не определено поведение при обработке завершения

Компилятор обнаружил одно из следующих ключевых слов:

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

вызывает переход из [__finally](../../cpp/try-finally-statement.md) или [наконец](../../dotnet/finally.md) блок во время аварийного завершения.

При возникновении исключения, и хотя стек развертывается во время выполнения обработчиков завершения ( `__finally` или блоков finally), и код переходит из `__finally` блокировать перед `__finally` завершения блока, поведение не определено. Элемент управления может не вернуться к развертываемый код, чтобы исключение не может быть обработано должным образом.

Если необходим переход из **__finally** block, сначала проверьте аварийное завершение.

Следующий пример приводит к возникновению ошибки C4532; просто закомментируйте операторов перехода, чтобы разрешить предупреждения.

```
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```