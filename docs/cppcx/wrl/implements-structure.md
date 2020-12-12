---
description: Дополнительные сведения см. в статье реализация структуры.
title: Implements - структура
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: b438e012b23e34b08956c969ffe604878d3065fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249832"
---
# <a name="implements-structure"></a>Implements - структура

Реализует `QueryInterface` и `GetIid` для указанных интерфейсов.

## <a name="syntax"></a>Синтаксис

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>Параметры

*I0*<br/>
Идентификатор интерфейса начальном. (обязательный параметр)

*I1*<br/>
Первый идентификатор интерфейса. (необязательно)

*I2*<br/>
Второй идентификатор интерфейса. (необязательно)

*I3*<br/>
Третий идентификатор интерфейса. (необязательно)

*I4*<br/>
Четвертый идентификатор интерфейса. (необязательно)

*I5*<br/>
Пятый идентификатор интерфейса. (необязательно)

*I6*<br/>
Шестой идентификатор интерфейса. (необязательно)

*I7*<br/>
Седьмой идентификатор интерфейса. (необязательно)

*I8*<br/>
Восьмой идентификатор интерфейса. (необязательно)

*I9*<br/>
Девятый идентификатор интерфейса. (необязательно)

*flags*<br/>
Флаги конфигурации для класса. Одно или несколько перечислений [RuntimeClassType](runtimeclasstype-enumeration.md) , указанных в структуре [RuntimeClassFlags](runtimeclassflags-structure.md) .

## <a name="remarks"></a>Комментарии

Является производным от списка указанных интерфейсов и реализует вспомогательные шаблоны для `QueryInterface` и `GetIid` .

Каждый параметр *I0* через интерфейс *i9* должен быть производным от `IUnknown` `IInspectable` шаблона [метод ChainInterfaces](chaininterfaces-structure.md) . Параметр *flags* определяет, будет ли создана поддержка для `IUnknown` или `IInspectable` .

## <a name="members"></a>Элементы

### <a name="public-typedefs"></a>Общедоступные определения типов

| Имя        | Описание                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Синоним для `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Защищенные методы

| Имя                                              | Описание                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements:: CanCastTo](#cancastto)               | Возвращает указатель на указанный интерфейс.                                                                    |
| [Implements:: CastToUnknown](#casttounknown)       | Возвращает указатель на базовый `IUnknown` интерфейс.                                                        |
| [Implements:: FillArrayWithIid](#fillarraywithiid) | Вставляет идентификатор интерфейса, указанный текущим параметром шаблона начальном, в указанный элемент массива. |

### <a name="protected-constants"></a>Защищенные константы

| Имя                              | Описание                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements:: IidCount](#iidcount) | Содержит число реализованных идентификаторов интерфейсов. |

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Требования

**Заголовок:** Implements. h

**Пространство имен:** Microsoft::WRL

## <a name="implementscancastto"></a><a name="cancastto"></a> Implements:: CanCastTo

Возвращает указатель на указанный интерфейс.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Параметры

*riid*<br/>
Ссылка на идентификатор интерфейса.

*ппв*<br/>
В случае успеха указатель на интерфейс, указанный параметром *riid*.

### <a name="return-value"></a>Возвращаемое значение

S_OK в случае успеха; в противном случае возвращается значение HRESULT, указывающее на ошибку, например E_NOINTERFACE.

### <a name="remarks"></a>Комментарии

Это внутренняя вспомогательная функция, которая выполняет операцию QueryInterface.

## <a name="implementscasttounknown"></a><a name="casttounknown"></a> Implements:: CastToUnknown

Возвращает указатель на базовый `IUnknown` интерфейс.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Возвращаемое значение

Эта операция всегда завершается с ошибкой и возвращает `IUnknown` указатель.

### <a name="remarks"></a>Комментарии

Внутренняя вспомогательная функция.

## <a name="implementsfillarraywithiid"></a><a name="fillarraywithiid"></a> Implements:: FillArrayWithIid

Вставляет идентификатор интерфейса, указанный текущим параметром шаблона начальном, в указанный элемент массива.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Параметры

*index*<br/>
Отсчитываемый от нуля индекс, указывающий начальный элемент массива для данной операции. По завершении этой операции *индекс* увеличивается на 1.

*идентификаторов IID*<br/>
Массив типа IID.

### <a name="remarks"></a>Комментарии

Внутренняя вспомогательная функция.

## <a name="implementsiidcount"></a><a name="iidcount"></a> Implements:: IidCount

Содержит число реализованных идентификаторов интерфейсов.

```cpp
static const unsigned long IidCount;
```
