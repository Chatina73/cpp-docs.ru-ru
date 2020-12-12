---
description: 'Дополнительные сведения: литералы Chrono'
title: литералы chrono
ms.date: 11/04/2016
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
ms.openlocfilehash: 497094d920a25635496fb0aa30295d378571418c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325159"
---
# <a name="chrono-literals"></a>литералы chrono

(C++ 14) \<chrono> Заголовок определяет 12 [пользовательских литералов](../cpp/user-defined-literals-cpp.md) для упрощения использования литералов, представляющих часы, минуты, секунды, миллисекунды, микросекунды и наносекундах. Каждый определяемый пользователем литерал имеет целочисленное значение и значение перегрузки с плавающей запятой. Литералы определяются во встроенном пространстве имен literals::chrono_literals, которое автоматически переводится в область действия, если в ней присутствует пространство имен std::chrono.

## <a name="syntax"></a>Синтаксис

```cpp
inline namespace literals {
  inline namespace chrono_literals {
    // return integral hours
    constexpr chrono::hours operator"" h(unsigned long long Val);

    // return floating-point hours
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

    // return integral minutes
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

    // return floating-point minutes
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

    // return integral seconds
    constexpr chrono::seconds operator"" s(unsigned long long Val);

    // return floating-point seconds
    constexpr chrono::duration<double> operator"" s(long double Val);

    // return integral milliseconds
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

    // return floating-point milliseconds
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

    // return integral microseconds
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

    // return floating-point microseconds
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

    // return integral nanoseconds
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

    // return floating-point nanoseconds
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

  } // inline namespace chrono_literals
} // inline namespace literals
```

## <a name="return-value"></a>Возвращаемое значение

Литералы, которые принимают **`long long`** аргумент, возвращают значение или соответствующий тип. Литералы, которые принимают аргумент с плавающей запятой, возвращают [duration](../standard-library/duration-class.md).

## <a name="example"></a>Пример

В следующем примере демонстрируется использование литералов chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```
