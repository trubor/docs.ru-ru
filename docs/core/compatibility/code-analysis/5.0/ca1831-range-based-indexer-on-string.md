---
title: 'Критическое изменение. CA1831: используйте AsSpan вместо индексаторов на основе диапазона для строки'
description: Сведения о критическом изменении в .NET 5, вызванном включением правила анализа кода CA1831.
ms.date: 08/21/2020
ms.openlocfilehash: 1ed4e2bdde9c3d525f95963f316551909ac3de7c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257795"
---
# <a name="warning-ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a>Предупреждение CA1831: используйте AsSpan вместо индексаторов на основе диапазона для строки

Правило анализатора кода .NET [CA1831](/visualstudio/code-quality/ca1831) включено по умолчанию, начиная с .NET 5.0. Оно создает предупреждение сборки для любого кода, в котором для строки используется индексатор на основе <xref:System.Range>, но копирование не планировалось.

## <a name="change-description"></a>Описание изменений

Начиная с .NET 5 пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md). Некоторые из этих правил включены по умолчанию, включая [CA1831](/visualstudio/code-quality/ca1831). Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.

Правило CA1831 находит экземпляры, в которых для строки используется индексатор на основе <xref:System.Range>, но копирование не планировалось. Если индексатор на основе <xref:System.Range> используется непосредственно в строке для создания неявного приведения, то создается ненужная копия запрошенной части строки. Пример:

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

CA1831 предлагает использовать индексатор на основе <xref:System.Range> в *span* строки. Пример:

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Чтобы исправить код и избежать ненужных выделений, вызовите <xref:System.MemoryExtensions.AsSpan(System.String)> или <xref:System.MemoryExtensions.AsMemory(System.String)> перед использованием индексатора на основе <xref:System.Range>. Пример:

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- Если вы не хотите изменять код, можно отключить правило, задав серьезность `suggestion` или `none`. Дополнительные сведения см. в разделе [Настройка правил анализа кода](../../../../fundamentals/code-analysis/configuration-options.md).

- Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта. Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Range?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Range`

### Category

Code analysis

-->
