---
title: Класс time_put_byname
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: 2da2bf4ea1c709b820c1a82dc20e288634139a83
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459994"
---
# <a name="timeputbyname-class"></a>Класс time_put_byname

Производный класс шаблона, описывающий объект, который можно использовать в качестве локального аспекта типа `time_put`\< CharType, OutputIterator >.

## <a name="syntax"></a>Синтаксис

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>Параметры

*_Locname*\
Имя языкового стандарта.

*_Refs*\
Начальное значение счетчика ссылок.

## <a name="remarks"></a>Примечания

Его поведение определяется с помощью [именованного](../standard-library/locale-class.md#name) языкового стандарта *_Locname*. Каждый конструктор инициализирует свой базовый объект с помощью [time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator >`_Refs`().

## <a name="requirements"></a>Требования

**Заголовок:** \<locale>

**Пространство имен:** std

## <a name="see-also"></a>См. также

[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
