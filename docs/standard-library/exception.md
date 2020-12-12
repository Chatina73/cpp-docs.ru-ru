---
description: 'Дополнительные сведения: &lt; Exception&gt;'
title: '&lt;exception&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: b4cba2def6416e7bcabb8d769e92c7c7f2af4281
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232529"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

Определяет несколько типов и функций, связанных с обработкой исключений. Обработка исключений используется в ситуациях, когда система может восстановиться после ошибки. Она предоставляет средства для возврата управления из функции в программу. Целью внедрения обработки исключений является повышение надежности программы с одновременным обеспечением возможности восстановления после ошибки определенным образом.

## <a name="requirements"></a>Требования

**Заголовок:**\<exception>

**Пространство имен:** std

## <a name="members"></a>Элементы

### <a name="typedefs"></a>Определения типов

|Имя|Описание|
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Тип, который описывает указатель на исключение.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Тип, который описывает указатель на функцию, подходящую для использования в качестве `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Тип, который описывает указатель на функцию, подходящую для использования в качестве `unexpected_handler`.|

### <a name="functions"></a>Функции

|Имя|Описание|
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Получает указатель на текущее исключение.|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|Получает текущую функцию `terminate_handler`.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Получает текущую функцию `unexpected_handler`.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Создает объект `exception_ptr`, содержащий копию исключения.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Создает исключение, переданное в качестве параметра.|
|[rethrow_if_nested](../standard-library/exception-functions.md#rethrow_if_nested)|Приводит и создает исключение, если вложенный.|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Создает новый `terminate_handler`, подлежащий вызову при завершении программы.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Создает новый `unexpected_handler`, подлежащий вызову при обнаружении неожиданного исключения.|
|[заканчива](../standard-library/exception-functions.md#terminate)|Вызывает обработчик завершения.|
|[throw_with_nested](../standard-library/exception-functions.md#throw_with_nested)|Создает исключение, если вложенный.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Возвращает, **`true`** только если в настоящее время обрабатывается исключение.|
|[известно](../standard-library/exception-functions.md#unexpected)|Вызывает непредвиденный обработчик.|

### <a name="classes"></a>Классы

|name|Описание|
|-|-|
|[Класс bad_exception](../standard-library/bad-exception-class.md)|Этот класс описывает исключение, которое можно вызывать из `unexpected_handler`.|
|[Класс Exception](../standard-library/exception-class.md)|Этот класс служит базовым классом для всех исключений, создаваемых определенными выражениями и стандартной библиотекой C++.|
|[Класс nested_exception](../standard-library/nested-exception-class.md)|Класс описывает исключение, которое можно записать и сохранить для последующего использования.|

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
