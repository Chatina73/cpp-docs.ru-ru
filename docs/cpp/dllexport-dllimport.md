---
title: dllexport, dllimport
ms.date: 11/04/2016
f1_keywords:
- dllimport_cpp
- dllexport_cpp
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
ms.openlocfilehash: 2ae284172828ed63b6499475df108c28aecb32ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398931"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport

**Блок, относящийся только к системам Microsoft**

**Dllexport** и **dllimport** атрибуты класса хранения это расширения Майкрософт для языков C и C++. Их можно использовать для экспорта функций, данных и объектов в библиотеку DLL или импорта из такой библиотеки.

## <a name="syntax"></a>Синтаксис

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>Примечания

Эти атрибуты явно определяют интерфейс DLL для ее клиента, который может быть исполняемым файлом или другой библиотекой DLL. Объявление функций как **dllexport** обходиться без файла определения модуля (DEF), по крайней мере в отношении спецификации экспортированных функций. **Dllexport** атрибут заменяет **__export** ключевое слово.

Если класс отмечен как declspec(dllexport), все специализации шаблонов класса в иерархии классов неявно отмечаются как declspec (dllexport). Это означает, что шаблоны класса создаются явно и члены класса должны быть определены.

**dllexport** функции предоставляет функцию с ее декорированным именем. Для функций C++ сюда входит видоизменение имени. Для функций C или функций, объявленных с модификатором `extern "C"`, сюда входит зависящее от платформы декорирование, основанное на соглашении о вызовах. Сведения о декорировании в коде C/C++, см. в разделе [декорированные имена](../build/reference/decorated-names.md). К экспортированным функциям C и функциям `extern "C"` C++, использующим соглашение о вызовах `__cdecl`, не применяется декорирование имен.

Чтобы экспортировать недекорированное имя, можно установить связь с помощью файла определения модуля (DEF-файла), определяющего недекорированное имя в разделе EXPORTS. Дополнительные сведения см. в разделе [ЭКСПОРТОВ](../build/reference/exports.md). Другой способ экспорта недекорированного имени — использование `#pragma comment(linker, "/export:alias=decorated_name")` директив в исходном коде.

При объявлении **dllexport** или **dllimport**, необходимо использовать [расширенный синтаксис атрибутов](../cpp/declspec.md) и **__declspec** ключевое слово.

## <a name="example"></a>Пример

```cpp
// Example of the dllimport and dllexport class attributes
__declspec( dllimport ) int i;
__declspec( dllexport ) void func();
```

Кроме того, чтобы сделать код более понятным, можно использовать макроопределения:

```cpp
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllImport int j;
DllExport int n;
```

Дополнительные сведения:

- [Определения и объявления](../cpp/definitions-and-declarations-cpp.md)

- [Определение встроенных функций C++ с помощью dllexport и dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [Общие правила и ограничения](../cpp/general-rules-and-limitations.md)

- [Использование dllimport и dllexport в классах C++](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[__declspec](../cpp/declspec.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)