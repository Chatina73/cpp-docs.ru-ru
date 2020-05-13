---
title: Вопросы, связанные с написанием кода пролога и эпилога
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: e1559c75808a72cd3f9674399bec036cf392b44f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334584"
---
# <a name="considerations-when-writing-prologepilog-code"></a>Вопросы, связанные с написанием кода пролога и эпилога

**Microsoft Специфический**

Прежде чем писать собственные последовательности пролога и эпилог-кода, важно понять, как выкладывается рамка стека. Также полезно знать, как использовать **__LOCAL_SIZE** предопределенную константу.

## <a name="cstack-frame-layout"></a><a name="_clang_c_stack_frame_layout"></a>Укладка кадров CStack

В данном примере показан стандартный код пролога, который может присутствовать в 32-разрядной функции.

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

Переменная `localbytes` представляет число байтов, которые требуются в стеке для локальных переменных, а переменная `registers` — это заполнитель, представляющий список сохраняемых в стеке регистров. После проталкивания регистров можно разместить в стеке все другие необходимые данные. Ниже приведен соответствующий код эпилога.

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

Стек всегда расширяется в направлении вниз (от старших адресов памяти к младшим). Указатель базы (`ebp`) указывает на помещенное в стек значение `ebp`. Область локальных переменных начинается с `ebp-2`. Для доступа к локальным переменным необходимо вычислить смещение от `ebp` путем вычитания соответствующего значения из `ebp`.

## <a name="the-__local_size-constant"></a><a name="_clang_the___local_size_constant"></a> Константа __LOCAL_SIZE

Компилятор предоставляет константу **__LOCAL_SIZE**, которую можно использовать использования во встроенном ассемблерном блоке кода пролога функции. Она служит для выделения пространства локальным переменным в кадре стека пользовательского кода пролога.

Значение константы **__LOCAL_SIZE** определяется компилятором. Это значение представляет общее количество байтов всех определяемых пользователем локальных переменных и временных переменных, создаваемых компилятором. Константу **__LOCAL_SIZE** можно использовать только в качестве непосредственного операнда, но не в выражениях. Значение этой константы не следует изменять и переопределять. Пример:

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

В следующем примере функции naked с пользовательскими последовательностями пролога и эпилога константа **__LOCAL_SIZE** используется в последовательности пролога.

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**END Microsoft Специфический**

## <a name="see-also"></a>См. также раздел

[Функции naked](../c-language/naked-functions.md)
