---
title: Класс basic_filebuf
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: fcf673d8e6d871a7920150b5f62fd3d62135b52c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500533"
---
# <a name="basicfilebuf-class"></a>Класс basic_filebuf

Описывает буфер потока, который управляет передачей элементов типа *Elem*, признаки символов определяются классом *Tr*, в и из последовательности элементов, сохраненную во внешнем файле.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_filebuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Параметры

*Elem*<br/>
Базовый элемент буфера файла.

*Tr*<br/>
Признаки базового элемента буфера файла (обычно `char_traits`< `Elem`>).

## <a name="remarks"></a>Примечания

Класс шаблона описывает буфер потока, который управляет передачей элементов типа *Elem*, признаки символов которого определяются с помощью класса *Tr*, в последовательность элементов, сохраненную во внешнем файле, и из нее.

> [!NOTE]
> Объекты типа `basic_filebuf` создаются с внутренним буфером типа `char *` вне зависимости от `char_type` , указанного параметром типа *Elem*. Это означает, что строка Юникода (содержащий **wchar_t** символы) преобразуются в строки ANSI (содержащий **char** символов) перед записью на внутренний буфер. Для хранения строк в Юникоде в буфере, создайте новый буфер типа **wchar_t** и задайте его с помощью [basic_streambuf::pubsetbuf](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` метод. Ниже приведен пример, демонстрирующий такие действия.

Объект класса `basic_filebuf`< `Elem`, `Tr`> сохраняет указатель файла, который определяет объект `FILE`, управляющий потоком, связанным с открытым файлом. Он также содержит указатели на два аспекта преобразования файла для использования защищенными функциями-членами [overflow](#overflow) и [underflow](#underflow). Дополнительные сведения см. в разделе [basic_filebuf::open](#open).

## <a name="example"></a>Пример

Следующий пример демонстрирует способ использования объекта типа `basic_filebuf<wchar_t>` для хранения символов Юникода в своем внутреннем буфере, с помощью метода `pubsetbuf()`.

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[basic_filebuf](#basic_filebuf)|Создает объект типа `basic_filebuf`.|

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[char_type](#char_type)|Связывает имя типа с параметром шаблона `Elem`.|
|[int_type](#int_type)|Делает этот тип в области `basic_filebuf` эквивалентным типу с таким же именем в области `Tr`.|
|[off_type](#off_type)|Делает этот тип в области `basic_filebuf` эквивалентным типу с таким же именем в области `Tr`.|
|[pos_type](#pos_type)|Делает этот тип в области `basic_filebuf` эквивалентным типу с таким же именем в области `Tr`.|
|[traits_type](#traits_type)|Связывает имя типа с параметром шаблона `Tr`.|

### <a name="member-functions"></a>Функции-члены

|Функция-член|Описание|
|-|-|
|[close](#close)|Закрывает файл.|
|[is_open](#is_open)|Указывает, открыт ли файл.|
|[open](#open)|Открывает файл.|
|[overflow](#overflow)|Защищенная виртуальная функция, которая может вызываться при вставке нового символа в полный буфер.|
|[pbackfail](#pbackfail)|Защищенная виртуальная функция-член пытается поместить элемент обратно во входной поток, затем делает его текущим (на него указывает следующий указатель).|
|[seekoff](#seekoff)|Защищенная виртуальная функция-член пытается изменить текущие положения управляемых потоков.|
|[seekpos](#seekpos)|Защищенная виртуальная функция-член пытается изменить текущие положения управляемых потоков.|
|[setbuf](#setbuf)|Защищенная виртуальная функция-член выполняет операции, относящиеся непосредственно к каждому производному буферу потока.|
|[Swap](#swap)|Меняет местами содержимое этого `basic_filebuf` и содержимое указанного параметра `basic_filebuf`.|
|[sync](#sync)|Защищенная виртуальная функция пытается синхронизировать управляемые потоки с любыми связанными внешними потоками.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Защищенная виртуальная функция для извлечения текущего элемента из входного потока.|
|[underflow](#underflow)|Защищенная виртуальная функция для извлечения текущего элемента из входного потока.|

## <a name="requirements"></a>Требования

**Заголовок:** \<fstream>

**Пространство имен:** std

## <a name="basic_filebuf"></a>  basic_filebuf::basic_filebuf

Создает объект типа `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Примечания

Первый конструктор сохраняет пустой указатель во всех указателях, управляющих входным и выходным буферами. Он также сохраняет пустой указатель в указателе файла.

Второй конструктор инициализирует объект с содержимым `right`, что рассматривается как ссылка rvalue.

## <a name="char_type"></a>  basic_filebuf::char_type

Связывает имя типа с параметром шаблона `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="close"></a>  basic_filebuf::close

Закрывает файл.

```cpp
basic_filebuf<Elem, Tr> *close();
```

### <a name="return-value"></a>Возвращаемое значение

Функция-член возвращает указатель null, если указатель файла является указателем null.

### <a name="remarks"></a>Примечания

`close` вызовы `fclose`( **fp**). Если эта функция возвращает ненулевое значение, то возвращается пустой указатель. В противном случае возвращается **this**, чтобы указать, что файл был успешно закрыт.

Что касается широкого потока, если после открытия такого потока или с момента последнего вызова `streampos` были произведены какие-либо вставки, то эта функция вызывает [переполнение](#overflow). Она также вставляет любую последовательность, необходимую для восстановления начального состояния преобразования, используя аспект преобразования файла `fac` для вызова `fac.unshift` при необходимости. Каждый элемент `byte` типа **char** созданный таким образом записывается в связанный поток, обозначенный указателем файла `fp` как в результате успешных вызовов формы `fputc`( **байтов**, **fp**). Если вызов `fac.unshift` или любой записи завершается с ошибкой, функция завершается неудачно.

### <a name="example"></a>Пример

В следующем примере предполагается 2 файла в текущем каталоге. basic_filebuf_close.txt (содержимое «тест») и iotest.txt (содержимое «ssss»).

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="int_type"></a>  basic_filebuf::int_type

Делает этот тип в области basic_filebuf эквивалентным типу с тем же именем в `Tr` области.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="is_open"></a>  basic_filebuf::is_open

Указывает, открыт ли файл.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение **true**, если указатель файла не является пустым указателем.

### <a name="example"></a>Пример

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="off_type"></a>  basic_filebuf::off_type

Делает этот тип в области basic_filebuf эквивалентным типу с тем же именем в `Tr` области.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="open"></a>  basic_filebuf::open

Открывает файл.

```cpp
basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Параметры

*_Filename*<br/>
Имя файла, который необходимо открыть.

*_Режим*<br/>
Одно из перечислений в [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Защита, эквивалентно открытия файла по умолчанию *shflag* параметр в [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Возвращаемое значение

Если указатель файла является пустым, эта функция возвращает пустой указатель. В противном случае возвращается **this**.

### <a name="remarks"></a>Примечания

Функция-член открывает файл с именем *имя_файла* путем вызова [fopen](../c-runtime-library/reference/fopen-wfopen.md)( *имя_файла*, **strmode**). `strmode` определяется на основе **режим &**~ ( [ate](../standard-library/ios-base-class.md#openmode) & &#124; [двоичных](../standard-library/ios-base-class.md#openmode)):

- `ios_base::in` становится **«r»** (открыть существующий файл для чтения).

- [ios_base::out](../standard-library/ios-base-class.md#fmtflags) или **ios_base::out &#124; ios_base::trunc** становится **"w"** (очистить существующий файл или создать файл для записи).

- **ios_base::out &#124; app** становится **"a"** (открыть существующий файл для добавления всех записей).

- **ios_base::in &#124; ios_base::out** становится **"r+"** (открыть существующий файл для чтения и записи).

- **ios_base::in &#124; ios_base::out &#124; ios_base::trunc** становится **"w+"** (очистить существующий файл или создать для чтения и записи).

- **ios_base::in &#124; ios_base::out &#124; ios_base::app** становится **"a+"** (открыть существующий файл для чтения и добавления всех записей).

Если **mode & ios_base::binary** имеет ненулевое значение, то функция добавляет `b` для `strmode` для открытия двоичного потока вместо текстового потока. Затем он сохраняет значение, возвращенное `fopen` в указатель файла `fp`. Если **mode & ios_base::ate** не равен нулю и указатель файла не является пустым указателем, то функция вызывает `fseek`( **fp**, 0, `SEEK_END`), чтобы разместить поток в конце файла. Если эта операция размещения завершается неудачно, эта функция вызывает [закрыть](#close)( `fp`) и сохраняет пустой указатель в указатель файла.

Если указатель файла не является пустым указателем, функция определяет аспект преобразования файла `use_facet`< `codecvt`< **Elem**, `char`, **traits_type::**[state_type](../standard-library/char-traits-struct.md#state_type)> >( [getloc](../standard-library/basic-streambuf-class.md#getloc)) для использования функциями [underflow](#underflow) и [overflow](#overflow).

Если указатель файла является пустым, эта функция возвращает пустой указатель. В противном случае возвращается **this**.

### <a name="example"></a>Пример

Пример, в котором используется `open`, см. в разделе [basic_filebuf::close](#close).

## <a name="op_eq"></a>  basic_filebuf::operator=

Назначьте содержимое этого объекта буфера потока. Это назначение перемещения, включающее rvalue, которое не оставляет копию.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Параметры

*right*<br/>
Ссылка rvalue на объект [basic_filebuf](../standard-library/basic-filebuf-class.md).

### <a name="return-value"></a>Возвращаемое значение

Возвращает *this.

### <a name="remarks"></a>Примечания

Оператор-член заменяет содержимое объекта с помощью содержимого *правой*, рассматривается как ссылка rvalue. Дополнительные сведения см. в статье [Декларатор ссылки Rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="overflow"></a>  basic_filebuf::overflow

Вызывается при вставке нового символа в полный буфер.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Параметры

*_Meta*<br/>
Символ для вставки в буфер или `traits_type::eof`.

### <a name="return-value"></a>Возвращаемое значение

Если функции не удалось выполниться успешно, возвращается значение `traits_type::eof`. В противном случае она возвращает **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Примечания

Если *_Meta* **! = traits_type::**[eof](../standard-library/char-traits-struct.md#eof), защищенная функция-член пытается вставить элемент **ch = traits_type::** [ to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*_Meta*) в выходной буфер. Для этого существует несколько способов.

- Если позиция записи доступна, можно сохранить элемент в позиции записи и увеличить следующий указатель для выходного буфера.

- Можно сделать позицию записи доступной, выделяя новое или дополнительное хранилище для выходного буфера.

- Он может преобразовать любые ожидающие выходные данные в выходном буфере, за которым следует `ch`, используя аспект преобразования файла `fac` для вызова `fac.out` при необходимости. Каждый элемент `ch` типа *char* созданный таким образом записывается в связанный поток, обозначенный указателем файла `fp` как в результате успешных вызовов формы `fputc`( **ch**, **fp**). В случае сбоя любого преобразования или записи эта функция завершается неудачно.

## <a name="pbackfail"></a>  basic_filebuf::pbackfail

Пытается поместить элемент обратно во входной поток, затем делает его текущим (на него указывает следующий указатель).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Параметры

*_Meta*<br/>
Символ для вставки в буфер или `traits_type::eof`.

### <a name="return-value"></a>Возвращаемое значение

Если функции не удалось выполниться успешно, возвращается значение `traits_type::eof`. В противном случае она возвращает **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Примечания

Защищенная виртуальная функция-член помещает элемент обратно во входной буфер, а затем делает его текущим (на него указывает следующий указатель). Если _ *Meta* **== traits_type::**[eof](../standard-library/char-traits-struct.md#eof), то элемент, который необходимо передать обратно, фактически уже находится в потоке перед текущим элементом. В противном случае этот элемент заменяется **ch = traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*). Функция может передать элемент обратно различными способами.

- Если позиция возврата доступна и сохраненный там элемент оценивается как равный `ch`, функция может уменьшить следующий указатель для входного буфера.

- Если функция может сделать `putback` позицию доступен, он может сделать это, задайте следующий указатель, чтобы они указывали на позицию и сохранить `ch` в этой позиции.

- Если функция может передать элемент обратно во входной поток, это можно сделать, например, путем вызова `ungetc` для элемента типа **char**.

## <a name="pos_type"></a>  basic_filebuf::pos_type

Делает этот тип в области basic_filebuf эквивалентным типу с тем же именем в `Tr` области.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_filebuf::seekoff

Пытается изменить текущие положения для управляемых потоков.

```cpp
virtual pos_type seekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Параметры

*_Off*<br/>
Позиция для поиска относительно *_Way*.

*_Way*<br/>
Начальная точка для операций смещения. Возможные значения см. в разделе [seekdir](../standard-library/ios-base-class.md#seekdir).

*_Which*<br/>
Задает режим для положения указателя. По умолчанию разрешается изменять позиции чтения и записи.

### <a name="return-value"></a>Возвращаемое значение

Возвращает новую позицию или недопустимую позицию потока.

### <a name="remarks"></a>Примечания

Защищенная виртуальная функция-член пытается изменить текущие положения для управляемых потоков. Для объекта класса [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> позиция потока может быть представлена объектом типа `fpos_t`, который хранит смещение и все сведения о состоянии, необходимые для анализа широкого потока. Нулевое смещение обозначает первый элемент в потоке. (Объект типа [pos_type](../standard-library/basic-streambuf-class.md#pos_type) хранит по крайней мере объект `fpos_t`.)

Для файла, открытого для чтения и записи, входной и выходной потоки располагаются вместе. Для переключения между режимами вставки и извлечения необходимо вызвать [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) или [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Вызовы `pubseekoff` (и соответственно `seekoff`) имеют различные ограничения для [текстовых потоков](../c-runtime-library/text-and-binary-streams.md), [двоичных потоков](../c-runtime-library/text-and-binary-streams.md) и [широких потоков](../c-runtime-library/byte-and-wide-streams.md).

Если указатель файла `fp` является пустым указателем, эта функция завершается неудачно. В противном случае она пытается изменить позицию потока путем вызова `fseek`( **fp**, `_Off`, `_Way`). Если эта функция выполняется успешно и полученную позицию `fposn` можно определить с помощью вызова `fgetpos`( **fp**, **& fposn**), функция выполняется успешно. Если функция выполняется успешно, он возвращает значение типа `pos_type` содержащий `fposn`. В противном случае она возвращает недопустимую позицию потока.

## <a name="seekpos"></a>  basic_filebuf::seekpos

Пытается изменить текущие положения для управляемых потоков.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Параметры

*_Sp*<br/>
Позиция для поиска.

*_Which*<br/>
Задает режим для положения указателя. По умолчанию разрешается изменять позиции чтения и записи.

### <a name="return-value"></a>Возвращаемое значение

Если указатель файла `fp` является пустым указателем, эта функция завершается неудачно. В противном случае она пытается изменить позицию потока путем вызова `fsetpos`( **fp**, **& fposn**), где `fposn` — `fpos_t` объект, хранящийся в `pos`. Если эта функция выполняется успешно, функция возвращает `pos`. В противном случае она возвращает недопустимую позицию потока. Чтобы определить, является ли позиция потока недопустимой, сравните возвращаемое значение с `pos_type(off_type(-1))`.

### <a name="remarks"></a>Примечания

Защищенная виртуальная функция-член пытается изменить текущие положения для управляемых потоков. Для объекта класса [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**> позиция потока может быть представлена объектом типа `fpos_t`, который хранит смещение и все сведения о состоянии, необходимые для анализа широкого потока. Нулевое смещение обозначает первый элемент в потоке. (Объект типа `pos_type` хранит по крайней мере объект `fpos_t`.)

Для файла, открытого для чтения и записи, входной и выходной потоки располагаются вместе. Для переключения между режимами вставки и извлечения необходимо вызвать [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) или [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Вызовы `pubseekoff` (и соответственно `seekoff`) имеют различные ограничения для текстовых, двоичных и широких потоков.

Что касается широкого потока, если после открытия такого потока или с момента последнего вызова `streampos` были произведены какие-либо вставки, то эта функция вызывает [переполнение](#overflow). Она также вставляет любую последовательность, необходимую для восстановления начального состояния преобразования, используя аспект преобразования файла `fac` для вызова **fac** `.unshift` при необходимости. Каждый элемент `byte` типа **char** созданный таким образом записывается в связанный поток, обозначенный указателем файла `fp` как в результате успешных вызовов формы `fputc`( **байтов**, **fp**). Если вызов `fac.unshift` или любой записи завершается с ошибкой, функция завершается неудачно.

## <a name="setbuf"></a>  basic_filebuf::setbuf

Выполняет операции, относящиеся непосредственно к каждому производному буферу потока.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Параметры

*_Buffer*<br/>
Указатель на буфер.

*count*<br/>
Размер буфера.

### <a name="return-value"></a>Возвращаемое значение

Эта защищенная функция-член возвращает нуль, если указатель файла `fp` является пустым указателем.

### <a name="remarks"></a>Примечания

`setbuf` вызывает `setvbuf`( **fp**, ( `char` \*) `_Buffer`, `_IOFBF`, `count` \* `sizeof` ( **Elem**) ), чтобы предложить массив элементов `count`, начинающийся в _ *Buffer*, в качестве буфера для потока. Если эта функция возвращает ненулевое значение, то возвращается пустой указатель. В противном случае она возвращает **this**, чтобы сообщить об успешном завершении.

## <a name="swap"></a>  basic_filebuf::swap

Меняет местами содержимое этого объекта `basic_filebuf` с содержимым указанного объекта `basic_filebuf`.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Параметры

*right*<br/>
Ссылка `lvalue` на другой объект `basic_filebuf`.

## <a name="sync"></a>  basic_filebuf::sync

Пытается синхронизировать управляемые потоки с любыми связанными внешними потоками.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает нуль, если указатель файла `fp` является пустым указателем. В противном случае нуль возвращается только тогда, когда вызовы [overflow](#overflow) и `fflush`( **fp**) успешно очистили все ожидающие выходные данные в потоке.

## <a name="traits_type"></a>  basic_filebuf::traits_type

Связывает имя типа с параметром шаблона `Tr`.

```cpp
typedef Tr traits_type;
```

## <a name="underflow"></a>  basic_filebuf::underflow

Извлекает текущий элемент из входного потока.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Возвращаемое значение

Если функция не может выполниться успешно, она возвращает **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). В противном случае возвращается `ch`, преобразованный, как описано в разделе "Примечания".

### <a name="remarks"></a>Примечания

Защищенная функция-член пытается извлечь текущий элемент `ch` из входного потока и возвратить элемент как **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`ch`). Для этого существует несколько способов.

- Если позиция чтения доступна, функция принимает `ch` как элемента, хранящегося в этой позиции чтения и перемещает следующий указатель для входного буфера.

- Оно может считывать один или несколько элементов типа **char**, как в результате успешных вызовов формы `fgetc`(**fp**) и преобразовывать их в элемент **ch** типа `Elem`, используя аспект преобразования файла fac для вызова `fac.in` при необходимости. В случае сбоя какого-либо преобразования или операции чтения эта функция завершается неудачно.

## <a name="see-also"></a>См. также

[\<fstream>](../standard-library/fstream.md)<br/>
[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Программирование iostream](../standard-library/iostream-programming.md)<br/>
[Соглашения iostreams](../standard-library/iostreams-conventions.md)<br/>
