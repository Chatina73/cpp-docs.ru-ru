---
title: Поддержка COM компилятора
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: f0b1d6280dc27641287de8fe539cd3a148048245
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154842"
---
# <a name="compiler-com-support"></a>Поддержка COM компилятора

## <a name="microsoft-specific"></a>Блок, относящийся только к системам Microsoft

Компилятор Visual C++ может непосредственно считать библиотеки типов COM-модели и преобразовать их содержимое в исходный код С++б который можно включить в компиляцию. Расширения языка позволяют выполнять программирование COM-модели на клиентской стороне.

С помощью [директиву препроцессора #import](../preprocessor/hash-import-directive-cpp.md), компилятор может прочитать библиотеку типов и преобразовать его в файл заголовка C++, который описывает COM интерфейсы как классы. Набор атрибутов `#import` доступен для пользовательского контроля содержимого в полученных файлах заголовка библиотеки типов.

Можно использовать [__declspec](../cpp/declspec.md) расширенный атрибут [uuid](../cpp/uuid-cpp.md) присвоить глобально уникальный идентификатор (GUID) для COM-объекта. Ключевое слово [__uuidof](../cpp/uuidof-operator.md) может использоваться для извлечения идентификатора GUID, связанный с COM-объекта. Другой **__declspec** атрибут, [свойство](../cpp/property-cpp.md), можно использовать для указания `get` и `set` методы для элемента данных COM-объекта.

Набор глобальных функций поддержки COM и классов обеспечивает поддержку `VARIANT` и `BSTR` типы, реализации интеллектуальных указателей и инкапсуляции объекта ошибок, вызванных `_com_raise_error`:

- [Глобальные функции COM-модели компилятора](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Классы поддержки модели COM компилятора](../cpp/compiler-com-support-classes.md)<br/>
[Глобальные функции COM-модели компилятора](../cpp/compiler-com-global-functions.md)