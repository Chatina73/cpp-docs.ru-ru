---
description: Дополнительные сведения:. МОДЕЛЬ (32-разрядный MASM)
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: a4324b89f1194227edd7f1d5b7bd70560eca16be
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951424"
---
# <a name="model-32-bit-masm"></a>. МОДЕЛЬ (32-разрядный MASM)

Инициализирует модель памяти программы. (только 32-разрядный MASM.)

## <a name="syntax"></a>Синтаксис

> **. Память модели** *— модель* ⟦__,__ *язык — тип*⟧ ⟦__,__ *Stack-Option*⟧

### <a name="parameters"></a>Параметры

*память-модель*\
Обязательный параметр, который определяет размер кода и указателей данных.

*Тип языка*\
Необязательный параметр, который задает соглашения о вызовах и именовании для процедур и открытых символов.

*Stack-параметр*\
Необязательный параметр.

*параметр Stack-* не используется, если *модель памяти* **плоская**.

Указание **неарстакк** группирует сегмент стека в один физический сегмент (**дграуп**) вместе с данными. Предполагается, что регистр сегмента стека (**SS**) содержит тот же адрес, что и регистр сегмента данных (**DS**). **Фарстакк** не будет группировать стек с **дграуп**; таким, **SS** не равно **DS**.

## <a name="remarks"></a>Комментарии

**. МОДЕЛЬ** не используется в [MASM для x64 (ml64.exe)](masm-for-x64-ml64-exe.md).

В следующей таблице перечислены возможные значения для каждого параметра при нацеливании на 16-разрядные и 32-разрядные платформы:

|Параметр|32-разрядные значения|16-разрядные значения (поддержка более ранней разработки 16-разрядных приложений)|
|---------------|--------------------|----------------------------------------------------------------|
|*память-модель*|**ВЫПУКЛАЯ**| **мелкий, Малый**, **компактный**, **средний**, **крупный**, **огромный**, **плоский**|
|*Тип языка*|**C**, **STDCALL**|**C**, **Basic**, **Fortran**, **Pascal**, **syscall**, **STDCALL**|
|*Stack-параметр*|Не используется|**неарстакк**, **фарстакк**|

## <a name="code"></a>Код

Для получения примеров, связанных с MASM, скачайте примеры компилятора на странице [примеров кода на Visual C++ и связанной документации для Visual Studio 2010](https://github.com/Microsoft/vcsamples).

В следующем примере иллюстрируется использование директивы `.MODEL`.

## <a name="example"></a>Пример

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

ifndef X64
.686p
.XMM
.model flat, C
endif

.data
; user data

.code
; user code

fxn PROC public
  xor eax, eax ; zero function return value
  ret
fxn ENDP

end
```

## <a name="see-also"></a>См. также раздел

[Справочник по директивам](directives-reference.md)\
[Грамматика MASM BNF](masm-bnf-grammar.md)
