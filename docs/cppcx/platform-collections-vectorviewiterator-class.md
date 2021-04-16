---
description: 'Дополнительные сведения о: Platform:: Collections:: VectorViewIterator Class'
title: Класс Platform::Collections::VectorViewIterator
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: fe5e1add183aa69bd4632355082c615378fd4050
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107576876"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Класс Platform::Collections::VectorViewIterator

Предоставляет итератор стандартной библиотеки шаблонов для объектов, производных от `IVectorView` интерфейса Среда выполнения Windows.

`ViewVectorIterator` — это итератор прокси-сервера, который хранит элементы типа `VectorProxy<T>`. Однако объект прокси-сервера практически никогда не отображается в пользовательском коде. Дополнительные сведения см. в разделе [Collections (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Синтаксис

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Параметры

*T*<br/>
Имя типа класса шаблона VectorViewIterator.

### <a name="members"></a>Элементы

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Описание|
|----------|-----------------|
|`difference_type`|Различие указателя (ptrdiff_t).|
|`iterator_category`|Категория итератора произвольного доступа (::std::random_access_iterator_tag).|
|`pointer`|Указатель на внутренний тип, необходимый для реализации итератора VectorViewIterator.|
|`reference`|Ссылка на внутренний тип, необходимый для реализации итератора VectorViewIterator.|
|`value_type`|Имя типа `T` .|

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[VectorViewIterator:: VectorViewIterator](#ctor)|Инициализирует новый экземпляр класса VectorViewIterator.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание|
|----------|-----------------|
|[Оператор VectorViewIterator:: operator-](#operator-minus)|Вычитает указанное количество элементов из текущего итератора, возвращая новый итератор, или вычитает указанный итератор из текущего итератора, возвращая количество элементов между итераторами.|
|[Оператор VectorViewIterator:: operator--](#operator-decrement)|Выполняет уменьшение текущего итератора VectorViewIterator.|
|[Оператор VectorViewIterator:: operator! =](#operator-inequality)|Указывает, отличен ли текущий объект VectorViewIterator от указанного объекта VectorViewIterator.|
|[Оператор VectorViewIterator:: operator *](#operator-dereference)|Извлекает ссылку на элемент, указанный текущим итератором VectorViewIterator.|
|[VectorViewIterator:: operator\[\]](#operator-at)|Извлекает ссылку на элемент, удаленный от текущего итератора VectorViewIterator на указанную величину смещения.|
|[Оператор VectorViewIterator:: operator +](#operator-plus)|Возвращает объект VectorViewIterator, указывающий на элемент с заданным смещением от указанного объекта VectorViewIterator.|
|[Оператор VectorViewIterator:: operator + +](#operator-increment)|Выполняет приращение текущего итератора VectorViewIterator.|
|[Оператор VectorViewIterator::operator+=](#operator-plus-equals)|Увеличивает текущий итератор VectorViewIterator на указанную величину смещения.|
|[Оператор VectorViewIterator:: operator<](#operator-less-than)|Указывает, действительно ли текущий объект VectorViewIterator меньше, чем указанный объект VectorViewIterator.|
|[Оператор VectorViewIterator:: operator \< =](#operator-less-than-or-equals)|Указывает, действительно ли текущий объект VectorViewIterator меньше указанного объекта VectorViewIterator или равен ему.|
|[Оператор VectorViewIterator:: operator-=](#operator-minus-assign)|Уменьшает текущий итератор VectorViewIterator на указанную величину смещения.|
|[Оператор VectorViewIterator:: operator = =](#operator-equality)|Указывает, равен ли текущий объект VectorViewIterator указанному объекту VectorViewIterator.|
|[Оператор VectorViewIterator:: operator>](#operator-greater-than)|Указывает, действительно ли текущий объект VectorViewIterator больше, чем указанный объект VectorViewIterator.|
|[Оператор VectorViewIterator:: operator->](#operator-arrow)|Извлекает адрес элемента, на который ссылается текущий итератор VectorViewIterator.|
|[Оператор VectorViewIterator:: operator>=](#operator-greater-than-or-equals)|Указывает, действительно ли текущий объект VectorViewIterator больше указанного объекта VectorViewIterator или равен ему.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`VectorViewIterator`

### <a name="requirements"></a>Требования

**Заголовок:** collection.h

**Пространство имен:** Platform::Collections

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>Оператор VectorViewIterator:: operator- &gt;

Извлекает адрес элемента, на который ссылается текущий итератор VectorViewIterator.

### <a name="syntax"></a>Синтаксис

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение элемента, на который ссылается текущий итератор VectorViewIterator.

Тип возвращаемого значения является неуказанным внутренним типом, необходимым для реализации этого оператора.

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a> Оператор VectorViewIterator:: operator--

Выполняет уменьшение текущего итератора VectorViewIterator.

### <a name="syntax"></a>Синтаксис

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Возвращаемое значение

Первый синтаксис выполняет уменьшение текущего итератора VectorViewIterator и возвращает его. Второй синтаксис возвращает копию текущего итератора VectorViewIterator, а затем выполняет уменьшение текущего итератора VectorViewIterator.

### <a name="remarks"></a>Замечания

Первый синтаксис выполняет уменьшение текущего итератора VectorViewIterator перед его использованием.

Второй синтаксис выполняет уменьшение текущего итератора VectorViewIterator после его использования. **`int`** Тип во втором синтаксисе указывает на операцию после декремента, а не на фактический целочисленный операнд.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>Оператор VectorViewIterator:: operator \*

Извлекает ссылку на элемент, указанный текущим итератором VectorViewIterator.

### <a name="syntax"></a>Синтаксис

```
reference operator*() const;
```

### <a name="return-value"></a>Возвращаемое значение

Элемент, указанный текущим итератором VectorIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a> Оператор VectorViewIterator:: operator = =

Указывает, равен ли текущий объект VectorViewIterator указанному объекту VectorViewIterator.

### <a name="syntax"></a>Синтаксис

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Параметры

*иной*<br/>
Другой объект VectorViewIterator.

### <a name="return-value"></a>Возвращаемое значение

**`true`** , если текущий объект `VectorViewIterator` равен *другому*; в противном случае — **`false`** .

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>Оператор VectorViewIterator:: operator &gt;

Указывает, действительно ли текущий объект VectorViewIterator больше, чем указанный объект VectorViewIterator.

### <a name="syntax"></a>Синтаксис

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Параметры

*иной*<br/>
Другой объект VectorViewIterator.

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если текущий VectorViewIterator больше *другого*; в противном случае — **`false`** .

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a> Оператор VectorViewIterator:: operator &gt; =

Указывает, что текущий объект `VectorViewIterator` больше или равен указанному `VectorViewIterator` .

### <a name="syntax"></a>Синтаксис

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Параметры

*иной*<br/>
Другой объект VectorViewIterator.

### <a name="return-value"></a>Возвращаемое значение

**`true`** , если текущий объект `VectorViewIterator` больше или равен *другому*; в противном случае — **`false`** .

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a> Оператор VectorViewIterator:: operator + +

Выполняет приращение текущего итератора VectorViewIterator.

### <a name="syntax"></a>Синтаксис

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Возвращаемое значение

Первый синтаксис выполняет приращение текущего итератора VectorViewIterator и возвращает его. Второй синтаксис возвращает копию текущего итератора VectorViewIterator, а затем выполняет приращение текущего итератора VectorViewIterator.

### <a name="remarks"></a>Замечания

Первый синтаксис выполняет приращение текущего итератора VectorViewIterator перед его использованием.

Второй синтаксис выполняет приращение текущего итератора VectorViewIterator после его использования. **`int`** Тип во втором синтаксисе указывает на операцию после приращения, а не на фактический целочисленный операнд.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a> Оператор VectorViewIterator:: operator! =

Указывает, отличен ли текущий объект VectorViewIterator от указанного объекта VectorViewIterator.

### <a name="syntax"></a>Синтаксис

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Параметры

*иной*<br/>
Другой объект VectorViewIterator.

### <a name="return-value"></a>Возвращаемое значение

**`true`** , если текущий `VectorViewIterator` не равен *другому*; в противном случае — **`false`** .

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>Оператор VectorViewIterator:: operator &lt;

Указывает, является ли текущий объект VectorIterator меньшим, чем указанный объект VectorIterator.

### <a name="syntax"></a>Синтаксис

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Параметры

*иной*<br/>
Другой объект `VectorIterator`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** , если текущий объект `VectorIterator` меньше *другого*; в противном случае — **`false`** .

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a> Оператор VectorViewIterator:: operator &lt; =

Указывает, является ли текущий объект `VectorIterator` меньшим или равным указанному `VectorIterator` .

### <a name="syntax"></a>Синтаксис

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Параметры

*иной*<br/>
Другой объект `VectorIterator`.

### <a name="return-value"></a>Возвращаемое значение

**`true`** , если текущий объект `VectorIterator` меньше или равен *другому*; в противном случае — **`false`** .

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a> Оператор VectorViewIterator:: operator-

Вычитает указанное количество элементов из текущего итератора, возвращая новый итератор, или вычитает указанный итератор из текущего итератора, возвращая количество элементов между итераторами.

### <a name="syntax"></a>Синтаксис

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Параметры

*n*<br/>
Количество элементов.

*иной*<br/>
Другой объект VectorViewIterator.

### <a name="return-value"></a>Возвращаемое значение

Синтаксис первого оператора возвращает объект VectorViewIterator, количество элементов которого меньше, чем у текущего объекта VectorViewIterator, на `n`. Синтаксис второго оператора возвращает количество элементов между текущим объектом VectorViewIterator и другим объектом VectorViewIterator, заданным параметром `other`.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a> Оператор VectorViewIterator:: operator + =

Увеличивает текущий итератор VectorViewIterator на указанную величину смещения.

### <a name="syntax"></a>Синтаксис

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Параметры

*n*<br/>
Целочисленная величина смещения.

### <a name="return-value"></a>Возвращаемое значение

Обновленный VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a> Оператор VectorViewIterator:: operator +

Возвращает объект VectorViewIterator, указывающий на элемент с заданным смещением от указанного объекта VectorViewIterator.

### <a name="syntax"></a>Синтаксис

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>Параметры

*T*<br/>
Во втором синтаксисе — имя типа объекта VectorViewIterator.

*n*<br/>
Целочисленная величина смещения.

*i*<br/>
Во втором синтаксисе — объект VectorViewIterator.

### <a name="return-value"></a>Возвращаемое значение

В первом синтаксисе — объект VectorViewIterator, указывающий на элемент с заданным смещением от текущего объекта VectorViewIterator.

Во втором синтаксисе — объект VectorViewIterator, указывающий на элемент с заданным смещением от начала `i` параметра.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a> Оператор VectorViewIterator:: operator-=

Уменьшает текущий итератор VectorIterator на указанную величину смещения.

### <a name="syntax"></a>Синтаксис

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Параметры

*n*<br/>
Целочисленная величина смещения.

### <a name="return-value"></a>Возвращаемое значение

Обновленный VectorIterator.

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a> VectorViewIterator:: operator\[\]

Извлекает ссылку на элемент, удаленный от текущего итератора VectorViewIterator на указанную величину смещения.

### <a name="syntax"></a>Синтаксис

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Параметры

*n*<br/>
Целочисленная величина смещения.

### <a name="return-value"></a>Возвращаемое значение

Элемент, удаленный от текущего итератора VectorViewIterator на `n`.

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a> Конструктор VectorViewIterator:: VectorViewIterator

Инициализирует новый экземпляр класса VectorViewIterator.

### <a name="syntax"></a>Синтаксис

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Параметры

*v*<br/>
Объект IVectorView \<T> .

### <a name="remarks"></a>Замечания

Первый пример синтаксиса является конструктором по умолчанию. Вторым примером синтаксиса является явный конструктор, который используется для создания VectorViewIterator из \<T> объекта IVectorView.

## <a name="see-also"></a>См. также раздел

[Пространство имен платформы](platform-namespace-c-cx.md)
