---
description: Подробнее об описателе класса хранения register
title: Спецификатор класса хранения register
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: a7e062f72191f6ee6d678d18b902ea184d362714
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120761"
---
# <a name="register-storage-class-specifier"></a>Спецификатор класса хранения register

**Блок, относящийся только к системам Майкрософт**

Компилятор Microsoft C/C++ не учитывает пользовательские запросы на переменные регистра. Но в целях обеспечения переносимости компилятор учитывает всю остальную семантику, связанную с ключевым словом **`register`** . Например, невозможно применить унарный оператор взятия адреса ( **&** ) к объекту регистра. Кроме того, ключевое слово **`register`** невозможно использовать в массивах.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Спецификаторы классов хранения для объявлений внутреннего уровня](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
