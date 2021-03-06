---
description: 'Подробнее о следующем: Вызов функций (C)'
title: Вызов функций (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: 7ebe8ded3e64f7b636aaf438ee2bff8e4f221610
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195974"
---
# <a name="function-call-c"></a>Вызов функций (C)

*Вызов функции* — это выражение, которое содержит имя вызываемой функции или значение указателя на функцию и, при необходимости, аргументы, передаваемые в эту функцию.

## <a name="syntax"></a>Синтаксис

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *assignment-expression*

Выражение *postfix-expression* должно вычислять адрес функции (например, идентификатор функции или значение указателя функции), а *argument-expression-list* содержит список выражений (разделенных запятыми), значения которых (аргументы) передаются функции. Аргумент *argument-expression-list* может быть пустым.

Выражение вызова функции имеет значение и тип возвращаемого значения функции. Функция не может возвращать объект типа массива. Если возвращаемый тип функции — **`void`** (то есть объявлено, что функция никогда не возвращает значение), выражение вызова функции также имеет тип **`void`** . (Дополнительные сведения см. в разделе [Вызовы функций](../c-language/function-calls.md).)

## <a name="see-also"></a>См. также

[Оператор вызова функции: ()](../cpp/function-call-operator-parens.md)
