---
title: ___lc_collate_cp_func
ms.date: 11/04/2016
apiname:
- ___lc_collate_cp_func
apilocation:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- ___lc_collate_cp_func
helpviewer_keywords:
- ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
ms.openlocfilehash: fac8b7ba2e9568dd53509e5cccbb96a6b2f1df8d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738883"
---
# <a name="lccollatecpfunc"></a>___lc_collate_cp_func

Внутренняя функция CRT. Получает текущую кодовую страницу сортировки потока.

## <a name="syntax"></a>Синтаксис

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Возвращаемое значение

Текущая кодовая страница сортировки потока.

## <a name="remarks"></a>Примечания

`___lc_collate_cp_func` — это внутренняя функция CRT, которая используется другими функциями CRT для получения текущей кодовой страницы сортировки из локального хранилища потока для данных CRT. Эти сведения также доступны при использовании функции [_get_current_locale](../c-runtime-library/reference/get-current-locale.md).

Внутренние функции CRT связаны с конкретной реализацией и подлежат изменению в каждом выпуске. Мы не рекомендуем использовать их в коде.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|`___lc_collate_cp_func`|crt\src\setlocal.h|

## <a name="see-also"></a>См. также

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
