---
title: Предупреждение компилятора (уровень 1) C4445
ms.date: 11/04/2016
f1_keywords:
- C4445
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
ms.openlocfilehash: 6c1b4f4ae4f60d0c4281e0bbcfc9ca2b58d81851
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611293"
---
# <a name="compiler-warning-level-1-c4445"></a>Предупреждение компилятора (уровень 1) C4445

function: в управляемом типе или типе WinRT виртуальный метод не может быть закрытым

Если виртуальная функция закрытая, у производного типа нет доступа к ней. Чтобы устранить эту ошибку, измените тип доступ виртуальной функции-члена на защищенный или общий.