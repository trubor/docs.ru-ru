---
title: Параметры конфигурации глобализации
description: Вы можете узнать о параметрах времени выполнения, настраивающих аспекты глобализации для приложения .NET Core, например способа анализа дат на японском языке.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: fc98e965093c28b75b9b66e4f1c9f147abd4680e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721921"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="40d4a-103">Параметры конфигурации времени выполнения для глобализации</span><span class="sxs-lookup"><span data-stu-id="40d4a-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="40d4a-104">Invariant mode (Инвариантный режим)</span><span class="sxs-lookup"><span data-stu-id="40d4a-104">Invariant mode</span></span>

- <span data-ttu-id="40d4a-105">Определяет, выполняется ли приложение .NET Core в инвариантном режиме глобализации без доступа к данным и поведению, зависящим от языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="40d4a-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="40d4a-106">Если этот параметр не задан, приложение будет работать с доступом к данным языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="40d4a-106">If you omit this setting, the app runs with access to cultural data.</span></span> <span data-ttu-id="40d4a-107">Это эквивалентно присвоению значения `false`.</span><span class="sxs-lookup"><span data-stu-id="40d4a-107">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="40d4a-108">Дополнительные сведения см. в статье [Инвариантный режим глобализации .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="40d4a-108">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="40d4a-109">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="40d4a-109">Setting name</span></span> | <span data-ttu-id="40d4a-110">Значения</span><span class="sxs-lookup"><span data-stu-id="40d4a-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="40d4a-111">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="40d4a-111">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="40d4a-112">`false` — доступ к данным языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="40d4a-112">`false` - access to cultural data</span></span><br/><span data-ttu-id="40d4a-113">`true` — выполнение в инвариантном режиме</span><span class="sxs-lookup"><span data-stu-id="40d4a-113">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="40d4a-114">**Свойство MSBuild**</span><span class="sxs-lookup"><span data-stu-id="40d4a-114">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="40d4a-115">`false` — доступ к данным языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="40d4a-115">`false` - access to cultural data</span></span><br/><span data-ttu-id="40d4a-116">`true` — выполнение в инвариантном режиме</span><span class="sxs-lookup"><span data-stu-id="40d4a-116">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="40d4a-117">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="40d4a-117">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="40d4a-118">`0` — доступ к данным языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="40d4a-118">`0` - access to cultural data</span></span><br/><span data-ttu-id="40d4a-119">`1` — выполнение в инвариантном режиме</span><span class="sxs-lookup"><span data-stu-id="40d4a-119">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="40d4a-120">Примеры</span><span class="sxs-lookup"><span data-stu-id="40d4a-120">Examples</span></span>

<span data-ttu-id="40d4a-121">Файл *runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="40d4a-121">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="40d4a-122">Файл проекта:</span><span class="sxs-lookup"><span data-stu-id="40d4a-122">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="40d4a-123">Era year ranges (Диапазоны лет эры)</span><span class="sxs-lookup"><span data-stu-id="40d4a-123">Era year ranges</span></span>

