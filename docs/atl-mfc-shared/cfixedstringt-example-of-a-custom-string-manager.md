---
description: 'Дополнительные сведения о: CFixedStringT: пример пользовательского диспетчера строк'
title: 'CFixedStringT: пример пользовательского диспетчера строк'
ms.date: 11/04/2016
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
ms.openlocfilehash: c9af2530500ad5972c01d063116e7ac981109493
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142510"
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT: пример пользовательского диспетчера строк

Библиотека ATL реализует один пример пользовательского диспетчера строк, используемого классом [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md), который называется **кфикседстрингмгр**. `CFixedStringT` является производным от [CStringT](../atl-mfc-shared/reference/cstringt-class.md) и реализует строку, которая выделяет свои символьные данные как часть `CFixedStringT` самого объекта, если строка меньше длины, заданной `t_nChars` параметром шаблона `CFixedStringT` . При таком подходе строка не нуждается в куче, если длина строки превышает размер фиксированного буфера. Поскольку не `CFixedStringT` всегда использует кучу для выделения строковых данных, она не может использоваться `CAtlStringMgr` в качестве диспетчера строк. Он использует пользовательский диспетчер строк ( `CFixedStringMgr` ), реализуя интерфейс [иатлстрингмгр](../atl-mfc-shared/reference/iatlstringmgr-class.md) . Этот интерфейс обсуждается в [реализации пользовательского диспетчера строк (Расширенный метод)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md).

Конструктор `CFixedStringMgr` принимает три параметра:

- *pData:* Указатель на фиксированную `CStringData` структуру для использования.

- типы *nchar:* Максимальное число символов, которое `CStringData` может храниться в структуре.

- *пмгр:* Указатель на `IAtlStringMgr` интерфейс "Диспетчер строк резервного копирования".

Конструктор сохраняет значения *pData* и *пмгр* в соответствующих переменных-членах ( `m_pData` и `m_pMgr` ). Затем он устанавливает длину буфера равным нулю, доступную длину, равную максимальному размеру фиксированного буфера, и число ссылок до-1. Значение счетчика ссылок указывает, что буфер заблокирован и используется экземпляр в `CFixedStringMgr` качестве диспетчера строк.

Пометка буфера как заблокированного не позволяет другим `CStringT` экземплярам удерживать общую ссылку на буфер. Если другим `CStringT` экземплярам разрешено совместное использование буфера, можно удалить буфер, содержащийся `CFixedStringT` в, в то время как другие строки по-прежнему использовали буфер.

`CFixedStringMgr` является полной реализацией `IAtlStringMgr` интерфейса. Реализация каждого метода обсуждается отдельно.

## <a name="implementation-of-cfixedstringmgrallocate"></a>Реализация Кфикседстрингмгр:: allocate

Реализация `CFixedStringMgr::Allocate` первой проверяет, является ли запрошенный размер строки меньшим или равным размеру фиксированного буфера (хранящегося в элементе `m_pData` ). Если фиксированный буфер достаточно большой, `CFixedStringMgr` блокирует фиксированный буфер с нулевой длиной. Пока длина строки не превышает размер фиксированного буфера, `CStringT` не потребуется перераспределять буфер.

Если запрошенный размер строки больше, чем фиксированный буфер, `CFixedStringMgr` перенаправляет запрос в Диспетчер строк резервного копирования. Предполагается, что диспетчер строк резервного копирования выделяет буфер из кучи. Однако перед возвратом этот буфер `CFixedStringMgr` блокирует буфер и заменяет указатель диспетчера строк буфера указателем на `CFixedStringMgr` объект. Это гарантирует, что попытки перераспределения или освобождения буфера `CStringT` будут вызывать метод `CFixedStringMgr` .

## <a name="implementation-of-cfixedstringmgrreallocate"></a>Реализация Кфикседстрингмгр:: перераспределения

Реализация `CFixedStringMgr::ReAllocate` очень похожа на ее реализацию `Allocate` .

Если перераспределенный буфер является фиксированным буфером, а запрошенный размер буфера меньше фиксированного буфера, выделение не выполняется. Однако если перераспределение буфера не является фиксированным буфером, это должен быть буфер, выделенный диспетчером резервного копирования. В этом случае для перераспределения буфера используется Диспетчер резервного копирования.

Если перераспределение буфера является фиксированным буфером, а новый размер буфера слишком велик для размещения в фиксированном буфере, `CFixedStringMgr` выделяет новый буфер с помощью диспетчера резервного копирования. Содержимое фиксированного буфера затем копируется в новый буфер.

## <a name="implementation-of-cfixedstringmgrfree"></a>Реализация Кфикседстрингмгр:: Free

Реализация соответствует тому `CFixedStringMgr::Free` же шаблону, что `Allocate` и и `ReAllocate` . Если освобожденный буфер является фиксированным буфером, метод устанавливает для него заблокированный буфер нулевой длины. Если освобожденный буфер был выделен с помощью диспетчера архивации, `CFixedStringMgr` для его освобождения используется Диспетчер резервного копирования.

## <a name="implementation-of-cfixedstringmgrclone"></a>Реализация Кфикседстрингмгр:: Clone

Реализация `CFixedStringMgr::Clone` всегда возвращает указатель на Диспетчер резервного копирования, а не на `CFixedStringMgr` самого себя. Это происходит потому, что каждый экземпляр `CFixedStringMgr` может быть связан только с одним экземпляром `CStringT` . Другие экземпляры, `CStringT` пытающиеся клонировать диспетчер, должны получить вместо этого диспетчер резервного копирования. Это связано с тем, что Диспетчер резервного копирования поддерживает общий доступ.

## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>Реализация Кфикседстрингмгр:: Жетнилстринг

Реализация `CFixedStringMgr::GetNilString` возвращает фиксированный буфер. Из-за соответствия "один к одному" для `CFixedStringMgr` и `CStringT` , данный экземпляр `CStringT` никогда не использует более одного буфера за раз. Таким образом, в то же время не требуется ни пустая строка, ни реальный буфер строк.

Всякий раз, когда фиксированный буфер не используется, `CFixedStringMgr` проверяет его инициализацию нулевой длины. Это позволяет использовать его в качестве пустой строки. В качестве дополнительной премии для `nAllocLength` элемента фиксированного буфера всегда устанавливается полный размер фиксированного буфера. Это означает, что `CStringT` может увеличивать строку без вызова [иатлстрингмгр:: reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate), даже для пустой строки.

## <a name="requirements"></a>Требования

**Заголовок:** CStringT. h

## <a name="see-also"></a>См. также раздел

[Управление памятью с помощью CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
