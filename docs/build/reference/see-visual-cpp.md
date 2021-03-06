---
description: 'Дополнительные сведения: &lt; см.&gt;'
title: '&lt;см. раздел> (комментарии к документации по C++)'
ms.date: 11/04/2016
f1_keywords:
- <see>
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: c1de0ec23854d159d661cd1b62df97169eab7317
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126225"
---
# <a name="ltseegt"></a>&lt;see&gt;

Тег \<see> позволяет задать ссылку из текста. Используется [\<seealso>](seealso-visual-cpp.md) для обозначения текста, который может потребоваться отобразить в разделе "см. также".

## <a name="syntax"></a>Синтаксис

```
<see cref="member"/>
```

#### <a name="parameters"></a>Параметры

*участниками*<br/>
Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.  Заключите имя в одинарные или двойные кавычки.

Компилятор проверяет, существует ли элемент кода, и разрешает `member` в имя элемента в выходных XML-данных.  Если компилятору не удается найти `member`, он выдает предупреждение.

## <a name="remarks"></a>Remarks

Скомпилируйте с [/doc](doc-process-documentation-comments-c-cpp.md) для обработки комментариев документации в файл.

См. [\<summary>](summary-visual-cpp.md) с примером использования \<see>.

Компилятор КОМПИЛЯТОРОМ MSVC будет пытаться разрешить ссылки cref в одном проходе через комментарии к документации.  Поэтому если при использовании правил поиска C++ компилятор не найдет символ, ссылка будет помечена как не разрешенная. [\<seealso>](seealso-visual-cpp.md)Дополнительные сведения см. в разделе.

## <a name="example"></a>Пример

Следующий пример показывает, как можно создать ссылку cref на универсальный тип, чтобы компилятор разрешил ее.

```cpp
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>См. также раздел

[Документация XML](xml-documentation-visual-cpp.md)
