---
description: 'Дополнительные сведения о: &lt; strstream&gt;'
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: e99a07df2a63b991232440f8dad0eb299d0e00b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183559"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Определяет несколько классов, поддерживающих операции iostream для последовательностей, хранящихся в выделенном массиве **`char`** объектов. Такие последовательности легко преобразуются в строки C и обратно.

## <a name="requirements"></a>Требования

**Заголовок:**\<strstream>

**Пространство имен:** std

## <a name="remarks"></a>Комментарии

Объекты типа `strstream` работают с **`char`** *, которые представляют собой строки на языке C. Используется [\<sstream>](../standard-library/sstream.md) для работы с объектами типа [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Классы в \<strstream> считаются устаревшими. Рекомендуется использовать вместо них классы в \<sstream>.

## <a name="members"></a>Элементы

### <a name="classes"></a>Классы

|name|Описание|
|-|-|
|[Класс strstreambuf](../standard-library/strstreambuf-class.md)|Класс описывает буфер потока, который управляет передачей элементов в последовательность элементов, хранящейся в объекте массива, и из нее **`char`** .|
|[Класс istrstream](../standard-library/istrstream-class.md)|Этот класс описывает объект, управляющий извлечением элементов и закодированных объектов из буфера потока класса [strstreambuf](../standard-library/strstreambuf-class.md).|
|[Класс ostrstream](../standard-library/ostrstream-class.md)|Этот класс описывает объект, управляющий вставкой элементов и закодированных объектов в буфер потока класса [strstreambuf](../standard-library/strstreambuf-class.md).|
|[Класс strstream](../standard-library/strstream-class.md)|Этот класс описывает объект, управляющий вставкой и извлечением элементов и закодированных объектов с помощью буфера потока класса [strstreambuf](../standard-library/strstreambuf-class.md).|

### <a name="functions"></a>Функции

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>См. также раздел

[\<strstream>](../standard-library/strstream.md)\
[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Программирование iostream](../standard-library/iostream-programming.md)\
[Соглашения iostream](../standard-library/iostreams-conventions.md)
