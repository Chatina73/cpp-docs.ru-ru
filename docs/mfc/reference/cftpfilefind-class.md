---
title: Класс CFtpFileFind
ms.date: 11/04/2016
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: 885005cc04da94ff4339a5f538956b1bfc96b4c3
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503679"
---
# <a name="cftpfilefind-class"></a>Класс CFtpFileFind

Помогает в поиске файлов Интернета на FTP-серверах.

## <a name="syntax"></a>Синтаксис

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Создает объект `CFtpFileFind`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|Находит файл на FTP-сервере.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Продолжает поиск файла из предыдущего вызова [FindFile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Получает URL-адрес, включая путь файла.|

## <a name="remarks"></a>Примечания

`CFtpFileFind` включает в себя функции-члены, начать поиск, укажите расположение файла и возвращать URL-адрес или другие описательные сведения о файле.

Другие классы MFC, предназначенные для Интернета и локальный файл, в котором выполняется поиск включают в себя [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) и [CFileFind](../../mfc/reference/cfilefind-class.md). Вместе с `CFtpFileFind`, эти классы предоставляют простой механизм для клиента, чтобы найти определенные файлы, независимо от сервера протокола или тип файла (локальном компьютере или удаленном сервере). Обратите внимание на то, что отсутствует класс MFC для поиска по HTTP-серверами, так как HTTP не поддерживает прямое файлами, необходимые для поиска.

Дополнительные сведения об использовании `CFtpFileFind` и другие классы WinInet, см. в статье [Internet программирование с использованием WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Пример

Следующий код демонстрирует, как перечислить все файлы в текущем каталоге FTP-сервера.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Требования

**Заголовок:** afxinet.h

##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind

Эта функция-член вызывается для создания `CFtpFileFind` объекта.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Параметры

*pConnection*<br/>
Указатель на объект `CFtpConnection` . FTP-подключение можно получить, вызвав [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
Идентификатор контекста для `CFtpFileFind` объекта. См. в разделе **"Примечания"** Дополнительные сведения об этом параметре.

### <a name="remarks"></a>Примечания

Значение по умолчанию для *dwContext* отправленные MFC для `CFtpFileFind` объекта из [CInternetSession](../../mfc/reference/cinternetsession-class.md) объекта, который создан `CFtpFileFind` объекта. Можно переопределить значение по умолчанию присвоено значение по своему выбору, идентификатор контекста. Идентификатор контекста возвращается [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) для предоставления состояния в объекте, с которой он определен. См. в статье [Internet первые шаги: WinInet](../../mfc/wininet-basics.md) Дополнительные сведения о идентификатора контекста.

### <a name="example"></a>Пример

  См. пример в обзоре класса ранее в этом разделе.

##  <a name="findfile"></a>  CFtpFileFind::FindFile

Вызов этой функции-члена для поиска файла FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Параметры

*pstrName*<br/>
Указатель на строку, содержащую имя файла для поиска. Если значение равно NULL, вызов будет выполнять поиск с подстановочными символами (*).

*dwFlags*<br/>
Флаги, описывающие способ обработки этого сеанса. Эти флаги можно объединить с помощью битового оператора или (&#124;) и выглядят следующим образом:

- INTERNET_FLAG_RELOAD получение данных из сети, даже если он кэшируется локально. Это флаг по умолчанию.

- INTERNET_FLAG_DONT_CACHE не кэшировать данные, локально или в всех шлюзов.

- INTERNET_FLAG_RAW_DATA переопределить значение по умолчанию для возвращения необработанных данных ( [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) структуры, для FTP-сервера).

- Защищает INTERNET_FLAG_SECURE транзакции по сети с помощью протокола SSL или использованию PCT. Этот флаг применим только для HTTP-запросов.

- INTERNET_FLAG_EXISTING_CONNECT Если это возможно, повторно использовать существующие подключения к серверу для новых `FindFile` запросов вместо создания нового сеанса для каждого запроса.

### <a name="return-value"></a>Возвращаемое значение

Имеет ненулевое значение в случае успешного выполнения, иначе — 0. Чтобы получить расширенные сведения об ошибке, вызовите функцию Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Примечания

После вызова метода `FindFile` для получения первого файла FTP, можно вызвать [FindNextFile](#findnextfile) для извлечения последующих файлов FTP.

### <a name="example"></a>Пример

  См. в разделе приведенного выше в этом разделе.

##  <a name="findnextfile"></a>  CFtpFileFind::FindNextFile

Вызовите эту функцию-член для продолжения поиска файла начался вызовом [FindFile](#findfile) функция-член.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, при наличии нескольких файлов; нуль, если найден файл является последним в каталоге или если возникает ошибка. Чтобы получить расширенные сведения об ошибке, вызовите функцию Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror). Если файл найден последнего файла в каталоге, или если соответствующие файлы можно найти, `GetLastError` функция возвращает ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Примечания

Эту функцию необходимо вызывать по крайней мере один раз перед вызовом любой функции атрибутов (см. в разделе [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile` Создает оболочку для функции Win32 [FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea).

### <a name="example"></a>Пример

  См. пример выше в этом разделе.

##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL

Эта функция члена для получения URL-адрес указанного файла.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Возвращаемое значение

Путь и имя файла из универсальный указатель ресурса (URL).

### <a name="remarks"></a>Примечания

`GetFileURL` похож на функцию-член [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), за исключением того, что она возвращает URL-адрес в форме `ftp://moose/dir/file.txt`.

## <a name="see-also"></a>См. также

[Класс CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Класс CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Класс CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Класс CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Класс CHttpFile](../../mfc/reference/chttpfile-class.md)
