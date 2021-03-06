---
description: 'Дополнительные сведения: упаковка (C++/CLI)'
title: упаковка-преобразование (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: 4914271dc5b1ae0bcee2a82b3cddb4433a2dc84f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282592"
---
# <a name="boxing-ccli"></a>упаковка-преобразование (C++/CLI)

Упаковка — это процесс преобразования типа значения в тип `object` или в любой тип интерфейса, реализуемый типом значения. Если поле среды CLR имеет тип значения, оно инкапсулирует значение в `System.Object` и сохраняет его в управляемой куче. Операция распаковки извлекает тип значения из объекта. Упаковка является неявной; распаковка является явной.

## <a name="related-articles"></a>Связанные статьи

|Заголовок|Описание|
|-----------|-----------------|
|[Как явно запрашивать упаковку-преобразование](../dotnet/how-to-explicitly-request-boxing.md)|Описывает, как явно запрашивать упаковку-преобразование для переменной.|
|[Как использовать gcnew для создания типов значений и использования неявной упаковки](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Показывает, как использовать **`gcnew`** для создания упакованного типа значения, который может быть размещен в управляемой куче с сбором мусора.|
|[Практическое руководство. Распаковка](../dotnet/how-to-unbox.md)|Показывает, как распаковать и изменить значение.|
|[Стандартные преобразования и неявная упаковка-преобразование](../dotnet/standard-conversions-and-implicit-boxing.md)|Показывает, что компилятор выбирает стандартное преобразование для преобразования, для которого требуется упаковка-преобразование.|
|[Программирование .NET с использованием C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Статья верхнего уровня по программированию .NET в документации по Visual C++.|
