---
description: 'Подробнее о: &lt; iostream&gt;'
title: '&lt;iostream&gt;'
ms.date: 09/20/2017
f1_keywords:
- <iostream>
- iostream/std::cerr
- iostream/std::cin
- iostream/std::clog
- iostream/std::cout
- iostream/std::wcerr
- iostream/std::wcin
- iostream/std::wclog
- iostream/std::wcout
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
ms.openlocfilehash: 6bb2bd8f10e459ef91d7f358ce5e1832e9ecdb34
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099681"
---
# `<iostream>`

Объявляет объекты, управляющие чтением из стандартных потоков и записью в них. Это, как правило, единственный заголовок, необходимый для ввода и вывода из программы на C++.

## <a name="syntax"></a>Синтаксис

```cpp
#include <iostream>
```

> [!NOTE]
> `<iostream>`Библиотека использует `#include <ios>` операторы,, `#include <streambuf>` `#include <istream>` и `#include <ostream>` .

## <a name="remarks"></a>Комментарии

Объекты можно разделить на две группы:

- [`cin`](#cin), [`cout`](#cout) , [`cerr`](#cerr) и [`clog`](#clog) являются ориентированными на байты, выполняя обычную передачу данных по времени.

- [`wcin`](#wcin), [`wcout`](#wcout) , [`wcerr`](#wcerr) и [`wclog`](#wclog) являются широкими, переводятся в расширенные символы, которые программа обрабатывает внутренним образом.

После выполнения определенных операций с потоком, например со стандартным входом, нельзя выполнять операции с разными ориентациями в одном потоке. Таким образом, программа не может одновременно взаимодействовать с [`cin`](#cin) и, например [`wcin`](#wcin) .

Все объекты, объявленные в этом заголовке, совместно используют свойство довольно необычная — вы можете предположить, что они созданы до любых статических объектов, которые вы определяете, в записи преобразования, которая включает `<iostream>` . Точно так же можно предположить, что эти объекты не уничтожаются до деструкторов для любых таких статических объектов, которые вы определяете. (Однако выходные потоки сбрасываются во время завершения программы.) Таким образом, можно безопасно считывать или записывать в стандартные потоки перед запуском программы и после завершения программы.

Однако эта гарантия не является универсальной. Статический конструктор может вызвать функцию в другой записи преобразования. Вызываемая функция не может предположить, что объекты, объявленные в этом заголовке, были созданы с учетом неопределенного порядка, в котором единицы преобразования участвуют в статической конструкции. Чтобы использовать эти объекты в таком контексте, сначала необходимо создать объект класса [`ios_base::Init`](../standard-library/ios-base-class.md#init) .

### <a name="global-stream-objects"></a>Глобальные объекты потоков

|Имя|Описание|
|-|-|
|[`cerr`](#cerr)|Указывает глобальный поток `cerr`.|
|[`cin`](#cin)|Указывает глобальный поток `cin`.|
|[`clog`](#clog)|Указывает глобальный поток `clog`.|
|[`cout`](#cout)|Указывает глобальный поток `cout`.|
|[`wcerr`](#wcerr)|Указывает глобальный поток `wcerr`.|
|[`wcin`](#wcin)|Указывает глобальный поток `wcin`.|
|[`wclog`](#wclog)|Указывает глобальный поток `wclog`.|
|[`wcout`](#wcout)|Указывает глобальный поток `wcout`.|

### <a name="cerr"></a><a name="cerr"></a> `cerr`

Объект `cerr` управляет выводом в буфер потока, связанный с объектом `stderr` , объявленный в `<cstdio>` .

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Возвращаемое значение

[`ostream`](../standard-library/ostream-typedefs.md#ostream)Объект.

#### <a name="remarks"></a>Комментарии

Этот объект управляет вставкой без буферизации в стандартный вывод ошибок в виде байтового потока. После создания объекта выражение `cerr.flags & unitbuf` имеет ненулевое значение и `cerr.tie() == &cout` . Дополнительные сведения см. в статьях [`cerr.flags`](../standard-library/ios-base-class.md#flags) и [`unitbuf`](../standard-library/ios-functions.md#unitbuf) .

#### <a name="example"></a>Пример

```cpp
// iostream_cerr.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void TestWide( )
{
   int i = 0;
   wcout << L"Enter a number: ";
   wcin >> i;
   wcerr << L"test for wcerr" << endl;
   wclog << L"test for wclog" << endl;
}

int main( )
{
   int i = 0;
   cout << "Enter a number: ";
   cin >> i;
   cerr << "test for cerr" << endl;
   clog << "test for clog" << endl;
   TestWide( );
}
```

### <a name="cin"></a><a name="cin"></a> `cin`

Указывает глобальный поток `cin`.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Возвращаемое значение

[`istream`](../standard-library/istream-typedefs.md#istream)Объект.

#### <a name="remarks"></a>Комментарии

Объект контролирует получение данных из стандартного ввода, как потока байтов. После создания объекта вызов [`cin.tie`](../standard-library/basic-ios-class.md#tie) возвращает [`&cout`](#cout) .

#### <a name="example"></a>Пример

В этом примере `cin` устанавливает бит сбоя в потоке, если он поступает между нечисловыми символами. Программа очищает бит сбоя и удаляет из потока недопустимый символ, чтобы продолжить.

```cpp
// iostream_cin.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
   int x;
   cout << "enter choice:";
   cin >> x;
   while (x < 1 || x > 4)
   {
      cout << "Invalid choice, try again:";
      cin >> x;
      // not a numeric character, probably
      // clear the failure and pull off the non-numeric character
      if (cin.fail())
      {
         cin.clear();
         char c;
         cin >> c;
      }
   }
}
```

```Output
2
```

### <a name="clog"></a><a name="clog"></a> `clog`

Указывает глобальный поток `clog`.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Возвращаемое значение

[`ostream`](../standard-library/ostream-typedefs.md#ostream)Объект.

#### <a name="remarks"></a>Комментарии

Этот объект управляет вставкой с буферизацей в стандартный вывод ошибок в виде байтового потока.

#### <a name="example"></a>Пример

См. [`cerr`](#cerr) с примером использования `clog`.

### <a name="cout"></a><a name="cout"></a> `cout`

Указывает глобальный поток `cout`.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Возвращаемое значение

[`ostream`](../standard-library/ostream-typedefs.md#ostream)Объект.

#### <a name="remarks"></a>Комментарии

Этот объект управляет вставкой в стандартный вывод в виде байтового потока.

#### <a name="example"></a>Пример

См. [`cerr`](#cerr) с примером использования `cout`.

### <a name="wcerr"></a><a name="wcerr"></a> `wcerr`

Указывает глобальный поток `wcerr`.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Возвращаемое значение

[`wostream`](../standard-library/ostream-typedefs.md#wostream)Объект.

#### <a name="remarks"></a>Комментарии

Этот объект управляет вставкой без буферизации в стандартный вывод ошибок в виде двухбайтового потока. После создания объекта выражение `wcerr.flags & unitbuf` не равно нулю. Дополнительные сведения см. в статьях [`wcerr.flags`](../standard-library/ios-base-class.md#flags) и [`unitbuf`](../standard-library/ios-functions.md#unitbuf) .

#### <a name="example"></a>Пример

См. [`cerr`](#cerr) с примером использования `wcerr`.

### <a name="wcin"></a><a name="wcin"></a> `wcin`

Указывает глобальный поток `wcin`.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Возвращаемое значение

[`wistream`](../standard-library/istream-typedefs.md#wistream)Объект.

#### <a name="remarks"></a>Комментарии

Этот объект управляет извлечением из стандартного ввода в виде двухбайтового потока. После создания объекта вызов [`wcin.tie`](../standard-library/basic-ios-class.md#tie) возвращает [`&wcout`](#wcout) .

#### <a name="example"></a>Пример

См. [`cerr`](#cerr) с примером использования `wcin`.

### <a name="wclog"></a><a name="wclog"></a> `wclog`

Указывает глобальный поток `wclog`.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Возвращаемое значение

[`wostream`](../standard-library/ostream-typedefs.md#wostream)Объект.

#### <a name="remarks"></a>Комментарии

Этот объект управляет вставкой с буферизацей в стандартный вывод ошибок в виде двухбайтового потока.

#### <a name="example"></a>Пример

См. [`cerr`](#cerr) с примером использования `wclog`.

### <a name="wcout"></a><a name="wcout"></a> `wcout`

Указывает глобальный поток `wcout`.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Возвращаемое значение

[`wostream`](../standard-library/ostream-typedefs.md#wostream)Объект.

#### <a name="remarks"></a>Комментарии

Этот объект управляет вставкой в стандартный вывод в качестве широкого потока.

#### <a name="example"></a>Пример

См. [`cerr`](#cerr) с примером использования `wcout`.

Экземпляры `CString`в операторе `wcout` необходимо привести к `const wchar_t*`, как показано в следующем примере.

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Дополнительные сведения см. в разделе [Базовые операции CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Программирование iostream](../standard-library/iostream-programming.md)\
[Соглашения iostream](../standard-library/iostreams-conventions.md)
