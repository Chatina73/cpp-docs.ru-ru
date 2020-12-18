---
description: 'Подробнее о следующем: Хранение битовых полей'
title: Хранение битовых полей
ms.date: 11/04/2016
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
ms.openlocfilehash: 43066fe648bc380a8278168f336ebcf10cbbbdf5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205308"
---
# <a name="storage-of-bit-fields"></a>Хранение битовых полей

**ANSI 3.5.2.1** Порядок назначения битовых полей в целом числе

Битовые поля в целом числе назначаются в направлении от младшего разряда к старшему. В приведенном ниже коде

```
struct mybitfields
{
   unsigned a : 4;
   unsigned b : 5;
   unsigned c : 7;
} test;

int main( void )
{
   test.a = 2;
   test.b = 31;
   test.c = 0;
}
```

биты размещаются следующим образом:

```
00000001 11110010
cccccccb bbbbaaaa
```

Поскольку в процессорах 80x86 младший байт целочисленных значений размещается перед старшим байтом, указанное выше целое число 0x01F2 будет храниться в физической памяти в следующем виде: 0xF2 0x01.

## <a name="see-also"></a>См. также

[Структуры, объединения, перечисления и битовые поля](../c-language/structures-unions-enumerations-and-bit-fields.md)
