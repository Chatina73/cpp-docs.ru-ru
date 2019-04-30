---
title: includelib (атрибут COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 57f039eeae527dd03884b12e7d9eb424d87f597f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409360"
---
# <a name="includelib-c"></a>includelib (C++)

В результате файл IDL или .h, должны быть включены в созданного IDL-файла.

## <a name="syntax"></a>Синтаксис

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Параметры

*Name.IDL*<br/>
Имя IDL-файла, который будет частью созданного IDL-файла.

## <a name="remarks"></a>Примечания

**Includelib** атрибут C++ вызывает файл IDL или .h, должны быть включены в созданного IDL-файла, после `importlib` инструкции.

## <a name="example"></a>Пример

В CPP-файле отображается следующий код:

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Требования

### <a name="attribute-context"></a>Контекст атрибута

|||
|-|-|
|**Применение**|В любом месте|
|**Повторяемый**|Да|
|**Обязательные атрибуты**|Нет|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также

[Атрибуты IDL](idl-attributes.md)<br/>
[Изолированные атрибуты](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)