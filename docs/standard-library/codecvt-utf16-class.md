---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: ca66a3273567a8d30a982211a6e977c129b00f5f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459712"
---
# <a name="codecvtutf16"></a>codecvt_utf16

Представляет аспект [языкового стандарта](../standard-library/locale-class.md), который выполняет преобразование между расширенными символами в кодировке UCS-2 или UCS-4 и потоком байтов в кодировке UTF-16LE или UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Параметры

*Elem*\
Тип двухбайтового элемента.

*макскоде*\
Максимальное количество символов для аспекта языкового стандарта.

*Режима*\
Сведения о конфигурации для аспекта языкового стандарта.

## <a name="remarks"></a>Примечания

Этот класс шаблона выполняет преобразование между расширенными символами в кодировке UCS-2 или UCS-4 и потоком байтов в кодировке UTF-16LE, если Mode & little_endian, или в кодировке UTF-16BE в ином случае.

Поток байтов должен записываться в двоичный файл; при записи в текстовый файл он может быть поврежден.

## <a name="requirements"></a>Требования

Заголовок: \<codecvt >

Пространство имен: STD