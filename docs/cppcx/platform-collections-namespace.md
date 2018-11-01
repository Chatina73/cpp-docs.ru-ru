---
title: Пространство имен Platform::Collections
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
ms.openlocfilehash: 025c25d6c01ab9a28c68574cc2a13e09dbf28388
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480370"
---
# <a name="platformcollections-namespace"></a>Пространство имен Platform::Collections

Содержит пространство имен Platform::Collections `Map`, `MapView`, `Vector`, и `VectorView` классы. Эти классы являются конкретными реализациями соответствующих интерфейсов, которые определены в пространстве имен [Windows::Foundation::Collections](/uwp/api/Windows.Foundation.Collections) . Конкретные типы коллекций не могут переноситься через интерфейс ABI (например, когда программа JavaScript или C# вызывает компонент C++), но они могут неявно преобразоваться в соответствующие типы интерфейсов. Например, если вы реализуете открытый метод, который заполняет и возвращает коллекцию, используйте [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) для внутренней реализации коллекции и [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) в качестве возвращаемого типа. Дополнительные сведения см. в разделе [коллекций](../cppcx/collections-c-cx.md) и [создание компонентов среды выполнения Windows в C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Можно создать Platform::Collections::Vector из [std::vector](../standard-library/vector-class.md) и [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) из [std::map](../standard-library/map-class.md).

Кроме того, пространство имен Platform::Collections обеспечивает поддержку вставкой и входных итераторов и `Vector` и `VectorView` итераторы.

Необходимо включить (`#include`) заголовок collection.h использовать типы в пространстве имен Platform::Collections.

## <a name="syntax"></a>Синтаксис

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>Участники

Это пространство имен содержит следующие члены.

|name|Описание|
|----------|-----------------|
|[Класс Platform::Collections::BackInsertIterator](../cppcx/platform-collections-backinsertiterator-class.md)|Представляет итератор, который вставляет элемент в конец коллекции.|
|[Класс Platform::Collections::InputIterator](../cppcx/platform-collections-inputiterator-class.md)|Представляет итератор, который вставляет элемент в начало коллекции.|
|[Класс Platform::Collections::Map](../cppcx/platform-collections-map-class.md)|Представляет изменяемую коллекцию пар "ключ-значение", доступ к которым можно получить по ключу. Аналогично [std::map](../standard-library/map-class.md).|
|[класс Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md)|Представляет доступную только для чтения коллекцию пар "ключ-значение", доступ к которым можно получить по ключу.|
|[Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)|Представляет изменяемую последовательность элементов. Аналогично [std::vector](../standard-library/vector-class.md).|
|[Класс Platform::Collections::VectorIterator](../cppcx/platform-collections-vectoriterator-class.md)|Представляет итератор, который обходит коллекцию `Vector` .|
|[Класс Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)|Представляет доступную только для чтения последовательность элементов.|
|[Класс Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md)|Представляет итератор, который обходит коллекцию `VectorView` .|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[Пространство имен Platform](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>Требования

**Метаданные:** platform.winmd

**Пространство имен:** Platform::Collections

**Параметр компилятора:** /ZW

## <a name="see-also"></a>См. также

[Пространство имен Platform](../cppcx/platform-namespace-c-cx.md)
