---
description: 'Дополнительные сведения: ключевые слова наследования'
title: Ключевые слова наследования
ms.date: 11/04/2016
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
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
ms.openlocfilehash: d2cd576d80b3e68eaf2a0d57fecf25309d0719b0
ms.sourcegitcommit: bf6d8a220f6392f1f19c0c0605d1467d0221ef6c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105551739"
---
# <a name="inheritance-keywords"></a>Ключевые слова наследования

**Блок, относящийся только к системам Microsoft**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

где:

*имя класса*<br/>
Имя объявляемого класса.

В C++ указатель на член класса можно объявить до определения класса. Например:

```cpp
class S;
int S::*p;
```

В приведенном выше коде `p` объявляется как указатель на целочисленный член класса S. Однако `class S` еще не определен в этом коде; он был только объявлен. Когда компилятор обнаруживает такой указатель, он должен создать обобщенное представление указателя. Размер представления зависит от указанной модели наследования. Указать модель наследования для компилятора можно четырьмя способами.

- В интегрированной среде разработки в **представлении указателя на член**

- В командной строке с параметром [/vmg](../build/reference/vmb-vmg-representation-method.md)

- Использование директивы pragma [pointers_to_members](../preprocessor/pointers-to-members.md)

- С помощью ключевых слов наследования **`__single_inheritance`** , **`__multiple_inheritance`** и **`__virtual_inheritance`** . При использовании этого метода управление моделью наследования осуществляется на уровне класса.

    > [!NOTE]
    >  Если указатель на член класса всегда объявляется после определения класса, нет необходимости использовать какой-либо из этих параметров.

Объявление указателя на член класса до определения класса влияет на размер и скорость полученного исполняемого файла. Чем сложнее наследование, используемое в классе, тем больше число байтов, требуемых для представления указателя на член класса, и тем больше код, необходимый для интерпретации указателя. Одиночное наследование является самым простым, а виртуальное наследование — самым сложным.

Если приведенный выше пример изменить на

```cpp
class __single_inheritance S;
int S::*p;
```

независимо от параметров командной строки или директив pragma указатели на члены `class S` будут использовать наименьшее возможное представление.

> [!NOTE]
> То же опережающее объявление представления указателя на член должно быть включено в каждую запись преобразования, которая объявляет указатели на члены этого класса, и объявление должно выполняться до объявления указателей на члены.

Для совместимости с предыдущими версиями,, **`_single_inheritance`** **`_multiple_inheritance`** и **`_virtual_inheritance`** являются синонимами для **`__single_inheritance`** , **`__multiple_inheritance`** и, **`__virtual_inheritance`** если не задан параметр компилятора [/Za \( Отключить расширения языка)](../build/reference/za-ze-disable-language-extensions.md) .

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Ключевые слова](../cpp/keywords-cpp.md)
