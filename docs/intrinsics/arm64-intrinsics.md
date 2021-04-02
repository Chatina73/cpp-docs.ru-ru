---
title: Встроенные объекты ARM64
description: Список ссылок встроенных функций ARM64, поддерживаемых компилятором Microsoft C++ в Visual Studio.
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
helpviewer_keywords:
- __break ARM64 intrinsic
- __addx18byte ARM64 intrinsic
- __addx18word ARM64 intrinsic
- __addx18dword ARM64 intrinsic
- __addx18qword ARM64 intrinsic
- __cas8 ARM64 intrinsic
- __cas16 ARM64 intrinsic
- __cas32 ARM64 intrinsic
- __cas64 ARM64 intrinsic
- __casa8 ARM64 intrinsic
- __casa16 ARM64 intrinsic
- __casa32 ARM64 intrinsic
- __casa64 ARM64 intrinsic
- __casl8 ARM64 intrinsic
- __casl16 ARM64 intrinsic
- __casl32 ARM64 intrinsic
- __casl64 ARM64 intrinsic
- __casal8 ARM64 intrinsic
- __casal16 ARM64 intrinsic
- __casal32 ARM64 intrinsic
- __casal64 ARM64 intrinsic
- __crc32b ARM64 intrinsic
- __crc32h ARM64 intrinsic
- __crc32w ARM64 intrinsic
- __crc32d ARM64 intrinsic
- __crc32cb ARM64 intrinsic
- __crc32ch ARM64 intrinsic
- __crc32cw ARM64 intrinsic
- __crc32cd ARM64 intrinsic
- __getReg ARM64 intrinsic
- __getRegFp ARM64 intrinsic
- __getCallerReg ARM64 intrinsic
- __getCallerRegFp ARM64 intrinsic
- __hlt ARM64 intrinsic
- __incx18byte ARM64 intrinsic
- __incx18word ARM64 intrinsic
- __incx18dword ARM64 intrinsic
- __incx18qword ARM64 intrinsic
- __ldar8 ARM64 intrinsic
- __ldar16 ARM64 intrinsic
- __ldar32 ARM64 intrinsic
- __ldar64 ARM64 intrinsic
- __ldapr8 ARM64 intrinsic
- __ldapr16 ARM64 intrinsic
- __ldapr32 ARM64 intrinsic
- __ldapr64 ARM64 intrinsic
- __prefetch2 ARM64 intrinsic
- __readx18byte ARM64 intrinsic
- __readx18word ARM64 intrinsic
- __readx18dword ARM64 intrinsic
- __readx18qword ARM64 intrinsic
- __setReg ARM64 intrinsic
- __setRegFp ARM64 intrinsic
- __setCallerReg ARM64 intrinsic
- __setCallerRegFp ARM64 intrinsic
- __stlr8 ARM64 intrinsic
- __stlr16 ARM64 intrinsic
- __stlr32 ARM64 intrinsic
- __stlr64 ARM64 intrinsic
- __swp8 ARM64 intrinsic
- __swp16 ARM64 intrinsic
- __swp32 ARM64 intrinsic
- __swp64 ARM64 intrinsic
- __swpa8 ARM64 intrinsic
- __swpa16 ARM64 intrinsic
- __swpa32 ARM64 intrinsic
- __swpa64 ARM64 intrinsic
- __swpl8 ARM64 intrinsic
- __swpl16 ARM64 intrinsic
- __swpl32 ARM64 intrinsic
- __swpl64 ARM64 intrinsic
- __swpal8 ARM64 intrinsic
- __swpal16 ARM64 intrinsic
- __swpal32 ARM64 intrinsic
- __swpal64 ARM64 intrinsic
- __sys ARM64 intrinsic
- __svc ARM64 intrinsic
- __writex18byte ARM64 intrinsic
- __writex18word ARM64 intrinsic
- __writex18dword ARM64 intrinsic
- __writex18qword ARM64 intrinsic
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 604658dbf4e6ac96b5c2344be5851f3baab3f641
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099499"
---
# <a name="arm64-intrinsics"></a>Встроенные объекты ARM64

