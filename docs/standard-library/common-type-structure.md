---
description: 'Дополнительные сведения: структура common_type'
title: Структура common_type
ms.date: 11/04/2016
f1_keywords:
- chrono/std::common_type
ms.assetid: 2b42722c-c3dc-4d62-8613-0271e52b6f00
ms.openlocfilehash: 09d0460235286cb1a08d2d06d6c5a5cba7500617
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325053"
---
# <a name="common_type-structure"></a>Структура common_type

Описывает специализации шаблона класса [common_type](../standard-library/common-type-class.md) для создания экземпляров [длительности](../standard-library/duration-class.md) и [time_point](../standard-library/time-point-class.md).

## <a name="syntax"></a>Синтаксис

```cpp
template <class Rep1, class Period1,
    class Rep2, class Period2>
struct common_type
<chrono::duration<Rep1, Period1>,
chrono::duration<Rep2, Period2>>;

template <class Clock,
    class Duration1, class Duration2>
struct common_type
<chrono::time_point<Clock, Duration1>,
chrono::time_point<Clock, Duration2>>;
```

## <a name="requirements"></a>Требования

**Заголовок:**\<chrono>

**Пространство имен:** std

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
