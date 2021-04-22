---
description: 'Дополнительные сведения о: основные сведения о деревьях синтаксического анализа'
title: Регистратор ATL и деревья синтаксического анализа
ms.date: 04/15/2021
helpviewer_keywords:
- parse trees
ms.openlocfilehash: b9442651d8d6e04ee6c309c9d93b76135fe05c57
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539538"
---
# <a name="understanding-parse-trees"></a>Основные сведения о деревьях синтаксического анализа

В скрипте регистратора можно определить одно или несколько деревьев синтаксического анализа, где каждое дерево синтаксического анализа имеет следующую форму:

> \<root-key>{\<registry expression>}+

где:

> *\<root-key>* ::=\
> &emsp;**`HKEY_CLASSES_ROOT`** &vert; **`HKEY_CURRENT_USER`** &vert;\
> &emsp;**`HKEY_LOCAL_MACHINE`** &vert; **`HKEY_USERS`** &vert;\
> &emsp;**`HKEY_PERFORMANCE_DATA`** &vert; **`HKEY_DYN_DATA`** &vert;\
> &emsp;**`HKEY_CURRENT_CONFIG`** &vert; **`HKCR`** &vert; **`HKCU`** &vert;\
> &emsp;**`HKLM`** &vert; **`HKU`** &vert; **`HKPD`** &vert; **`HKDD`** &vert; **`HKCC`**
>
> *\<registry-expression>* ::=\
> &emsp; *\<Add-Key>* &vert; *\<Delete-Key>*
>
> *\<Add-Key>* ::=\
> &emsp; \[**`ForceRemove`** &vert; **`NoRemove`** &vert; **`val`**] *\<Key-Name>* \[*\<Key-Value>*] \[ **`{`** *\<Add-Key>* **`}`** ]
>
> *\<Delete-Key>* ::=\
> &emsp; **`Delete`** *\<Key-Name>*
>
> *\<Key-Name>* ::=\
> &emsp; **`'`**_\<AlphaNumeric>_+**`'`**
>
> *\<AlphaNumeric>* ::=\
> &emsp; любой символ, отличный от NULL.
>
> *\<Key-Value>* ::=\
> &emsp; *\<Key-Type>* *\<Key-Name>*
>
> *\<Key-Type>* ::=\
> &emsp; **`s`** &vert; **`d`**

> [!NOTE]
> **`HKEY_CLASSES_ROOT`** и **`HKCR`** являются эквивалентными; **`HKEY_CURRENT_USER`** и **`HKCU`** эквивалентны; и т. д.

Дерево синтаксического анализа может добавлять в. несколько ключей и подразделов \<root-key> . Регистратор сохраняет все открытые маркеры, пока синтаксический анализатор не завершит анализ всех подразделов. Это более эффективно, чем работа с одним ключом за раз. Ниже приведен пример:

```rgs
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

Здесь сначала открывается регистратор (создает) `HKEY_CLASSES_ROOT\MyVeryOwnKey` . Затем он видит, что `MyVeryOwnKey` имеет подраздел. Вместо того, чтобы закрывать ключ `MyVeryOwnKey` , регистратор сохраняет его и открывает (создает) `HasASubKey` с помощью этого родительского маркера. (Если родительский обработчик не открыт, системный реестр может быть медленнее.) Поэтому открытие, `HKEY_CLASSES_ROOT\MyVeryOwnKey` а затем открытие `HasASubKey` с помощью в `MyVeryOwnKey` качестве родительского элемента выполняется быстрее, чем открытие `MyVeryOwnKey` , закрытие `MyVeryOwnKey` и последующее открытие `MyVeryOwnKey\HasASubKey` .

## <a name="see-also"></a>См. также раздел

[Создание скриптов регистратора](../atl/creating-registrar-scripts.md)