- <span data-ttu-id="40d4a-124">Определяет, являются ли проверки диапазона для календарей, поддерживающих несколько эр, нестрогими, или даты, превышающие диапазон дат эры, вызывают <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="40d4a-124">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="40d4a-125">Если этот параметр не задан, проверки диапазона будут нестрогими.</span><span class="sxs-lookup"><span data-stu-id="40d4a-125">If you omit this setting, range checks are relaxed.</span></span> <span data-ttu-id="40d4a-126">Это эквивалентно присвоению значения `false`.</span><span class="sxs-lookup"><span data-stu-id="40d4a-126">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="40d4a-127">Дополнительные сведения см. в разделе [Календари, эры и диапазоны дат: нестрогие проверки диапазонов](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="40d4a-127">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="40d4a-128">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="40d4a-128">Setting name</span></span> | <span data-ttu-id="40d4a-129">Значения</span><span class="sxs-lookup"><span data-stu-id="40d4a-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="40d4a-130">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="40d4a-130">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="40d4a-131">`false` — нестрогие проверки диапазонов</span><span class="sxs-lookup"><span data-stu-id="40d4a-131">`false` - relaxed range checks</span></span><br/><span data-ttu-id="40d4a-132">`true` — исключение при переполнении</span><span class="sxs-lookup"><span data-stu-id="40d4a-132">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="40d4a-133">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="40d4a-133">**Environment variable**</span></span> | <span data-ttu-id="40d4a-134">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40d4a-134">N/A</span></span> | <span data-ttu-id="40d4a-135">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40d4a-135">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="40d4a-136">Japanese date parsing (Анализ дат на японском языке)</span><span class="sxs-lookup"><span data-stu-id="40d4a-136">Japanese date parsing</span></span>

- <span data-ttu-id="40d4a-137">Определяет, успешно ли анализируется строка, содержащая "1" или "Ганнен" в качестве года, либо поддерживается только значение "1".</span><span class="sxs-lookup"><span data-stu-id="40d4a-137">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="40d4a-138">Если этот параметр не задан, строки, содержащие "1" или "Ганнен" в качестве года, будут успешно проанализированы.</span><span class="sxs-lookup"><span data-stu-id="40d4a-138">If you omit this setting, strings that contain either "1" or "Gannen" as the year parse successfully.</span></span> <span data-ttu-id="40d4a-139">Это эквивалентно присвоению значения `false`.</span><span class="sxs-lookup"><span data-stu-id="40d4a-139">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="40d4a-140">Дополнительные сведения см. в разделе [Представление дат в календарях с несколькими эрами](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="40d4a-140">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="40d4a-141">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="40d4a-141">Setting name</span></span> | <span data-ttu-id="40d4a-142">Значения</span><span class="sxs-lookup"><span data-stu-id="40d4a-142">Values</span></span> |
| - | - | - |
| <span data-ttu-id="40d4a-143">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="40d4a-143">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="40d4a-144">`false` — поддерживается "Ганнен" или "1"</span><span class="sxs-lookup"><span data-stu-id="40d4a-144">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="40d4a-145">`true` — поддерживается только "1"</span><span class="sxs-lookup"><span data-stu-id="40d4a-145">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="40d4a-146">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="40d4a-146">**Environment variable**</span></span> | <span data-ttu-id="40d4a-147">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40d4a-147">N/A</span></span> | <span data-ttu-id="40d4a-148">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40d4a-148">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="40d4a-149">Japanese year format (Японский формат года)</span><span class="sxs-lookup"><span data-stu-id="40d4a-149">Japanese year format</span></span>

- <span data-ttu-id="40d4a-150">Определяет, форматируется ли первый год японской календарной эры как "Ганнен" или как число.</span><span class="sxs-lookup"><span data-stu-id="40d4a-150">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="40d4a-151">Если этот параметр не задан, первый год форматируется, как "Ганнен".</span><span class="sxs-lookup"><span data-stu-id="40d4a-151">If you omit this setting, the first year is formatted as "Gannen".</span></span> <span data-ttu-id="40d4a-152">Это эквивалентно присвоению значения `false`.</span><span class="sxs-lookup"><span data-stu-id="40d4a-152">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="40d4a-153">Дополнительные сведения см. в разделе [Представление дат в календарях с несколькими эрами](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="40d4a-153">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="40d4a-154">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="40d4a-154">Setting name</span></span> | <span data-ttu-id="40d4a-155">Значения</span><span class="sxs-lookup"><span data-stu-id="40d4a-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="40d4a-156">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="40d4a-156">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="40d4a-157">`false` — формат в виде "Ганнен"</span><span class="sxs-lookup"><span data-stu-id="40d4a-157">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="40d4a-158">`true` — формат в виде числа</span><span class="sxs-lookup"><span data-stu-id="40d4a-158">`true` - format as number</span></span> |
| <span data-ttu-id="40d4a-159">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="40d4a-159">**Environment variable**</span></span> | <span data-ttu-id="40d4a-160">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40d4a-160">N/A</span></span> | <span data-ttu-id="40d4a-161">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40d4a-161">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="40d4a-162">NLS</span><span class="sxs-lookup"><span data-stu-id="40d4a-162">NLS</span></span>

- <span data-ttu-id="40d4a-163">Определяет, использует ли .NET API глобализации для приложений Windows: National Language Support (NLS) и International Components for Unicode (ICU).</span><span class="sxs-lookup"><span data-stu-id="40d4a-163">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="40d4a-164">.NET 5.0 и более поздних версий использует API глобализации ICU по умолчанию в обновлении Windows за 10 мая 2019 г. и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="40d4a-164">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="40d4a-165">Если этот параметр не задан, .NET по умолчанию использует API глобализации ICU.</span><span class="sxs-lookup"><span data-stu-id="40d4a-165">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="40d4a-166">Это эквивалентно присвоению значения `false`.</span><span class="sxs-lookup"><span data-stu-id="40d4a-166">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="40d4a-167">См. сведения об [API глобализации, которые используют библиотеки ICU в Windows](../compatibility/globalization/5.0/icu-globalization-api.md).</span><span class="sxs-lookup"><span data-stu-id="40d4a-167">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

| | <span data-ttu-id="40d4a-168">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="40d4a-168">Setting name</span></span> | <span data-ttu-id="40d4a-169">Значения</span><span class="sxs-lookup"><span data-stu-id="40d4a-169">Values</span></span> | <span data-ttu-id="40d4a-170">Введенный</span><span class="sxs-lookup"><span data-stu-id="40d4a-170">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="40d4a-171">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="40d4a-171">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="40d4a-172">`false` — использование API глобализации ICU</span><span class="sxs-lookup"><span data-stu-id="40d4a-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="40d4a-173">`true` — использование API глобализации NLS</span><span class="sxs-lookup"><span data-stu-id="40d4a-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="40d4a-174">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="40d4a-174">.NET 5.0</span></span> |
| <span data-ttu-id="40d4a-175">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="40d4a-175">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="40d4a-176">`false` — использование API глобализации ICU</span><span class="sxs-lookup"><span data-stu-id="40d4a-176">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="40d4a-177">`true` — использование API глобализации NLS</span><span class="sxs-lookup"><span data-stu-id="40d4a-177">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="40d4a-178">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="40d4a-178">.NET 5.0</span></span> |
