---
description: 'Дополнительные сведения: перечисления (C++/CX)'
title: Перечисления (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: cdf058dc1549a8bc483127cffaeb347492d80716
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341962"
---
# <a name="enums-ccx"></a>Перечисления (C++/CX)

C++/CX поддерживает `public enum class` ключевое слово, аналогичное стандартному C++ `scoped  enum` . При использовании перечислителя, объявленного с помощью ключевого слова `public enum class` , необходимо использовать идентификатор перечисления, чтобы определить область каждого значения перечислителя.

### <a name="remarks"></a>Комментарии

Объект `public enum class` , который не имеет спецификатора доступа, например **`public`** , обрабатывается как стандартное [перечисление с областью действия](../cpp/enumerations-cpp.md)C++.

`public enum class`Объявление или `public enum struct` может иметь базовый тип любого целочисленного типа, хотя сам среда выполнения Windows требует, чтобы тип был Int32, или UInt32 для перечисления flags. Следующий синтаксис описывает части объявления `public enum class` или `public enum struct`.

В этом примере показано, как определить открытый класс перечисления:

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

В следующем примере показано, как использовать его:

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Примеры

В следующих примерах показано, как объявить перечисление.

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

В следующем примере показано, как выполнять приведение к числовым эквивалентами и выполнять сравнения. Обратите внимание, что область использования перечислителя `One` определяется идентификатором перечисления `Enum1` , а область использования перечислителя `First` — идентификатором `Enum2`.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>См. также раздел

[Система типов](../cppcx/type-system-c-cx.md)<br/>
[Справочник по языку C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Справочник по пространствам имен](../cppcx/namespaces-reference-c-cx.md)
