---
description: 'Подробнее о следующем: Текст функции'
title: Текст функции
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: 098a759a8fd4fd9ab69e487ab84f7ed7d0d2c25c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195987"
---
# <a name="function-body"></a>Текст функции

*Тело функции* — это составной оператор, содержащий операторы, которые определяют выполняемые функцией действия.

## <a name="syntax"></a>Синтаксис

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* поддерживается только компилятором Майкрософт \*/

*compound-statement*: /\* Текст функции \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

Если не указано иное, переменные, объявленные в теле функции (*локальные переменные*), имеют класс хранения **`auto`** . При вызове функции создается хранилище для локальных переменных и выполняются локальные инициализации. Управление передается первому оператору в составном выражении *compound-statement* и продолжается до тех пор, пока не будет выполнен оператор **`return`** или достигнут конец тела функции. Затем управление возвращается в точку, из которой вызвана функция.

Если функция должна возвращать значение, должен быть выполнен оператор **`return`** , содержащий выражение. Если оператор **`return`** не выполнен или если оператор **`return`** не содержит выражения, возвращаемое значение функции не определено.

## <a name="see-also"></a>См. также

[Определения функций в C](../c-language/c-function-definitions.md)
