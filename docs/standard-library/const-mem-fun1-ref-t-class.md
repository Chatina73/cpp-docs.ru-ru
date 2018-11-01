---
title: Класс const_mem_fun1_ref_t
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: e90ac09543c0704cf900e0fc5448e295034dcb66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516453"
---
# <a name="constmemfun1reft-class"></a>Класс const_mem_fun1_ref_t

Класс адаптера, который позволяет вызывать функцию-член **const**, принимающую один аргумент, как объект бинарной функции при инициализации с ссылочным аргументом.

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

*PM*<br/>
Указатель на функцию-член класса `Type` для преобразования в объект функции.

*left*<br/>
**Const** объекта, *Pm* вызывается функция-член.

*right*<br/>
Аргумент, который передается в *Pm*.

## <a name="return-value"></a>Возвращаемое значение

Адаптируемая бинарная функция.

## <a name="remarks"></a>Примечания

Класс шаблона сохраняет копию *Pm*, который должен быть указателем на функцию-член класса `Type`, в частном члене объекта. Он определяет функцию-член `operator()` как возвращающую ( `left`.\* Pm)( `right`) **const**.

## <a name="example"></a>Пример

Конструктор `const_mem_fun1_ref_t` обычно не используется напрямую; для адаптации функций-членов используется вспомогательная функция `mem_fun_ref`. Примеры использования адаптеров функций-членов см. в разделе [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).

## <a name="requirements"></a>Требования

**Заголовок:** \<functional>

**Пространство имен:** std

## <a name="see-also"></a>См. также

[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)<br/>
