---
description: 'Дополнительные сведения о: Ошибка компилятора C2708'
title: Ошибка компилятора C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: c965375c92c98a58a0fb6d0d51b3358e6b5798b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320874"
---
# <a name="compiler-error-c2708"></a>Ошибка компилятора C2708

"идентификатор": длина фактических параметров в байтах отличается от предыдущего вызова или ссылки

Функции [__stdcall](../../cpp/stdcall.md) должен предшествовать прототип. В противном случае компилятор интерпретирует первый вызов функции как прототип, и эта ошибка возникает, когда компилятор обнаруживает несовпадающий вызов.

Чтобы устранить эту ошибку, добавьте прототип функции.
