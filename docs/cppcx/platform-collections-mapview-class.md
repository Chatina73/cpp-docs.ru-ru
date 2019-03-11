---
title: Класс Platform::Collections::MapView
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
ms.openlocfilehash: 1e38865f1d43edac4fc895052f1ea1b5a54a34ab
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749260"
---
# <a name="platformcollectionsmapview-class"></a>Класс Platform::Collections::MapView

Представляет доступное только для чтения представление на *карте*, которое является коллекцией пар "ключ-значение".

## <a name="syntax"></a>Синтаксис

```
template <
   typename K,
   typename V,
   typename C = ::std::less<K>>
ref class MapView sealed;
```

#### <a name="parameters"></a>Параметры

*K*<br/>
Тип ключа в паре "ключ-значение".

*V*<br/>
Тип значения в паре "ключ-значение".

*C*<br/>
Тип, предоставляющий объект функции, который может сравнить значения двух элементов как ключи сортировки, чтобы определить их относительный порядок в объекте MapView. По умолчанию [std::less\<K >](../standard-library/less-struct.md).

### <a name="remarks"></a>Примечания

MapView — это конкретная реализация C++ [Windows::Foundation::Collections::IMapView \<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) интерфейс, который передается через двоичный интерфейс приложений (ABI). Дополнительные сведения см. в разделе [Collections (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание:|
|----------|-----------------|
|[MapView::MapView](#ctor)|Инициализирует новый экземпляр класса MapView.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание:|
|----------|-----------------|
|[MapView::First](#first)|Возвращает итератор, который инициализируется первым элементом в представлении карты.|
|[MapView::HasKey](#haskey)|Определяет, содержит ли текущий объект MapView указанный ключ.|
|[MapView::Lookup](#lookup)|Извлекает элемент по указанному ключу в текущем объекте MapView.|
|[MapView::Size](#size)|Возвращает количество элементов в текущем объекте MapView.|
|[MapView::Split](#split)|Разделяет исходный объект MapView на два объекта MapView.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`MapView`

### <a name="requirements"></a>Требования

**Заголовок:** collection.h

**Пространство имен:** Platform::Collections

## <a name="first"></a> Метод MapView::First

Возвращает итератор, указывающий первый элемент в представлении сопоставления.

### <a name="syntax"></a>Синтаксис

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Возвращаемое значение

Итератор, указывающий первый элемент в представлении сопоставления.

### <a name="remarks"></a>Примечания

Удобный способ сохранения итератора, возвращаемого методом First() — присвоить возвращаемое значение переменной, объявленной с **автоматически** ключевым словом вывода типа. Например, `auto x = myMapView->First();`.

## <a name="haskey"></a>  Метод MapView::HasKey

Определяет, содержит ли текущий объект MapView указанный ключ.

### <a name="syntax"></a>Синтаксис

```

bool HasKey(K key);
```

### <a name="parameters"></a>Параметры

*key*<br/>
Ключ, используемый для поиска элемента MapView. Тип *ключ* является именем типа *K*.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если ключ найден; в противном случае — значение **false**.

##  <a name="lookup"></a> Метод MapView::Lookup

Возвращает значение типа V, связанное с указанным ключом типа K.

### <a name="syntax"></a>Синтаксис

```
V Lookup(K key);
```

### <a name="parameters"></a>Параметры

*key*<br/>
Ключ, используемый для поиска элемента в объекте MapView. Тип `key` является именем типа *K*.

### <a name="return-value"></a>Возвращаемое значение

Значение, связанное с ключом `key`. Тип возвращаемого значения является именем типа *V*.

##  <a name="ctor"></a> Конструктор MapView::MapView

Инициализирует новый экземпляр класса MapView.

### <a name="syntax"></a>Синтаксис

```cpp
explicit MapView(const C& comp = C());

explicit MapView(const ::std::map<K, V, C>& m);

explicit MapView(std::map<K, V, C>&& m);

template <typename InIt> MapView(
    InIt first,
    InIt last,
    const C& comp = C());

MapView(
    ::std::initializer_list<std::pair<const K, V>> il,
    const C& comp = C());
```

### <a name="parameters"></a>Параметры

*InIt*<br/>
Имя типа текущего объекта MapView.

*Зап.*<br/>
Тип, предоставляющий объект функции, который может сравнить два значения элементов в качестве ключей сортировки для определения их относительного порядка в объекте MapView.

*m*<br/>
Ссылка или [значения lvalue и rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) для `map Class` , используемый для инициализации текущего объекта MapView.

*Первый*<br/>
Итератор ввода первого элемента в диапазоне элементов, используемый для инициализации текущего объекта MapView.

*последний*<br/>
Итератор ввода первого элемента после диапазона элементов, используемый для инициализации текущего объекта MapView.

*il*<br/>
Объект [std::initializer_list < std::pair\<K, V >>](../standard-library/initializer-list-class.md) , элементы которого будут вставлены в MapView.

##  <a name="size"></a> Метод MapView::Size

Возвращает количество элементов в текущем объекте MapView.

### <a name="syntax"></a>Синтаксис

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Возвращаемое значение

Количество элементов в текущем объекте MapView.

##  <a name="split"></a> Метод MapView::Split

Разделяет текущий объект MapView на два объекта MapView. Этот метод не выполняет никаких действий.

### <a name="syntax"></a>Синтаксис

```
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>Параметры

*firstPartition*<br/>
Первая часть исходного объекта MapView.

*secondPartition*<br/>
Вторая часть исходного объекта MapView.

### <a name="remarks"></a>Примечания

Этот метод не выполняет никаких действий.

## <a name="see-also"></a>См. также

[Пространство имен Platform](platform-namespace-c-cx.md)
