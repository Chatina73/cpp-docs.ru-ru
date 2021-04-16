---
description: 'Дополнительные сведения: ключевые слова наследования'
title: Ключевые слова наследования
ms.date: 04/12/2021
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.openlocfilehash: 4daf2899b7b0a556d41779974539aef253b2b4d2
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107576941"
---
# <a name="inheritance-keywords"></a>Ключевые слова наследования

**Блок, относящийся только к системам Microsoft**

> **`class`** *`class-name`*\
> **`class __single_inheritance`** *`class-name`*\
> **`class __multiple_inheritance`** *`class-name`*\
> **`class __virtual_inheritance`** *`class-name`*

где:

*`class-name`*<br/>
Имя объявляемого класса.

C++ позволяет объявить указатель на член класса перед определением класса. Пример:

```cpp
class S;
int S::*p;
```

В приведенном выше коде `p` объявляется как указатель на целочисленный член класса S. Однако `class S` еще не определена в этом коде; он объявлен только как. Когда компилятор обнаруживает такой указатель, он должен создать обобщенное представление указателя. Размер представления зависит от указанной модели наследования. Существует три способа указания модели наследования для компилятора:

- В командной строке с [`/vmg`](../build/reference/vmb-vmg-representation-method.md) параметром

- Использование [`pointers_to_members`](../preprocessor/pointers-to-members.md) директивы pragma

- С помощью ключевых слов наследования **`__single_inheritance`** , **`__multiple_inheritance`** и **`__virtual_inheritance`** . При использовании этого метода управление моделью наследования осуществляется на уровне класса.

    > [!NOTE]
    >  Если указатель на член класса всегда объявляется после определения класса, нет необходимости использовать какой-либо из этих параметров.

Если вы объявили указатель на член класса до определения класса, он может негативно повлиять на размер и скорость получаемого исполняемого файла. Чем сложнее наследование, используемое классом, тем больше число байтов, необходимое для представления указателя на член класса. И, чем больше код, необходимый для интерпретации указателя. Одиночное (или нет) наследование не менее сложное, а виртуальное наследование является наиболее сложным. Указатели на члены, объявляемые до определения класса, всегда используют наибольшее, более сложное представление.

Если приведенный выше пример изменить на

```cpp
class __single_inheritance S;
int S::*p;
```

в то же время, независимо от указанных параметров командной строки или директив pragma, указатели на члены `class S` будут использовать наименьшее возможное представление.

> [!NOTE]
> То же опережающее объявление представления указателя на член должно быть включено в каждую запись преобразования, которая объявляет указатели на члены этого класса, и объявление должно выполняться до объявления указателей на члены.

Для совместимости с предыдущими версиями,, **`_single_inheritance`** **`_multiple_inheritance`** и **`_virtual_inheritance`** являются синонимами для **`__single_inheritance`** , **`__multiple_inheritance`** и, **`__virtual_inheritance`** если не задан параметр компилятора, если не [ `/Za` \( Отключить расширения языка)](../build/reference/za-ze-disable-language-extensions.md) .

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Ключевые слова](../cpp/keywords-cpp.md)
