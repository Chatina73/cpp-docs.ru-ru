---
description: 'Дополнительные сведения: _CrtDbgReport, _CrtDbgReportW'
title: _CrtDbgReport, _CrtDbgReportW
ms.date: 11/04/2016
api_name:
- _CrtDbgReport
- _CrtDbgReportW
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
ms.openlocfilehash: 523dc65f846804b13b83bf08b0499b2459fe22ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319808"
---
# <a name="_crtdbgreport-_crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

Создает отчет с сообщением об отладке и отправляет его в три возможных назначения (только отладочная версия).

## <a name="syntax"></a>Синтаксис

```C
int _CrtDbgReport(
   int reportType,
   const char *filename,
   int linenumber,
   const char *moduleName,
   const char *format [,
   argument] ...
);
int _CrtDbgReportW(
   int reportType,
   const wchar_t *filename,
   int linenumber,
   const wchar_t *moduleName,
   const wchar_t *format [,
   argument] ...
);
```

### <a name="parameters"></a>Параметры

*reportType*<br/>
Тип отчета: **_CRT_WARN**, **_CRT_ERROR** и **_CRT_ASSERT**.

*filename*<br/>
Указатель на имя исходного файла, в котором возникло утверждение или отчет, или **значение NULL**.

*LineNumber*<br/>
Номер строки в исходном файле, где возникло утверждение или отчет, или **значение NULL**.

*moduleName*<br/>
Указатель на имя модуля (EXE или DLL), в котором возникло утверждение или отчет.

*format*<br/>
Указатель на строку управления форматом, которая использовалась для создания сообщения для пользователя.

*argument*<br/>
Необязательные аргументы подстановки, используемые в *формате*.

## <a name="return-value"></a>Возвращаемое значение

Для всех назначений отчетов **_CrtDbgReport** и **_CrtDbgReportW** возвращают-1 при возникновении ошибки и 0, если ошибки не обнаружены. Однако если назначение отчета — окно с сообщением об отладке, а пользователь нажимает кнопку **Повторить**, эти функции возвращают значение 1. Если пользователь нажимает кнопку **Прервать** в окне с сообщением об отладке, эти функции немедленно прерываются и не возвращают значение.

Макросы [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) отладки вызывают **_CrtDbgReport** для создания отчетов об отладке. Версии этих макросов для расширенных символов, а также [_ASSERT, _ASSERTE](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) и [_RPTFW](rpt-rptf-rptw-rptfw-macros.md)используют **_CrtDbgReportW** для создания отладочных отчетов. Если **_CrtDbgReport** или **_CrtDbgReportW** возвращает 1, эти макросы запускают отладчик при УСЛОВии, что JIT-отладка включена.

## <a name="remarks"></a>Комментарии

**_CrtDbgReport** и **_CrtDbgReportW** могут отправить отчет об отладке в три разных назначения: файл отчета отладки, монитор отладки (отладчик Visual Studio) или окно сообщения отладки. Две функции настройки, [_CrtSetReportMode](crtsetreportmode.md) и [_CrtSetReportFile](crtsetreportfile.md), используются для задания назначения (назначений) для каждого типа отчета. Эти функции позволяют управлять назначением или назначениями для каждого типа отчета по отдельности. Например, можно указать, что *reportType* **_CRT_WARN** отправляться только в монитор отладки, а **_CRT_ASSERT** *reportType* — в окно сообщения отладки и в определенный пользователем файл отчета.

**_CrtDbgReportW** — это версия **_CrtDbgReport** для расширенных символов. Все выходные данные и параметры строки отображаются как строки расширенных символов; в противном случае — аналогично версии с однобайтовыми символами.

**_CrtDbgReport** и **_CrtDbgReportW** создать пользовательское сообщение для отчета об отладке, подставив аргументы [**n** *] аргументов в* строку *формата* , используя те же правила, которые определены функциями **printf** или **wprintf** . Затем эти функции создают отчет об отладке и определяют назначение или назначения на основе текущих режимов отчета и файла, определенного для *reportType*. При отправке отчета в окно сообщения отладки *имя файла*, **LineNumber** и *ModuleName* включаются в сведения, отображаемые в окне.

В следующей таблице перечислены доступные варианты режима или режимов отчета, а также результаты работы **_CrtDbgReport** и **_CrtDbgReportW**. Эти параметры определяются как битовые флаги в \<crtdbg.h> .

|Режим отчета|Файл отчета|**_CrtDbgReport**, **_CrtDbgReportW** поведение|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|Неприменимо|Записывает сообщение, используя [OutputDebugString](/windows/win32/api/debugapi/nf-debugapi-outputdebugstringw) API Windows.|
|**_CRTDBG_MODE_WNDW**|Неприменимо|Вызывает API Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) для создания окна сообщения, в котором будет отображаться сообщение вместе с кнопками **Прервать**, **Повторить** и **Пропустить**. Если пользователь нажимает кнопку **прервать**, **_CrtDbgReport** или **_CrtDbgReport** немедленно прерывается. Если пользователь нажимает кнопку **Повторить**, функция возвращает значение 1. Если пользователь нажимает кнопку **пропустить**, выполнение продолжится, а **_CrtDbgReport** и **_CrtDbgReportW** возвращают 0. Учтите, что нажатие кнопки **Пропустить** при наличии условия ошибки часто приводит к возникновению "неопределенного поведения".|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Записывает сообщение в пользовательский **обработчик** с помощью Windows [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) API и не проверяет допустимость файла. приложение отвечает за открытие файла отчета и передачу допустимого маркера файла.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Записывает сообщение в **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Записывает сообщение в **stdout**.|

Этот отчет можно отправить в одно, два или три назначения (или ни в одно из назначений). Дополнительные сведения о задании режима (режимов) и файла отчета см. в описании функций [_CrtSetReportMode](crtsetreportmode.md) и [_CrtSetReportFile](crtsetreportfile.md). Дополнительные сведения об использовании макросов отладки и функций отчетов см. в разделе [Макросы для создания отчетов](/visualstudio/debugger/macros-for-reporting).

Если приложению требуется больше гибкости, чем предоставлено **_CrtDbgReport** и **_CrtDbgReportW**, можно написать собственную функцию создания отчетов и подключить ее к механизму создания отчетов библиотеки времени выполнения C с помощью функции [_CrtSetReportHook](crtsetreporthook.md) .

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** и **_CrtDbgReportW** являются расширениями Майкрософт. Дополнительные сведения см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Библиотеки

Только отладочные версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Пример

```C
// crt_crtdbgreport.c
#include <crtdbg.h>

int main(int argc, char *argv[]) {
#ifdef _DEBUG
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);
#endif
}
```

Примеры изменения функций создания отчетов см. в разделе [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>См. также раздел

[Отладочные подпрограммы](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
