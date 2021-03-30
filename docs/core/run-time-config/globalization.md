---
title: Параметры конфигурации глобализации
description: Вы можете узнать о параметрах времени выполнения, настраивающих аспекты глобализации для приложения .NET Core, например способа анализа дат на японском языке.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: e8179a7e1421a3ff0ceacf07a2843c1b77af6143
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873553"
---
# <a name="run-time-configuration-options-for-globalization"></a>Параметры конфигурации времени выполнения для глобализации

## <a name="invariant-mode"></a>Invariant mode (Инвариантный режим)

- Определяет, выполняется ли приложение .NET Core в инвариантном режиме глобализации без доступа к данным и поведению, зависящим от языка и региональных параметров.
- Если этот параметр не задан, приложение будет работать с доступом к данным языка и региональных параметров. Это эквивалентно присвоению значения `false`.
- Дополнительные сведения см. в статье [Инвариантный режим глобализации .NET Core](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).

| | Имя параметра | Значения |
| - | - | - |
| **runtimeconfig.json** | `System.Globalization.Invariant` | `false` — доступ к данным языка и региональных параметров<br/>`true` — выполнение в инвариантном режиме |
| **Свойство MSBuild** | `InvariantGlobalization` | `false` — доступ к данным языка и региональных параметров<br/>`true` — выполнение в инвариантном режиме |
| **Переменная среды** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0` — доступ к данным языка и региональных параметров<br/>`1` — выполнение в инвариантном режиме |

### <a name="examples"></a>Примеры

Файл *runtimeconfig.json*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

Файл проекта:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a>Era year ranges (Диапазоны лет эры)

- Определяет, являются ли проверки диапазона для календарей, поддерживающих несколько эр, нестрогими, или даты, превышающие диапазон дат эры, вызывают <xref:System.ArgumentOutOfRangeException>.
- Если этот параметр не задан, проверки диапазона будут нестрогими. Это эквивалентно присвоению значения `false`.
- Дополнительные сведения см. в разделе [Календари, эры и диапазоны дат: нестрогие проверки диапазонов](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Имя параметра | Значения |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false` — нестрогие проверки диапазонов<br/>`true` — исключение при переполнении |
| **Переменная среды** | Н/Д | Н/Д |

## <a name="japanese-date-parsing"></a>Japanese date parsing (Анализ дат на японском языке)

- Определяет, успешно ли анализируется строка, содержащая "1" или "Ганнен" в качестве года, либо поддерживается только значение "1".
- Если этот параметр не задан, строки, содержащие "1" или "Ганнен" в качестве года, будут успешно проанализированы. Это эквивалентно присвоению значения `false`.
- Дополнительные сведения см. в разделе [Представление дат в календарях с несколькими эрами](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Имя параметра | Значения |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false` — поддерживается "Ганнен" или "1"<br/>`true` — поддерживается только "1" |
| **Переменная среды** | Н/Д | Н/Д |

## <a name="japanese-year-format"></a>Japanese year format (Японский формат года)

- Определяет, форматируется ли первый год японской календарной эры как "Ганнен" или как число.
- Если этот параметр не задан, первый год форматируется, как "Ганнен". Это эквивалентно присвоению значения `false`.
- Дополнительные сведения см. в разделе [Представление дат в календарях с несколькими эрами](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Имя параметра | Значения |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false` — формат в виде "Ганнен"<br/>`true` — формат в виде числа |
| **Переменная среды** | Н/Д | Н/Д |

## <a name="nls"></a>NLS

- Определяет, использует ли .NET API глобализации для приложений Windows: National Language Support (NLS) и International Components for Unicode (ICU). .NET 5.0 и более поздних версий использует API глобализации ICU по умолчанию в обновлении Windows за 10 мая 2019 г. и более поздних версиях.
- Если этот параметр не задан, .NET по умолчанию использует API глобализации ICU. Это эквивалентно присвоению значения `false`.
- См. сведения об [API глобализации, которые используют библиотеки ICU в Windows](../compatibility/globalization/5.0/icu-globalization-api.md).

| | Имя параметра | Значения | Введенный |
| - | - | - | - |
| **runtimeconfig.json** | `System.Globalization.UseNls` | `false` — использование API глобализации ICU<br/>`true` — использование API глобализации NLS | .NET 5.0 |
| **Переменная среды** | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | `false` — использование API глобализации ICU<br/>`true` — использование API глобализации NLS | .NET 5.0 |
