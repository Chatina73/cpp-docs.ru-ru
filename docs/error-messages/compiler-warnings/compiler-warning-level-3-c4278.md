---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 3) C4278'
title: Предупреждение компилятора (уровень 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: f7a53b54422e28f94096b91502651cb9355a244e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344150"
---
# <a name="compiler-warning-level-3-c4278"></a>Предупреждение компилятора (уровень 3) C4278

> "*идентификатор*": идентификатор в библиотеке типов "*tlb*" уже является макросом; используйте квалификатор "Rename"

При использовании [#import](../../preprocessor/hash-import-directive-cpp.md)идентификатор в импортируемой библиотеке типов пытается объявить *идентификатор* идентификатора. Однако он уже является допустимым символом.

Используйте атрибут `#import` **Rename** , чтобы назначить псевдоним символу в библиотеке типов.
