---
description: 'Дополнительные сведения: утверждения и User-Supplied сообщения (C++)'
title: Утверждение и сообщения об ошибках, предоставленные пользователем (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
ms.openlocfilehash: eb0dd5d94ffe49017ecb89f53063993bedd12382
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319577"
---
# <a name="assertion-and-user-supplied-messages-c"></a>Утверждение и сообщения об ошибках, предоставленные пользователем (C++)

Язык C++ поддерживает три механизма обработки ошибок, которые помогут вам выполнить отладку приложения: [директива #error](../preprocessor/hash-error-directive-c-cpp.md), ключевое слово [static_assert](../cpp/static-assert.md) и [макрос assert, _ASSERT _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) . Все три механизма создают сообщения об ошибках, а два их них также проверяют утверждения программного обеспечения. Программное утверждение определяет условие, которое должно выполняться на определенном этапе работы программы. Если утверждение времени компиляции ложно, компилятор создает диагностическое сообщение и ошибку компиляции. Если утверждение времени выполнения ложно, операционная система выводит диагностическое сообщение и закрывает приложение.

## <a name="remarks"></a>Комментарии

Жизненный цикл приложения состоит из этапа предварительной обработки, этапа компиляции и этапа времени выполнения. Каждый механизм обработки ошибок обращается к отладочной информации, доступной в ходе одного из этих этапов. Для эффективной отладки выберите механизм, обеспечивающий требуемую информацию об этом этапе.

- [Директива #error](../preprocessor/hash-error-directive-c-cpp.md) действует во время предварительной обработки. Она безусловно выводит определенное пользователем сообщение и вызывает сбой компиляции с ошибкой. Сообщение может содержать текст, управляемый директивами препроцессора, но никакие результирующие выражения не вычисляются.

- Объявление [static_assert](../cpp/static-assert.md) действует во время компиляции. Оно проверяет утверждения программного обеспечения, которые определяются заданным пользователем целочисленным выражением, допускающим преобразование в логическое значение. Если выражение равно нулю (ложно), компилятор выдает определенное пользователем сообщение и компиляция завершается сбоем с ошибкой.

   **`static_assert`** Объявление особенно полезно для отладки шаблонов, так как аргументы шаблона могут включаться в указанное пользователем выражение.

- [Макрос assert, _ASSERT, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) макрос действует во время выполнения. Он вычисляет определенное пользователем выражение, и если результат равен нулю, система выводит диагностическое сообщение и закрывает приложение. Многие другие макросы, такие как[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) и _ASSERTE, похожи на этот макрос, но выдают различные системные и определяемые пользователем диагностические сообщения.

## <a name="see-also"></a>См. также раздел

[Директива #error (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[Макрос assert, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Макросы _ASSERT, _ASSERTE и _ASSERT_EXPR](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)<br/>
[static_assert](../cpp/static-assert.md)<br/>
[Макрос _STATIC_ASSERT](../c-runtime-library/reference/static-assert-macro.md)<br/>
[Шаблоны](../cpp/templates-cpp.md)
