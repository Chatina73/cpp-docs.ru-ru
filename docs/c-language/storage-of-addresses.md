---
description: 'Подробнее о следующем: Хранение адресов'
title: Хранение адресов
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 8f0b51370659d7a23739d75f53492d171c17e422
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296697"
---
# <a name="storage-of-addresses"></a>Хранение адресов

Объем хранилища, необходимый для адреса, и значение адреса зависят от реализации компилятора. Одинаковая длина указателей на разные типы не гарантируется. Поэтому значение **sizeof(char \*)** необязательно равно значению **sizeof(int \*)** .

**Блок, относящийся только к системам Microsoft**

Для компилятора Microsoft C значение **sizeof(char \*)** равно значению **sizeof(int \*)** .

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Объявления указателей](../c-language/pointer-declarations.md)
