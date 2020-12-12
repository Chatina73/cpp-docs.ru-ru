---
description: 'Дополнительные сведения: &lt; вариант&gt;'
title: '&lt;variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 994bd18a66dd78c8f6042afea10df69ff08a1487
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312477"
---
# <a name="ltvariantgt"></a>&lt;variant&gt;

Объект Variant содержит и управляет значением. Если вариант содержит значение, тип этого значения должен быть одним из типов аргументов шаблона, заданных в Variant. Эти аргументы шаблона называются альтернативными.

## <a name="requirements"></a>Требования

**Заголовок:**\<variant>

**Пространство имен:** std

## <a name="members"></a>Элементы

### <a name="operators"></a>Операторы

|Имя|Описание|
|-|-|
|[Оператор = =](../standard-library/forward-list-operators.md#op_eq_eq)|Проверяет, равен ли объект Variant слева от оператора объекту Variant в правой части.|
|[operator! =](../standard-library/forward-list-operators.md#op_neq)|Проверяет, не равен ли объект Variant слева от оператора объекту Variant в правой части.|
|[Оператор<](../standard-library/forward-list-operators.md#op_lt)|Проверяет, меньше ли объект Variant слева от оператора, чем объект Variant в правой части.|
|[Оператор<=](../standard-library/forward-list-operators.md#op_lt_eq)|Проверяет, что объект Variant слева от оператора меньше или равен объекту Variant в правой части.|
|[Оператор>](../standard-library/forward-list-operators.md#op_gt)|Проверяет, больше ли объект Variant слева от оператора, чем объект Variant в правой части.|
|[Оператор>=](../standard-library/forward-list-operators.md#op_lt_eq)|Проверяет, что объект Variant слева от оператора больше или равен объекту Variant в правой части.|

### <a name="functions"></a>Функции

|Имя|Описание|
|-|-|
|[get](../standard-library/variant-functions.md#get)|Возвращает вариант объекта.|
|[get_if](../standard-library/variant-functions.md#get_if)|Возвращает вариант объекта, если он существует.|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|Возвращает **`true`** , если существует вариант.|
|[позиции](../standard-library/variant-functions.md#swap)|Меняет местами **вариант**.|
|[перехода](../standard-library/variant-functions.md#visit)|Переходит к следующему **варианту**.|

### <a name="classes"></a>Классы

|name|Описание|
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|Объекты, выдаваемые для сообщения о недопустимых обращениях к значению объекта Variant.|
|[variant](../standard-library/variant.md)|Объект для хранения значения одного из альтернативных типов или значение No.|

### <a name="structs"></a>Структуры

|Имя|Описание|
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[штат](../standard-library/monostate-structure.md)|Альтернативный тип для варианта, чтобы сделать тип Variant по умолчанию конструируемым.|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|Помогает объектам типа Variant.|
|[variant_size](../standard-library/variant-size-structure.md)|Помогает объектам типа Variant.|

### <a name="objects"></a>Объекты

|Имя|Описание|
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)
