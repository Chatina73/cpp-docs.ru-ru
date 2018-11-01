---
title: Класс ITarget
ms.date: 11/04/2016
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
ms.openlocfilehash: fed6f6c9b93869602eb43dabfef4743fbce3a3d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430008"
---
# <a name="itarget-class"></a>Класс ITarget

Класс `ITarget` является интерфейсом для всех целевых блоков. Целевые блоки потребляют сообщения, предлагаемые ими блоками `ISource`.

## <a name="syntax"></a>Синтаксис

```
template<class T>
class ITarget;
```

#### <a name="parameters"></a>Параметры

*T*<br/>
Тип данных полезных данных внутри сообщений, принимаемых целевым блоком.

## <a name="members"></a>Участники

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Описание|
|----------|-----------------|
|`filter_method`|Подпись любого метода, используемая блоком, который возвращает `bool` значение, чтобы определить, следует ли принять предложенное сообщение.|
|`type`|Псевдоним для `T`.|

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[~ Деструктор ITarget](#dtor)|Уничтожает `ITarget` объекта.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[распространение](#propagate)|При переопределении в производном классе, асинхронно передает сообщение из блока источника этой целевой блок.|
|[send](#send)|При переопределении в производном классе синхронно передает сообщение в целевой блок.|
|[supports_anonymous_source](#supports_anonymous_source)|При переопределении в производном классе возвращает значение true или false в зависимости от того, принимает ли блок сообщений сообщения, предоставляемые не связанным с ним источником. Если переопределенный метод возвращает **true**, целевой объект не может отложить предоставленное сообщение, как потребление отложенного сообщения позже требуется, чтобы определить в реестре ссылок источник.|

### <a name="protected-methods"></a>Защищенные методы

|Имя|Описание|
|----------|-----------------|
|[link_source](#link_source)|При переопределении в производном классе связывает блок указанного источника с это `ITarget` блока.|
|[unlink_source](#unlink_source)|При переопределении в производном классе удаляет связь указанной исходной блока из этого `ITarget` блока.|
|[unlink_sources](#unlink_sources)|При переопределении в производном классе удаляет связь всех блоков источника, из этого `ITarget` блока.|

## <a name="remarks"></a>Примечания

Дополнительные сведения см. в разделе [асинхронные блоки сообщений](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`ITarget`

## <a name="requirements"></a>Требования

**Заголовок:** agents.h

**Пространство имен:** concurrency

##  <a name="dtor"></a> ~ ITarget

Уничтожает `ITarget` объекта.

```
virtual ~ITarget();
```

##  <a name="link_source"></a> link_source

При переопределении в производном классе связывает блок указанного источника с это `ITarget` блока.

```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Параметры

*_PSource*<br/>
`ISource` Block, связанным с это `ITarget` блока.

### <a name="remarks"></a>Примечания

Эта функция не должна вызываться непосредственно на `ITarget` блока. Блоки должны быть соединены друг с другом с помощью `link_target` метод `ISource` блоков, который будет вызывать `link_source` метод на соответствующий целевой объект.

##  <a name="propagate"></a> распространение

При переопределении в производном классе, асинхронно передает сообщение из блока источника этой целевой блок.

```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Параметры

*_PMessage*<br/>
Указатель на объект `message`.

*_PSource*<br/>
Указатель на блок источника, предлагающий сообщение.

### <a name="return-value"></a>Возвращаемое значение

Объект [message_status](concurrency-namespace-enums.md) указывает, что целевой объект решил сделать с сообщением.

### <a name="remarks"></a>Примечания

Метод вызывает [invalid_argument](../../../standard-library/invalid-argument-class.md) исключение, если параметр `_PMessage` или `_PSource` параметр `NULL`.

##  <a name="send"></a> Отправить

При переопределении в производном классе синхронно передает сообщение в целевой блок.

```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Параметры

*_PMessage*<br/>
Указатель на объект `message`.

*_PSource*<br/>
Указатель на блок источника, предлагающий сообщение.

### <a name="return-value"></a>Возвращаемое значение

Объект [message_status](concurrency-namespace-enums.md) указывает, что целевой объект решил сделать с сообщением.

### <a name="remarks"></a>Примечания

Метод вызывает [invalid_argument](../../../standard-library/invalid-argument-class.md) исключение, если параметр `_PMessage` или `_PSource` параметр `NULL`.

С помощью `send` метод вне инициации сообщения и передавать сообщения в сети является опасной операцией и может привести к взаимоблокировке.

Когда `send` возвращает сообщение либо уже было принято и переданные в целевой блок, или было отклонено целевым объектом.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source

При переопределении в производном классе возвращает значение true или false в зависимости от того, принимает ли блок сообщений сообщения, предоставляемые не связанным с ним источником. Если переопределенный метод возвращает **true**, целевой объект не может отложить предоставленное сообщение, как потребление отложенного сообщения позже требуется, чтобы определить в реестре ссылок источник.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если блок может принимать сообщения из источника, который не связан с ним **false** в противном случае.

##  <a name="unlink_source"></a> unlink_source

При переопределении в производном классе удаляет связь указанной исходной блока из этого `ITarget` блока.

```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Параметры

*_PSource*<br/>
`ISource` Block, связь которого с это `ITarget` блока.

### <a name="remarks"></a>Примечания

Эта функция не должна вызываться непосредственно на `ITarget` блока. Блоки должно быть отключено с помощью `unlink_target` или `unlink_targets` методы `ISource` блоков, который будет вызывать `unlink_source` метод на соответствующий целевой объект.

##  <a name="unlink_sources"></a> unlink_sources

При переопределении в производном классе удаляет связь всех блоков источника, из этого `ITarget` блока.

```
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>См. также

[Пространство имен concurrency](concurrency-namespace.md)<br/>
[Класс ISource](isource-class.md)
