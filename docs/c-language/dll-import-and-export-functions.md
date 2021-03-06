---
description: 'Подробнее о следующем: Функции импорта и экспорта DLL'
title: Функции импорта и экспорта DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
ms.openlocfilehash: 9f734d4415b473717ad8cd7c94213f1beaff9dc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213934"
---
# <a name="dll-import-and-export-functions"></a>Функции импорта и экспорта DLL

**Блок, относящийся только к системам Microsoft**

Наиболее полную и актуальную информацию по этой теме можно найти в статье [dllexport, dllimport](../cpp/dllexport-dllimport.md).

Модификаторы класса хранения **`dllimport`** и `dllexport` — это расширения языка С для систем Microsoft. Эти модификаторы явным образом определяют интерфейс библиотеки DLL к ее клиенту (исполняемому файлу или другой библиотеке DLL). Объявление функции в качестве `dllexport` позволяет обойтись без файла определения модуля (.DEF). Кроме того, модификаторы **`dllimport`** и `dllexport` можно использовать с данными и объектами.

Модификаторы класса хранения **`dllimport`** и `dllexport` должны использоваться с ключевым словом расширенного синтаксиса атрибутов **`__declspec`** , как показано в следующем примере:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllExport int j;
DllExport int n;
```

Дополнительные сведения о синтаксисе расширенных модификаторов класса хранения см. в статье [C Extended Storage-Class Attributes](../c-language/c-extended-storage-class-attributes.md) (Расширенные атрибуты классов хранения C).

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Определения функций в C](../c-language/c-function-definitions.md)
