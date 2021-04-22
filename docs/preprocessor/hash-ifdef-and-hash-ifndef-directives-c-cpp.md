---
description: 'Дополнительные сведения: директивы #ifdef и #ifndef (C/C++)'
title: '#Директивы ifdef и #ifndef (C/C++)'
ms.date: 04/14/2021
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.openlocfilehash: 8a5d65f22e3ea5d7324c5c4c2d1222f74140ebc0
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577416"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>`#ifdef``#ifndef`директивы и (C/C++)

**`#ifdef`** **`#ifndef`** Директивы препроцессора и имеют тот же результат, что и [`#if`](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) директива, когда она используется с **`defined`** оператором.

## <a name="syntax"></a>Синтаксис

> **`#ifdef`** *`identifier`*\
> **`#ifndef`** *`identifier`*

Эти директивы эквивалентны следующим:

> **`#if defined`** *`identifier`*\
> **`#if !defined`** *`identifier`*

## <a name="remarks"></a>Замечания

Можно использовать **`#ifdef`** **`#ifndef`** директивы и в любом месте `#if` . **`#ifdef`** *`identifier`* Инструкция эквивалентна, `#if 1` Если *`identifier`* определен параметр. Он эквивалентен `#if 0` , если не *`identifier`* был определен или был неопределен **`#undef`** директивой. Эти директивы проверяют наличие или отсутствие только идентификаторов, определенных с директивой `#define`, а не идентификаторов, объявленных в исходном коде C или C++.

Эти директивы предназначены только для совместимости с предыдущими версиями языка. Для **`defined(`** *`identifier`* **`)`** директивы рекомендуется использовать константное выражение `#if` .

**`#ifndef`** Директива проверяет наличие противоположного условия, установленного **`#ifdef`** . Если идентификатор не был определен или его определение было удалено с помощью `#undef` , условие имеет значение true (отличное от нуля). В противном случае условие не выполняется (false, значение равно 0).

**Блок, относящийся только к системам Microsoft**

*Идентификатор* можно передать из командной строки с помощью [`/D`](../build/reference/d-preprocessor-definitions.md) параметра. С можно указать до 30 макросов `/D` .

**`#ifdef`** Директива полезна для проверки существования определения, так как определение может быть передано из командной строки. Пример:

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Директивы препроцессора](../preprocessor/preprocessor-directives.md)
