---
title: 'Критическое изменение. CA2013: не используйте ReferenceEquals с типами значений'
description: Сведения о критическом изменении в .NET 5, вызванном включением правила анализа кода CA2013.
ms.date: 09/03/2020
ms.openlocfilehash: fc68d9a3af0d629dc39aba0091d32b1982d6f2c5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257769"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a>Предупреждение CA2013: не используйте ReferenceEquals с типами значений

Правило [CA2013](/visualstudio/code-quality/ca2013) анализатора кода .NET включено по умолчанию начиная с .NET 5.0. Оно создает предупреждение сборки для любого кода, где для сравнения одного или нескольких типов значений на предмет равенства используется <xref:System.Object.ReferenceEquals(System.Object,System.Object)>.

## <a name="change-description"></a>Описание изменений

Начиная с .NET 5 пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md). Некоторые из этих правил включены по умолчанию, в том числе [CA2013](/visualstudio/code-quality/ca2013). Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.

Правило CA2013 находит экземпляры, где для сравнения одного или нескольких типов значений на предмет равенства используется <xref:System.Object.ReferenceEquals(System.Object,System.Object)>. Сравнение типов значений на предмет равенства таким образом может привести к неверным результатам, так как значения упаковываются до их сравнения. <xref:System.Object.ReferenceEquals(System.Object,System.Object)> будет возвращать `false` даже в том случае, если сравниваемые значения представляют один и тот же экземпляр типа значения.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Измените код, чтобы использовать соответствующий оператор равенства, например `==`. Не следует отключать это предупреждение.

- Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта. Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->
