---
title: собственных pragma
description: Встроенная функция КОМПИЛЯТОРОМ MSVC pragma используется для указания поддерживаемых встроенных функций для использования в качестве встроенных.
ms.date: 01/22/2021
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragma, intrinsic
no-loc:
- pragma
ms.openlocfilehash: 618705c42c20baf2b99f89e138b30d5633b9e592
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713549"
---
# <a name="intrinsic-no-locpragma"></a>`intrinsic` pragma

Указывает, что вызовы функций, указанных в pragma списке аргументов, являются встроенными.

## <a name="syntax"></a>Синтаксис

> **`#pragma intrinsic(`***function_1* [ **`,`** *function_2* ...]**`)`**

## <a name="remarks"></a>Примечания

**`intrinsic`** pragma Сообщает компилятору, что функция имеет известное поведение. Компилятор может вызвать функцию и не заменять вызов функции подставляемыми инструкциями, если это позволит повысить производительность.

Ниже перечислены функции библиотеки со встроенными формами. После того как объект **`intrinsic`** pragma виден, он вступает в силу в первом определении функции, содержащем указанную подставляемую функцию. Результат переходит к концу исходного файла или к внешнему виду, в котором `function` pragma указана та же встроенная функция. **`intrinsic`** pragma Можно использовать только за пределами определения функции на глобальном уровне.

Следующие функции имеют встроенные формы, а встроенные формы используются при указании [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) :

:::row:::
   :::column span="":::
      [`abs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md)\
      [`_disable`](../intrinsics/disable.md)\
      [`_enable`](../intrinsics/enable.md)\
      [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md)\
      [`_inp`](../c-runtime-library/inp-inpw-inpd.md)\
      [`_inpw`](../c-runtime-library/inp-inpw-inpd.md)\
   :::column-end:::
   :::column span="":::
      [`labs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md)\
      [`_lrotl`](../c-runtime-library/reference/lrotl-lrotr.md)\
      [`_lrotr`](../c-runtime-library/reference/lrotl-lrotr.md)\
      [`memcmp`](../c-runtime-library/reference/memcmp-wmemcmp.md)\
      [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md)\
   :::column-end:::
   :::column span="":::
      [`memset`](../c-runtime-library/reference/memset-wmemset.md)\
      [`_outp`](../c-runtime-library/outp-outpw-outpd.md)\
      [`_outpw`](../c-runtime-library/outp-outpw-outpd.md)\
      [`_rotl`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)\
      [`_rotr`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)\
   :::column-end:::
   :::column span="":::
      [`strcat`](../c-runtime-library/reference/strcat-wcscat-mbscat.md)\
      [`strcmp`](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)\
      [`strcpy`](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)\
      [`strlen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
      [`_strset`](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)\
   :::column-end:::
:::row-end:::

Программы, использующие встроенные функции, выполняются быстрее, так как они не имеют издержек на вызовы функций. Однако они могут быть больше из-за созданного дополнительного кода.

### <a name="x86-specific-example"></a>Пример для x86

`_disable` `_enable` Встроенная функция и создает инструкции режима ядра для отключения или включения прерываний и может быть полезна в драйверах режима ядра.

Скомпилируйте следующий код из командной строки с помощью `cl -c -FAs sample.c` и посмотрите *`sample.asm`* , что они включают в себя команды CLI для x86 и сти:

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

### <a name="intrinsic-floating-point-functions"></a>Встроенные функции с плавающей запятой

Эти функции с плавающей запятой не имеют истинных встроенных форм. Вместо этого они имеют версии, которые передают аргументы непосредственно в микросхему с плавающей запятой, а не отправляя их в стек:

:::row:::
   :::column span="":::
      [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md)\
      [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md)\
   :::column-end:::
   :::column span="":::
      [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md)\
      [`fmod`](../c-runtime-library/reference/fmod-fmodf.md)\
   :::column-end:::
   :::column span="":::
      [`pow`](../c-runtime-library/reference/pow-powf-powl.md)\
      [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md)\
   :::column-end:::
   :::column span="":::
      [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md)\
   :::column-end:::
:::row-end:::

Эти функции с плавающей запятой имеют истинные встроенные формы при указании [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) и [`/fp:fast`](../build/reference/fp-specify-floating-point-behavior.md) (или любых параметрах, включающих **`/Oi`** : [`/Ox`](../build/reference/ox-full-optimization.md) , [`/O1`](../build/reference/o1-o2-minimize-size-maximize-speed.md) и [`/O2`](../build/reference/o1-o2-minimize-size-maximize-speed.md) ):

:::row:::
   :::column span="":::
      [`atan`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md)\
   :::column-end:::
   :::column span="":::
      [`exp`](../c-runtime-library/reference/exp-expf.md)\
      [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
   :::column-end:::
   :::column span="":::
      [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md)\
   :::column-end:::
   :::column span="":::
      [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)\
      [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md)\
   :::column-end:::
:::row-end:::

Можно использовать [`/fp:strict`](../build/reference/fp-specify-floating-point-behavior.md) или [`/Za`](../build/reference/za-ze-disable-language-extensions.md) для переопределения создания истинных встроенных параметров с плавающей запятой. В этом случае функции будут создаваться как библиотечные процедуры, которые передают аргументы напрямую в микросхему операций с плавающей запятой, а не в стек программы.

[`#pragma function`](../preprocessor/function-c-cpp.md)Дополнительные сведения и пример включения и отключения встроенных функций для блока исходного текста см. в разделе.

## <a name="see-also"></a>См. также раздел

[Директивы pragma и `__pragma` `_Pragma` Ключевые слова и](./pragma-directives-and-the-pragma-keyword.md)\
[Встроенные функции компилятора](../intrinsics/compiler-intrinsics.md)
