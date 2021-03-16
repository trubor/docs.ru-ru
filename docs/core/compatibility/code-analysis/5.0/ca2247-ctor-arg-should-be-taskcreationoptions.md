---
title: 'Критическое изменение. CA2247: аргумент для конструктора TaskCompletionSource должен соответствовать значению TaskCreationOptions'
description: Сведения о критическом изменении в .NET 5, вызванном включением правила анализа кода CA2247.
ms.date: 09/03/2020
ms.openlocfilehash: 6c7accaad312352a1448406f2bbf4189f3df1ee5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257704"
---
# <a name="warning-ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a>Предупреждение CA2247: аргумент для конструктора TaskCompletionSource должен соответствовать значению TaskCreationOptions

Правило [CA2247](/visualstudio/code-quality/ca2247) анализатора кода .NET включено по умолчанию, начиная с .NET 5.0. Оно создает предупреждение сборки для вызовов конструктора <xref:System.Threading.Tasks.TaskCompletionSource%601>, которые передают аргумент типа <xref:System.Threading.Tasks.TaskContinuationOptions>.

## <a name="change-description"></a>Описание изменений

Начиная с .NET 5 пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md). Некоторые из этих правил включены по умолчанию, в том числе [CA2247](/visualstudio/code-quality/ca2247). Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.

Правило CA2247 находит вызовы конструктора <xref:System.Threading.Tasks.TaskCompletionSource%601>, которые передают аргумент типа <xref:System.Threading.Tasks.TaskContinuationOptions>. Тип <xref:System.Threading.Tasks.TaskCompletionSource%601> имеет конструктор, принимающий значение <xref:System.Threading.Tasks.TaskCreationOptions>, и другой конструктор, принимающий <xref:System.Object>. Если вы случайно передадите значение <xref:System.Threading.Tasks.TaskContinuationOptions> вместо значения <xref:System.Threading.Tasks.TaskCreationOptions>, конструктор с параметром <xref:System.Object> будет вызван во время выполнения. Код будет компилироваться и выполняться, но поведение будет отличаться от ожидаемого.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Замените аргумент <xref:System.Threading.Tasks.TaskContinuationOptions> соответствующим значением <xref:System.Threading.Tasks.TaskCreationOptions>. Не отключайте это предупреждение, так как оно почти всегда выделяет ошибку в коде. См. раздел [CA2247](/visualstudio/code-quality/ca2247).

- Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта. Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

### Category

Code analysis

-->
