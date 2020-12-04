---
title: Критическое изменение. CA1417. OutAttribute в строковом параметре для P/Invoke
description: Сведения о критическом изменении в .NET 5.0, вызванном включением правила анализа кода CA1417.
ms.date: 09/29/2020
ms.openlocfilehash: 3316d07108ec7f9da985494413336cba6d560dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759589"
---
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a><span data-ttu-id="adbc6-103">Предупреждение CA1417: OutAttribute в строковом параметре для P/Invoke</span><span class="sxs-lookup"><span data-stu-id="adbc6-103">Warning CA1417: OutAttribute on string parameter for P/Invoke</span></span>

<span data-ttu-id="adbc6-104">Правило [CA1417](/visualstudio/code-quality/ca1417) анализатора кода .NET включено по умолчанию начиная с .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="adbc6-104">.NET code analyzer rule [CA1417](/visualstudio/code-quality/ca1417) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="adbc6-105">Оно создает предупреждение сборки для любого определения метода [вызова неуправляемого кода (P/Invoke)](../../../../standard/native-interop/pinvoke.md), в которых параметр <xref:System.String> передается по значению и отмечается с помощью <xref:System.Runtime.InteropServices.OutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="adbc6-105">It produces a build warning for any [Platform Invoke (P/Invoke)](../../../../standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is passed by value and marked with <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

## <a name="change-description"></a><span data-ttu-id="adbc6-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="adbc6-106">Change description</span></span>

<span data-ttu-id="adbc6-107">Начиная с .NET 5.0, пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="adbc6-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="adbc6-108">Некоторые из этих правил включены по умолчанию, включая [CA1417](/visualstudio/code-quality/ca1417).</span><span class="sxs-lookup"><span data-stu-id="adbc6-108">Several of these rules are enabled, by default, including [CA1417](/visualstudio/code-quality/ca1417).</span></span> <span data-ttu-id="adbc6-109">Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.</span><span class="sxs-lookup"><span data-stu-id="adbc6-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="adbc6-110">Флаги правила CA1417 определения методов [P/Invoke](../../../../standard/native-interop/pinvoke.md), в которых параметр <xref:System.String> отмечен атрибутом <xref:System.Runtime.InteropServices.OutAttribute> и передается по значению.</span><span class="sxs-lookup"><span data-stu-id="adbc6-110">Rule CA1417 flags [P/Invoke](../../../../standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is marked with the <xref:System.Runtime.InteropServices.OutAttribute> attribute and is passed by value.</span></span> <span data-ttu-id="adbc6-111">Пример:</span><span class="sxs-lookup"><span data-stu-id="adbc6-111">For example:</span></span>

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

<span data-ttu-id="adbc6-112">Среда выполнения .NET поддерживает таблицу, называемую пулом интернирования, которая содержит одну ссылку на каждую уникальную строку литерала в программе.</span><span class="sxs-lookup"><span data-stu-id="adbc6-112">The .NET runtime maintains a table, called the intern pool, that contains a single reference to each unique literal string in a program.</span></span> <span data-ttu-id="adbc6-113">Если интернированная строка, помеченная <xref:System.Runtime.InteropServices.OutAttribute>, передается по значению в метод P/Invoke, среду выполнения можно дестабилизировать.</span><span class="sxs-lookup"><span data-stu-id="adbc6-113">If an interned string marked with <xref:System.Runtime.InteropServices.OutAttribute> is passed by value to a P/Invoke method, the runtime can be destabilized.</span></span> <span data-ttu-id="adbc6-114">Дополнительные сведения об интернировании строк см. в разделе примечаний для <xref:System.String.Intern(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="adbc6-114">For more information about string interning, see the remarks for <xref:System.String.Intern(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="adbc6-115">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="adbc6-115">Version introduced</span></span>

<span data-ttu-id="adbc6-116">5.0</span><span class="sxs-lookup"><span data-stu-id="adbc6-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="adbc6-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="adbc6-117">Recommended action</span></span>

- <span data-ttu-id="adbc6-118">Если необходимо выполнить маршалирование измененных строковых данных обратно в вызывающий объект, передайте строку по ссылке.</span><span class="sxs-lookup"><span data-stu-id="adbc6-118">If you need to marshal modified string data back to the caller, pass the string by reference instead.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- <span data-ttu-id="adbc6-119">Если вам не нужно маршалировать измененные строковые данные обратно вызывающему объекту, просто удалите <xref:System.Runtime.InteropServices.OutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="adbc6-119">If you don't need to marshal modified string data back to the caller, simply remove the <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  <span data-ttu-id="adbc6-120">Дополнительные сведения в разделе [CA1417](/visualstudio/code-quality/ca1417).</span><span class="sxs-lookup"><span data-stu-id="adbc6-120">For more information, see [CA1417](/visualstudio/code-quality/ca1417).</span></span>

- <span data-ttu-id="adbc6-121">Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="adbc6-121">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="adbc6-122">Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="adbc6-122">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="adbc6-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="adbc6-123">Affected APIs</span></span>

<span data-ttu-id="adbc6-124">Невозможно обнаружить с помощью анализа API.</span><span class="sxs-lookup"><span data-stu-id="adbc6-124">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
