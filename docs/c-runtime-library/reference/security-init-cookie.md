---
title: __security_init_cookie
ms.date: 11/04/2016
apiname:
- __security_init_cookie
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: c7b25e05b4574a7b397cd07d55000a5e53db58f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356840"
---
# <a name="securityinitcookie"></a>__security_init_cookie

Инициализирует глобальный cookie-файл безопасности.

## <a name="syntax"></a>Синтаксис

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Примечания

Глобальный cookie-файл безопасности используется для защиты от переполнения буфера в коде, скомпилированном с параметром [/GS (проверка безопасности буфера)](../../build/reference/gs-buffer-security-check.md), и в коде, в котором используется структурная обработка исключений. При входе в функцию с защитой от переполнения cookie-файл помещается в стек, а при выходе значение в стеке сравнивается с глобальным cookie-файлом. Любое различие между ними указывает, что произошло переполнение буфера, что приводит к немедленному завершению работы программы.

Как правило **__security_init_cookie** вызывается средой CRT при его инициализации. Если пропустить инициализацию CRT, например, если вы используете [/Entry](../../build/reference/entry-entry-point-symbol.md) для указания точки ввода, то нужно вызвать **__security_init_cookie** самостоятельно. Если **__security_init_cookie** не вызывается, глобальный файл cookie безопасности присвоено значение по умолчанию и нарушается защита от переполнения буфера. Так как злоумышленник может использовать это значение по умолчанию файл cookie, чтобы обойти проверку переполнения буфера, рекомендуется всегда вызывать **__security_init_cookie** при определении собственной точки входа.

Вызов **__security_init_cookie** необходимо вызывать до любой защищенную от переполнения вводе функции; в противном случае будет обнаружено ложное переполнение буфера. Подробнее: [Ошибка R6035 времени выполнения C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="example"></a>Пример

Примеры см. в разделе [Ошибка R6035 времени выполнения C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie** является расширением Майкрософт для стандартной библиотеки C времени выполнения. Сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[Microsoft Security Response Center](https://www.microsoft.com/msrc?rtc=1)
