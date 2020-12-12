---
description: 'Подробнее: рекомендации по написанию кода пролога или эпилога'
title: Рекомендации по написанию кода Prolog-Epilog
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: 6deb6e9120c83992a7fe2529d0c9366b8e191056
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204775"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Особенности написания кода пролога и эпилога

**Блок, относящийся только к системам Microsoft**

Перед написанием собственных последовательностей кода пролога и эпилога важно понимать, как располагается кадр стека. Также полезно иметь представление об использовании `__LOCAL_SIZE` символа.

## <a name="stack-frame-layout"></a><a name="_pluslang_c.2b2b_.stack_frame_layout"></a> Макет кадра стека

В данном примере показан стандартный код пролога, который может присутствовать в 32-разрядной функции.

```
push        ebp                ; Save ebp
mov         ebp, esp           ; Set stack frame pointer
sub         esp, localbytes    ; Allocate space for locals
push        <registers>        ; Save registers
```

Переменная `localbytes` представляет число байтов, которые требуются в стеке для локальных переменных, а переменная `<registers>` — это заполнитель, представляющий список сохраняемых в стеке регистров. После проталкивания регистров можно разместить в стеке все другие необходимые данные. Ниже приведен соответствующий код эпилога.

```
pop         <registers>   ; Restore registers
mov         esp, ebp      ; Restore stack pointer
pop         ebp           ; Restore ebp
ret                       ; Return from function
```

Стек всегда расширяется в направлении вниз (от старших адресов памяти к младшим). Указатель базы (`ebp`) указывает на помещенное в стек значение `ebp`. Область локальных переменных начинается с адреса `ebp-4`. Для доступа к локальным переменным необходимо вычислить смещение от `ebp` путем вычитания соответствующего значения из `ebp`.

## <a name="__local_size"></a><a name="_pluslang___local_size"></a> __LOCAL_SIZE

Компилятор предоставляет символ, `__LOCAL_SIZE` который используется во встроенном ассемблерном блоке кода пролога функции. Этот символ служит для выделения пространства локальным переменным в кадре стека пользовательского кода пролога.

Компилятор определяет значение `__LOCAL_SIZE` . Это значение представляет общее количество байтов всех определяемых пользователем локальных переменных и временных переменных, создаваемых компилятором. `__LOCAL_SIZE` может использоваться только в качестве немедленного операнда; его нельзя использовать в выражении. Значение этого символа не следует изменять и переопределять. Пример:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

В следующем примере функции с атрибутом naked, содержащей пользовательские последовательности пролога и эпилога, используется `__LOCAL_SIZE` символ в последовательности пролога:

```cpp
// the__local_size_symbol.cpp
// processor: x86
__declspec ( naked ) int main() {
   int i;
   int j;

   __asm {      /* prolog */
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */
   __asm {   /* epilog */
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Вызовы функций с атрибутом naked](../cpp/naked-function-calls.md)
