---
title: Регистратор ATL и деревьях синтаксического анализа
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: e1aea573e78e6f6a9a86bc4e3987ee448815f329
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273326"
---
# <a name="understanding-parse-trees"></a>Основные сведения о деревьях синтаксического анализа

Можно определить один или несколько деревьях синтаксического анализа в скрипте регистратора, где каждое дерево синтаксического анализа имеет следующий вид:

```
<root key>{<registry expression>}+
```

Здесь:

```
<root key> ::= HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |
    HKEY_LOCAL_MACHINE | HKEY_USERS |
    HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |
    HKEY_CURRENT_CONFIG | HKCR | HKCU |
    HKLM | HKU | HKPD | HKDD | HKCC
<registry expression> ::= <Add Key> | <Delete Key>
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name> [<Key Value>][{<Add Key>}]
<Delete Key> ::= Delete<Key Name>
<Key Name> ::= '<AlphaNumeric>+'
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0
<Key Value> ::== <Key Type><Key Name>
<Key Type> ::= s | d
<Key Value> ::= '<AlphaNumeric>'
```

> [!NOTE]
> `HKEY_CLASSES_ROOT` и `HKCR` эквивалентны; `HKEY_CURRENT_USER` и `HKCU` эквивалентны; и т. д.

Дерево синтаксического анализа можно добавить несколько разделов и подразделов для \<корневой ключ >. Таким образом, он поддерживает подраздел дескриптор открытым завершения синтаксического анализа, все его подразделы средство синтаксического анализа. Этот подход более эффективен, чем работе один ключ одновременно, как показано в следующем примере:

```
HKEY_CLASSES_ROOT
{
    'MyVeryOwnKey'
    {
        'HasASubKey'
        {
            'PrettyCool'
        }
    }
}
```

Здесь, изначально открывает регистратор (создает) `HKEY_CLASSES_ROOT\MyVeryOwnKey`. Затем видит, что `MyVeryOwnKey` содержит подраздел. Вместо закрыть ключ, чтобы `MyVeryOwnKey`, регистратор сохраняет дескриптор и откроется (создает) `HasASubKey` использования этого дескриптора родительского. (Системного реестра может быть медленнее при открытом не дескриптор родительского.) Таким образом, открыв `HKEY_CLASSES_ROOT\MyVeryOwnKey` и открытия `HasASubKey` с `MyVeryOwnKey` как родительский выполняется быстрее, чем Открытие `MyVeryOwnKey`, закрытие `MyVeryOwnKey`, а затем откройте `MyVeryOwnKey\HasASubKey`.

## <a name="see-also"></a>См. также

[Создание скриптов регистратора](../atl/creating-registrar-scripts.md)
