---
title: Класс source_link_manager
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: d4979eaf9065183be646be72cfdd5a94500edf55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337587"
---
# <a name="sourcelinkmanager-class"></a>Класс source_link_manager

Объект `source_link_manager` управляет сетевыми соединениями блоков обмена сообщениями с блоками `ISource`.

## <a name="syntax"></a>Синтаксис

```
template<class _LinkRegistry>
class source_link_manager;
```

#### <a name="parameters"></a>Параметры

*_LinkRegistry*<br/>
Реестр сетевых ссылок.

## <a name="members"></a>Участники

### <a name="public-typedefs"></a>Общедоступные определения типов

|name|Описание|
|----------|-----------------|
|`const_pointer`|Тип, предоставляющий указатель на `const` элемент `source_link_manager` объекта.|
|`const_reference`|Тип, предоставляющий ссылку на `const` элемент хранится в `source_link_manager` объект для чтения и выполнения операций const.|
|`iterator`|Тип, предоставляющий итератор, который может считывать или изменять любой элемент в `source_link_manager` объекта.|
|`type`|Тип реестра ссылку под ее управлением `source_link_manager` объекта.|

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[source_link_manager](#ctor)|Создает объект `source_link_manager`.|
|[~ source_link_manager деструктор](#dtor)|Уничтожает `source_link_manager` объекта.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[add](#add)|Добавляет ссылку на источник `source_link_manager` объекта.|
|[begin](#begin)|Возвращает итератор, указывающий на первый элемент в `source_link_manager` объекта.|
|[Содержит](#contains)|Поиск `network_link_registry` в рамках этого `source_link_manager` объекта для указанного блока.|
|[count](#count)|Подсчитывает количество связанных блоков в `source_link_manager` объекта.|
|[reference](#reference)|Получает ссылку на `source_link_manager` объекта.|
|[register_target_block](#register_target_block)|Регистрирует целевой блок, который содержит эту коллекцию `source_link_manager` объекта.|
|[release](#release)|Освобождает ссылку на `source_link_manager` объекта.|
|[remove](#remove)|Удаляет ссылку из `source_link_manager` объекта.|
|[set_bound](#set_bound)|Задает максимальное число ссылок источника, который может быть добавлен к этому `source_link_manager` объекта.|

## <a name="remarks"></a>Примечания

В настоящее время блоки источника имеется счетчик ссылок. Это оболочка на `network_link_registry` объект, который допускает параллельный доступ к ссылкам и предоставляет возможность обращаться через обратные вызовы ссылки. Блоки сообщений ( `target_block`s или `propagator_block`s) следует использовать этот класс для источника ссылки.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`source_link_manager`

## <a name="requirements"></a>Требования

**Заголовок:** agents.h

**Пространство имен:** concurrency

##  <a name="add"></a> Добавить

Добавляет ссылку на источник `source_link_manager` объекта.

```
void add(_EType _Link);
```

### <a name="parameters"></a>Параметры

*_Link*<br/>
Указатель на блок для добавления.

##  <a name="begin"></a> начать

Возвращает итератор, указывающий на первый элемент в `source_link_manager` объекта.

```
iterator begin();
```

### <a name="return-value"></a>Возвращаемое значение

Итератор, адресующий первый элемент в `source_link_manager` объекта.

### <a name="remarks"></a>Примечания

Конечное состояние итератора обозначается `NULL` ссылку.

##  <a name="contains"></a> Содержит

Поиск `network_link_registry` в рамках этого `source_link_manager` объекта для указанного блока.

```
bool contains(_EType _Link);
```

### <a name="parameters"></a>Параметры

*_Link*<br/>
Указатель на блок, который необходимо найти в `source_link_manager` объекта.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** указанного блока, если было обнаружено **false** в противном случае.

##  <a name="count"></a> число

Подсчитывает количество связанных блоков в `source_link_manager` объекта.

```
size_t count();
```

### <a name="return-value"></a>Возвращаемое значение

Число связанных блоков в `source_link_manager` объекта.

##  <a name="reference"></a> Справочник по

Получает ссылку на `source_link_manager` объекта.

```
void reference();
```

##  <a name="register_target_block"></a> register_target_block

Регистрирует целевой блок, который содержит эту коллекцию `source_link_manager` объекта.

```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Параметры

*_PTarget*<br/>
Целевой блок, содержащий это `source_link_manager` объекта.

##  <a name="release"></a> выпуск

Освобождает ссылку на `source_link_manager` объекта.

```
void release();
```

##  <a name="remove"></a> удалить

Удаляет ссылку из `source_link_manager` объекта.

```
bool remove(_EType _Link);
```

### <a name="parameters"></a>Параметры

*_Link*<br/>
Указатель на блок удалены, если найден.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если ссылки был найден и удален, **false** в противном случае.

##  <a name="set_bound"></a> set_bound

Задает максимальное число ссылок источника, который может быть добавлен к этому `source_link_manager` объекта.

```
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Параметры

*_MaxLinks*<br/>
Максимальное число ссылок.

##  <a name="ctor"></a> source_link_manager

Создает объект `source_link_manager`.

```
source_link_manager();
```

##  <a name="dtor"></a> ~source_link_manager

Уничтожает `source_link_manager` объекта.

```
~source_link_manager();
```

## <a name="see-also"></a>См. также

[Пространство имен concurrency](concurrency-namespace.md)<br/>
[Класс single_link_registry](single-link-registry-class.md)<br/>
[Класс multi_link_registry](multi-link-registry-class.md)
