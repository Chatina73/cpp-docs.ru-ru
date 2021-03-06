---
description: 'Дополнительные сведения: Ошибка средств компоновщика LNK2031'
title: Ошибка средств компоновщика LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 3d955f106f569f91df9640bacfcca4df511ffd95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275676"
---
# <a name="linker-tools-error-lnk2031"></a>Ошибка средств компоновщика LNK2031

> не удалось создать p/Invoke для "*function_declaration*" *decorated_name*; Соглашение о вызовах отсутствует в метаданных

## <a name="remarks"></a>Комментарии

При попытке импортировать собственную функцию в чистый образ Помните, что неявные соглашения о вызовах отличаются от собственных и чистых компиляций. Дополнительные сведения об чистых образах см. в разделе [чистый и проверяемый код (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Параметр компилятора **/clr: pure** является устаревшим в visual Studio 2015 и не поддерживается в visual Studio 2017.

## <a name="examples"></a>Примеры

Этот пример кода создает компонент с экспортированной собственной функцией, соглашение о вызовах которого неявно [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

В следующем примере создается чистый клиент, использующий собственную функцию. Однако соглашение о вызовах в **/clr: pure** [__clrcall](../../cpp/clrcall.md). Следующий пример приводит к возникновению ошибки LNK2031.

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

В следующем примере показано, как использовать собственную функцию из чистого образа. Обратите внимание на явный **`__cdecl`** спецификатор соглашения о вызовах.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
