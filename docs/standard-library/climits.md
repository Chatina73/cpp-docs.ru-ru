---
title: '&lt;climits&gt;'
ms.date: 11/04/2016
f1_keywords:
- <climits>
helpviewer_keywords:
- climits header
ms.assetid: 7ca8a539-aa45-4ac3-86e8-74513be3f07e
ms.openlocfilehash: 67cddab4f42d10c4d1c78762c32ed1e4fd1e6175
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244793"
---
# <a name="ltclimitsgt"></a>&lt;climits&gt;

Включает заголовок стандартной библиотеки C, \<limits.h > и добавляет связанные имена в `std` пространства имен. Включение этого заголовка гарантирует, что имена, объявленные с внешней компоновкой в заголовке стандартной библиотеки C, объявляются в `std` пространства имен.

## <a name="syntax"></a>Синтаксис

```cpp
#include <climits>
```

## <a name="macros"></a>Макросы

```cpp
#define CHAR_BIT
#define SCHAR_MIN
#define SCHAR_MAX
#define UCHAR_MAX
#define CHAR_MIN
#define CHAR_MAX
#define MB_LEN_MAX
#define SHRT_MIN
#define SHRT_MAX
#define USHRT_MAX
#define INT_MIN
#define INT_MAX
#define UINT_MAX
#define LONG_MIN
#define LONG_MAX
#define ULONG_MAX
#define LLONG_MIN
#define LLONG_MAX
#define ULLONG_MAX
```

## <a name="see-also"></a>См. также

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)<br/>
[Общие сведения о стандартной библиотеке C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
