---
description: 'Дополнительные сведения о: fwrite'
title: fwrite
ms.date: 4/2/2020
api_name:
- fwrite
- _o_fwrite
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: 6d650e03af95b527c3e0752f975d8dceb03e5eb8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273661"
---
# <a name="fwrite"></a>fwrite

Записывает данные в поток.

## <a name="syntax"></a>Синтаксис

```C
size_t fwrite(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Параметры

*двойной*<br/>
Указатель на записываемые данные.

*size*<br/>
Размер элемента, в байтах.

*count*<br/>
Максимальное число записываемых элементов.

*вышестоящий*<br/>
Указатель на структуру **FILE**.

## <a name="return-value"></a>Возвращаемое значение

**fwrite** возвращает число фактически записанных полных элементов, что может быть меньше *количества* при возникновении ошибки. Кроме того, в случае возникновения ошибки невозможно определить индикатор положения файла. Если *Stream* или *buffer* является пустым указателем или если в режиме Юникода указано нечетное число байтов, то функция вызывает обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эта функция **устанавливает** **еинвал** и возвращает 0.

## <a name="remarks"></a>Комментарии

Функция **fwrite** записывает до количества элементов *, длина каждой из которых равна* *количеству* из *буфера* в *поток* вывода. Указатель файла, связанный с *потоком* (при его наличии) увеличивается на число фактически записанных байтов. Если *поток* открыт в текстовом режиме, каждый перевод строки заменяется парой символов возврата каретки и перевода строки. Замена не влияет на возвращаемое значение.

Если *поток* открыт в режиме преобразования Юникода, например если *поток* открыт с помощью вызова **fopen** и параметра mode, который включает **CCS = Unicode**, **CCS = UTF-16LE** или **CCS = UTF-8**, или, если режим был изменен на режим преобразования в юникоде с помощью **_setmode** и параметр mode, включающий **_O_WTEXT**, **_O_U16TEXT** или **_O_U8TEXT**,*буфер* интерпретируется как указатель на массив **`wchar_t`** , содержащий данные UTF-16. Попытка записи нечетного числа байт в этом режиме приводит к возникновению ошибки проверки параметра.

Поскольку эта функция блокирует вызывающий поток, она потокобезопасна. Сведения о версии без блокировки см. в разделе **_fwrite_nolock**.

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

## <a name="requirements"></a>Требования

|Функция|Обязательный заголовок|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

См. пример для [fread](fread.md).

## <a name="see-also"></a>См. также раздел

[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
