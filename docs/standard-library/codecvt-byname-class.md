---
description: 'Дополнительные сведения о: codecvt_byname классе'
title: Класс codecvt_byname
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_byname
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
ms.openlocfilehash: 526988f46b729e1a3d4ab6892d2c8f1fecba78a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234076"
---
# <a name="codecvt_byname-class"></a>Класс codecvt_byname

Шаблон производного класса, который описывает объект, который может служить в качестве аспекта сортировки для данного языкового стандарта, позволяя получать информацию, относящуюся к области культуры, в отношении преобразований.

## <a name="syntax"></a>Синтаксис

```cpp
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```

```cpp
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```

```cpp
protected:
    virtual ~codecvt_byname();

};
```

### <a name="parameters"></a>Параметры

*_Locname*\
Именованный языковой стандарт.

*_Refs*\
Начальное значение счетчика ссылок.

## <a name="remarks"></a>Комментарии

Аспекты Byname создаются автоматически при создании именованного языкового стандарта.

Его поведение определяется с помощью именованного языкового стандарта *_Locname*. Каждый конструктор инициализирует свой базовый объект с помощью [codecvt](../standard-library/codecvt-class.md) \<CharType, Byte, StateType> ( `_Refs` ).

## <a name="requirements"></a>Требования

**Заголовок:**\<locale>

**Пространство имен:** std

## <a name="see-also"></a>См. также раздел

[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
