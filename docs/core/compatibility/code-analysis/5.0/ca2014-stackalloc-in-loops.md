---
title: 'Критическое изменение. CA2014: не используйте stackalloc в циклах'
description: Сведения о критическом изменении в .NET 5, вызванном включением правила анализа кода CA2014.
ms.date: 09/03/2020
ms.openlocfilehash: ac17c8ee588576947e21618a55c0eea883aa37ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257782"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a>Предупреждение CA2014: не используйте stackalloc в циклах

Правило [CA2014](/visualstudio/code-quality/ca2014) анализатора кода .NET включено по умолчанию, начиная с .NET 5.0. Оно создает предупреждение сборки для любого кода C#, в котором используется выражение [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) внутри цикла.

## <a name="change-description"></a>Описание изменений

Начиная с .NET 5, пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md). Некоторые из этих правил включены по умолчанию, в том числе [CA2014](/visualstudio/code-quality/ca2014). Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.

Правило CA2014 ищет код C#, в котором выражение [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) используется внутри цикла. [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) выделяет память из текущего кадра стека. Память не освобождается до тех пор, пока не будет возвращен текущий вызов метода, что может привести к переполнению стека. Так как вы не можете перехватывать исключения переполнения стека, в таком случае работа приложения будет завершена.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Старайтесь не использовать [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) в циклах. Выделяйте блок памяти за пределами цикла и используйте его повторно внутри цикла. См. раздел [CA2014](/visualstudio/code-quality/ca2014).

- Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта. Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Затронутые API

Невозможно обнаружить с помощью анализа API.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
