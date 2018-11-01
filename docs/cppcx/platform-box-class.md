---
title: Класс Platform::Box
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 387fa03caebed599d51292dd1b6d18ad4afd921c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429077"
---
# <a name="platformbox-class"></a>Класс Platform::Box

Позволяет сохранять тип значения, такой как `Windows::Foundation::DateTime` , или скалярный тип, такой как `int` , в типе `Platform::Object` . Как правило, нет необходимости использовать `Box` явным образом, так как процесс упаковки выполняется неявно при приведении значения типа к `Object^`.

### <a name="syntax"></a>Синтаксис

```cpp
ref class Box abstract;
```
  ### <a name="remarks"></a>Примечания

### <a name="requirements"></a>Требования

**Заголовок:** vccorlib.h

**Пространство имен:** Platform
|Член|Описание|
|------------|-----------------|
|[Box](#ctor)|Создает объект `Box`, который может инкапсулировать значение указанного типа.|
|[оператор поле&lt;const T&gt;^](#box-const-t)|Позволяет осуществлять преобразования-упаковки класса значений `const` `T` или `enum` класса `T` в `Box<T>`.|
|[оператор поле&lt;const volatile T&gt;^](#box-const-volatile-t)|Позволяет осуществлять преобразования-упаковки из класса значений `const volatile` `T` или `enum` типа `T` в `Box<T>`. |
|[оператор поле&lt;T&gt;^](#box-t)|Позволяет осуществлять преобразования-упаковки класса значений `T` в `Box<T>`.|
|[оператор поле&lt;volatile T&gt;^](#box-volatile-t)|Позволяет осуществлять преобразования-упаковки из класса значений `volatile` `T` или `enum` типа `T` в `Box<T>`.|
|[Box::operator T](#t)|Позволяет осуществлять преобразования-упаковки класса значений `T` или `enum` класса `T` в `Box<T>`.|
## <a name="ctor"></a> Конструктор Box::Box

Создает `Box` который может инкапсулировать значение указанного типа. | |[ Значение свойства](#value)| Возвращает значение, которое инкапсулируется в `Box` объекта. |
### <a name="syntax"></a>Синтаксис

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Параметры

*valueArg*<br/>
Тип упаковываемого значения — например, `int`, `bool`, `float64`, `DateTime`.

## <a name="box-const-t"></a> Box::operator Box&lt;const T&gt;^ оператор

Позволяет осуществлять преобразования-упаковки класса значений `const` `T` или `enum` класса `T` в `Box<T>`.

### <a name="syntax"></a>Синтаксис

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Параметры

*T*<br/>
Любой класс значений, структура значений или тип перечисления. Включает встроенные типы в [пространство имен по умолчанию](../cppcx/default-namespace.md).

### <a name="return-value"></a>Возвращаемое значение

Объект `Platform::Box<T>^` экземпляр, представляющий исходное значение, упакованное в класс ссылки.

## <a name="box-const-volatile-t"></a> Box::operator Box&lt;const volatile T&gt;^ оператор

Позволяет осуществлять преобразования-упаковки из класса значений `const volatile` `T` или `enum` типа `T` в `Box<T>`.

### <a name="syntax"></a>Синтаксис

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Параметры

*T*<br/>
Любой тип перечисления, класс значений или структура значений. Включает встроенные типы в [пространство имен по умолчанию](../cppcx/default-namespace.md).

### <a name="return-value"></a>Возвращаемое значение

Объект `Platform::Box<T>^` экземпляр, представляющий исходное значение, упакованное в класс ссылки.

## <a name="box-t"></a> Box::operator Box&lt;T&gt;^ оператор

Позволяет осуществлять преобразования-упаковки класса значений `T` в `Box<T>`.

### <a name="syntax"></a>Синтаксис

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Параметры

*T*<br/>
Любой тип перечисления, класс значений или структура значений. Включает встроенные типы в [пространство имен по умолчанию](../cppcx/default-namespace.md).

### <a name="return-value"></a>Возвращаемое значение

Объект `Platform::Box<T>^` экземпляр, представляющий исходное значение, упакованное в класс ссылки.

## <a name="box-volatile-t"></a> Box::operator Box&lt;volatile T&gt;^ оператор

Позволяет осуществлять преобразования-упаковки из класса значений `volatile` `T` или `enum` типа `T` в `Box<T>`.

### <a name="syntax"></a>Синтаксис

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Параметры

*T*<br/>
Любой тип перечисления, класс значений или структура значений. Включает встроенные типы в [пространство имен по умолчанию](../cppcx/default-namespace.md).

### <a name="return-value"></a>Возвращаемое значение

Объект `Platform::Box<T>^` экземпляр, представляющий исходное значение, упакованное в класс ссылки.

## <a name="t"></a>  Оператор Box::operator T

Позволяет осуществлять преобразования-упаковки класса значений `T` или `enum` класса `T` в `Box<T>`.

### <a name="syntax"></a>Синтаксис

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Параметры

*T*<br/>
Любой тип перечисления, класс значений или структура значений. Включает встроенные типы в [пространство имен по умолчанию](../cppcx/default-namespace.md).

### <a name="return-value"></a>Возвращаемое значение

Объект `Platform::Box<T>^` экземпляр, представляющий исходное значение, упакованное в класс ссылки.

## <a name="value"></a> Свойство Box::value

Возвращает значение, которое инкапсулируется в объекте `Box`.

### <a name="syntax"></a>Синтаксис

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает упакованное значение с тем же типом, который у него был до упаковки.

## <a name="see-also"></a>См. также

[Пространство имен Platform](../cppcx/platform-namespace-c-cx.md)<br/>
[Упаковка-преобразование](../cppcx/boxing-c-cx.md)