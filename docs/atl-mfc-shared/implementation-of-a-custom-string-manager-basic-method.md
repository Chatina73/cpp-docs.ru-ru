---
title: Реализация из пользовательского диспетчера строк (базовый метод)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: c30c08217a09f600f8801bec9f50c4341e983a6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235905"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Реализация из пользовательского диспетчера строк (базовый метод)

Самый простой способ настроить схемы выделения памяти для строковых данных является использование предоставляемых ATL `CAtlStringMgr` класса, но предоставляют свои собственные памяти процедур выделения. Конструктор для `CAtlStringMgr` принимает один параметр: указатель на `IAtlMemMgr` объект. `IAtlMemMgr` — Это абстрактный базовый класс, который предоставляет универсальный интерфейс в кучу. С помощью `IAtlMemMgr` интерфейс, `CAtlStringMgr` выделяет, повторно выделяет и освобождает память, используемую для хранения строковых данных. Можно либо реализовать `IAtlMemMgr` интерфейс самостоятельно или использовать один из пяти manager классов ATL предоставляемой памяти. Диспетчеры ATL предоставляемой памяти просто перенести существующие средства выделения памяти:

- [CCRTHeap](../atl/reference/ccrtheap-class.md) создает оболочку для стандартных функций кучи CRT ([malloc](../c-runtime-library/reference/malloc.md), [бесплатный](../c-runtime-library/reference/free.md), и [realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md) переносит обрабатывать кучи Win32, с помощью [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc), [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree), и [HeapRealloc](/windows/desktop/api/heapapi/nf-heapapi-heaprealloc)

- [CLocalHeap](../atl/reference/clocalheap-class.md) создает оболочку для API-интерфейсов Win32: [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree), и [LocalRealloc](/windows/desktop/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md) создает оболочку для API-интерфейсов Win32: [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc), [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree), и [GlobalRealloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc).

- [CComHeap](../atl/reference/ccomheap-class.md) создает оболочку для API-интерфейсы распределителя COM-задач: [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree), и [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

Для целей строка управление памятью, наиболее полезных класс является `CWin32Heap` , так как он позволяет создавать несколько независимых куч. Например если вы хотите использовать отдельной куче только для строк, удалось сделайте следующее:

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

Чтобы использовать этот диспетчер закрытую строковую для управления памятью для `CString` переменной, передайте указатель этот диспетчер в качестве параметра `CString` конструктор переменной:

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>См. также

[Управление памятью с помощью CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
