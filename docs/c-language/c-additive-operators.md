---
title: Аддитивные операторы в C
ms.date: 10/18/2018
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
ms.openlocfilehash: af7302adaafc3a91287f6d15a11c8e784f35c33d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650713"
---
# <a name="c-additive-operators"></a>Аддитивные операторы в C

Аддитивные операторы выполняют сложение (**+**) и вычитание (**-**).

## <a name="syntax"></a>Синтаксис

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **+** *multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **-** *multiplicative-expression*

> [!NOTE]
> Хотя синтаксис *выражения-сложения* включает *выражение-умножения*, это не означает, что требуются выражения, в которых используется умножение. Синтаксис *выражения-умножения*, *выражения-приведения* и *унарного выражения* см. в документе [Краткие сведения о синтаксисе языка C](../c-language/c-language-syntax-summary.md).

Операнды могут быть целыми значениями или значениями с плавающей запятой. Некоторые аддитивные операции также можно выполнять со значениями указателя, как описано в разделах, посвященных каждому оператору.

Аддитивные операторы выполняют обычные арифметические преобразования с операндами целочисленного типа и типа с плавающей запятой. После преобразования тип результата совпадает с типом операндов. Поскольку преобразования, выполняемые аддитивными операторами, не обеспечивают условия переполнения или потери значимости, данные могут быть потеряны, если результат аддитивной операции невозможно представить в типе операндов после преобразования.

## <a name="see-also"></a>См. также

[Аддитивные операторы: + и -](../cpp/additive-operators-plus-and.md)