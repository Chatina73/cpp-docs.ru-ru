---
description: 'Дополнительные сведения о: allocator_suballoc классе'
title: Класс allocator_suballoc
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 7e542b4b8f419f1ac219c63b113aced7e0bd7cda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163591"
---
# <a name="allocator_suballoc-class"></a>Класс allocator_suballoc

Описывает объект, управляющий выделением и освобождением памяти для объектов типа *Type* , использующих кэш типа [cache_suballoc](cache-suballoc-class.md).

## <a name="syntax"></a>Синтаксис

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>Параметры

*Тип*\
Тип элементов, распределяемых распределителем.

## <a name="remarks"></a>Комментарии

Макрос [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) передает этот класс в качестве параметра *Name* в следующей инструкции: `ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Требования

**Заголовок:**\<allocators>

**Пространство имен:** stdext

## <a name="see-also"></a>См. также раздел

[\<allocators>](allocators-header.md)
