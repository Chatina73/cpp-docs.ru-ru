---
title: Класс CRBMap
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: e5dedb26544bb2755bc74894cf36a622f5141f89
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301510"
---
# <a name="crbmap-class"></a>Класс CRBMap

Этот класс представляет структуру сопоставления, с помощью двоичного красно-черного дерева.

## <a name="syntax"></a>Синтаксис

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>Параметры

*K*<br/>
Тип ключа элемента.

*V*<br/>
Тип значения элемента.

*KTraits*<br/>
Код, используемый для копирования или перемещения ключевые элементы. См. в разделе [класс CElementTraits](../../atl/reference/celementtraits-class.md) для получения дополнительных сведений.

*VTraits*<br/>
Код, используемый для копирования или перемещения элементов value.

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание:|
|----------|-----------------|
|[CRBMap::CRBMap](#crbmap)|Конструктор.|
|[CRBMap:: ~ CRBMap](#dtor)|Деструктор|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание:|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|Вызовите этот метод для поиска ключей и значений в `CRBMap` объекта.|
|[CRBMap::RemoveKey](#removekey)|Вызовите этот метод для удаления элемента из `CRBMap` объекту, заданному ключу.|
|[CRBMap::SetAt](#setat)|Этот метод используется для вставки пары элементов в сопоставление.|

## <a name="remarks"></a>Примечания

`CRBMap` предоставляет поддержку для сопоставления массива заданного типа, управление упорядоченный массив ключей элементов и связанных с ними значений. Каждый ключ может иметь только одно связанное значение. Элементы, (состоящей из ключа и значения) хранятся в двоичном дереве структуры с помощью [CRBMap::SetAt](#setat) метод. Элементы можно удалить с помощью [CRBMap::RemoveKey](#removekey) метод, который удаляет элемент с заданным значением ключа.

Обход дерева стало возможным с методами например [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), и [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

*KTraits* и *VTraits* параметры являются traits-классы, содержащие любой дополнительный код, необходимый для копирования или перемещения элементов.

`CRBMap` является производным от [CRBTree](../../atl/reference/crbtree-class.md), который реализует по двоичному дереву с помощью алгоритма красно-черного. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) представляет собой вариант, который разрешает несколько значений для каждого ключа. Он слишком является производным от `CRBTree`и поэтому использует множество функций с `CRBMap`.

Альтернативой оба `CRBMap` и `CRBMultiMap` предложенного [CAtlMap](../../atl/reference/catlmap-class.md) класса. Если только небольшое количество элементов должно быть сохранено, рассмотрите возможность использования [CSimpleMap](../../atl/reference/csimplemap-class.md) вместо этого класса.

Более полное описание различных классов коллекций и функций и характеристики производительности, см. в разделе [классы коллекций ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Требования

**Заголовок:** atlcoll.h

##  <a name="crbmap"></a>  CRBMap::CRBMap

Конструктор.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Параметры

*nBlockSize*<br/>
Размер блока.

### <a name="remarks"></a>Примечания

*NBlockSize* параметр — это мера объем памяти, выделяемый при новый элемент является обязательным. Увеличенный размер блока, уменьшите количество вызовов процедур выделения памяти, но использовать больше ресурсов. Значение по умолчанию будет выделить место для 10 элементов за раз.

См. в документации для базового класса [CRBTree](../../atl/reference/crbtree-class.md) сведения о других методах, доступных.

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMap:: ~ CRBMap

Деструктор

```
~CRBMap() throw();
```

### <a name="remarks"></a>Примечания

Освобождает все выделенные ресурсы.

См. в документации для базового класса [CRBTree](../../atl/reference/crbtree-class.md) сведения о других методах, доступных.

##  <a name="lookup"></a>  CRBMap::Lookup

Вызовите этот метод для поиска ключей и значений в `CRBMap` объекта.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Параметры

*key*<br/>
Задает ключ, определяющий элемент, выполняется поиск.

*value*<br/>
Переменная, которая получает искомого значения.

### <a name="return-value"></a>Возвращаемое значение

В первой форме метода возвращает значение true, если ключ найден, в противном случае — значение false. Второй и третьей форме возвращают указатель на [CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Примечания

См. в документации для базового класса [CRBTree](../../atl/reference/crbtree-class.md) сведения о других методах, доступных.

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

##  <a name="removekey"></a>  CRBMap::RemoveKey

Вызовите этот метод для удаления элемента из `CRBMap` объекту, заданному ключу.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Параметры

*key*<br/>
Ключ, соответствующий пары элементов действительно необходимо удалить.

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение true, если ключ найден и удален, и false в случае сбоя.

### <a name="remarks"></a>Примечания

См. в документации для базового класса [CRBTree](../../atl/reference/crbtree-class.md) сведения о других методах, доступных.

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

##  <a name="setat"></a>  CRBMap::SetAt

Этот метод используется для вставки пары элементов в сопоставление.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Параметры

*key*<br/>
Значение ключа, чтобы добавить `CRBMap` объекта.

*value*<br/>
Значение, которое нужно добавить `CRBMap` объекта.

### <a name="return-value"></a>Возвращаемое значение

Возвращает позицию элемента пары ключ/значение в `CRBMap` объекта.

### <a name="remarks"></a>Примечания

`SetAt` заменяет существующий элемент, если найден соответствующий ключ. Если ключ не найден, создается новую пару ключ значение.

См. в документации для базового класса [CRBTree](../../atl/reference/crbtree-class.md) сведения о других методах, доступных.

### <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>См. также

[Класс CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Класс CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Класс CRBMultiMap](../../atl/reference/crbmultimap-class.md)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