Компилятор Microsoft C++ (КОМПИЛЯТОРОМ MSVC) делает доступными следующие встроенные функции в архитектуре ARM64. Дополнительные сведения о ARM см. в разделах Архитектура и средства разработки программного обеспечения на веб-сайте [документации разработчика ARM](https://developer.arm.com/docs) .

## <a name="neon"></a><a name="top"></a> NEON

Расширения наборов инструкций NEON Vector для ARM64 предоставляют возможности Single Instruction Multiple Data (SIMD). Они похожи на наборы команд для векторных инструкций MMX и SSE, общие для процессоров архитектуры x86 и x64.

Поддерживаются встроенные функции NEON, указанные в файле заголовка *arm64_neon. h*. Поддержка КОМПИЛЯТОРОМ MSVC для встроенных функций NEON напоминает компилятор ARM64, который описан в [встроенном справочнике по ARM Neon](https://developer.arm.com/architectures/instruction-sets/simd-isas/neon/intrinsics) на веб-сайте центра справочных данных ARM.

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a> Список встроенных компонентов для ARM64

|Имя функции|Инструкция|Прототип функции|
|-------------------|-----------------|------------------------|
|__break|брк|void __break (int)|
|__addx18byte||void __addx18byte (Long без знака, без знака)|
|__addx18word||void __addx18word (длинное целое без знака, короткое без знака)|
|__addx18dword||void __addx18dword (Long без знака, длинное целое без знака)|
|__addx18qword||void __addx18qword (длинное целое без знака, без знака __int64)|
|__cas8|касб|неподписанные __int8 __cas8 (неподписанные __int8 volatile * _Target, без подписи __int8 _Comp, без подписи __int8 _Value)|
|__cas16|ОПЛАТЫ|неподписанные __int16 __cas16 (неподписанные __int16 volatile * _Target, без подписи __int16 _Comp, без подписи __int16 _Value)|
|__cas32|Сервер клиентского доступа|неподписанные __int32 __cas32 (неподписанные __int32 volatile * _Target, без подписи __int32 _Comp, без подписи __int32 _Value)|
|__cas64|Сервер клиентского доступа|неподписанные __int64 __cas64 (неподписанные __int64 volatile * _Target, без подписи __int64 _Comp, без подписи __int64 _Value)|
|__casa8|касаб|неподписанные __int8 __casa8 (неподписанные __int8 volatile * _Target, без подписи __int8 _Comp, без подписи __int8 _Value)|
|__casa16|касах|неподписанные __int16 __casa16 (неподписанные __int16 volatile * _Target, без подписи __int16 _Comp, без подписи __int16 _Value)|
|__casa32|CASA|неподписанные __int32 __casa32 (неподписанные __int32 volatile * _Target, без подписи __int32 _Comp, без подписи __int32 _Value)|
|__casa64|CASA|неподписанные __int64 __casa64 (неподписанные __int64 volatile * _Target, без подписи __int64 _Comp, без подписи __int64 _Value)|
|__casl8|каслб|неподписанные __int8 __casl8 (неподписанные __int8 volatile * _Target, без подписи __int8 _Comp, без подписи __int8 _Value)|
|__casl16|каслх|неподписанные __int16 __casl16 (неподписанные __int16 volatile * _Target, без подписи __int16 _Comp, без подписи __int16 _Value)|
|__casl32|касл|неподписанные __int32 __casl32 (неподписанные __int32 volatile * _Target, без подписи __int32 _Comp, без подписи __int32 _Value)|
|__casl64|касл|неподписанные __int64 __casl64 (неподписанные __int64 volatile * _Target, без подписи __int64 _Comp, без подписи __int64 _Value)|
|__casal8|касалб|неподписанные __int8 __casal8 (неподписанные __int8 volatile * _Target, без подписи __int8 _Comp, без подписи __int8 _Value)|
|__casal16|касалх|неподписанные __int16 __casal16 (неподписанные __int16 volatile * _Target, без подписи __int16 _Comp, без подписи __int16 _Value)|
|__casal32|касал|неподписанные __int32 __casal32 (неподписанные __int32 volatile * _Target, без подписи __int32 _Comp, без подписи __int32 _Value)|
|__casal64|касал|неподписанные __int64 __casal64 (неподписанные __int64 volatile * _Target, без подписи __int64 _Comp, без подписи __int64 _Value)|
|__crc32b|CRC32B|неподписанный __int32 __crc32b (неподписанные __int32, без знака __int32)|
|__crc32h|CRC32H|неподписанный __int32 __crc32h (неподписанные __int32, без знака __int32)|
|__crc32w|CRC32W|неподписанный __int32 __crc32w (неподписанные __int32, без знака __int32)|
|__crc32d|CRC32X|неподписанный __int32 __crc32d (неподписанные __int32, без знака __int64)|
|__crc32cb|CRC32CB|неподписанный __int32 __crc32cb (неподписанные __int32, без знака __int32)|
|__crc32ch|CRC32CH|неподписанный __int32 __crc32ch (неподписанные __int32, без знака __int32)|
|__crc32cw|CRC32CW|неподписанный __int32 __crc32cw (неподписанные __int32, без знака __int32)|
|__crc32cd|CRC32CX|неподписанный __int32 __crc32cd (неподписанные __int32, без знака __int64)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> Вставляет операцию барьера памяти в поток инструкций. Параметр `_Type` указывает тип ограничения, которое накладывает барьер.<br /><br /> Дополнительные сведения о типах ограничений, которые могут быть применены, см. в разделе [ограничения на барьер памяти](#BarrierRestrictions).|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> Вставляет операцию барьера памяти в поток инструкций. Параметр `_Type` указывает тип ограничения, которое накладывает барьер.<br /><br /> Дополнительные сведения о типах ограничений, которые могут быть применены, см. в разделе [ограничения на барьер памяти](#BarrierRestrictions).|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> Вставляет операцию барьера памяти в поток инструкций. Параметр `_Type` указывает тип ограничения, которое накладывает барьер.<br /><br /> Дополнительные сведения о типах ограничений, которые могут быть применены, см. в разделе [ограничения на барьер памяти](#BarrierRestrictions).|
|__getReg||неподписанный __int64 __getReg (int)|
|__getRegFp||Double __getRegFp (int)|
|__getCallerReg||неподписанный __int64 __getCallerReg (int)|
|__getCallerRegFp||Double __getCallerRegFp (int)|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|ИНСТРУКЦИЙ|int __hlt (целое число без знака,...)|
|__incx18byte||void __incx18byte (беззнаковое длинное)|
|__incx18word||void __incx18word (беззнаковое длинное)|
|__incx18dword||void __incx18dword (беззнаковое длинное)|
|__incx18qword||void __incx18qword (беззнаковое длинное)|
|__iso_volatile_load16||__int16 \_ _iso_volatile_load16 (const volatile \_ _int16 \* )<br /><br /> Дополнительные сведения см. в статье [__iso_volatile_load/Store встроенные функции](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \_ _iso_volatile_load32 (const volatile \_ _int32 \* )<br /><br /> Дополнительные сведения см. в статье [__iso_volatile_load/Store встроенные функции](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \_ _iso_volatile_load64 (const volatile \_ _int64 \* )<br /><br /> Дополнительные сведения см. в статье [__iso_volatile_load/Store встроенные функции](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \_ _iso_volatile_load8 (const volatile \_ _int8 \* )<br /><br /> Дополнительные сведения см. в статье [__iso_volatile_load/Store встроенные функции](#IsoVolatileLoadStore).|
|__iso_volatile_store16||void __iso_volatile_store16 (volatile \_ _int16 \* , \_ _int16)<br /><br /> Дополнительные сведения см. в статье [__iso_volatile_load/Store встроенные функции](#IsoVolatileLoadStore).|
|__iso_volatile_store32||void __iso_volatile_store32 (volatile \_ _int32 \* , \_ _int32)<br /><br /> Дополнительные сведения см. в статье [__iso_volatile_load/Store встроенные функции](#IsoVolatileLoadStore).|
|__iso_volatile_store64||void __iso_volatile_store64 (volatile \_ _int64 \* , \_ _int64)<br /><br /> Дополнительные сведения см. в статье [__iso_volatile_load/Store встроенные функции](#IsoVolatileLoadStore).|
|__iso_volatile_store8||void __iso_volatile_store8 (volatile \_ _int8 \* , \_ _int8)<br /><br /> Дополнительные сведения см. в статье [__iso_volatile_load/Store встроенные функции](#IsoVolatileLoadStore).|
|__ldar8|лдарб|неподписанный __int8 __ldar8 (неподписанные __int8 volatile * _Target)|
|__ldar16|лдарх|неподписанный __int16 __ldar16 (неподписанные __int16 volatile * _Target)|
|__ldar32|лдар|неподписанный __int32 __ldar32 (неподписанные __int32 volatile * _Target)|
|__ldar64|лдар|неподписанный __int64 __ldar64 (неподписанные __int64 volatile * _Target)|
|__ldapr8|лдапрб|неподписанный __int8 __ldapr8 (неподписанные __int8 volatile * _Target)|
|__ldapr16|лдапрх|неподписанный __int16 __ldapr16 (неподписанные __int16 volatile * _Target)|
|__ldapr32|LDAP|неподписанный __int32 __ldapr32 (неподписанные __int32 volatile * _Target)|
|__ldapr64|LDAP|неподписанный __int64 __ldapr64 (неподписанные __int64 volatile * _Target)|
|__mulh||\___mulh _int64 ( \_ _int64, \_ _int64)|
|__prefetch|прфм|void __cdecl \_ _prefetch (const void \* )<br /><br /> Предоставляет `PRFM` подсказку памяти с операцией предвыборки `PLDL1KEEP` в системе, в ближайшее время доступ к которой может получить память или близко к указанному адресу. В некоторых системах можно оптимизировать шаблон доступа к памяти для повышения производительности во время выполнения. Тем не менее, с точки зрения языка C++, функция на имеет видимой активности и вообще может не предпринимать никаких действий.|
|__prefetch2|прфм|void __cdecl \_ _prefetch (const void \* , uint8_t прфоп)<br /><br /> Предоставляет `PRFM` подсказку памяти с предоставленной операцией предвыборки в системе, к которой скоро может быть получен объем памяти или около указанного адреса. В некоторых системах можно оптимизировать шаблон доступа к памяти для повышения производительности во время выполнения. Тем не менее, с точки зрения языка C++, функция на имеет видимой активности и вообще может не предпринимать никаких действий.|
|__readx18byte||__readx18byte char без знака (длинное целое)|
|__readx18word||короткое __readx18word без знака (длинное целое)|
|__readx18dword||длинное __readx18dword без знака (длинное целое)|
|__readx18qword||неподписанный __int64 __readx18qword (длинное целое)|
|__setReg||void __setReg (int, без знака __int64)|
|__setRegFp||void __setRegFp (int, Double)|
|__setCallerReg||void __setCallerReg (int, без знака __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, Double)|
|__sev|SEV|void __sev(void)|
|__static_assert||void __static_assert (int, const char \* )|
|__stlr8|стлрб|void __stlr8 (неподписанные __int8 volatile * _Target, неподписанные __int8 _Value)|
|__stlr16|стлрх|void __stlr16 (неподписанные __int16 volatile * _Target, неподписанные __int16 _Value)|
|__stlr32|стлр|void __stlr32 (неподписанные __int32 volatile * _Target, неподписанные __int32 _Value)|
|__stlr64|стлр|void __stlr64 (неподписанные __int64 volatile * _Target, неподписанные __int64 _Value)|
|__swp8|свпб|неподписанный __int8 __swp8 (неподписанные __int8 volatile * _Target, без знака __int8 _Value)|
|__swp16|свф|неподписанный __int16 __swp16 (неподписанные __int16 volatile * _Target, без знака __int16 _Value)|
|__swp32|свп|неподписанный __int32 __swp32 (неподписанные __int32 volatile * _Target, без знака __int32 _Value)|
|__swp64|свп|неподписанный __int64 __swp64 (неподписанные __int64 volatile * _Target, без знака __int64 _Value)|
|__swpa8|свпаб|неподписанный __int8 __swpa8 (неподписанные __int8 volatile * _Target, без знака __int8 _Value)|
|__swpa16|свпах|неподписанный __int16 __swpa16 (неподписанные __int16 volatile * _Target, без знака __int16 _Value)|
|__swpa32|свпа|неподписанный __int32 __swpa32 (неподписанные __int32 volatile * _Target, без знака __int32 _Value)|
|__swpa64|свпа|неподписанный __int64 __swpa64 (неподписанные __int64 volatile * _Target, без знака __int64 _Value)|
|__swpl8|свплб|неподписанный __int8 __swpl8 (неподписанные __int8 volatile * _Target, без знака __int8 _Value)|
|__swpl16|свплх|неподписанный __int16 __swpl16 (неподписанные __int16 volatile * _Target, без знака __int16 _Value)|
|__swpl32|свпл|неподписанный __int32 __swpl32 (неподписанные __int32 volatile * _Target, без знака __int32 _Value)|
|__swpl64|свпл|неподписанный __int64 __swpl64 (неподписанные __int64 volatile * _Target, без знака __int64 _Value)|
|__swpal8|свпалб|неподписанный __int8 __swpal8 (неподписанные __int8 volatile * _Target, без знака __int8 _Value)|
|__swpal16|свпалх|неподписанный __int16 __swpal16 (неподписанные __int16 volatile * _Target, без знака __int16 _Value)|
|__swpal32|свпал|неподписанный __int32 __swpal32 (неподписанные __int32 volatile * _Target, без знака __int32 _Value)|
|__swpal64|свпал|неподписанный __int64 __swpal64 (неподписанные __int64 volatile * _Target, без знака __int64 _Value)|
|__sys|ПРЕДСТАВЛЕНИЯ|Целочисленное __sys без знака (int, __int64)|
|__svc|SVC|Целочисленное __svc без знака (целое число без знака,...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||void __writex18byte (Long без знака, без знака)|
|__writex18word||void __writex18word (длинное целое без знака, короткое без знака)|
|__writex18dword||void __writex18dword (Long без знака, длинное целое без знака)|
|__writex18qword||void __writex18qword (длинное целое без знака, без знака __int64)|
|__umulh||неподписанный \_ _int64 __umulh (неподписанные \_ _int64, без знака \_ _int64)|
|_CopyDoubleFromInt64||двойной _CopyDoubleFromInt64 ( \_ _int64)|
|_CopyFloatFromInt32||_CopyFloatFromInt32 с плавающей запятой ( \_ _int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||Целочисленное _CountLeadingOnes64 без знака (_int64 без знака \_ )|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||Целочисленное _CountLeadingSigns64 без знака ( \_ _int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||Целочисленное _CountLeadingZeros64 без знака (_int64 без знака \_ )|
|_ReadStatusReg|MRS|\__ReadStatusReg _int64 (int)|
|_WriteStatusReg|MSR|void _WriteStatusReg (int, \_ _int64)|

[[Вернуться к началу](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a> Ограничения барьера памяти

Встроенные функции `__dmb` (барьер памяти данных), `__dsb` (барьер синхронизации данных) и `__isb` (барьер синхронизации инструкций) используют следующие предопределенные значения для указания ограничения барьера памяти в терминах домена общего доступа и типа доступа, затрагиваемого операцией.

|Restriction Value|Описание|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Полная система, операции чтения и записи.|
|_ARM64_BARRIER_ST|Полная система, только запись.|
|_ARM64_BARRIER_LD|Полная система, только для чтения.|
|_ARM64_BARRIER_ISH|Внутренний общий, чтение и запись.|
|_ARM64_BARRIER_ISHST|Внутренний общий, только запись.|
|_ARM64_BARRIER_ISHLD|Внутренние совместно используемый, только для чтения.|
|_ARM64_BARRIER_NSH|Не общий, чтение и запись.|
|_ARM64_BARRIER_NSHST|Не общий, только запись.|
|_ARM64_BARRIER_NSHLD|Без совместного просмотра, только для чтения.|
|_ARM64_BARRIER_OSH|Внешний общий, чтение и запись.|
|_ARM64_BARRIER_OSHST|Внешний общий, только запись.|
|_ARM64_BARRIER_OSHLD|Внешнее совместное, доступное только для чтения.|

Для `__isb` встроенного ограничения единственным допустимым ограничением является _ARM64_BARRIER_SY. все остальные значения зарезервированы архитектурой.

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a> встроенные функции/Store __iso_volatile_load

Эти встроенные функции явно выполняют загрузку и хранение, которые не подчиняются оптимизации компилятора.

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>Параметры

*Расположение*\
Адрес области памяти для чтения или записи.

*Значение*\
Значение, записываемое в указанное расположение в памяти (только встроенные функции хранилища).

#### <a name="return-value-load-intrinsics-only"></a>Возвращаемое значение (только для внутренних функций Load)

Значение расположения в памяти, указанное в параметре *Location*.

#### <a name="remarks"></a>Комментарии

`__iso_volatile_load8/16/32/64` `__iso_volatile_store8/16/32/64` Встроенные функции и можно использовать для явного выполнения доступа к памяти, которые не подчиняются оптимизации компилятора. Компилятор не может удалить, синсетизе или изменить относительный порядок этих операций. Однако он не создает неявные барьеры аппаратной памяти. Таким образом оборудование по-прежнему может переупорядочить возникающие операции доступа к памяти между несколькими потоками. Точнее, эти встроенные функции эквивалентны следующим выражениям, скомпилированным в **/volatile: ISO**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Обратите внимание, что встроенные функции принимают временные указатели для размещения временных переменных. Однако нет необходимости или рекомендации по использованию переменных указателей в качестве аргументов. Семантика этих операций в точности одинакова, если используется обычный, не зависящий от постоянного типа.

Дополнительные сведения о аргументе командной строки **/volatile: ISO** см. в разделе [/volatile (интерпретация ключевого слова "volatile")](../build/reference/volatile-volatile-keyword-interpretation.md).

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a> ARM64 поддержка встроенных функций из других архитектур

В следующей таблице перечислены встроенные функции из других архитектур, которые поддерживаются на платформах ARM64. Если поведение встроенного в ARM64 отличается от его поведения на других аппаратных архитектурах, будут указаны дополнительные сведения.

|Имя функции|Прототип функции|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|void __code_seg (const char \* )|
|__debugbreak|void __cdecl \_ _debugbreak (void)|
|__fastfail|__declspec (noreturn) void \_ _fastfail (беззнаковое целое)|
|__nop|void __nop(void)|
|__yield|void __yield (void) **Примечание.**  на платформах ARM64 эта функция создает инструкцию yield. Эта инструкция указывает, что поток выполняет задачу, которая может быть временно приостановлена от выполнения, например, с помощью взаимоблокировки, без негативного воздействия на программу. Он позволяет ЦП выполнять другие задачи во время циклов выполнения, которые в противном случае будут потеряны.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress (void)|
|_BitScanForward|_BitScanForward char без знака (длинное _Index без знака \* , длинное _Mask)|
|_BitScanForward64|неподписанный _BitScanForward64 char (Long _Index без знака \* , неподписанные __int64 _Mask)|
|_BitScanReverse|_BitScanReverse char без знака (длинное _Index без знака \* , длинное _Mask)|
|_BitScanReverse64|неподписанный _BitScanReverse64 char (Long _Index без знака \* , неподписанные __int64 _Mask)|
|_bittest|_bittest char без знака (Long const \* , Long)|
|_bittest64|_bittest64 char без знака (__int64 const \* , __int64)|
|_bittestandcomplement|_bittestandcomplement char без знака (длинное целое \* )|
|_bittestandcomplement64|_bittestandcomplement64 char без знака (__int64 \* , __int64)|
|_bittestandreset|_bittestandreset char без знака (длинное целое \* )|
|_bittestandreset64|_bittestandreset64 char без знака (__int64 \* , __int64)|
|_bittestandset|_bittestandset char без знака (длинное целое \* )|
|_bittestandset64|_bittestandset64 char без знака (__int64 \* , __int64)|
|_byteswap_uint64|неподписанный __int64 \_ _cdecl _byteswap_uint64 (без знака \_ _int64)|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|void __cdecl _disable (void) **Примечание.**  на платформах ARM64 эта функция создает инструкцию `MSR DAIFCLR,#2` ; она доступна только как встроенная.|
|_enable|void __cdecl _enable (void) **Примечание.**  на платформах ARM64 эта функция создает инструкцию `MSR DAIFSET,#2` ; она доступна только как встроенная.|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|void \* _ReturnAddress (void)|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|неподписанный __int64 \_ _cdecl _rotl64 (неподписанный \_ _int64 _Value, int _Shift)|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|неподписанный __int64 \_ _cdecl _rotr64 (неподписанный \_ _int64 _Value, int _Shift)|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[Вернуться к началу](#top)]

## <a name="interlocked-intrinsics"></a>Блокируемые встроенные функции

Блокирующие встроенные функции представляют собой набор встроенных функций, которые используются для выполнения атомарных операций чтения, изменения и записи. Некоторые из них общие для всех платформ. Они перечислены отдельно, так как их большое количество. Так как их определения в основном избыточны, проще подумать о них в общих условиях. Их имена можно использовать для понимания точного поведения.

В следующей таблице приведена сводка поддержки ARM64 для встроенных функций, не связанных с биттест. Каждая ячейка в таблице соответствует имени, полученном путем добавления имени операции в самой левой ячейке строки к имени типа в самой верхней ячейке столбца для `_Interlocked`. Например, ячейка на пересечении `Xor` строки и `8` столбца соответствует `_InterlockedXor8` и полностью поддерживается. Основные поддерживаемые функции предоставляют следующие дополнительные суффиксы: `_acq`, `_rel` и `_nf`. Суффикс `_acq` указывает «получить» семантику и суффикс `_rel` указывает «освободить» семантику. `_nf`Суффикс или "без ограждения" уникален для ARM и ARM64 и рассматривается в следующем разделе.

|Операция|8|16|32|64|128|С|
|-|-------|--------|--------|--------|-------|-------|
|Добавить|Нет|Нет|Полное|Полное|Нет|Нет|
|И|Полное|Полное|Полное|Полное|Нет|Нет|
|CompareExchange|Полное|Полное|Полное|Полное|Полное|Полное|
|Decrement|Нет|Полное|Полное|Полное|Нет|Нет|
|Exchange|Полное|Полное|Полное|Полное|Нет|Полное|
|ExchangeAdd|Полное|Полное|Полное|Полное|Нет|Нет|
|Приращение|Нет|Полное|Полное|Полное|Нет|Нет|
|либо|Полное|Полное|Полное|Полное|Нет|Нет|
|Xor|Полное|Полное|Полное|Полное|Нет|Нет|

Ключ:

- **Full**: поддерживает простые `_acq` формы,, `_rel` и `_nf` .

- **Нет**: не поддерживается

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a> суффикс _nf (без ограждения)

`_nf`Суффикс или "без ограждения" означает, что операция не работает как какой-либо барьер памяти, в отличие от других трех форм (обычных, `_acq` и `_rel` ), которые ведут себя как некоторый барьер. Одним из возможных способов использования `_nf` форм является поддержка счетчика статистики, который обновляется несколькими потоками одновременно, но значение которых не используется в течение нескольких потоков.

### <a name="list-of-interlocked-intrinsics"></a>Список блокируемых встроенных функций

|Имя функции|Прототип функции|
|-------------------|------------------------|
|_InterlockedAdd|длинный _InterlockedAdd (длинный _volatile \* , длинный)|
|_InterlockedAdd64|__int64 _InterlockedAdd64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd_acq|длинный _InterlockedAdd_acq (Long volatile \* , Long)|
|_InterlockedAdd_nf|длинный _InterlockedAdd_nf (Long volatile \* , Long)|
|_InterlockedAdd_rel|длинный _InterlockedAdd_rel (Long volatile \* , Long)|
|_InterlockedAnd|длинный _InterlockedAnd (Long volatile \* , Long)|
|_InterlockedAnd16|короткий _InterlockedAnd16 (короткий временный \* , короткий)|
|_InterlockedAnd16_acq|короткий _InterlockedAnd16_acq (короткий временный \* , короткий)|
|_InterlockedAnd16_nf|короткий _InterlockedAnd16_nf (короткий временный \* , короткий)|
|_InterlockedAnd16_rel|короткий _InterlockedAnd16_rel (короткий временный \* , короткий)|
|_InterlockedAnd64|__int64 _InterlockedAnd64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd8|Char _InterlockedAnd8 (char volatile \* , char)|
|_InterlockedAnd8_acq|Char _InterlockedAnd8_acq (char volatile \* , char)|
|_InterlockedAnd8_nf|Char _InterlockedAnd8_nf (char volatile \* , char)|
|_InterlockedAnd8_rel|Char _InterlockedAnd8_rel (char volatile \* , char)|
|_InterlockedAnd_acq|длинный _InterlockedAnd_acq (Long volatile \* , Long)|
|_InterlockedAnd_nf|длинный _InterlockedAnd_nf (Long volatile \* , Long)|
|_InterlockedAnd_rel|длинный _InterlockedAnd_rel (Long volatile \* , Long)|
|_InterlockedCompareExchange|_InterlockedCompareExchange длинное __cdecl (Long volatile \* , Long, Long)|
|_InterlockedCompareExchange_acq|длинный _InterlockedCompareExchange_acq (Long volatile \* , Long, Long)|
|_InterlockedCompareExchange_nf|длинный _InterlockedCompareExchange_nf (Long volatile \* , Long, Long)|
|_InterlockedCompareExchange_rel|длинный _InterlockedCompareExchange_rel (Long volatile \* , Long, Long)|
|_InterlockedCompareExchange16|короткий _InterlockedCompareExchange16 (короткий энергонезависимый \* , короткий, короткий)|
|_InterlockedCompareExchange16_acq|короткий _InterlockedCompareExchange16_acq (короткий энергонезависимый \* , короткий, короткий)|
|_InterlockedCompareExchange16_nf|короткий _InterlockedCompareExchange16_nf (короткий энергонезависимый \* , короткий, короткий)|
|_InterlockedCompareExchange16_rel|короткий _InterlockedCompareExchange16_rel (короткий энергонезависимый \* , короткий, короткий)|
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64 ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange8|Char _InterlockedCompareExchange8 (char volatile \* , char, char)|
|_InterlockedCompareExchange8_acq|Char _InterlockedCompareExchange8_acq (char volatile \* , char, char)|
|_InterlockedCompareExchange8_nf|Char _InterlockedCompareExchange8_nf (char volatile \* , char, char)|
|_InterlockedCompareExchange8_rel|Char _InterlockedCompareExchange8_rel (char volatile \* , char, char)|
|_InterlockedCompareExchangePointer|void \* _InterlockedCompareExchangePointer (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchangePointer_acq|void \* _InterlockedCompareExchangePointer_acq (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchangePointer_nf|void \* _InterlockedCompareExchangePointer_nf (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchangePointer_rel|void \* _InterlockedCompareExchangePointer_rel (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchange128|_InterlockedCompareExchange128 char без знака ( \_ _int64 volatile \* _Destination, \_ _int64 _ExchangeHigh, _int64 _ExchangeLow, _int64 \_ \_ \* _ComparandResult)|
|_InterlockedCompareExchange128_acq|_InterlockedCompareExchange128_acq char без знака ( \_ _int64 volatile \* _Destination, \_ _int64 _ExchangeHigh, _int64 _ExchangeLow, _int64 \_ \_ \* _ComparandResult)|
|_InterlockedCompareExchange128_nf|_InterlockedCompareExchange128_nf char без знака ( \_ _int64 volatile \* _Destination, \_ _int64 _ExchangeHigh, _int64 _ExchangeLow, _int64 \_ \_ \* _ComparandResult)|
|_InterlockedCompareExchange128_rel|_InterlockedCompareExchange128_rel char без знака ( \_ _int64 volatile \* _Destination, \_ _int64 _ExchangeHigh, _int64 _ExchangeLow, _int64 \_ \_ \* _ComparandResult)|
|_InterlockedDecrement|_InterlockedDecrement длинный __cdecl (Long volatile \* )|
|_InterlockedDecrement16|короткий _InterlockedDecrement16 (Short volatile \* )|
|_InterlockedDecrement16_acq|короткий _InterlockedDecrement16_acq (Short volatile \* )|
|_InterlockedDecrement16_nf|короткий _InterlockedDecrement16_nf (Short volatile \* )|
|_InterlockedDecrement16_rel|короткий _InterlockedDecrement16_rel (Short volatile \* )|
|_InterlockedDecrement64|_InterlockedDecrement64 __int64 ( \_ _int64 volatile \* )|
|_InterlockedDecrement64_acq|_InterlockedDecrement64_acq __int64 ( \_ _int64 volatile \* )|
|_InterlockedDecrement64_nf|_InterlockedDecrement64_nf __int64 ( \_ _int64 volatile \* )|
|_InterlockedDecrement64_rel|_InterlockedDecrement64_rel __int64 ( \_ _int64 volatile \* )|
|_InterlockedDecrement_acq|длинный _InterlockedDecrement_acq (Long volatile \* )|
|_InterlockedDecrement_nf|длинный _InterlockedDecrement_nf (Long volatile \* )|
|_InterlockedDecrement_rel|длинный _InterlockedDecrement_rel (Long volatile \* )|
|_InterlockedExchange|_InterlockedExchange длинное __cdecl (Long volatile \* _Target, Long)|
|_InterlockedExchange_acq|длинный _InterlockedExchange_acq (Long volatile \* _Target, Long)|
|_InterlockedExchange_nf|длинный _InterlockedExchange_nf (Long volatile \* _Target, Long)|
|_InterlockedExchange_rel|длинный _InterlockedExchange_rel (Long volatile \* _Target, Long)|
|_InterlockedExchange16|короткий _InterlockedExchange16 (короткий временный \* _Target, короткий)|
|_InterlockedExchange16_acq|короткий _InterlockedExchange16_acq (короткий временный \* _Target, короткий)|
|_InterlockedExchange16_nf|короткий _InterlockedExchange16_nf (короткий временный \* _Target, короткий)|
|_InterlockedExchange16_rel|короткий _InterlockedExchange16_rel (короткий временный \* _Target, короткий)|
|_InterlockedExchange64|__int64 _InterlockedExchange64 ( \_ _int64 volatile \* _Target, \_ _int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq ( \_ _int64 volatile \* _Target, \_ _int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf ( \_ _int64 volatile \* _Target, \_ _int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel ( \_ _int64 volatile \* _Target, \_ _int64)|
|_InterlockedExchange8|Char _InterlockedExchange8 (char volatile \* _Target, char)|
|_InterlockedExchange8_acq|Char _InterlockedExchange8_acq (char volatile \* _Target, char)|
|_InterlockedExchange8_nf|Char _InterlockedExchange8_nf (char volatile \* _Target, char)|
|_InterlockedExchange8_rel|Char _InterlockedExchange8_rel (char volatile \* _Target, char)|
|_InterlockedExchangeAdd|_InterlockedExchangeAdd длинное __cdecl (Long volatile \* , Long)|
|_InterlockedExchangeAdd16|короткий _InterlockedExchangeAdd16 (короткий временный \* , короткий)|
|_InterlockedExchangeAdd16_acq|короткий _InterlockedExchangeAdd16_acq (короткий временный \* , короткий)|
|_InterlockedExchangeAdd16_nf|короткий _InterlockedExchangeAdd16_nf (короткий временный \* , короткий)|
|_InterlockedExchangeAdd16_rel|короткий _InterlockedExchangeAdd16_rel (короткий временный \* , короткий)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd8|Char _InterlockedExchangeAdd8 (char volatile \* , char)|
|_InterlockedExchangeAdd8_acq|Char _InterlockedExchangeAdd8_acq (char volatile \* , char)|
|_InterlockedExchangeAdd8_nf|Char _InterlockedExchangeAdd8_nf (char volatile \* , char)|
|_InterlockedExchangeAdd8_rel|Char _InterlockedExchangeAdd8_rel (char volatile \* , char)|
|_InterlockedExchangeAdd_acq|длинный _InterlockedExchangeAdd_acq (Long volatile \* , Long)|
|_InterlockedExchangeAdd_nf|длинный _InterlockedExchangeAdd_nf (Long volatile \* , Long)|
|_InterlockedExchangeAdd_rel|длинный _InterlockedExchangeAdd_rel (Long volatile \* , Long)|
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer (void \* volatile \* , _Target, void \* )|
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq (void \* volatile \* , _Target, void \* )|
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf (void \* volatile \* , _Target, void \* )|
|_InterlockedExchangePointer_rel|void \* _InterlockedExchangePointer_rel (void \* volatile \* , _Target, void \* )|
|_InterlockedIncrement|_InterlockedIncrement длинный __cdecl (Long volatile \* )|
|_InterlockedIncrement16|короткий _InterlockedIncrement16 (Short volatile \* )|
|_InterlockedIncrement16_acq|короткий _InterlockedIncrement16_acq (Short volatile \* )|
|_InterlockedIncrement16_nf|короткий _InterlockedIncrement16_nf (Short volatile \* )|
|_InterlockedIncrement16_rel|короткий _InterlockedIncrement16_rel (Short volatile \* )|
|_InterlockedIncrement64|_InterlockedIncrement64 __int64 ( \_ _int64 volatile \* )|
|_InterlockedIncrement64_acq|_InterlockedIncrement64_acq __int64 ( \_ _int64 volatile \* )|
|_InterlockedIncrement64_nf|_InterlockedIncrement64_nf __int64 ( \_ _int64 volatile \* )|
|_InterlockedIncrement64_rel|_InterlockedIncrement64_rel __int64 ( \_ _int64 volatile \* )|
|_InterlockedIncrement_acq|длинный _InterlockedIncrement_acq (Long volatile \* )|
|_InterlockedIncrement_nf|длинный _InterlockedIncrement_nf (Long volatile \* )|
|_InterlockedIncrement_rel|длинный _InterlockedIncrement_rel (Long volatile \* )|
|_InterlockedOr|длинный _InterlockedOr (Long volatile \* , Long)|
|_InterlockedOr16|короткий _InterlockedOr16 (короткий временный \* , короткий)|
|_InterlockedOr16_acq|короткий _InterlockedOr16_acq (короткий временный \* , короткий)|
|_InterlockedOr16_nf|короткий _InterlockedOr16_nf (короткий временный \* , короткий)|
|_InterlockedOr16_rel|короткий _InterlockedOr16_rel (короткий временный \* , короткий)|
|_InterlockedOr64|__int64 _InterlockedOr64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr8|Char _InterlockedOr8 (char volatile \* , char)|
|_InterlockedOr8_acq|Char _InterlockedOr8_acq (char volatile \* , char)|
|_InterlockedOr8_nf|Char _InterlockedOr8_nf (char volatile \* , char)|
|_InterlockedOr8_rel|Char _InterlockedOr8_rel (char volatile \* , char)|
|_InterlockedOr_acq|длинный _InterlockedOr_acq (Long volatile \* , Long)|
|_InterlockedOr_nf|длинный _InterlockedOr_nf (Long volatile \* , Long)|
|_InterlockedOr_rel|длинный _InterlockedOr_rel (Long volatile \* , Long)|
|_InterlockedXor|длинный _InterlockedXor (Long volatile \* , Long)|
|_InterlockedXor16|короткий _InterlockedXor16 (короткий временный \* , короткий)|
|_InterlockedXor16_acq|короткий _InterlockedXor16_acq (короткий временный \* , короткий)|
|_InterlockedXor16_nf|короткий _InterlockedXor16_nf (короткий временный \* , короткий)|
|_InterlockedXor16_rel|короткий _InterlockedXor16_rel (короткий временный \* , короткий)|
|_InterlockedXor64|__int64 _InterlockedXor64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor8|Char _InterlockedXor8 (char volatile \* , char)|
|_InterlockedXor8_acq|Char _InterlockedXor8_acq (char volatile \* , char)|
|_InterlockedXor8_nf|Char _InterlockedXor8_nf (char volatile \* , char)|
|_InterlockedXor8_rel|Char _InterlockedXor8_rel (char volatile \* , char)|
|_InterlockedXor_acq|длинный _InterlockedXor_acq (Long volatile \* , Long)|
|_InterlockedXor_nf|длинный _InterlockedXor_nf (Long volatile \* , Long)|
|_InterlockedXor_rel|длинный _InterlockedXor_rel (Long volatile \* , Long)|

[[Вернуться к началу](#top)]

### <a name="_interlockedbittest-intrinsics"></a>встроенные функции _interlockedbittest

Встроенные функции обычного блокируемого двоичного теста являются общими для всех платформ. ARM64 добавляет `_acq` `_rel` типы, и `_nf` , которые просто изменяют семантику барьера операции, как описано в подразделе [_nf (без ограждения)](#nf_suffix) в этой статье ранее.

|Имя функции|Прототип функции|
|-------------------|------------------------|
|_interlockedbittestandreset|_interlockedbittestandreset char без знака (Long volatile \* , Long)|
|_interlockedbittestandreset_acq|_interlockedbittestandreset_acq char без знака (Long volatile \* , Long)|
|_interlockedbittestandreset_nf|_interlockedbittestandreset_nf char без знака (Long volatile \* , Long)|
|_interlockedbittestandreset_rel|_interlockedbittestandreset_rel char без знака (Long volatile \* , Long)|
|_interlockedbittestandreset64|_interlockedbittestandreset64 char без знака (__int64 volatile \* , __int64)|
|_interlockedbittestandreset64_acq|_interlockedbittestandreset64_acq char без знака (__int64 volatile \* , __int64)|
|_interlockedbittestandreset64_nf|_interlockedbittestandreset64_nf char без знака (__int64 volatile \* , __int64)|
|_interlockedbittestandreset64_rel|_interlockedbittestandreset64_rel char без знака (__int64 volatile \* , __int64)|
|_interlockedbittestandset|_interlockedbittestandset char без знака (Long volatile \* , Long)|
|_interlockedbittestandset_acq|_interlockedbittestandset_acq char без знака (Long volatile \* , Long)|
|_interlockedbittestandset_nf|_interlockedbittestandset_nf char без знака (Long volatile \* , Long)|
|_interlockedbittestandset_rel|_interlockedbittestandset_rel char без знака (Long volatile \* , Long)|
|_interlockedbittestandset64|_interlockedbittestandset64 char без знака (__int64 volatile \* , __int64)|
|_interlockedbittestandset64_acq|_interlockedbittestandset64_acq char без знака (__int64 volatile \* , __int64)|
|_interlockedbittestandset64_nf|_interlockedbittestandset64_nf char без знака (__int64 volatile \* , __int64)|
|_interlockedbittestandset64_rel|_interlockedbittestandset64_rel char без знака (__int64 volatile \* , __int64)|

[[Вернуться к началу](#top)]

## <a name="see-also"></a>См. также раздел

[Встроенные функции компилятора](../intrinsics/compiler-intrinsics.md)\
[Встроенные объекты ARM](arm-intrinsics.md)\
[Справочник по ассемблеру ARM](../assembler/arm/arm-assembler-reference.md)\
[Справочник по языку C++](../cpp/cpp-language-reference.md)
