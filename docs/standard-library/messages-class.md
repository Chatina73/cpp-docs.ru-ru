---
title: Класс messages
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: 7a024a8cad8c536b25127d033468874de5ebd8af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383585"
---
# <a name="messages-class"></a>Класс messages

Класс шаблона, описывающий объект, который можно использовать в качестве аспекта языкового стандарта для извлечения локализованных сообщений из каталога интернационализированных сообщений для заданного языкового стандарта.

В настоящее время при использовании данного класса сообщений сообщения не создаются.

## <a name="syntax"></a>Синтаксис

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Параметры

*CharType*<br/>
Тип, используемый внутри программы для кодирования символов в языковом стандарте.

## <a name="remarks"></a>Примечания

Как и в случае любого другого аспекта языкового стандарта, начальное сохраненное значение статического идентификатора объекта равно нулю. Первая попытка получить доступ к сохраненному значению сохранит уникальное положительное значение в **id.**

По сути, этот аспект открывает каталог сообщений, заданных в базовом классе messages_base, извлекает необходимую информацию и закрывает каталог.

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[messages](#messages)|Функция конструктора аспекта сообщения.|

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[char_type](#char_type)|Тип символа, используемого для отображения сообщений.|
|[string_type](#string_type)|Тип, описывающий строку типа `basic_string`, содержащую символы типа `CharType`.|

### <a name="member-functions"></a>Функции-члены

|Функция-член|Описание|
|-|-|
|[close](#close)|Закрывает каталог сообщений.|
|[do_close](#do_close)|Виртуальная функция, вызываемая для закрытия каталога сообщений.|
|[do_get](#do_get)|Виртуальная функция, вызываемая для извлечения каталога сообщений.|
|[do_open](#do_open)|Виртуальная функция, вызываемая для открытия каталога сообщений.|
|[get](#get)|Извлекает каталог сообщений.|
|[open](#open)|Открывает каталог сообщений.|

## <a name="requirements"></a>Требования

**Заголовок:** \<locale>

**Пространство имен:** std

## <a name="char_type"></a>  messages::char_type

Тип символа, используемого для отображения сообщений.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Примечания

Тип является синонимом для параметра-шаблона **CharType**.

## <a name="close"></a>  messages::close

Закрывает каталог сообщений.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Параметры

*_Catval*<br/>
Каталог для закрытия.

### <a name="remarks"></a>Примечания

Функция-член вызывает [do_close](#do_close)(_ *Catval*).

## <a name="do_close"></a>  messages::do_close

Виртуальная функция, вызываемая для закрытия каталога сообщений.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Параметры

*_Catval*<br/>
Каталог для закрытия.

### <a name="remarks"></a>Примечания

Защищенная функция-член закрывает каталог сообщений *_Catval*, который должен быть открыт с предыдущими вызовами [do_open](#do_open).

Значение *_Catval* должно быть получено из ранее открытого каталога, который не закрыт.

### <a name="example"></a>Пример

См. пример для [close](#close), в котором вызывается `do_close`.

## <a name="do_get"></a>  messages::do_get

Виртуальная функция, вызываемая для извлечения каталога сообщений.

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Параметры

*_Catval*<br/>
Значение идентификации, указывающее каталог сообщений для поиска.

*_Set*<br/>
Первый идентификатор, использованный для поиска сообщения в каталоге сообщений.

*_Message*<br/>
Второй идентификатор, использованный для поиска сообщения в каталоге сообщений.

*_Dfault*<br/>
Строка, которая будет возвращаться при сбое.

### <a name="return-value"></a>Возвращаемое значение

Он возвращает копию объекта *_Dfault* в случае сбоя. В противном случае он возвращает копию указанной последовательности сообщений.

### <a name="remarks"></a>Примечания

Защищенная функция-член пытается получить последовательность сообщений из каталога сообщений *_Catval*. Может быть использование *_задание*, *_Message*, и *_Dfault* таким образом.

### <a name="example"></a>Пример

См. пример для [get](#get), в котором вызывается `do_get`.

## <a name="do_open"></a>  messages::do_open

Виртуальная функция, вызываемая для открытия каталога сообщений.

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Параметры

*_Catname*<br/>
Имя каталога для поиска.

*_Loc*<br/>
Языковой стандарт, который ищется в каталоге.

### <a name="return-value"></a>Возвращаемое значение

Он возвращает значение, которое при сбое получает значение меньше нуля. В противном случае возвращаемое значение может использоваться в качестве первого аргумента в последующем вызове [get](#get).

### <a name="remarks"></a>Примечания

Защищенная функция-член пытается открыть каталог сообщений с именем *_Catname*. Может быть использовать языковой стандарт *_Loc* таким образом

Возвращаемое значение следует использовать как аргумент для последующего вызова [close](#close).

### <a name="example"></a>Пример

См. пример для [open](#open), в котором вызывается `do_open`.

## <a name="get"></a>  messages::get

Извлекает каталог сообщений.

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Параметры

*_Catval*<br/>
Значение идентификации, указывающее каталог сообщений для поиска.

*_Set*<br/>
Первый идентификатор, использованный для поиска сообщения в каталоге сообщений.

*_Message*<br/>
Второй идентификатор, использованный для поиска сообщения в каталоге сообщений.

*_Dfault*<br/>
Строка, которая будет возвращаться при сбое.

### <a name="return-value"></a>Возвращаемое значение

Он возвращает копию объекта *_Dfault* в случае сбоя. В противном случае он возвращает копию указанной последовательности сообщений.

### <a name="remarks"></a>Примечания

Функция-член возвращает [do_get](#do_get)(`_Catval`, `_Set`, `_Message`, `_Dfault`).

## <a name="messages"></a>  messages::messages

Функция конструктора аспекта сообщения.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Параметры

*_Refs*<br/>
Целочисленное значение, используемое для указания типа управления памятью для объекта.

*_Locname*<br/>
Имя языкового стандарта.

### <a name="remarks"></a>Примечания

Возможные значения *_Refs* параметра и их важность:

- 0: Время существования объекта управляется языковыми стандартами, которые его содержат.

- 1: Время существования объекта должно управляться вручную.

- \> 1: Эти значения не определены.

Прямые примеры привести нельзя, так как деструктор защищен.

Конструктор инициализирует свой базовый объект с **locale::**[facet](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="open"></a>  messages::open

Открывает каталог сообщений.

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Параметры

*_Catname*<br/>
Имя каталога для поиска.

*_Loc*<br/>
Языковой стандарт, который ищется в каталоге.

### <a name="return-value"></a>Возвращаемое значение

Он возвращает значение, которое при сбое получает значение меньше нуля. В противном случае возвращаемое значение может использоваться в качестве первого аргумента в последующем вызове [get](#get).

### <a name="remarks"></a>Примечания

Функция-член возвращает [do_open](#do_open)(`_Catname`, `_Loc`).

## <a name="string_type"></a>  messages::string_type

Тип, описывающий строку типа `basic_string`, содержащую символы типа `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Примечания

Тип описывает специализацию класса-шаблона [basic_string](../standard-library/basic-string-class.md), объекты которого могут хранить копии последовательностей сообщений.

## <a name="see-also"></a>См. также

[\<locale>](../standard-library/locale.md)<br/>
[Класс messages_base](../standard-library/messages-base-class.md)<br/>
[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
