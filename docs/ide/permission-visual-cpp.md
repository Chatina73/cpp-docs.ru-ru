---
title: '&lt;permission&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: 5cbcfd6bee97c3ca937ddfac363cd70276ee4d1e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529120"
---
# <a name="ltpermissiongt-visual-c"></a>&lt;permission&gt; (Visual C++)

Тег \<permission> tag позволяет документировать уровень доступа для члена. <xref:System.Security.PermissionSet> позволяет задать уровень доступа для члена.

## <a name="syntax"></a>Синтаксис

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>Параметры

*member*<br/>
Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции. Компилятор проверяет, существует ли элемент кода, и приводит `member` к каноническому имени элемента в выходных XML-данных.  Заключите имя в одинарные или двойные кавычки.

Если компилятору не удается найти `member`, он выдает предупреждение.

Дополнительные сведения о создании ссылки cref на универсальный тип см. в разделе [\<see>](../ide/see-visual-cpp.md).

*description*<br/>
Описание уровня доступа для члена.

## <a name="remarks"></a>Примечания

Чтобы обработать и сохранить комментарии документации в файл, при компиляции необходимо использовать параметр [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md).

Компилятор Visual C++ будет пытаться разрешить ссылки cref за один проход по комментариям документации.  Поэтому если при использовании правил поиска C++ компилятор не найдет символ, ссылка будет помечена как не разрешенная. Дополнительные сведения см. в описании [\<seealso>](../ide/seealso-visual-cpp.md).

## <a name="example"></a>Пример

```
// xml_permission_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_permission_tag.dll
using namespace System;
/// Text for class TestClass.
public ref class TestClass {
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>
   void Test() {}
};
```

## <a name="see-also"></a>См. также

[Документация XML](../ide/xml-documentation-visual-cpp.md)