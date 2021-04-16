---
description: 'Дополнительные сведения о: &lt; Chrono&gt;'
title: '&lt;chrono&gt;'
ms.date: 05/07/2019
f1_keywords:
- <chrono>
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: 45e59f4c09371398cc5030b78b6378ad12d6a77b
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539504"
---
# `<chrono>`

Включите стандартный заголовок `<chrono>` для определения классов и функций, которые представляют и обрабатывают длительность и время ожидания.

Начиная с Visual Studio 2015, реализация `steady_clock` была изменена в соответствии со стандартными требованиями C++ для обеспечения стабильности и монотонности. `steady_clock` Теперь основан на `QueryPerformanceCounter()` и `high_resolution_clock` теперь является typedef для `steady_clock` . В результате в компиляторе Microsoft C++ `steady_clock::time_point` теперь есть `typedef` для `chrono::time_point<steady_clock>` ; однако это правило не обязательно для других реализаций.

## <a name="requirements"></a>Требования

**Заголовок:**`<chrono>`

**Пространство имен:** std

## <a name="members"></a>Члены

### <a name="classes"></a>Классы

|name|Описание|
|-|-|
|[`duration` См](../standard-library/duration-class.md)|Описывает тип, содержащий интервал времени.|
|[`time_point` См](../standard-library/time-point-class.md)|Описывает тип, представляющий момент времени.|

### <a name="structs"></a>Структуры

|Имя|Описание|
|-|-|
|[`common_type` Дереве](../standard-library/common-type-structure.md)|Описывает специализации шаблона класса [`common_type`](../standard-library/common-type-class.md) для создания экземпляров `duration` и `time_point` .|
|[`duration_values` Дереве](../standard-library/duration-values-structure.md)|Предоставляет конкретные значения для параметра `Rep` шаблона `duration`.|
|[`high_resolution_clock` struct](../standard-library/high-resolution-clock-struct.md)||
|[`steady_clock` struct](../standard-library/steady-clock-struct.md)|Представляет часы `steady`.|
|[`system_clock` Дереве](../standard-library/system-clock-structure.md)|Представляет объект *`clock type`* , основанный на часах системы в реальном времени.|
|[`treat_as_floating_point` Дереве](../standard-library/treat-as-floating-point-structure.md)|Указывает, может ли тип рассматриваться как тип с плавающей запятой.|

### <a name="functions"></a>Функции

|Имя|Описание|
|-|-|
|[`duration_cast`](../standard-library/chrono-functions.md#duration_cast)|Приводит объект `duration` к указанному типу.|
|[`time_point_cast`](../standard-library/chrono-functions.md#time_point_cast)|Приводит объект `time_point` к указанному типу.|

### <a name="operators"></a>Операторы

|Имя|Описание|
|-|-|
|[`operator-`](../standard-library/chrono-operators.md#operator-)|Оператор вычитания или отрицания объектов `duration` и `time_point`.|
|[`operator!=`](../standard-library/chrono-operators.md#op_neq)|Оператор неравенства, используемый с объектами `duration` или `time_point`.|
|[`operator modulo`](../standard-library/chrono-operators.md#op_modulo)|Оператор для операций вычисления остатка от деления над объектами `duration`.|
|[`operator*`](../standard-library/chrono-operators.md#op_star)|Оператор умножения для объектов `duration`.|
|[`operator/`](../standard-library/chrono-operators.md#op_div)|Оператор деления для объектов `duration`.|
|[`operator+`](../standard-library/chrono-operators.md#op_add)|Складывает объекты `duration` и `time_point`.|
|[`operator<`](../standard-library/chrono-operators.md#op_lt)|Определяет, справедливо ли, что один из объектов `duration` или `time_point` меньше, чем другой объект `duration` или `time_point`.|
|[`operator<=`](../standard-library/chrono-operators.md#op_lt_eq)|Определяет, справедливо ли, что один из объектов `duration` или `time_point` меньше или равен другому объекту `duration` или `time_point`.|
|[Оператор = =](../standard-library/chrono-operators.md#op_eq_eq)|Определяет, справедливо ли, что два объекта `duration` представляют интервалы времени, имеющие одинаковую длину, или, что два объекта `time_point` представляют один и тот же момент времени.|
|[`operator>`](../standard-library/chrono-operators.md#op_gt)|Определяет, справедливо ли, что один из объектов `duration` или `time_point` больше, чем другой объект `duration` или `time_point`.|
|[`operator>=`](../standard-library/chrono-operators.md#op_gt_eq)|Определяет, справедливо ли, что один из объектов `duration` или `time_point` больше или равен другому объекту `duration` или `time_point`.|

### <a name="typedefs-predefined-duration-types"></a>Определения типов (предопределенные типы длительности)

Дополнительные сведения о типах отношений, используемых в следующих определениях типов, см. в разделе [`<ratio>`](../standard-library/ratio.md) .

|Имя|Описание|
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|Синоним для `duration` типа с тактовым периодом 1 НС.|
|`typedef duration<long long, micro> microseconds;`|Синоним для `duration` типа с тактовым периодом 1 микросекунда.|
|`typedef duration<long long, milli> milliseconds;`|Синоним для `duration` типа с тактовым периодом 1 миллисекунда.|
|`typedef duration<long long> seconds;`|Синоним для `duration` типа с тактовым периодом в 1 секунду.|
|`typedef duration<int, ratio<60> > minutes;`|Синоним для `duration` типа с тактовым периодом в 1 минуту.|
|`typedef duration<int, ratio<3600> > hours;`|Синоним для `duration` типа с тактовым периодом в 1 час.|

### <a name="literals"></a>Литералы

**(C++ 11)** В `<chrono>` заголовке определяются следующие [пользовательские литералы](../cpp/user-defined-literals-cpp.md) , которые можно использовать для более удобного удобства, обеспечения безопасности типов и поддержки кода. Эти литералы определяются во `literals::chrono_literals` встроенном пространстве имен и находятся в области видимости, если находятся `std::chrono` в области.

|Объявление|Описание|
|-|-|
|`hours operator "" h(unsigned long long Val)`|Указывает часы как целочисленное значение.|
|`duration<double, ratio<3600> > operator "" h(long double Val)`|Указывает часы как значение с плавающей запятой.|
|`minutes (operator "" min)(unsigned long long Val)`|Указывает минуты как целочисленное значение.|
|`duration<double, ratio<60> > (operator "" min)( long double Val)`|Указывает минуты как значение с плавающей запятой.|
|`seconds operator "" s(unsigned long long Val)`|Указывает минуты как целочисленное значение.|
|`duration<double> operator "" s(long double Val)`|Указывает секунды как значение с плавающей запятой.|
|`milliseconds operator "" ms(unsigned long long Val)`|Указывает миллисекунды как целочисленное значение.|
|`duration<double, milli> operator "" ms(long double Val)`|Указывает миллисекунды как значение с плавающей запятой.|
|`microseconds operator "" us(unsigned long long Val)`|Указывает микросекунды как целочисленное значение.|
|`duration<double, micro> operator "" us(long double Val)`|Указывает микросекунды как значение с плавающей запятой.|
|`nanoseconds operator "" ns(unsigned long long Val)`|Указывает наносекунды как целочисленное значение.|
|`duration<double, nano> operator "" ns(long double Val)`|Указывает наносекунды как значение с плавающей запятой.|

В следующем примере демонстрируется использование литералов chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)
