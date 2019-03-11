---
title: marshal_as
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 2294d8fe94a32f281332c963b21a542366ae3207
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751515"
---
# <a name="marshalas"></a>marshal_as

Этот метод преобразует данные между собственной и управляемой средами.

## <a name="syntax"></a>Синтаксис

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>Параметры

*Входные данные*<br/>
[in] Значение, которое требуется маршалировать `To_Type` переменной.

## <a name="return-value"></a>Возвращаемое значение

Переменная типа `To_Type` , представляющий преобразованное значение из `input`.

## <a name="remarks"></a>Примечания

Этот метод является предоставляет упрощенный способ преобразования данных между неуправляемыми и управляемыми типами. Чтобы определить, какие типы данных поддерживаются, см. в разделе [Общие сведения о маршалинге в C++](../dotnet/overview-of-marshaling-in-cpp.md). Некоторые преобразования данных требуется контекст. Эти типы данных можно преобразовать с помощью [класс marshal_context](../dotnet/marshal-context-class.md).

При попытке маршалинга типов данных, которые не поддерживаются, пару `marshal_as` приведет к ошибке [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) во время компиляции. Читает сообщение, в состав сведения об этой ошибке. `C4996` Ошибка может возникать для более чем просто нерекомендуемые функции. Один из примеров пытается маршалировать пару типов данных, которые не поддерживаются.

Библиотека маршалинга состоит из нескольких файлов заголовка. Любые преобразования требуется только один файл, но может включать дополнительные файлы, если необходимо выполнить другие преобразования. Чтобы выяснить, какие преобразования связаны с файлов, найдите в таблице в `Marshaling Overview`. Независимо от того какой преобразования требуется сделать, пространство имен требование настроена на срабатывание всегда.

## <a name="example"></a>Пример

В этом примере маршалирует из `const char*` для `System::String` тип переменной.

```
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>Требования

**Файл заголовка:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, или \<msclr\marshal_atl.h >

**Пространство имен:** msclr::interop

## <a name="see-also"></a>См. также

[Общие сведения о маршалинге в C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[Класс marshal_context](../dotnet/marshal-context-class.md)
