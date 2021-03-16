---
title: Критическое изменение. Отсутствует проверка суффикса A/W на платформах, отличных от Windows
description: Сведения о критическом изменении взаимодействия в .NET 5, где суффиксы больше не добавляются к именам экспортируемых функций во время проверки для P/Invokes на платформах, отличных от Windows.
ms.date: 08/13/2020
ms.openlocfilehash: 924cbcb6c432e2f7c52c7218d48a938b61306c9c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256625"
---
# <a name="no-aw-suffix-probing-on-non-windows-platforms"></a>Отсутствует проверка суффикса A/W на платформах, отличных от Windows

Среды выполнения .NET больше не добавляют суффиксы `A` или `W` к именам экспортируемых функций во время проверки для P/Invokes на платформах, отличных от Windows.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="change-description"></a>Описание изменений

[По соглашению Windows](/windows/win32/intl/conventions-for-function-prototypes), к именам функций Windows SDK, которые соответствуют кодовой странице Windows и версиям Юникода, добавляются суффиксы `A` и `W` соответственно.

В предыдущих версиях .NET в средах выполнения CoreCLR и Mono к именам экспорта добавлялись суффиксы `A` или `W` во время обнаружения экспорта для P/Invokes *на всех платформах*.

В .NET 5 и более поздней версии суффиксы `A` или `W` добавляется к именам экспорта во время обнаружения экспорта *только в Windows*. На платформах UNIX суффикс не добавляется. Семантика обеих сред выполнения на платформе Windows остается неизменной.

## <a name="reason-for-change"></a>Причина изменения

Это изменение было внесено с целью упрощения проверки на нескольких платформах. Это изменение не должно привести к дополнительным издержкам, так как платформы, отличные от Windows, не содержат такой семантики.

## <a name="recommended-action"></a>Рекомендованное действие

Чтобы ослабить эффект этого изменения, можно вручную добавить требуемый суффикс на платформах, отличных от Windows. Пример:

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

### Category

Interop

-->
