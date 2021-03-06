---
description: 'Дополнительные сведения: _CrtSetAllocHook'
title: _CrtSetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: a60024eff510f457cfc16f4afa3035efef37cca4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319668"
---
# <a name="_crtsetallochook"></a>_CrtSetAllocHook

Устанавливает определяемую клиентом функцию выделения памяти путем ее прикрепления к отладочному процессу выделения памяти среды выполнения языка C (только отладочная версия).

## <a name="syntax"></a>Синтаксис

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>Параметры

*аллочук*<br/>
Новая, определенная клиентом функция выделения памяти, которую требуется прикрепить к отладочному процессу выделения памяти среды выполнения C.

## <a name="return-value"></a>Возвращаемое значение

Возвращает ранее определенную функцию-обработчик выделения или **значение NULL** , если *Аллочук* имеет **значение NULL**.

## <a name="remarks"></a>Комментарии

**_CrtSetAllocHook** позволяет приложению подключать собственную функцию выделения памяти в отладочную библиотеку времени выполнения C. В результате каждый вызов функции отладочного выделения памяти для выделения, перераспределения или освобождения блока памяти запускает вызов функции-обработчика приложения. **_CrtSetAllocHook** предоставляет приложению простой способ для тестирования того, как приложение обрабатывает нехватку памяти, возможность исследовать закономерности выделения ресурсов и возможность регистрировать сведения о выделении для последующего анализа. Если [_DEBUG](../../c-runtime-library/debug.md) не определено, вызовы **_CrtSetAllocHook** удаляются во время предварительной обработки.

Функция **_CrtSetAllocHook** устанавливает новую определяемую клиентом функцию выделения, указанную в *аллочук* , и возвращает ранее определенную функцию-обработчик. В следующем примере показано, как должен объявляться прототип определяемого клиентом обработчика выделения памяти:

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

Аргумент **аллоктипе** задает тип операции выделения (**_HOOK_ALLOC**, **_HOOK_REALLOC** и **_HOOK_FREE**), который инициировал вызов функции-ловушки выделения. Если тип выделения триггера — **_HOOK_FREE**, то *UserData* — это указатель на раздел пользовательских данных блока памяти, который должен быть освобожден. Однако если тип выделения триггера — **_HOOK_ALLOC** или **_HOOK_REALLOC**, то *UserData* имеет **значение NULL** , так как блок памяти еще не был выделен.

*Размер* определяет размер блока памяти в байтах, *блокктипе* указывает тип блока памяти, *рекуестнумбер* — номер порядка выделения объектов в блоке памяти, а если он доступен, *filename* и **LineNumber** указывают имя исходного файла и номер строки, где была инициирована операция выделения.

После обработки функция-обработчик должна возвращать логическое значение, которое указывает главному процессу выделения памяти среды выполнения C, как продолжить выполнение. Когда функции-обработчику требуется, чтобы основной процесс выделения продолжался, как если бы функция-обработчик никогда не вызывалась, функция-обработчик должна вернуть **значение true**. Это приводит к запуску выполнения исходной операции выделения памяти. С помощью этой реализации функция-обработчик может получать и сохранять данные о выделении памяти для дальнейшего анализа, не препятствуя текущей операции выделения памяти и не изменяя состояние отладочной кучи.

Когда функции-обработчику требуется, чтобы основной процесс выделения продолжался, как если бы была вызвана операция выделения памяти, вызвавшая сбой, функция-обработчик должна вернуть **значение false**. С помощью этой реализации функция-обработчик может имитировать широкий спектр состояний памяти и состояний отладочной кучи для проверки обработки приложением каждой ситуации.

Чтобы очистить функцию-обработчик, передайте **значение NULL** в **_CrtSetAllocHook**.

Дополнительные сведения о том, как **_CrtSetAllocHook** можно использовать с другими функциями управления памятью, а также о написании собственных определяемых клиентом функций-обработчиков см. в разделе [запись отладочной функции-ловушки](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_CrtSetAllocHook** не поддерживается в **/clr: pure**. Параметры компилятора **/clr: pure** и **/clr: Сейф** являются устаревшими в Visual Studio 2015 и удаляются в Visual Studio 2017.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

Дополнительные сведения о совместимости см. в разделе [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Библиотеки

Только отладочные версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Пример

Пример использования **_CrtSetAllocHook** см. в разделе [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>См. также раздел

[Отладочные подпрограммы](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
