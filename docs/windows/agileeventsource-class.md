---
title: Класс AgileEventSource
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: 8e99c5930fa4df5be686a9c738586ecbb21e2855
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526573"
---
# <a name="agileeventsource-class"></a>Класс AgileEventSource

Представляет событие, произошедшее в компоненте agile, который является компонентом, который может осуществляться из любого потока. Наследует от [EventSource](eventsource-class.md) и переопределяет `Add` функция-член с параметром дополнительный тип для указания параметров для способ вызова agile события.

## <a name="syntax"></a>Синтаксис

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Параметры

*TDelegateInterface*<br/>
Интерфейс делегат, представляющий обработчик событий.

*TEventSourceOptions*<br/>
[InvokeModeOptions](invokemodeoptions-structure.md) структура, поля которого invokeMode задается `InvokeMode::StopOnFirstError` или `InvokeMode::FireAll`.

## <a name="remarks"></a>Примечания

Подавляющее большинство компонентов в среде выполнения Windows — agile компоненты. Дополнительные сведения см. в разделе [работа с потоками и маршалинг (C + +/ CX)](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>Требования

**Заголовок:** event.h

**Пространство имен:** Microsoft::WRL

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[Метод AgileEventSource::Add](#add)|Добавляет обработчик событий agile, представленный указанным интерфейсом делегата к набору обработчиков событий для текущего **AgileEventSource** объекта.|

## <a name="add"></a> Метод AgileEventSource::Add

Добавляет обработчик событий, представленный указанным интерфейсом делегата к набору обработчиков событий для текущего [EventSource](eventsource-class.md) объекта.

### <a name="syntax"></a>Синтаксис

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Параметры

*delegateInterface*<br/>
Интерфейс для объекта делегата, который представляет обработчик событий.

*Маркер*<br/>
После завершения операции представляет дескриптор события. Использовать этот маркер в качестве параметра `Remove()` метод для удаления обработчика событий.

### <a name="return-value"></a>Возвращаемое значение

Значение S_OK, если операция завершилась успешно; в противном случае — значение HRESULT, указывающее на ошибку.

## <a name="see-also"></a>См. также

[Пространство имен Microsoft::WRL](../windows/microsoft-wrl-namespace.md)