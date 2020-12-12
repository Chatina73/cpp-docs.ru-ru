---
description: Дополнительные сведения см. в статье поддержка COM компилятором.
title: Поддержка COM компилятора
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 1dd64d34b39a2b5cd2f0648d38deddf51e8541a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120468"
---
# <a name="compiler-com-support"></a>Поддержка COM компилятора

**Блок, относящийся только к системам Microsoft**

Компилятор Microsoft C++ может напрямую читать библиотеки типов модели COM и переводить содержимое в исходный код C++, который может быть добавлен в компиляцию. Расширения языка доступны для упрощения программирования COM на стороне клиента для классических приложений.

С помощью [директивы препроцессора #import](../preprocessor/hash-import-directive-cpp.md)компилятор может прочитать библиотеку типов и преобразовать ее в заголовочный файл C++, ОПИСЫВАЮЩИЙ COM-интерфейсы в качестве классов. Набор атрибутов `#import` доступен для пользовательского контроля содержимого в полученных файлах заголовка библиотеки типов.

Можно использовать идентификатор [UUID](../cpp/uuid-cpp.md) расширенного атрибута [__declspec](../cpp/declspec.md) , чтобы назначить глобально уникальный идентификатор (GUID) для COM-объекта. Ключевое слово [__uuidof](../cpp/uuidof-operator.md) можно использовать для извлечения идентификатора GUID, связанного с COM-объектом. **`__declspec`** Можно использовать другой атрибут [Property](../cpp/property-cpp.md), чтобы указать `get` `set` методы и для элемента данных COM-объекта.

Набор функций COM поддерживает глобальные функции и классы, предназначенные для поддержки `VARIANT` типов и `BSTR` , реализации смарт-указателей и инкапсуляции объекта Error, вызываемого `_com_raise_error` :

- [Глобальные функции компилятора COM](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Классы поддержки COM компилятора](../cpp/compiler-com-support-classes.md)<br/>
[Глобальные функции компилятора COM](../cpp/compiler-com-global-functions.md)
