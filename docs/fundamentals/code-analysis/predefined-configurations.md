---
title: Предопределенные файлы конфигурации (анализ кода)
description: Сведения о том, как использовать предопределенные файлы EditorConfig и наборов правил для применения конкретных типов анализа кода.
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 748ab8a9ddfcfcadeb33da877769cedac901655a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876595"
---
# <a name="predefined-configuration-files"></a>Предопределенные файлы конфигурации

Предопределенные файлы EditorConfig и [наборов правил](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) позволяют быстро и легко включить конкретную категорию правил качества кода, например правил безопасности или разработки. Включая определенную категорию правил, вы сможете выявлять соответствующие проблемы и проверять условия. Чтобы использовать предопределенные файлы, установите пакет NuGet [Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) для анализатора.

[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) содержит предопределенные файлы EditorConfig и наборы правил для следующих категорий правил:

- Все правила
- Поток данных
- Конструирование
- Документация
- Глобализация
- Взаимодействие
- Удобство обслуживания
- Именование
- Производительность
- Перенесенные из FxCop
- надежность;
- Безопасность
- Использование

Для каждой из этих категорий правил предоставляется файл EditorConfig или набора правил, который позволяет выполнить следующее:

- включить все правила в категории (и отключить все остальные правила);
- указать для каждого правила уровень серьезности по умолчанию и состояние включения по умолчанию (и отключите все остальные правила).

> [!TIP]
> Для категории "Все правила" есть дополнительный файл EditorConfig или набора правил, который отключает все правила. Этот файл поможет вам быстро избавиться от всех предупреждений и ошибок анализатора в проекте.

## <a name="predefined-editorconfig-files"></a>Предопределенные файлы EditorConfig

Предопределенные файлы EditorConfig для пакета анализатора Microsoft.CodeAnalysis.NetAnalyzers размещены в подкаталоге *editorconfig* того каталога, где установлен пакет NuGet. Например, файл EditorConfig для включения всех правил безопасности находится в папке *editorconfig/SecurityRulesEnabled/.editorconfig*.

Скопируйте нужный файл с расширением *.editorconfig* в корневой каталог проекта.

## <a name="predefined-rule-sets"></a>Предопределенные наборы правил

Предопределенные файлы наборов правил для пакета анализатора Microsoft.CodeAnalysis.NetAnalyzers размещены в подкаталоге *rulesets* того каталога, где установлен пакет NuGet. Например, файл набора правил для включения всех правил безопасности находится в папке *rulesets/SecurityRulesEnabled.ruleset*. Скопируйте один или несколько наборов правил и вставьте их в каталог со своим проектом.

## <a name="see-also"></a>См. также раздел

- [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/main/docs/Analyzer%20Configuration.md)
- [Параметры правила стиля кода для .NET в EditorConfig](code-style-rule-options.md)
