---
description: 'Дополнительные сведения: strtol , wcstol , _strtol_l , _wcstol_l'
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 4/2/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- _o__strtol_l
- _o__wcstol_l
- _o_strtol
- _o_wcstol
api_location:
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: 8dd175929335533f8ade91450608db7f39bc0cc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288676"
---
# <a name="no-locstrtol-no-locwcstol-no-loc_strtol_l-no-loc_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Преобразование строк в **`long`** целочисленное значение.

## <a name="syntax"></a>Синтаксис

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Параметры

*Строка*\
Строка, завершающаяся символом NULL, для преобразования.

*end_ptr*\
Выходной параметр, заданный для указания символа после последнего интерпретируемого символа. Игнорируется, если **значение равно NULL**.

*из*\
Используемое числовое основание.

*языкового стандарта*\
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

**strtol**, **wcstol** , **_strtol_l** и **_wcstol_l** возвращают значение, представленное в виде *строки*. Они возвращают 0, если преобразование невозможно. Если представление вызовет переполнение, они возвращают **LONG_MAX** или **LONG_MIN** .

**errno** имеет значение, **ERANGE** Если происходит переполнение или потеря значимости. Он имеет значение, **EINVAL** Если *строка* имеет **значение NULL**. Или, если значение *base* не равно нулю и меньше 2 или больше 36. Дополнительные сведения о **ERANGE** , **EINVAL** и других кодах возврата см. в разделе [_dos errno , errno , _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Комментарии

**strtol** Функции, **wcstol** , **_strtol_l** и **_wcstol_l** преобразуют *строку* в **`long`** . Они прекращают чтение *строки* с первого символа, который не распознается как часть числа. Это может быть завершающий символ null или первый буквенно-цифровой символ, который больше или равен *base*.

**wcstol** и **_wcstol_l** — это версии и для расширенных символов **strtol** **_strtol_l** . Их *строковый* аргумент является строкой расширенных символов. Эти функции ведут себя одинаково в **strtol** и **_strtol_l** иным образом. Параметр категории языкового стандарта **LC_NUMERIC** определяет распознавание символа системы счисления (маркер дробной части или десятичной запятой) в *строке*. Функции **strtol** и **wcstol** используют текущий языковой стандарт. **_strtol_l** и **_wcstol_l** использовать переданный языковой стандарт. Дополнительные сведения см. в разделе [ setlocale ] и [языковой стандарт](../../c-runtime-library/locale.md).

Если *end_ptr* имеет **значение NULL**, он игнорируется. В противном случае указатель на символ, который остановил просмотр, хранится в расположении, на которое указывает *end_ptr*. Преобразование невозможно, если не найдены допустимые цифры или указан недопустимый базовый. Затем значение *строки* сохраняется в расположении, на которое указывает *end_ptr*.

**strtol***строка* должна указывать на строку следующего вида:

> [*пробел*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*буквенно-цифровые символы*]

Квадратные скобки ( `[ ]` ) окружают необязательные элементы. Фигурные скобки и вертикальная черта ( `{ | }` ) заключить альтернативные варианты для одного элемента. *пробелы* могут состоять из пробелов и символов табуляции, которые игнорируются. *буквенно-цифровые* буквы являются десятичными цифрами или буквами от a до z (или от a до z). Первый символ, который не соответствует этой форме, останавливает проверку. Если значение *base* — от 2 до 36, то оно используется в качестве основания для числа. Если значение *base* равно 0, начальные символы строки, на которую указывает *строка* , используются для определения базового объекта. Если первый символ равен 0, а второй символ — не "x" или "X", строка интерпретируется как восьмеричное целое число. Если первый символ — 0, а второй символ равен x или X, строка интерпретируется как шестнадцатеричное целое число. Если первый символ — от 1 до 9, строка интерпретируется как десятичное целое число. Буквам от "a" до "z" (или от "A" до "Z") присваиваются значения от 10 до 35. Сканирование допускает только те буквы, значения которых меньше *базового*. Первый символ за пределами диапазона основания останавливает сканирование. Например, предположим, что *строка* начинается с «01». Если значение *base* равно 0, то средство проверки предполагает, что это восьмеричное целое число. Символ "8" или "9" останавливает сканирование.

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> или \<wchar.h>|
|**_strtol_l**|\<stdlib.h>|
|**_wcstol_l**|\<stdlib.h> или \<wchar.h>|

**_strtol_l** Функции и **_wcstol_l** являются специфичными для Microsoft, а не частью стандартной библиотеки C. Дополнительные сведения о совместимости см. в статье [Compatibility](../compatibility.md).

## <a name="example"></a>Пример

См. пример для [strtod](strtod-strtod-l-wcstod-wcstod-l.md) .

## <a name="see-also"></a>См. также раздел

[Преобразование данных](../data-conversion.md)\
[Языкового стандарта](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[Функции типа "строка — числовое значение"](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
