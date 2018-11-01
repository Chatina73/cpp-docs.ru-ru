---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
ms.date: 11/04/2016
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
ms.openlocfilehash: 65d96d79a45e05e4b371315c0612ed086f6ea2a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452264"
---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Преобразует время UTC, представленное **структуры** **tm** время в формате UTC, представленные **time_t** типа.

## <a name="syntax"></a>Синтаксис

```C
time_t _mkgmtime(
   struct tm* timeptr
);
__time32_t _mkgmtime32(
   struct tm* timeptr
);
__time64_t _mkgmtime64(
   struct tm* timeptr
);
```

### <a name="parameters"></a>Параметры

*timeptr*<br/>
Указатель на то время UTC, что **структуры** **tm** для преобразования.

## <a name="return-value"></a>Возвращаемое значение

Количество для типа **__time32_t** или **__time64_t** представляющий количество секунд, истекших после полуночи 1 января 1970 года в формате UTC (UTC). Если дата находится вне диапазона (см. в разделе "Примечания") или входные данные не могут восприниматься как допустимое время, возвращается значение-1.

## <a name="remarks"></a>Примечания

**_Mkgmtime32** и **_mkgmtime64** функции преобразовать время в формате UTC для **__time32_t** или **__time64_t** тип, представляющий время в В ФОРМАТЕ UTC. Чтобы преобразовать время в формате UTC в местное время, используйте **mktime**, **_mktime32**, и **_mktime64** вместо этого.

**_mkgmtime** — это встроенная функция, результатом которого является **_mkgmtime64**, и **time_t** эквивалентен **__time64_t**. Если вам нужно заставить компилятор интерпретировать **time_t** как старое 32-разрядное **time_t**, можно определить **_USE_32BIT_TIME_T**. Это не рекомендуется, поскольку приложение может завершиться ошибкой после 18 января 2038 года (максимальный диапазон 32-разрядного **time_t**), и абсолютно не допускается на 64-разрядных платформах.

Переданная структура времени будет необходимо изменить следующим образом, так же, как они изменяются с помощью **_mktime** функции: **tm_wday** и **tm_yday** поля задаются новых значения на основе значений из **tm_mday** и **tm_year**. При указании **tm** структуры времени, задайте **tm_isdst** поле:

- нуль (0), чтобы указать, что действует стандартное время;

- значение больше нуля, чтобы указать, что действует переход на зимнее время;

- значение меньше нуля, чтобы указать, что код библиотеки времени выполнения языка C должен вычислить, действует ли стандартное время или переход на зимнее время.

Библиотека времени выполнения языка C использует переменную среды TZ для определения правильного летнего времени. Если TZ не задана, для получения верного регионального поведения по летнему времени отправляется запрос операционной системе. **tm_isdst** — это обязательное поле. Если не задано, его значение не определено и возвращаемое значение из **mktime** непредсказуем.

Диапазон **_mkgmtime32** функция — от полуночи 1 января 1970 года, время в формате UTC 23:59:59 18 января 2038 года в формате UTC. Диапазон **_mkgmtime64** — от полуночи 1 января 1970 года, UTC до 23:59:59 31 декабря 3000 года в формате UTC. Дата вне диапазона приводит возвращаемое значение-1. Диапазон **_mkgmtime** зависит от того **_USE_32BIT_TIME_T** определен. Если не определено (по умолчанию), диапазон — такой **_mkgmtime64**; в противном случае диапазон ограничен 32-разрядным диапазоном **_mkgmtime32**.

Обратите внимание, что **gmtime** и **localtime** используют для преобразования один статически выделенный буфер. Если вы предоставляете этот буфер **mkgmtime**, предыдущее содержимое удаляется.

## <a name="example"></a>Пример

```C
// crt_mkgmtime.c
#include <stdio.h>
#include <time.h>

int main()
{
    struct tm t1, t2;
    time_t now, mytime, gmtime;
    char buff[30];

    time( & now );

    _localtime64_s( &t1, &now );
    _gmtime64_s( &t2, &now );

    mytime = mktime(&t1);
    gmtime = _mkgmtime(&t2);

    printf("Seconds since midnight, January 1, 1970\n");
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);

    /* Use asctime_s to display these times. */

    _localtime64_s( &t1, &mytime );
    asctime_s( buff, sizeof(buff), &t1 );
    printf( "Local Time: %s\n", buff );

    _gmtime64_s( &t2, &gmtime );
    asctime_s( buff, sizeof(buff), &t2 );
    printf( "Greenwich Mean Time: %s\n", buff );

}
```

### <a name="sample-output"></a>Пример результатов выполнения

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

В следующем примере показано, как неполная структура заполняется вычисленными значения дня недели и дня года.

```C
// crt_mkgmtime2.c
#include <stdio.h>
#include <time.h>
#include <memory.h>

int main()
{
    struct tm t1, t2;
    time_t gmtime;
    char buff[30];

    memset(&t1, 0, sizeof(struct tm));
    memset(&t2, 0, sizeof(struct tm));

    t1.tm_mon = 1;
    t1.tm_isdst = 0;
    t1.tm_year = 103;
    t1.tm_mday = 12;

    // The day of the week and year will be incorrect in the output here.
    asctime_s( buff, sizeof(buff), &t1);
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

    gmtime = _mkgmtime(&t1);

    // The correct day of the week and year were determined.
    asctime_s( buff, sizeof(buff), &t1);
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

}
```

### <a name="output"></a>Вывод

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>См. также

[Управление временем](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
