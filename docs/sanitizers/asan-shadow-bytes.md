---
title: Аддресссанитизер теневых байт
description: Техническое описание теневых байтов, записанных и прочитанных кодом, созданным компилятором, и средой выполнения Аддресссанитизер.
ms.date: 03/02/2021
helpviewer_keywords:
- Shadow bytes
- AddressSanitizer shadow bytes
- Address Sanitizer shadow bytes
- ASan shadow bytes
ms.openlocfilehash: 89c3051d2e68d579f2f187fcd12b45ff52cd8a58
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471178"
---
# <a name="addresssanitizer-shadow-bytes"></a>Аддресссанитизер теневых байт

Вкратце кратко обобщена концепция теневых байтов и то, как они могут использоваться реализацией среды выполнения [`/fsanitize=address`](../build/reference/fsanitize.md) . Дополнительные сведения см. в [документе основополагающую](https://www.usenix.org/system/files/conference/atc12/atc12-final39.pdf) и [алгоритме аддресссанитизер](https://github.com/google/sanitizers/wiki/AddressSanitizerAlgorithm).

## <a name="core-concept"></a>Основная концепция

Каждые **8 байт** в виртуальном адресном пространстве приложения можно описать с помощью **одного байта с тенью**.

Один теневой байт описывает, сколько байт доступно в данный момент следующим образом:

- 0 означает все 8 байт
- 1-7 — от одного до семи байт
- Отрицательные числа кодируются контекст для среды выполнения, используемой для диагностики отчетов.

### <a name="shadow-byte-legend"></a>Условные обозначения байт с тенью

Рассмотрим это условные обозначения теневого байта, где определены все отрицательные значения:

:::image type="content" source="./media/asan-shadow-byte-legend.png" alt-text="Снимок экрана с условными обозначениями Аддресссанитизер в виде теневого байта.":::

## <a name="mapping---describing-your-address-space"></a>Сопоставление — описание адресного пространства

Каждые 8 байт в виртуальном адресном пространстве приложения с выровняйтем "0-mod-8" можно сопоставить с теневым байтом, который описывает этот слот в виртуальном адресном пространстве.  Это сопоставление можно выполнить с помощью **простой смены и добавления**.

На платформе x86:

```cpp
char shadow_byte_value = *((Your_Address >> 3) + 0x30000000)
```

На x64:

```cpp
char shadow_byte_value = *((Your_Address >> 3) + _asan_runtime_assigned_offset)
```

## <a name="code-generation---tests"></a>Создание кода — тесты

Определите, как могут записываться определенные теневые байты: кодом, сгенерированным компилятором, статическими данными или средой выполнения. Этот псевдокод показывает, как можно создать проверку перед любой нагрузкой или хранилищем:

```cpp
ShadowAddr = (Addr >> 3) + Offset;
if (*ShadowAddr != 0) {
    ReportAndCrash(Addr);
}
```

При инструментировании ссылки на память, размер которой не превышает 8 байт, инструментирование немного сложнее. Если значение тени является положительным (то есть можно получить доступ только к первому байту в 8-байтном слове), необходимо сравнить последние 3 бита адреса с k.

```cpp
ShadowAddr = (Addr >> 3) + Offset;
k = *ShadowAddr;
if (k != 0 && ((Addr & 7) + AccessSize > k)) {
    ReportAndCrash(Addr);
}
```

Среда выполнения и код, созданный компилятором, одновременно записывают байты. Эти теневые байты разрешают или отменяют доступ при освобождении областей или памяти. Приведенные выше проверки проводят теневые байты, описывающие 8-байтные "слоты" в адресном пространстве приложения в определенное время выполнения программы. Помимо этих явно созданных проверок среда выполнения также проверяет теневые байты после перехвата (или "перехватчики") многих функций в CRT.

Дополнительные сведения см. в списке [перехваченных функций](./asan-runtime.md#default-interceptors).

## <a name="setting-shadow-bytes"></a>Задание байтов с тенью

Код, создаваемый компилятором, и среда выполнения Аддресссанитизер могут записывать теневые байты. Например, компилятор может задать теневые байты, чтобы разрешить доступ фиксированного размера к локальным переменным стека, определенным во внутренней области. Среда выполнения может окружить глобальные переменные в разделе данных теневыми байтами.

## <a name="see-also"></a>См. также раздел

[Обзор Аддресссанитизер](./asan.md)\
[Известные проблемы Аддресссанитизер](./asan-known-issues.md)\
[Справочник по сборке и языку Аддресссанитизер](./asan-building.md)\
[Справочник по среде выполнения Аддресссанитизер](./asan-runtime.md)\
[Аддресссанитизер облачное или распределенное тестирование](./asan-offline-crash-dumps.md)\
[Интеграция отладчика Аддресссанитизер](./asan-debugger-integration.md)\
[Примеры ошибок Аддресссанитизер](./asan-error-examples.md)