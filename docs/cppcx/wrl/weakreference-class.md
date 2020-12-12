---
description: 'Дополнительные сведения о: WeakReference Class'
title: Класс WeakReference
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: 743a705fae93d015d190df24d2534de62613e542
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116553"
---
# <a name="weakreference-class"></a>Класс WeakReference

Поддерживает инфраструктуру WRL и не предназначен для непосредственного использования в коде.

## <a name="syntax"></a>Синтаксис

```cpp
class WeakReference;
```

## <a name="remarks"></a>Remarks

Представляет *слабую ссылку* , которую можно использовать с среда выполнения Windows или классическим com. Слабая ссылка представляет собой объект, который может быть доступен или недоступен.

`WeakReference`Объект поддерживает *строгую ссылку*, которая является указателем на объект, и *строгим счетчиком ссылок*, представляющим количество копий строгой ссылки, которые были распространены `Resolve()` методом. Хотя число строгих ссылок не равно нулю, строгая ссылка является допустимой и объект доступен. Если значение счетчика строгого числа ссылок становится равным нулю, строгая ссылка недействительна и объект недоступен.

`WeakReference`Объект обычно используется для представления объекта, существование которого управляется внешним потоком или приложением. Например, создайте `WeakReference` объект из ссылки на файловый объект. Пока открыт файл, строгая ссылка является действительной. Но если закрыть файл, строгая ссылка станет недействительной.

`WeakReference`Методы являются потокобезопасными.

## <a name="members"></a>Элементы

### <a name="public-constructors"></a>Открытые конструкторы

name                                                  | Описание
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference:: WeakReference](#weakreference)        | Инициализирует новый экземпляр класса `WeakReference`.
[WeakReference:: ~ WeakReference](#tilde-weakreference) | Выполняет деинициализацию (уничтожает) текущий экземпляр `WeakReference` класса.

### <a name="public-methods"></a>Открытые методы

name                                                                 | Описание
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::D Екрементстронгреференце](#decrementstrongreference) | Уменьшает значение счетчика строгой ссылки текущего `WeakReference` объекта.
[WeakReference:: Инкрементстронгреференце](#incrementstrongreference) | Увеличивает значение счетчика строгой ссылки текущего `WeakReference` объекта.
[WeakReference:: Resolve](#resolve)                                   | Устанавливает указанный указатель на текущее значение строгой ссылки, если число строгих ссылок не равно нулю.
[WeakReference:: Сетункновн](#setunknown)                             | Устанавливает строгую ссылку текущего `WeakReference` объекта на указанный указатель интерфейса.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`WeakReference`

## <a name="requirements"></a>Требования

**Заголовок:** Implements. h

**Пространство имен:** Microsoft:: WRL::D состояния

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a> WeakReference:: ~ WeakReference

Поддерживает инфраструктуру WRL и не предназначен для непосредственного использования в коде.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

Выполняет деинициализацию текущего экземпляра `WeakReference` класса.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a> WeakReference::D Екрементстронгреференце

Поддерживает инфраструктуру WRL и не предназначен для непосредственного использования в коде.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Комментарии

Уменьшает значение счетчика строгой ссылки текущего `WeakReference` объекта.

Если значение счетчика строгой ссылки становится равным нулю, строгой ссылке присваивается значение **`nullptr`** .

### <a name="return-value"></a>Возвращаемое значение

Число уменьшения строгой ссылки.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a> WeakReference:: Инкрементстронгреференце

Поддерживает инфраструктуру WRL и не предназначен для непосредственного использования в коде.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Возвращаемое значение

Увеличенный счетчик ссылок со строгим значением.

### <a name="remarks"></a>Комментарии

Увеличивает значение счетчика строгой ссылки текущего `WeakReference` объекта.

## <a name="weakreferenceresolve"></a><a name="resolve"></a> WeakReference:: Resolve

Поддерживает инфраструктуру WRL и не предназначен для непосредственного использования в коде.

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Параметры

*riid*<br/>
Идентификатор интерфейса.

*ппвобжект*<br/>
Когда эта операция завершается, копия текущей строгой ссылки, если значение счетчика строгой ссылки не равно нулю, не используется.

### <a name="return-value"></a>Возвращаемое значение

- S_OK, если эта операция прошла успешно и Счетчик строгой ссылки равен нулю. Параметр *ппвобжект* имеет значение **`nullptr`** .

- S_OK, если эта операция прошла успешно, а строгое число ссылок не равно нулю. Для параметра *ппвобжект* задана строгая ссылка.

- В противном случае возвращается значение HRESULT, указывающее причину сбоя операции.

### <a name="remarks"></a>Комментарии

Устанавливает указанный указатель на текущее значение строгой ссылки, если число строгих ссылок не равно нулю.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a> WeakReference:: Сетункновн

Поддерживает инфраструктуру WRL и не предназначен для непосредственного использования в коде.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Параметры

*унк*<br/>
Указатель на `IUnknown` интерфейс объекта.

### <a name="remarks"></a>Комментарии

Устанавливает строгую ссылку текущего `WeakReference` объекта на указанный указатель интерфейса.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a> WeakReference:: WeakReference

Поддерживает инфраструктуру WRL и не предназначен для непосредственного использования в коде.

```cpp
WeakReference();
```

### <a name="remarks"></a>Комментарии

Инициализирует новый экземпляр класса `WeakReference`.

Инициализируется указатель строгой ссылки на `WeakReference` объект **`nullptr`** , а строгий счетчик ссылок инициализируется значением 1.
