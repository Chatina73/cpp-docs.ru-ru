---
description: 'Дополнительные сведения о: const_mem_fun1_ref_t классе'
title: Класс const_mem_fun1_ref_t
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: f2d8b96c3888e3b7b07b5cccef8ce58cdedb6732
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324949"
---
# <a name="const_mem_fun1_ref_t-class"></a>Класс const_mem_fun1_ref_t

Класс адаптера, который позволяет **`const`** вызывать функцию-член, которая принимает один аргумент, как объект бинарной функции при инициализации со ссылочным аргументом. Не рекомендуется использовать в C++ 11, удалено в C++ 17.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Result, class Type, class Arg>
    class const_mem_fun1_ref_t
        : public binary_function<Type, Arg, Result>
{
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
};
```

### <a name="parameters"></a>Параметры

*PM*\
Указатель на функцию-член класса `Type` для преобразования в объект функции.

*слева*\
**`const`** Объект, для которого вызывается функция-член *PM* .

*Правильно*\
Аргумент, присваиваемый *PM*.

## <a name="return-value"></a>Возвращаемое значение

Адаптируемая бинарная функция.

## <a name="remarks"></a>Комментарии

Шаблон класса сохраняет копию *PM*, которая должна быть указателем на функцию-член класса `Type` в закрытом объекте-члене. Он определяет свою функцию `operator()` -член как возвращающую ( `left` . \* *PM*) ( `right` ) **`const`** .

## <a name="example"></a>Пример

Конструктор `const_mem_fun1_ref_t` обычно не используется напрямую; для адаптации функций-членов используется вспомогательная функция `mem_fun_ref`. Примеры использования адаптеров функций-членов см. в разделе [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).
