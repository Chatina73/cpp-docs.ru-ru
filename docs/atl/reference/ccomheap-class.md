---
description: 'Дополнительные сведения о: Ккомхеап Class'
title: Класс Ккомхеап
ms.date: 11/04/2016
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
ms.openlocfilehash: 2ced98194bea8e186cee17504ca9e3abf7c212c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152039"
---
# <a name="ccomheap-class"></a>Класс Ккомхеап

Этот класс реализует [иатлмеммгр](../../atl/reference/iatlmemmgr-class.md) с помощью функций выделения памяти com.

> [!IMPORTANT]
> Этот класс и его члены не могут использоваться в приложениях, выполняемых в среда выполнения Windows.

## <a name="syntax"></a>Синтаксис

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Члены

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[Ккомхеап:: allocate](#allocate)|Вызовите этот метод, чтобы выделить блок памяти.|
|[Ккомхеап:: Free](#free)|Вызовите этот метод, чтобы освободить блок памяти, выделенный этим диспетчером памяти.|
|[Ккомхеап:: DataSize](#getsize)|Вызовите этот метод, чтобы получить выделенный размер блока памяти, выделенного этим диспетчером памяти.|
|[Ккомхеап:: перераспределение](#reallocate)|Вызовите этот метод для перераспределения памяти, выделенной данным диспетчером памяти.|

## <a name="remarks"></a>Комментарии

`CComHeap`реализует функции выделения памяти с помощью функций выделения COM, включая [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree), [unalloc::](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)котаскмемреаллок и [](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc). Максимальный объем памяти, который может быть выделен, равен INT_MAX (2147483647) байт.

## <a name="example"></a>Пример

См. пример для [иатлмеммгр](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Требования

**Заголовок:** Атлкоммем. h

## <a name="ccomheapallocate"></a><a name="allocate"></a> Ккомхеап:: allocate

Вызовите этот метод, чтобы выделить блок памяти.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Параметры

*nBytes*<br/>
Запрошенное число байтов в новом блоке памяти.

### <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на начало выделенного блока памяти.

### <a name="remarks"></a>Комментарии

Вызовите метод [ккомхеап:: Free](#free) или [ккомхеап:: reallocate](#reallocate) , чтобы освободить память, выделенную этим методом.

Реализуется с помощью функции [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc).

## <a name="ccomheapfree"></a><a name="free"></a> Ккомхеап:: Free

Вызовите этот метод, чтобы освободить блок памяти, выделенный этим диспетчером памяти.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Параметры

*p*<br/>
Указатель на область памяти, выделенную ранее данным диспетчером памяти. Значение NULL является допустимым и не выполняет никаких действий.

### <a name="remarks"></a>Комментарии

Реализуется с помощью [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree).

## <a name="ccomheapgetsize"></a><a name="getsize"></a> Ккомхеап:: DataSize

Вызовите этот метод, чтобы получить выделенный размер блока памяти, выделенного этим диспетчером памяти.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Параметры

*p*<br/>
Указатель на область памяти, выделенную ранее данным диспетчером памяти.

### <a name="return-value"></a>Возвращаемое значение

Возвращает размер выделенного блока памяти в байтах.

### <a name="remarks"></a>Комментарии

Реализуется с помощью [unalloc:: DataSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize).

## <a name="ccomheapreallocate"></a><a name="reallocate"></a> Ккомхеап:: перераспределение

Вызовите этот метод для перераспределения памяти, выделенной данным диспетчером памяти.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Параметры

*p*<br/>
Указатель на область памяти, выделенную ранее данным диспетчером памяти.

*nBytes*<br/>
Запрошенное число байтов в новом блоке памяти.

### <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на начало выделенного блока памяти.

### <a name="remarks"></a>Комментарии

Вызовите метод [ккомхеап:: Free](#free) , чтобы освободить память, выделенную этим методом.

Реализуется с помощью [котаскмемреаллок](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>См. также раздел

[Пример Динамикконсумер](../../overview/visual-cpp-samples.md)<br/>
[Общие сведения о классах](../../atl/atl-class-overview.md)<br/>
[Класс CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Класс CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Класс CCRTHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Класс Ккрсеап](../../atl/reference/ccrtheap-class.md)<br/>
[Класс Иатлмеммгр](../../atl/reference/iatlmemmgr-class.md)
