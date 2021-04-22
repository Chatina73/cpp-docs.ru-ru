---
description: 'Дополнительные сведения: set_unexpected (CRT)'
title: set_unexpected (CRT)
ms.date: 1/14/2021
api_name:
- set_unexpected
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: f5922cb5fb6b06cc809818fcfd324b6fc825c5a6
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577110"
---
# <a name="set_unexpected-crt"></a>`set_unexpected` Электрон

Устанавливает собственную функцию завершения, которая вызывается **`unexpected`** .

## <a name="syntax"></a>Синтаксис

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Параметры

*`unexpFunction`*\
Указатель на функцию, которую вы пишете для замены **`unexpected`** функции.

## <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на предыдущую функцию завершения, зарегистрированную в, **`_set_unexpected`** чтобы предыдущую функцию можно было восстановить позже. Если Предыдущая функция не задана, то возвращаемое значение может использоваться для восстановления поведения по умолчанию; Это значение может быть равно **`NULL`** .

## <a name="remarks"></a>Замечания

**`set_unexpected`** Функция устанавливает *унекспфунктион* в качестве функции, вызываемой **`unexpected`** . **`unexpected`** не используется в текущей реализации обработки исключений C++. **`unexpected_function`** Тип определяется в EH. H в качестве указателя на определяемую пользователем непредвиденную функцию, *унекспфунктион* , возвращающую **`void`** . Пользовательская функция *унекспфунктион* не должна возвращаться к ее вызывающему объекту.

```cpp
typedef void ( *unexpected_function )( );
```

По умолчанию **`unexpected`** вызывает **`terminate`** . Это поведение по умолчанию можно изменить, написав собственную функцию завершения и вызвав ее **`set_unexpected`** с именем функции в качестве аргумента. **`unexpected`** вызывает последнюю функцию, заданную в качестве аргумента для **`set_unexpected`** .

В отличие от пользовательской функции завершения, установленной с помощью вызова **`set_terminate`** , исключение может быть вызвано из **`unexpFunction`** .

В многопоточной среде непредвиденные функции поддерживаются отдельно для каждого потока. Каждый новый поток требует установки собственной непредвиденной функции. Таким образом, каждый поток отвечает за собственную обработку непредвиденных функций.

В текущей реализации Майкрософт обработки исключений C++ **`unexpected`** вызовы по **`terminate`** умолчанию и никогда не вызываются библиотекой времени выполнения, обрабатывающей исключения. Нет особых преимуществ для вызова, **`unexpected`** а не **`terminate`** .

**`set_unexpected`** Для всех динамически связанных библиотек DLL или exe существует один обработчик, даже если вы вызываете **`set_unexpected`** обработчик, он может быть заменен другим или заменять обработчик, заданный другим DLL или exe.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**`set_unexpected`**|`<eh.h>`|

Дополнительные сведения о совместимости см. в разделе [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также раздел

[Подпрограммы обработки исключений](../../c-runtime-library/exception-handling-routines.md)\
[`abort`](abort.md)\
[`_get_unexpected`](get-unexpected.md)\
[`set_terminate`](set-terminate-crt.md)\
[`terminate`](terminate-crt.md)\
[`unexpected`](unexpected-crt.md)\
