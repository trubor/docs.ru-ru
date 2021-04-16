---
title: Файлы конфигурации для правил анализа кода
description: Сведения о различных файлах конфигурации для настройки правил анализа кода.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: b98fdd48f2373bd23fcd3273834860a60c682969
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "99216386"
---
# <a name="configuration-files-for-code-analysis-rules"></a>Файлы конфигурации для правил анализа кода

Для правил анализа кода доступно несколько [параметров конфигурации](configuration-options.md). Эти параметры указываются в виде пар "ключ-значение" в одном из следующих файлов конфигурации анализатора:

- Файл [EditorConfig](#editorconfig): параметры конфигурации на основе файлов или папок.
- Глобальный файл [AnalyzerConfig](#global-analyzerconfig): параметры конфигурации на уровне проекта. Полезно, когда некоторые файлы проекта находятся за пределами папки проекта.

## EditorConfig

Файлы [EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) используются для предоставления **параметров, которые применяются к конкретным исходным файлам или папкам**. Параметры размещаются под заголовками разделов, позволяя идентифицировать соответствующие файлы и папки. Добавьте запись для каждого правила, которое необходимо настроить, и разместите его в соответствующем разделе расширения имени файла, например `[*.cs]`.

```ini
[*.cs]
<option_name> = <option_value>
```

В приведенном выше примере `[*.cs]` — это заголовок раздела editorconfig для выбора всех файлов C# с расширением имени файла `.cs` в текущей папке, включая вложенные папки. Последующая запись, `<option_name> = <option_value>`, — это параметр анализатора, который будет применяться ко всем файлам C#.

Соглашения о файлах EditorConfig можно применять к папке, проекту или всему репозиторию, помещая файл в соответствующий каталог. Эти параметры применяются при выполнении анализа во время сборки, а также при редактировании кода в Visual Studio.

Если у вас уже есть файл *.editorconfig* для параметров редактора, таких как размер отступа или необходимость обрезать пробелы в конце, параметры конфигурации анализа кода можно поместить в тот же файл.

> [!TIP]
> Visual Studio предоставляет шаблон элемента *.editorconfig*, который упрощает добавление одного из этих файлов в проект. Дополнительные сведения см. в разделе [Добавление файла EditorConfig в проект](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).

### <a name="example"></a>Пример

Ниже приведен пример файла EditorConfig для настройки параметров и важности правила:

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a>Глобальный AnalyzerConfig

Начиная с пакета SDK для .NET 5 (который поддерживается в Visual Studio 2019 версии 16.8 и более поздних версиях) можно также настроить параметры анализатора с помощью глобальных файлов _AnalyzerConfig_. Эти файлы используются для предоставления **параметров, которые применяются ко всем исходным файлам в проекте**, независимо от их имен или путей к файлам.

В отличие от файлов [EditorConfig](#editorconfig), глобальные файлы конфигурации нельзя использовать для настройки параметров стиля редактора для IDE, таких как размер отступа или необходимость обрезки конечных пробелов. Вместо этого они предназначены исключительно для указания параметров конфигурации анализатора уровня проекта.

### <a name="format"></a>Формат

В отличие от файлов EditorConfig, которые должны иметь заголовки разделов, например `[*.cs]`, для обнаружения подходящих файлов и папок, глобальные файлы AnalyzerConfig не имеют заголовков разделов. Вместо этого им требуется запись верхнего уровня формы `is_global = true`, чтобы отличать их от обычных файлов EditorConfig. Это указывает, что все параметры в файле применяются ко всему проекту. Пример:

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a>Именование

В отличие от файлов EditorConfig, которые должны называться `.editorconfig`, глобальные файлы конфигурации необязательно должны иметь определенное имя или расширение. Однако если вы назовете эти файлы `.globalconfig`, они будут неявно применены ко всем проектам C# и Visual Basic в текущей папке, включая вложенные папки. В противном случае необходимо явно добавить элемент `GlobalAnalyzerConfigFiles` в файл проекта MSBuild:

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> Запись верхнего уровня, `is_global = true`, требуется, даже если файл называется `.globalconfig`.

### <a name="example"></a>Пример

Ниже приведен пример глобального файла AnalyzerConfig для настройки параметров и серьезности правил на уровне проекта:

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a>Приоритет

Как файлы EditorConfig, так и глобальные файлы AnalyzerConfig задают пару "ключ-значение" для каждого параметра. Конфликты возникают, когда имеется несколько записей с одинаковым ключом, но разными значениями.

### <a name="general-options"></a>Общие параметры

При возникновении конфликтов между параметрами для разрешения конфликтов используются следующие правила приоритета:

- Конфликтующие записи в одном файле конфигурации: выигрывает запись, которая появилась позже в файле. Это справедливо для конфликтующих записей в одном файле EditorConfig, равно как и в одном глобальном файле AnalyzerConfig.

- Конфликтующие записи в двух файлах EditorConfig: выигрывает запись в файле EditorConfig, который находится глубже в файловой системе и у которого, следовательно, длиннее путь к файлу.

- Конфликтующие записи в двух глобальных файлах AnalyzerConfig: выводится предупреждение компилятора, и обе записи игнорируются.

- Конфликтующие записи в файле EditorConfig и глобальном файле AnalyzerConfig: выигрывает запись в файле EditorConfig.

### <a name="severity-options"></a>Параметры серьезности

Вышеприведенные [общие правила приоритета](#general-options) применяются ко всем параметрам, указанным в файлах конфигурации. Для параметров [конфигурации уровня серьезности](configuration-options.md#severity-level) применяются следующие дополнительные правила приоритета:

- Параметры серьезности, указанные в командной строке как параметры компилятора (`/nowarn` или `/warnaserror`), всегда переопределяют параметры [конфигурации серьезности](configuration-options.md#severity-level), указанные в EditorConfig и глобальных файлах AnalyzerConfig.

- Параметры серьезности также можно указать с помощью файла [RuleSet](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules). Однако файлы ruleset устарели и заменены на EditorConfig и глобальные файлы AnalyzerConfig. Рекомендуется [преобразовывать файлы RuleSet в эквивалентный файл EditorConfig](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file). Приоритет для конфликтующих записей серьезности из файла ruleset и EditorConfig или глобальных файлов AnalyzerConfig _не определен_.

- Сведения о правилах приоритета для связанных параметров серьезности с различными ключами, например при указании различных уровней серьезности для одного правила и категории, к которой относится правило, см. в разделе [Параметры конфигурации для анализа кода](configuration-options.md#precedence).

## <a name="see-also"></a>См. также раздел

- [EditorConfig и общая проблема разработки AnalyzerConfig](https://github.com/dotnet/roslyn/issues/47707)
