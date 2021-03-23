---
title: Анализ кода в .NET
titleSuffix: ''
description: Сведения об анализе исходного кода в пакете SDK для .NET.
ms.date: 12/04/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: 1a0b31f7aca6415510ed0fcd08e9f9a0f8f39bf5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876608"
---
# <a name="overview-of-net-source-code-analysis"></a>Обзор анализа исходного кода .NET

Анализаторы .NET Compiler Platform (Roslyn) проверяют код C# или Visual Basic на наличие проблем с качеством и стилем. Начиная с .NET 5.0, эти анализаторы включены в пакет SDK для .NET. Их не нужно устанавливать отдельно. Если ваш проект предназначен для .NET 5 или более поздней версии, анализ кода будет включен по умолчанию. Если ваш проект предназначен для другой реализации .NET, например .NET Core, .NET Standard или .NET Framework, необходимо вручную включить анализ кода, установив для свойства [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) значение `true`.

Если вы не хотите переходить на использование пакета SDK для .NET 5+, работаете с проектом, стиль которого отличается от стиля пакета SDK для .NET Framework, или предпочитаете использовать модель на основе пакетов NuGet, тогда вы можете воспользоваться анализаторами, которые также доступны в [пакете NuGet Microsoft.CodeAnalysis .NetAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Возможно, вы предпочтете модель на основе пакета для обновлений версий по требованию.

> [!NOTE]
> Анализаторы .NET не зависят от целевой платформы. То есть при работе с проектом не нужно ориентироваться на конкретную реализацию .NET. Анализаторы можно использовать для проектов, предназначенных для `net5.0`, а также для более ранних версий .NET, таких как `netcoreapp3.1` и `net472`. Однако для включения анализа кода с помощью свойства [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) ваш проект должен содержать ссылку на [пакет SDK проекта](../../core/project-sdk/overview.md).

Если анализатор обнаруживает нарушения правил, он отправляет о них оповещение в виде предложения, предупреждения или ошибки, в зависимости от [настройки](configuration-options.md) каждого правила. Нарушения анализа кода появляются с префиксом CA или IDE. Этот префикс отличает их от ошибок компилятора.

## <a name="code-quality-analysis"></a>Анализ качества кода

Правила *анализа качества кода* (CAxxxx) проверяют код C# или Visual Basic на наличие проблем с безопасностью, производительностью, дизайном и т. д. По умолчанию анализ включен для проектов, предназначенных для .NET 5.0 или более поздних версий. Можно включить анализ кода для проектов, предназначенных для более ранних версий .NET, задав для свойства [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) значение `true`. Кроме того, вы можете отключить анализ кода для своего проекта, установив для `EnableNETAnalyzers` значение `false`.

> [!TIP]
> Если вы используете Visual Studio:
>
> - Многие правила анализатора связаны с *исправлениями кода*, которые можно применить для устранения проблемы. Исправления кода показаны в меню со значком лампочки.
> - Вы можете включить или отключить анализ кода, щелкнув правой кнопкой мыши проект в Обозревателе решений и выбрав **Свойства** > **Анализ кода** > **Enable .NET analyzers** (Включить анализаторы .NET).

### <a name="enabled-rules"></a>Включенные правила

По умолчанию в .NET 5.0 включены указанные ниже правила.

| ИД диагностики | Категория | Уровень серьезности | Описание: |
| - | - | - | - |
| [CA1416](/visualstudio/code-quality/ca1416) | Совместимость | Предупреждение | Анализатор совместимости платформ |
| [CA1417](/visualstudio/code-quality/ca1417) | Совместимость | Предупреждение | Не используйте `OutAttribute` в параметрах строки для P/Invokes |
| [CA1831](/visualstudio/code-quality/ca1831) | Производительность | Предупреждение | При необходимости используйте `AsSpan` вместо индексаторов на основе диапазона для строки |
| [CA2013](/visualstudio/code-quality/ca2013) | надежность; | Предупреждение | Не используйте `ReferenceEquals` с типами значений |
| [CA2014](/visualstudio/code-quality/ca2014) | надежность; | Предупреждение | Не используйте `stackalloc` в циклах |
| [CA2015](/visualstudio/code-quality/ca2015) | надежность; | Предупреждение | Не определяйте методы завершения для типов, производных от <xref:System.Buffers.MemoryManager%601> |
| [CA2200](/visualstudio/code-quality/ca2200) | Использование | Предупреждение | Повторно порождайте исключения для сохранения сведений стека
| [CA2247](/visualstudio/code-quality/ca2247) | Использование | Предупреждение | Аргумент, передаваемый конструктору TaskCompletionSource, должен иметь значение перечисления <xref:System.Threading.Tasks.TaskCreationOptions> вместо <xref:System.Threading.Tasks.TaskContinuationOptions> |

Вы можете изменить важность этих правил, чтобы отключить их или повысить их до уровня ошибок. Вы также можете [включить большее количество правил](#enable-additional-rules).

- Список правил, включенных в каждую версию пакета SDK для .NET, см. на странице[Выпуски анализатора](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).
- Список всех правил качества кода см. на [этой странице](quality-rules/index.md).

### <a name="enable-additional-rules"></a>Включение дополнительных правил

*Режим анализа* относится к предопределенной конфигурации анализа кода, в которой правила отключены или включены (несколько или все). В режиме анализа по умолчанию лишь небольшое количество правил [включено в качестве предупреждений сборки](#enabled-rules). Вы можете изменить режим анализа для своего проекта, установив свойство [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) в файле проекта. Допустимые значения:

| Значение | Описание |
| - | - |
| `AllDisabledByDefault` | Это самый консервативный режим. По умолчанию все правила отключены. Можно выборочно [принять](configuration-options.md) отдельные правила, чтобы включить их.<br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | Это самый агрессивный режим. Все правила включены как предупреждения сборки. Вы можете выборочно [отказаться от](configuration-options.md) отдельных правил, чтобы отключить их.<br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | Режим по умолчанию, в котором одни правила включены как предупреждения, другие — только как предложения IDE Visual Studio с соответствующими исправлениями кода, а третьи — полностью отключены. Вы можете выборочно [принять отдельные правила или отключить их](configuration-options.md).<br /><br />`<AnalysisMode>Default</AnalysisMode>` |

Чтобы узнать уровень важности по умолчанию для каждого доступного правила и определить, включено ли правило в режиме анализа по умолчанию, см. [полный список правил](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).

### <a name="treat-warnings-as-errors"></a>Рассматривать предупреждения как ошибки

Если вы используете флажок `-warnaserror` при сборке проектов, все предупреждения анализа кода также обрабатываются как ошибки. Если вы не хотите, чтобы предупреждения о качестве кода (CAxxxx) рассматривались как ошибки при наличии `-warnaserror`, вы можете установить для свойства MSBuild `CodeAnalysisTreatWarningsAsErrors` значение `false` в файле проекта.

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

Предупреждения анализа кода будут отображаться по-прежнему, но при этом они не будут нарушать сборку.

### <a name="latest-updates"></a>Последние обновления

По умолчанию вы будете получать последние правила анализа кода и стандартные уровни важности правил при обновлении до более новых версий пакета SDK для .NET. Если такое поведение вас не устраивает, например, если вы хотите убедиться, что новые правила включены или отключены, вы можете переопределить его одним из следующих способов:

- Задайте для свойства MSBuild `AnalysisLevel` определенное значение, чтобы заблокировать предупреждения для этого набора. При обновлении до более новой версии пакета SDK вы по-прежнему будете получать исправления ошибок для этих предупреждений, однако новые предупреждения не будут включены, а существующие не будут отключены. Например, чтобы заблокировать набор правил для предупреждений, поставляемых с версией 5.0 пакета SDK для .NET, добавьте приведенную ниже запись в файл проекта.

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > Значение по умолчанию для свойства `AnalysisLevel` — `latest`. Это означает, что вы всегда получаете последние правила анализа кода при переходе к использованию более новых версий пакета SDK для .NET.

  Дополнительные сведения и список возможных значений см. на странице [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel).

- Установите [пакет NuGet Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers), чтобы отделить обновления правил от обновлений пакета SDK для .NET. Для проектов, предназначенных для .NET 5+, при установке пакета отключаются встроенные анализаторы SDK. Вы получите предупреждение о сборке, если пакет SDK содержит более новую версию сборки анализатора, чем пакет NuGet. Чтобы отключить предупреждение, установите для свойства `_SkipUpgradeNetAnalyzersNuGetWarning` значение `true`.

  > [!NOTE]
  > При установке пакета NuGet Microsoft.CodeAnalysis.NetAnalyzers не нужно добавлять свойство [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) в файл проекта или в файл *Directory.Build.props*. После установки пакета NuGet и задания для свойства `EnableNETAnalyzers` значения `true` создастся предупреждение сборки.

## <a name="code-style-analysis"></a>Анализ стиля кода

Правила *анализа стиля кода* (IDExxxx) позволяют определять и поддерживать согласованный стиль кода в базе кода. Параметры включения по умолчанию:

- Сборка из командной строки: анализ стиля кода по умолчанию отключен для всех проектов .NET при сборке из командной строки.

  Начиная с .NET 5.0, вы можете [включить анализ стиля кода при сборке](#enable-on-build) как в командной строке, так и внутри Visual Studio. Нарушения стиля кода отображаются в виде предупреждений или ошибок с префиксом IDE. Это позволяет вам применять согласованные стили кода во время сборки.

- Visual Studio: анализ стиля кода включен по умолчанию для всех проектов .NET внутри Visual Studio в виде [быстрых действий по рефакторингу кода](/visualstudio/ide/code-generation-in-visual-studio).

Полный список правил анализа стиля кода см. на [этой странице](style-rules/index.md).

### <a name="enable-on-build"></a>Включение при сборке

С помощью пакета SDK для .NET 5.0 и более поздних версий вы можете включить анализ стиля кода при сборке из командной строки и в Visual Studio. (Однако по соображениям производительности [некоторые правила стиля кода](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95) по-прежнему будут применяться только в IDE Visual Studio.)

Выполните следующие действия, чтобы включить анализ стиля кода при сборке:

1. Установите для свойства MSBuild [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) значение `true`.

1. В файле *.editorconfig* [настройте](configuration-options.md) каждое правило стиля кода с префиксом IDE, которое вы хотите запускать при сборке как предупреждение или ошибку. Пример.

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   Кроме того, вы можете настроить всю категорию как предупреждение или ошибку по умолчанию, а затем выборочно отключить правила в этой категории, которые не нужно запускать при сборке. Пример.

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

> [!NOTE]
> Функция анализа стиля кода является экспериментальной и может отличаться в версиях .NET 5 и .NET 6.

## <a name="suppress-a-warning"></a>Отключение предупреждений

Один из способов пропустить нарушение правила — установить для параметра важности этого идентификатора правила значение `none` в файле EditorConfig. Пример.

```ini
dotnet_diagnostic.CA1822.severity = none
```

Дополнительные сведения и другие способы отключения предупреждений см. на [этой странице](suppress-warnings.md).

## <a name="third-party-analyzers"></a>Сторонние анализаторы

Помимо официальных анализаторов .NET, вы также можете установить сторонние анализаторы, такие как [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/) и [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).

## <a name="see-also"></a>См. также раздел

- [Справочник по правилам анализа качества кода](quality-rules/index.md)
- [Справочник по правилам анализа стиля кода](style-rules/index.md)
- [Анализ кода в Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview)
- [Пакет SDK для .NET Compiler Platform](../../csharp/roslyn-sdk/index.md)
- [Учебник. Создание средства для анализа и исправления кода](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
