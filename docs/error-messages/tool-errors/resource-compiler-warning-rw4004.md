---
description: Дополнительные сведения см. в статье предупреждение компилятора ресурсов RW4004
title: Предупреждение компилятора ресурсов RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: 5609d49e242ba7d74025622c53c279ae1b0da854
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237001"
---
# <a name="resource-compiler-warning-rw4004"></a>Предупреждение компилятора ресурсов RW4004

Символ ASCII не соответствует виртуальному коду клавиши.

Строковый литерал был использован для виртуального кода клавиши в акселераторе VIRTKEY.

Это предупреждение позволяет продолжить работу, но имейте в виду, что созданные сочетания клавиш могут не соответствовать указанной строке. (акселераторы VIRTKEY используют другие коды клавиш, чем акселераторы ASCII).

Хотя строковые литералы являются синтаксически допустимыми, вы можете только убедиться, что вы получаете нужный ускоритель, используя значения **VK_ \* #define** в Windows. h.
