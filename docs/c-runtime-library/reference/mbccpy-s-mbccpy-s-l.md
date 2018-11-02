---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 11/04/2016
apiname:
- _mbccpy_s
- _mbccpy_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
ms.openlocfilehash: f9a7554630bd3b46196358c01c21b99978c53e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575068"
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s, _mbccpy_s_l

Копирует один многобайтовый символ из одной строки в другую. Это версии функций [_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md) с усовершенствованной безопасностью, как описано в разделе [Функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Этот API нельзя использовать в приложениях, выполняемых в среде выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>Параметры

*dest*<br/>
Место назначения копирования.

*buffSizeInBytes*<br/>
Размер буфера назначения.

*pCopied*<br/>
Заполняется числом скопированных байтов (1 или 2 в случае успешного выполнения). Передайте **NULL** вы не заботитесь о числе.

*src*<br/>
Многобайтовый символ для копирования.

*locale*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Возвращает нуль в случае успеха или код ошибки в случае неудачи. Если *src* или *dest* — **NULL**, или если более чем **buffSizeinBytes** байтов будут скопированы *dest*, Затем вызывается обработчик недопустимого параметра, как описано в разделе [проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, функции возвращают **EINVAL** и **errno** присваивается **EINVAL**.

## <a name="remarks"></a>Примечания

**_Mbccpy_s** функция копирует один Многобайтовый символ из *src* для *dest*. Если *src* не указывает на старший байт многобайтового символа, как определяется неявный вызов [_ismbblead](ismbblead-ismbblead-l.md), один байт, *src* указывает копируется. Если *src* указывает на старший байт, однако следующий байт соответствует 0 и таким образом недопустимые, а затем копируется 0 *dest*, **errno** присваивается **EILSEQ**и Возвращает **EILSEQ**.

**_mbccpy_s** не добавляет завершающий нуль-символ; тем не менее, если *src* указывает на нуль-символом, а затем копируется значение null для *dest* (это просто обычное — однобайтовое копирование).

Значение в *pCopied* заполняется числом скопированных байтов. В случае успешного выполнения операции возможны значения 1 и 2. Если **NULL** передается в, этот параметр учитывается.

|*src*|скопировать *dest*|*pCopied*|Возвращаемое значение|
|-----------|----------------------|---------------|------------------|
|не старший байт|не старший байт|1|0|
|0|0|1|0|
|старший байт, за которым следует не 0|старший байт, за которым следует не 0|2|0|
|старший байт, за которым следует 0|0|1|**EILSEQ**|

Обратите внимание, что вторая строка представляет собой особый случай первой. Также Обратите внимание, что в таблице предполагается *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** использует текущий языковой стандарт для любого поведения, зависящего от языкового стандарта. **_mbccpy_s_l** идентична **_mbccpy_s** за исключением того, что **_mbccpy_s_l** использует переданный параметр языкового стандарта для любого поведения, зависящего от языкового стандарта.

В C++ использование этих функций упрощено шаблонными перегрузками; перегрузки могут определить длину буфера автоматически, устраняя необходимость указывать аргумент size. Дополнительные сведения см. в разделе [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста

|Подпрограмма Tchar.h|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Сопоставляется макросу или встраиваемой функции.|**_mbccpy_s**|Сопоставляется макросу или встраиваемой функции.|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[Языковой стандарт](../../c-runtime-library/locale.md)<br/>
[Интерпретация последовательностей многобайтовых символов](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
