---
description: 'Дополнительные сведения о: Кшаредфиле Class'
title: Класс Кшаредфиле
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: 0eb2f76bdfa9e10c660f405e225698289b506014
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342835"
---
# <a name="csharedfile-class"></a>Класс Кшаредфиле

Класс, производный от [кмемфиле](../../mfc/reference/cmemfile-class.md), который поддерживает файлы общей памяти.

## <a name="syntax"></a>Синтаксис

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Кшаредфиле:: Кшаредфиле](#csharedfile)|Формирует объект `CSharedFile`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[Кшаредфиле::D етач](#detach)|Закрывает файл общей памяти и возвращает маркер его блока памяти.|
|[Кшаредфиле:: Сесандле](#sethandle)|Присоединяет файл общей памяти к блоку памяти.|

## <a name="remarks"></a>Комментарии

Файлы памяти ведут себя как файлы на диске. Разница заключается в том, что файл памяти хранится в ОЗУ, а не на диске. Файл памяти полезен для быстрого временного хранения, а также для передачи необработанных байтов или сериализованных объектов между независимыми процессами.

Файлы общей памяти отличаются от других файлов памяти в этой памяти для их выделения с помощью функции Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) . `CSharedFile`Класс хранит данные в глобально выделенном блоке памяти (созданном с помощью `GlobalAlloc` ), и этот блок памяти может использоваться совместно с помощью DDE, буфера обмена или других универсальных операций обмена данными OLE/COM, например с помощью `IDataObject` .

`GlobalAlloc` Возвращает маркер ХГЛОБАЛ, а не указатель на память, например указатель, возвращаемый функцией [malloc](../../c-runtime-library/reference/malloc.md). В некоторых приложениях необходим обработчик ХГЛОБАЛ. Например, чтобы разместить данные в буфере обмена, необходим обработчик ХГЛОБАЛ.

`CSharedFile` не использует отображенные в память файлы, и данные не могут быть предоставлены напрямую между процессами.

`CSharedFile` объекты могут автоматически распределять собственную память. Или можно присоединить собственный блок памяти к `CSharedFile` объекту, вызвав [кшаредфиле:: сесандле](#sethandle). В любом случае память для увеличения размера файла памяти автоматически выделяется по `nGrowBytes` размеру, если `nGrowBytes` не равен нулю.

Дополнительные сведения см. в статьях [файлы MFC](../../mfc/files-in-mfc.md) и [Обработка файлов](../../c-runtime-library/file-handling.md) в *справочнике по библиотеке времени выполнения*.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Требования

**Заголовок:** афксадв. h

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a> Кшаредфиле:: Кшаредфиле

Создает `CSharedFile` объект и выделяет память для него.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Параметры

*наллокфлагс*<br/>
Флаги, указывающие, как выделяется память. Список допустимых значений флагов см. в разделе [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) .

*нгровбитес*<br/>
Шаг выделения памяти в байтах.

## <a name="csharedfiledetach"></a><a name="detach"></a> Кшаредфиле::D етач

Вызовите эту функцию, чтобы закрыть файл памяти и отсоединить его от блока памяти.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Возвращаемое значение

Маркер блока памяти, который содержит содержимое файла памяти.

### <a name="remarks"></a>Комментарии

Его можно открыть повторно, вызвав [сесандле](#sethandle), используя маркер, возвращаемый функцией **Detach**.

## <a name="csharedfilesethandle"></a><a name="sethandle"></a> Кшаредфиле:: Сесандле

Вызовите эту функцию, чтобы присоединить блок глобальной памяти к `CSharedFile` объекту.

```cpp
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Параметры

*хглобалмемори*<br/>
Обрабатывает глобальную память, подсоединяемую к `CSharedFile` .

*балловгров*<br/>
Указывает, разрешено ли увеличение блока памяти.

### <a name="remarks"></a>Комментарии

Если *балловгров* имеет ненулевое значение, размер блока памяти увеличивается по мере необходимости, например при попытке записи в файл большего числа байтов, чем размер блока памяти.

## <a name="see-also"></a>См. также раздел

[Класс Кмемфиле](../../mfc/reference/cmemfile-class.md)<br/>
[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Класс Кмемфиле](../../mfc/reference/cmemfile-class.md)
