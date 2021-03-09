---
title: Безопасные перегрузки шаблонов
description: Описание перегрузок шаблонов среды выполнения Microsoft C, предоставляющих функции с повышенным уровнем безопасности.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
ms.openlocfilehash: 69ddeed831bde26de23e0a29ece9f5550de8cf9f
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514529"
---
# <a name="secure-template-overloads"></a>Безопасные перегрузки шаблонов

Корпорация Майкрософт объявила устаревшими многие функции библиотеки C времени выполнения (CRT), заменив их версиями с более высоким уровнем безопасности. Например, `strcpy_s` является более безопасной заменой для `strcpy`. Устаревшие функции — это распространенные источники ошибок безопасности, так как они не предотвращают операции, которые могут перезаписывать память. По умолчанию компилятор выдает предупреждение об устаревании, если в коде присутствует любая из этих функций. CRT предоставляет для этих функций перегруженные шаблоны C++, которые помогают упростить переход к более безопасным вариантам.

Например, для этого фрагмента кода создается предупреждение, поскольку функция `strcpy` объявлена устаревшей:

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Предупреждение об устаревании сообщает вам, что используемый код может быть небезопасным. Если вы проверили, что код не может перезаписывать память, существует несколько вариантов. Вы можете просто игнорировать это предупреждение. Вы можете добавить символ `_CRT_SECURE_NO_WARNINGS` перед инструкциями include в заголовках CRT, чтобы подавить предупреждение. Также вы можете изменить код, заменив эту функцию на `strcpy_s`:

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

Перегруженные версии шаблонов предоставляют дополнительные возможности. Если вы определите `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` со значением "1", для стандартных функций CRT будет разрешено использование перегруженных шаблонов, которые автоматически используют более безопасные варианты. Если `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` имеет значение "1", никаких изменений в коде не требуется. Вызов функции `strcpy` в фоновом режиме заменяется вызовом функции `strcpy_s` с автоматической подстановкой аргумента размера.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Макрос `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` не влияет на функции, которые принимают число, например `strncpy` . Чтобы включить перегруженные шаблоны для функций, принимающих количество, определите `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` как значение "1". Однако перед этим действием следует убедиться, что код передает количество символов, а не размер буфера (частая ошибка). Кроме того, код, который явно записывает значение NULL в конец буфера после вызова функции, является необязательным, если вызывается безопасный вариант. Если требуется поведение усечения см. документацию [_TRUNCATE](../c-runtime-library/truncate.md).

> [!NOTE]
> Макрос `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` требует, чтобы `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` также был определен как значение "1". Если `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` определен как значение "1" и `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` определен как значение "0", в приложении не выполняются никакие перегрузки шаблонов.

Если вы определите `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` со значением "1", включается перегрузка шаблонов безопасными вариантами (имена которых оканчиваются на "_s"). В этом случае, если `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` определен как значение "1", в исходном коде необходимо сделать одно небольшое изменение.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Требуется изменить только имена функций (добавив к ним символы "_s"), а перегрузка шаблона автоматически подставит аргумент размера.

По умолчанию `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` и `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` определены как "0" (запрещено), а `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` определен как "1" (разрешено).

Эти перегрузки шаблонов работают только для статических массивов. Динамически выделенные буферы требуют дополнительных изменений исходного кода. В приведенных выше примерах:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; change it to
                       // strcpy_s(szBuf, 10, "test");
```

А также:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>См. также

[Функции безопасности в CRT](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Файлы среды выполнения C (CRT) и библиотеки стандартных библиотек C++ (STL) `.lib`](../c-runtime-library/crt-library-features.md)
