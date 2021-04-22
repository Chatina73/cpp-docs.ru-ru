---
title: float_control pragma
description: Описывает использование и эффекты pragma директивы float_control. Директива float_control управляет состоянием точной семантики с плавающей точкой и семантикой исключений во время выполнения.
ms.date: 04/15/2021
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragma, float_control
no-loc:
- pragma
ms.openlocfilehash: b7a02acf729d04527300454fed6e74e7d06bbfe9
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539768"
---
# <a name="float_control-pragma"></a>`float_control` pragma

Указывает поведение чисел с плавающей запятой для функции.

## <a name="syntax"></a>Синтаксис

> **`#pragma float_control`**\
> **`#pragma float_control( precise,`** { **`on`** &vert; **`off`** } [ **`, push`** ] **`)`**\
> **`#pragma float_control( except,`** { **`on`** &vert; **`off`** } [ **`, push`** ] **`)`**\
> **`#pragma float_control(`** { **`push`** &vert; **`pop`** } **`)`**

## <a name="options"></a>Варианты

**`precise`**, **`on`** | **`off`**, **`push`**\
Указывает, следует ли включать ( **`on`** ) или отключать ( **`off`** ) точную семантику с плавающей запятой. Сведения о различиях с **`/fp:precise`** параметром компилятора см. в разделе "Примечания". Необязательный **`push`** маркер отправляет текущее значение для **`float_control`** во внутреннем стеке компилятора.

**`except`**, **`on`** | **`off`**, **`push`**\
Указывает, следует ли включать ( **`on`** ) или отключать ( **`off`** ) семантику исключений с плавающей запятой. Необязательный **`push`** маркер отправляет текущее значение для **`float_control`** во внутреннем стеке компилятора.

**`except`** может иметь значение, только **`on`** Если **`precise`** параметр имеет значение **`on`** .

**`push`**\
Помещает текущее **`float_control`** значение параметра во внутренний стек компилятора.

**`pop`**\
Удаляет **`float_control`** параметр из верхнего внутреннего стека компилятора и создает новый **`float_control`** параметр.

## <a name="remarks"></a>Комментарии

**`float_control`** pragma Не имеет того же поведения, что и [`/fp`](../build/reference/fp-specify-floating-point-behavior.md) параметр компилятора. **`float_control`** pragma Компонент управляет только частью поведения операций с плавающей запятой. Его необходимо сочетать с [`fp_contract`](../preprocessor/fp-contract.md) [`fenv_access`](../preprocessor/fenv-access.md) pragma директивами и для повторного создания **`/fp`** параметров компилятора. В следующей таблице приведены эквивалентные pragma параметры для каждого параметра компилятора.

| Параметр | `float_control(precise, *)` | `float_control(except, *)` | `fp_contract(*)` | `fenv_access(*)` |
|-|-|-|-|-|
| `/fp:strict`             | `on`  | `on`  | `off` | `on`  |
| `/fp:precise`            | `on`  | `off` | `on`  | `off` |
| `/fp:fast`               | `off` | `off` | `on`  | `off` |

Иными словами, может потребоваться использовать несколько pragma директив в сочетании для эмуляции **`/fp:fast`** **`/fp:precise`** **`/fp:strict`** параметров командной строки, и.

Существует ряд ограничений, которые можно использовать **`float_control`** **`fenv_access`** в сочетании с директивами и с плавающей запятой pragma .

- Параметр можно использовать только **`float_control`** в **`except`** **`on`** том случае, если включена точная семантика. Точная семантика может быть включена либо параметром **`float_control`** pragma , либо с помощью **`/fp:precise`** **`/fp:strict`** параметров компилятора или.

- Нельзя **`float_control`** Отключить **`precise`** , если включена семантика исключений, будь то **`float_control`** pragma **`/fp:except`** параметр компилятора или.

- Невозможно включить **`fenv_access`** , если не включена точная семантика, независимо от того, является ли **`float_control`** pragma параметр компилятора или.

- Нельзя отключить, **`float_control`** **`precise`** Если **`fenv_access`** включен.

Эти ограничения означают, что порядок некоторых директив с плавающей запятой pragma важен. Для перехода от быстрой модели к конкретной модели с помощью pragma директив используйте следующий код:

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

Чтобы переходить от определенной модели к быстрой модели с помощью **`float_control`** pragma , используйте следующий код:

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // enable contractions
```

Если параметры не указаны, не **`float_control`** оказывает никакого влияния.

## <a name="example"></a>Пример

В следующем примере показано, как перехватить исключение переполнения с плавающей запятой с помощью pragma **`float_control`** .

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>См. также раздел

[Директивы pragma и `__pragma` `_Pragma` Ключевые слова и](./pragma-directives-and-the-pragma-keyword.md)\
[`fenv_access` pragma](../preprocessor/fenv-access.md)\
[`fp_contract` pragma](../preprocessor/fp-contract.md)
