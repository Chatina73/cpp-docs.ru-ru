---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 4) C4710'
title: Предупреждение компилятора (уровень 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: b10a2add132335db48c49ae69740d04f792f126e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330583"
---
# <a name="compiler-warning-level-4-c4710"></a>Предупреждение компилятора (уровень 4) C4710

"функция": функция не встроена

Данная функция была выбрана для встроенного расширения, но компилятор не выполнил встраивание.

Встраивание выполняется по усмотрению компилятора. **`inline`** Ключевое слово, как и **`register`** ключевое слово, используется в качестве подсказки для компилятора. Компилятор использует эвристику, чтобы определить, должна ли она подставлять определенную функцию для ускорения кода при компиляции для ускорения, или если она должна подставлять определенную функцию, чтобы уменьшить размер кода при компиляции пространства. Компилятор будет подставляем только немалые функции при компиляции для пространства.

В некоторых случаях компилятор не будет встроеет определенную функцию по механическим причинам. Список причин, по которым компилятор может не подставляемь функцию, см. в разделе [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) .

Это предупреждение отключено по умолчанию. Подробнее: [Выключенные по умолчанию предупреждения компилятора](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .
