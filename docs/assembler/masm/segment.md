---
description: 'Дополнительные сведения о: сегмент'
title: SEGMENT
ms.date: 12/16/2019
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: aeb99080043cbfb13fdec1c2e82df3a6d16b306d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97125597"
---
# <a name="segment"></a>SEGMENT

Определяет сегмент программы *с именем, имеющим атрибуты* сегмента

## <a name="syntax"></a>Синтаксис

> *имя* **сегмент** ⟦**ReadOnly**⟧ ⟦*aligned*⟧ ⟦*Combine*⟧ ⟦*использовать*⟧ ⟦*характеристики*⟧ **псевдоним (**_строка_**)** ⟦__"__*класс*__"__⟧ \
> *инструкции*\
> *имя* **заканчивается**

#### <a name="parameters"></a>Параметры

*нижнем*\
Диапазон адресов памяти, из которых можно выбрать начальный адрес для сегмента. Тип выравнивания может быть одним из следующих:

|Тип выровняйте|Начальный адрес|
|----------------|----------------------|
|**BYTE**|Следующий доступный байтовый адрес.|
|**WORD**|Следующий доступный адрес слова (2 байта на слово).|
|**DWORD**|Адрес следующего доступного двойного слова (4 байта на двойное слово).|
|**СЛАБ**|Следующий доступный адрес абзаца (16 байт на абзац).|
|**СТРАНИЦ**|Следующий доступный адрес страницы (256 байт на страницу).|
|**Выровняйте**(*n*)|Следующий доступный *n*-й байтовый адрес. Дополнительные сведения см. в разделе "Примечания".|

Если этот параметр не указан, по умолчанию используется **para** .

*Combine* (только 32-разрядный MASM) \
**Общедоступный**, **стек**, **Общий**, **память**, **по**<em>адресу</em>, **частный**

*Используйте* (только 32-разрядный MASM) \
**USE16**, **USE32**, **плоский**

*показатели*\
**Сведения**, **Чтение**, **запись**, **выполнение**, **Общий**, **страничный**, **некэш** и **Отмена**

Они поддерживаются только для COFF и соответствуют характеристикам раздела COFF с аналогичным именем (например, **Shared** соответствует IMAGE_SCN_MEM_SHARED). READ устанавливает флаг IMAGE_SCN_MEM_READ. Флаг obsolete READONLY привел к очистке флага IMG_SCN_MEM_WRITE. Если заданы какие-либо *характеристики* , то характеристики по умолчанию не используются и действуют только флаги, указанные программистом.

_Строка_\
Эта строка используется в качестве имени раздела в выпущенном объекте COFF.  Создает несколько разделов с одинаковым внешним именем с разными именами сегментов MASM.

Не поддерживается с **/OMF**.

*см*\
Определяет, как сегменты должны объединяться и упорядочиваться в собранном файле. Типичные значения: `'DATA'` , `'CODE'` , `'CONST'` и `'STACK'`

## <a name="remarks"></a>Комментарии

Для `ALIGN(n)` , *n* может иметь любую степень числа 2 от 1 до 8192; не поддерживается в **/OMF**.

## <a name="see-also"></a>См. также раздел

[Справочник по директивам](directives-reference.md)\
[Грамматика MASM BNF](masm-bnf-grammar.md)
