---
title: _configthreadlocale
ms.date: 11/04/2016
apiname:
- _configthreadlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _configthreadlocale
- configthreadlocale
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
ms.openlocfilehash: 99e10a0330ba4880ea181e9fe3d56f3fb6bd6493
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326047"
---
# <a name="configthreadlocale"></a>_configthreadlocale

Настраивает параметры языкового стандарта для каждого потока.

## <a name="syntax"></a>Синтаксис

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>Параметры

*per_thread_locale_type*<br/>
Задаваемый параметр. Один из параметров, перечисленных в следующей таблице.

## <a name="return-value"></a>Возвращаемое значение

Предыдущее состояние языкового стандарта отдельного потока (**_DISABLE_PER_THREAD_LOCALE** или **_ENABLE_PER_THREAD_LOCALE**), или значение -1 в случае сбоя.

## <a name="remarks"></a>Примечания

**_Configurethreadlocale** функция используется для управления использованием языковых стандартов для конкретного потока. Использовать один из следующих *per_thread_locale_type* параметры для определения состояния языкового стандарта отдельного потока:

| Параметр | Описание |
|-|-|
| **_ENABLE_PER_THREAD_LOCALE** | В текущем потоке будет использоваться заданный конкретно для него языковой стандарт. Последующие вызовы **setlocale** в этом потоке влияют только собственный языковой стандарт потока. |
| **_DISABLE_PER_THREAD_LOCALE** | В текущем потоке будет использоваться глобальный языковой стандарт. Последующие вызовы **setlocale** в этом потоке влияют на другие потоки, использующие глобальный языковой стандарт. |
| **0** | Извлекает текущую настройку для данного потока. |

Эти функции влияют на поведение **setlocale**, **_tsetlocale**, **_wsetlocale**, и **_setmbcp**. Если языковой стандарт отдельного потока — отключено, любой последующий вызов **setlocale** или **_wsetlocale** изменяет языковой стандарт всех потоков, использующих глобальный языковой стандарт. Если языковой стандарт отдельного потока включен, **setlocale** или **_wsetlocale** влияет только на языковой стандарт текущего потока.

Если вы используете **_configurethreadlocale** чтобы языкового стандарта отдельного потока, мы рекомендуем вызывать **setlocale** или **_wsetlocale** для задания предпочтительного языкового стандарта в этом потоке сразу же после этого.

Если *per_thread_locale_type* не является одним из значений в списке в таблице, эта функция вызывает обработчик недопустимого параметра, как описано в разделе [проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эта функция задает **errno** для **EINVAL** и возвращает – 1.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_configthreadlocale**|\<locale.h>|

## <a name="example"></a>Пример

```cpp
// crt_configthreadlocale.cpp
//
// This program demonstrates the use of _configthreadlocale when
// using two independent threads.
//
// Compile by using: cl /EHsc /W4 crt_configthreadlocale.cpp

#include <locale.h>
#include <mbctype.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date and time in the current
// locale's format.
int get_time(unsigned char* str)
{
    __time64_t  ltime;
    struct tm   thetime;

    // Retieve the time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // using %#x is the long date representation,
    // appropriate to the current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm*)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to German
// and prints the time.
unsigned __stdcall SecondThreadFunc( void* /*pArguments*/ )
{
    unsigned char str[BUFF_SIZE];

    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the thread code page
    _setmbcp(_MB_CP_ANSI);

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "German"));

    // Retrieve the time string from the helper function
    if (get_time(str) == 0)
    {
        printf("The time in German locale is: '%s'\n", str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread spawns a second thread (above) and then
// sets the locale to English and prints the time.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Retrieve the time string from the helper function
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "English"));

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      NULL, 0, &threadID );

    if (get_time(str) == 0)
    {
        // Retrieve the time string from the helper function
        printf("The time in English locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to English_United States.1252.
The time in English locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to German_Germany.1252.
The time in German locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>См. также

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
[Языковой стандарт](../../c-runtime-library/locale.md)<br/>
[Многопоточность и языковые стандарты](../../parallel/multithreading-and-locales.md)<br/>
