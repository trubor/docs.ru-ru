---
title: 'Критическое изменение. Blazor: Незначащие пробелы удалены из компонентов во время компиляции'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Незначащие пробелы удалены из компонентов во время компиляции
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: d29171c43e587eba648de3f877e1cbb1c7156499
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498208"
---
# <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="20744-103">Blazor: Незначащие пробелы удалены из компонентов во время компиляции</span><span class="sxs-lookup"><span data-stu-id="20744-103">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="20744-104">Начиная с ASP.NET Core 5.0, предварительная версия 7, компилятор Razor пропускает незначащий пробел в компонентах Blazor (*RAZOR*-файлах) во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="20744-104">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="20744-105">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span><span class="sxs-lookup"><span data-stu-id="20744-105">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="20744-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="20744-106">Version introduced</span></span>

<span data-ttu-id="20744-107">5.0 (предварительная версия 7)</span><span class="sxs-lookup"><span data-stu-id="20744-107">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="20744-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="20744-108">Old behavior</span></span>

<span data-ttu-id="20744-109">В Blazor Server и Blazor WebAssembly версий 3.x символы пробела учитываются в исходном коде компонента.</span><span class="sxs-lookup"><span data-stu-id="20744-109">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="20744-110">Текстовые узлы, состоящие только из пробелов, отображаются в модели DOM браузера даже при отсутствии визуального эффекта.</span><span class="sxs-lookup"><span data-stu-id="20744-110">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="20744-111">Рассмотрим следующий код компонента Blazor:</span><span class="sxs-lookup"><span data-stu-id="20744-111">Consider the following Blazor component code:</span></span>

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

<span data-ttu-id="20744-112">В предыдущем примере отображаются два узла пробелов:</span><span class="sxs-lookup"><span data-stu-id="20744-112">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="20744-113">за пределами блока кода `@foreach`;</span><span class="sxs-lookup"><span data-stu-id="20744-113">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="20744-114">вокруг элемента `<li>`;</span><span class="sxs-lookup"><span data-stu-id="20744-114">Around the `<li>` element.</span></span>
* <span data-ttu-id="20744-115">вокруг выходных данных `@item.Text`.</span><span class="sxs-lookup"><span data-stu-id="20744-115">Around the `@item.Text` output.</span></span>

<span data-ttu-id="20744-116">Список, содержащий 100 элементов, формирует 402 узла пробелов.</span><span class="sxs-lookup"><span data-stu-id="20744-116">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="20744-117">Это более половины всех отображаемых узлов, хотя ни один из узлов пробелов не влияет на отображаемые выходные данные.</span><span class="sxs-lookup"><span data-stu-id="20744-117">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="20744-118">При отрисовке статического HTML для компонентов пробелы внутри тега не сохраняются.</span><span class="sxs-lookup"><span data-stu-id="20744-118">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="20744-119">Например, просмотрите исходный код следующего компонента:</span><span class="sxs-lookup"><span data-stu-id="20744-119">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="20744-120">Пробел не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="20744-120">Whitespace isn't preserved.</span></span> <span data-ttu-id="20744-121">Предварительно преобразованные для просмотра выходные данные имеют следующий вид:</span><span class="sxs-lookup"><span data-stu-id="20744-121">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

## <a name="new-behavior"></a><span data-ttu-id="20744-122">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="20744-122">New behavior</span></span>

<span data-ttu-id="20744-123">Если директива `@preservewhitespace` не используется со значением `true`, узлы пробелов удаляются в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="20744-123">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="20744-124">они находятся в начале или конце элемента;</span><span class="sxs-lookup"><span data-stu-id="20744-124">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="20744-125">они находятся в начале или конце параметра `RenderFragment`.</span><span class="sxs-lookup"><span data-stu-id="20744-125">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="20744-126">Например, дочернее содержимое передается другому компоненту.</span><span class="sxs-lookup"><span data-stu-id="20744-126">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="20744-127">они находятся в начале или конце блока кода C#, например `@if` и `@foreach`.</span><span class="sxs-lookup"><span data-stu-id="20744-127">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="20744-128">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="20744-128">Reason for change</span></span>

<span data-ttu-id="20744-129">Платформа Blazor в ASP.NET Core 5.0 предназначена для повышения производительности визуализации и сравнения.</span><span class="sxs-lookup"><span data-stu-id="20744-129">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="20744-130">Узлам дерева незначащих пробелов требовалось до 40 процентов времени отрисовки в тестах производительности.</span><span class="sxs-lookup"><span data-stu-id="20744-130">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="20744-131">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="20744-131">Recommended action</span></span>

<span data-ttu-id="20744-132">В большинстве случаев визуальный макет отображаемого компонента не затрагивается.</span><span class="sxs-lookup"><span data-stu-id="20744-132">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="20744-133">Однако при использовании правила CSS, такого как `white-space: pre`, удаление пробелов может повлиять на отображаемые выходные данные.</span><span class="sxs-lookup"><span data-stu-id="20744-133">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="20744-134">Чтобы отключить эту оптимизацию производительности и сохранить пробелы, выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="20744-134">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="20744-135">Добавьте директиву `@preservewhitespace true` в начало  *RAZOR*-файла, чтобы применить предпочтение к конкретному компоненту.</span><span class="sxs-lookup"><span data-stu-id="20744-135">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="20744-136">Добавьте директиву `@preservewhitespace true` внутрь файла *_Imports.razor*, чтобы применить предпочтение ко всему подкаталогу или проекту целиком.</span><span class="sxs-lookup"><span data-stu-id="20744-136">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="20744-137">В большинстве случаев никаких действий не требуется, так как приложения обычно продолжают работать в обычном режиме (но быстрее).</span><span class="sxs-lookup"><span data-stu-id="20744-137">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="20744-138">Если удаление пробелов приводит к возникновению проблем в конкретном компоненте, используйте `@preservewhitespace true` в этом компоненте, чтобы отключить эту оптимизацию.</span><span class="sxs-lookup"><span data-stu-id="20744-138">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="20744-139">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="20744-139">Affected APIs</span></span>

<span data-ttu-id="20744-140">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="20744-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
