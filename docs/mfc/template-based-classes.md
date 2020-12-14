---
description: 'Дополнительные сведения: Template-Based классы'
title: Классы на основе шаблонов
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
ms.openlocfilehash: 87b03c649bfb6acf401c3ee78e6db07c1185dff5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216318"
---
# <a name="template-based-classes"></a>Классы на основе шаблонов

В этой статье объясняются типобезопасные классы коллекций на основе шаблонов в MFC версии 3,0 и более поздних. Использование этих шаблонов для создания строго типизированных коллекций является более удобным и помогает обеспечить безопасность типов более эффективно, чем использование классов коллекций, не основанных на шаблонах.

MFC предварительно определяет две категории коллекций на основе шаблонов:

- [Простые классы Array, List и Map](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Массивы, списки и карты типизированных указателей](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Классы простых коллекций являются производными от класса `CObject` , поэтому они наследуют сериализацию, динамическое создание и другие свойства `CObject` . Классы коллекций типизированных указателей задают класс, производный от, который должен быть одной из нешаблонных коллекций указателей, предопределенных MFC, например `CPtrList` или `CPtrArray` . Новый класс коллекции наследует от указанного базового класса, а функции члена нового класса используют инкапсулированные вызовы членов базового класса для обеспечения безопасности типов.

Дополнительные сведения о шаблонах C++ см. [](../cpp/templates-cpp.md) в разделе Шаблоны *справочника по языку c++*.

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> Использование простых массивов, списков и шаблонов карт

Чтобы использовать шаблоны простых коллекций, необходимо знать, какие данные можно хранить в этих коллекциях, и какие параметры следует использовать в объявлениях коллекции.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a> Простой использование массивов и списков

Простые классы Array и List, [CArray](../mfc/reference/carray-class.md) и [CList](../mfc/reference/clist-class.md), принимают два параметра: *Type* и `ARG_TYPE` . Эти классы могут хранить любой тип данных, указанный в параметре *Type* :

- Основные типы данных C++, такие как **`int`** , **`char`** и **`float`**

- Структуры и классы C++

- Другие определяемые типы

Для удобства и эффективности можно использовать параметр *ARG_TYPE* , чтобы указать тип аргументов функции. Как правило, вы указываете *ARG_TYPE* в качестве ссылки на тип, указанный в параметре *Type* . Пример:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

В первом примере объявляется коллекция массивов, `myArray` которая содержит **`int`** s. Во втором примере объявляется коллекция списков, `myList` которая хранит `CPerson` объекты. Некоторые функции-члены классов коллекций принимают аргументы, тип которых задан параметром шаблона *ARG_TYPE* . Например, `Add` функция члена класса `CArray` принимает аргумент *ARG_TYPE* :

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a> Простое использование карт

Простой класс Map, [кмап](../mfc/reference/cmap-class.md), принимает четыре параметра: *Key*, *ARG_KEY*, *value* и *ARG_VALUE*. Подобно классам Array и List, классы Map могут хранить любые типы данных. В отличие от массивов и списков, которые индексируют и упорядочивают данные, которые они хранят, сопоставляют ключи и значения. доступ к значению, сохраненному на карте, можно получить, указав соответствующий ключ значения. Параметр *Key* задает тип данных ключей, используемых для доступа к данным, хранящимся на карте. Если тип *ключа* является структурой или классом, то *ARG_KEY* параметр обычно является ссылкой на тип, указанный в *Key*. Параметр *value* задает тип элементов, хранящихся на карте. Если тип *ARG_VALUE* является структурой или классом, то параметр *ARG_VALUE* обычно является ссылкой на тип, указанный в *значении*. Пример:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

Первый пример сохраняет `MY_STRUCT` значения, обращается к ним по **`int`** ключам и возвращает доступ к `MY_STRUCT` элементам по ссылке. Второй пример сохраняет `CPerson` значения, обращается к ним по `CString` ключам и возвращает ссылки на элементы, к которым осуществляется доступ. Этот пример может представлять простую адресную книгу, в которой вы ищете людей по фамилии.

Так как параметр *ключа* имеет тип `CString` и параметр *KEY_TYPE* имеет тип `LPCSTR` , ключи хранятся в карте как элементы типа, `CString` но на них есть ссылки в таких функциях, как `SetAt` указатели типа `LPCSTR` . Пример:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a> Использование шаблонов коллекции Typed-Pointer

Чтобы использовать шаблоны коллекций с типизированными указателями, необходимо знать, какие типы данных можно хранить в этих коллекциях, и какие параметры следует использовать в объявлениях коллекции.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a> Typed-Pointer использование массивов и списков

Классы массива и списка типизированных указателей, [ктипедптраррай](../mfc/reference/ctypedptrarray-class.md) и [ктипедптрлист](../mfc/reference/ctypedptrlist-class.md), принимают два параметра: *base_class* и *Type*. Эти классы могут хранить любой тип данных, указанный в параметре *типа* . Они являются производными от одного из классов нешаблонной коллекции, в котором хранятся указатели; Этот базовый класс указывается в *base_class*. Для массивов используйте либо `CObArray` или `CPtrArray` . Для списков используйте либо `CObList` или `CPtrList` .

Фактически, при объявлении коллекции на основе, скажем `CObList` , новый класс не только наследует члены своего базового класса, но также объявляет ряд дополнительных функций и операторов-членов, обеспечивающих строгую типизацию, которые обеспечивают безопасность типов путем инкапсуляции вызовов к членам базового класса. Эти инкапсуляции управляют всеми необходимыми преобразованиями типов. Пример:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

В первом примере объявляется массив типизированных указателей, `myArray` производный от `CObArray` . Массив хранит и возвращает указатели на `CPerson` объекты (где `CPerson` является классом, производным от `CObject` ). Можно вызвать любую `CObArray` функцию-член или вызвать новые типобезопасные `GetAt` функции, а также использовать строго типизированный `ElementAt` оператор **[]** .

Во втором примере объявляется список типизированных указателей, `myList` производный от `CPtrList` . В списке хранятся и возвращаются указатели на `MY_STRUCT` объекты. Класс, основанный на `CPtrList` , используется для хранения указателей на объекты, не являющиеся производными от `CObject` . `CTypedPtrList` имеет ряд строго типизированных функций-членов: `GetHead` , `GetTail` , `RemoveHead` , `RemoveTail` ,, и `GetNext` `GetPrev` `GetAt` .

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a> Typed-Pointer использования карт

Класс карт типизированного указателя, [ктипедптрмап](../mfc/reference/ctypedptrmap-class.md), принимает три параметра: *base_class*, *ключ* и *значение*. Параметр *base_class* указывает класс, из которого следует создать новый класс: `CMapPtrToWord` , `CMapPtrToPtr` , `CMapStringToPtr` ,, `CMapWordToPtr` `CMapStringToOb` и т. д. *Ключ* аналогичен *ключу* в `CMap` : он указывает тип ключа, используемого для уточняющих запросов. *Значение* аналогично *значению* в `CMap` : указывает тип объекта, хранящегося на карте. Пример:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Первый пример — это сопоставление на основе `CMapPtrToPtr` — в нем используются `CString` ключи, сопоставленные с указателями на `MY_STRUCT` . Можно найти сохраненный указатель, вызвав строго типизированную функцию- `Lookup` член. Оператор **[]** можно использовать для поиска сохраненного указателя и его добавления, если он не найден. Вы также можете выполнить итерацию по карте с помощью строго типизированной `GetNextAssoc` функции. Можно также вызвать другие функции членов класса `CMapPtrToPtr` .

Второй пример — это сопоставление на основе `CMapStringToOb` — он использует строковые ключи, сопоставленные с сохраненными указателями на `CMyObject` объекты. Можно использовать те же типобезопасные члены, которые описаны в предыдущем абзаце, или вызывать члены класса `CMapStringToOb` .

> [!NOTE]
> Если **`class`** **`struct`** для параметра *значения* указан тип или, а не указатель или ссылка на тип, то класс или структура должны иметь конструктор копии.

Дополнительные сведения см. в разделе [Создание коллекции Type-Safe](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>См. также раздел

[Коллекции](../mfc/collections.md)
