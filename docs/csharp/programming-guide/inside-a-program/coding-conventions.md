---
title: Руководство по программированию на C#. Соглашения о написании кода на C#
description: Узнайте о соглашениях о написании кода в C#. Соглашения о написании кода помогают сделать код единообразным, а также упрощают его копирование, изменение и обслуживание.
ms.date: 03/31/2021
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.openlocfilehash: 019bf02ea3cdfec2c4ae0d73b5b375781c5fcd9a
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231327"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="cdc45-104">Соглашения о написании кода на C# (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="cdc45-104">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="cdc45-105">Соглашения о написании кода предназначены для реализации следующих целей.</span><span class="sxs-lookup"><span data-stu-id="cdc45-105">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="cdc45-106">Создание согласованного вида кода, позволяющего читателям сосредоточиться на содержимом, а не на структуре.</span><span class="sxs-lookup"><span data-stu-id="cdc45-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="cdc45-107">Предоставление читателям возможности делать предположения, основанные на опыте, и поэтому быстрее понимать код.</span><span class="sxs-lookup"><span data-stu-id="cdc45-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="cdc45-108">Упрощение процессов копирования, изменения и обслуживания кода.</span><span class="sxs-lookup"><span data-stu-id="cdc45-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="cdc45-109">Предоставление лучших методик C#.</span><span class="sxs-lookup"><span data-stu-id="cdc45-109">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="cdc45-110">Майкрософт использует приведенные в этой статье рекомендации для разработки примеров и документации.</span><span class="sxs-lookup"><span data-stu-id="cdc45-110">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="cdc45-111">Соглашения об именах</span><span class="sxs-lookup"><span data-stu-id="cdc45-111">Naming conventions</span></span>  
  
- <span data-ttu-id="cdc45-112">В коротких примерах, где нет [директив using](../../language-reference/keywords/using-directive.md), рекомендуется использовать полные указания для пространства имен.</span><span class="sxs-lookup"><span data-stu-id="cdc45-112">In short examples that don't include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="cdc45-113">Если известно, что пространство имен импортируется в проект по умолчанию, вам не нужно указывать полные имена из этого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="cdc45-113">If you know that a namespace is imported by default in a project, you don't have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="cdc45-114">Полные имена, если они слишком длинные для одной строки, можно разбить после точки (.), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="cdc45-114">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet1":::

- <span data-ttu-id="cdc45-115">Вам не нужно изменять имена объектов, созданных с помощью инструментов разработки Visual Studio, чтобы привести их в соответствие с другими рекомендациями.</span><span class="sxs-lookup"><span data-stu-id="cdc45-115">You don't have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="cdc45-116">Соглашения о макете</span><span class="sxs-lookup"><span data-stu-id="cdc45-116">Layout conventions</span></span>  

<span data-ttu-id="cdc45-117">Чтобы выделить структуру кода и облегчить чтение кода, в хорошем макете используется форматирование.</span><span class="sxs-lookup"><span data-stu-id="cdc45-117">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="cdc45-118">Примеры и образцы корпорации Майкрософт соответствуют следующим соглашениям.</span><span class="sxs-lookup"><span data-stu-id="cdc45-118">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="cdc45-119">Использование параметров редактора кода по умолчанию (логичные отступы, отступы по четыре символа, использование пробелов для табуляции).</span><span class="sxs-lookup"><span data-stu-id="cdc45-119">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="cdc45-120">Дополнительные сведения см. в разделе ["Параметры", "Текстовый редактор", C#, "Форматирование"](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="cdc45-120">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="cdc45-121">Запись только одного оператора в строке.</span><span class="sxs-lookup"><span data-stu-id="cdc45-121">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="cdc45-122">Запись только одного объявления в строке.</span><span class="sxs-lookup"><span data-stu-id="cdc45-122">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="cdc45-123">Если отступ для дополнительных строк не ставится автоматически, необходимо сделать для них отступ на одну позицию табуляции (четыре пробела).</span><span class="sxs-lookup"><span data-stu-id="cdc45-123">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="cdc45-124">Добавление по крайней мере одной пустой строки между определениями методов и свойств.</span><span class="sxs-lookup"><span data-stu-id="cdc45-124">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="cdc45-125">Использование скобок для ясности предложений в выражениях, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="cdc45-125">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet2":::

## <a name="commenting-conventions"></a><span data-ttu-id="cdc45-126">Соглашения о комментариях</span><span class="sxs-lookup"><span data-stu-id="cdc45-126">Commenting conventions</span></span>  
  
- <span data-ttu-id="cdc45-127">Комментарий размещается на отдельной строке, а не в конце строки кода.</span><span class="sxs-lookup"><span data-stu-id="cdc45-127">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="cdc45-128">Текст комментария начинается с заглавной буквы.</span><span class="sxs-lookup"><span data-stu-id="cdc45-128">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="cdc45-129">Текст комментария завершается точкой.</span><span class="sxs-lookup"><span data-stu-id="cdc45-129">End comment text with a period.</span></span>  
  
- <span data-ttu-id="cdc45-130">Между разделителем комментария (/ /) и текстом комментария вставляется один пробел, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="cdc45-130">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet3":::

- <span data-ttu-id="cdc45-131">Не создавайте форматированные блоки из звездочек вокруг комментариев.</span><span class="sxs-lookup"><span data-stu-id="cdc45-131">Don't create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="cdc45-132">Рекомендации по использованию языка</span><span class="sxs-lookup"><span data-stu-id="cdc45-132">Language guidelines</span></span>  

<span data-ttu-id="cdc45-133">В следующих подразделах описаны методики, которыми руководствуется команда C# для подготовки примеров и образцов кода.</span><span class="sxs-lookup"><span data-stu-id="cdc45-133">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="cdc45-134">Строковый тип данных</span><span class="sxs-lookup"><span data-stu-id="cdc45-134">String data type</span></span>  
  
- <span data-ttu-id="cdc45-135">Для сцепления коротких строк рекомендуется использовать [интерполяцию строк](../../language-reference/tokens/interpolated.md), как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="cdc45-135">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet6":::

- <span data-ttu-id="cdc45-136">Для добавления строк в циклах, особенно при работе с текстами больших размеров, используйте объект <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="cdc45-136">To append strings in loops, especially when you're working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="cdc45-137">Неявно типизированные локальные переменные</span><span class="sxs-lookup"><span data-stu-id="cdc45-137">Implicitly typed local variables</span></span>  
  
- <span data-ttu-id="cdc45-138">В случаях, когда тип переменной понятен из правой части назначения или когда точный тип не важен, рекомендуется использовать [неявное типизирование](../classes-and-structs/implicitly-typed-local-variables.md) для локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="cdc45-138">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet8":::
  
- <span data-ttu-id="cdc45-139">Если тип в правой части назначения не является очевидным, не рекомендуется использовать [var](../../language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="cdc45-139">Don't use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span> <span data-ttu-id="cdc45-140">Не полагайтесь на то, что имя метода предоставляет информацию о типе.</span><span class="sxs-lookup"><span data-stu-id="cdc45-140">Don't assume the type is clear from a method name.</span></span> <span data-ttu-id="cdc45-141">Тип переменной можно считать очевидным, если используется оператор `new` или явное приведение типа.</span><span class="sxs-lookup"><span data-stu-id="cdc45-141">A variable type is considered clear if it's a `new` operator or an explicit cast.</span></span>
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet9":::

- <span data-ttu-id="cdc45-142">Не полагайтесь на имя переменной при указании ее типа.</span><span class="sxs-lookup"><span data-stu-id="cdc45-142">Don't rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="cdc45-143">Имя может быть неверным.</span><span class="sxs-lookup"><span data-stu-id="cdc45-143">It might not be correct.</span></span> <span data-ttu-id="cdc45-144">В следующем примере имя переменной `inputInt` вводит в заблуждение.</span><span class="sxs-lookup"><span data-stu-id="cdc45-144">In the following example, the variable name `inputInt` is misleading.</span></span> <span data-ttu-id="cdc45-145">На самом деле это строка.</span><span class="sxs-lookup"><span data-stu-id="cdc45-145">It's a string.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet10":::

- <span data-ttu-id="cdc45-146">Рекомендуется избегать использования `var` вместо [dynamic](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="cdc45-146">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span> <span data-ttu-id="cdc45-147">Используйте `dynamic`, если требуется определение типа во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="cdc45-147">Use `dynamic` when you want run-time type inference.</span></span> <span data-ttu-id="cdc45-148">Дополнительные сведения см. в статье [Использование типа dynamic (руководство по программированию на C#)](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="cdc45-148">For more information, see [Using type dynamic (C# Programming Guide)](../types/using-type-dynamic.md).</span></span>
  
- <span data-ttu-id="cdc45-149">Рекомендуется использовать неявное типизирование для определения типа переменной цикла в циклах [for](../../language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="cdc45-149">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
  <span data-ttu-id="cdc45-150">В следующем примере неявное типизирование используется в операторе `for`.</span><span class="sxs-lookup"><span data-stu-id="cdc45-150">The following example uses implicit typing in a `for` statement.</span></span>  

    :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

- <span data-ttu-id="cdc45-151">Не используйте неявную типизацию для определения типа переменной цикла в циклах [foreach](../../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="cdc45-151">Don't use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

  <span data-ttu-id="cdc45-152">В следующем примере явное типизирование используется в операторе `foreach`.</span><span class="sxs-lookup"><span data-stu-id="cdc45-152">The following example uses explicit typing in a `foreach` statement.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet12":::

  > [!NOTE]
  > <span data-ttu-id="cdc45-153">Следите за тем, чтобы случайно не изменить тип элемента итерируемой коллекции.</span><span class="sxs-lookup"><span data-stu-id="cdc45-153">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="cdc45-154">Например, можно легко переключиться с <xref:System.Linq.IQueryable?displayProperty=nameWithType> на <xref:System.Collections.IEnumerable?displayProperty=nameWithType> в инструкции `foreach`, изменяющей выполнение запроса.</span><span class="sxs-lookup"><span data-stu-id="cdc45-154">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-types"></a><span data-ttu-id="cdc45-155">Беззнаковые типы данных</span><span class="sxs-lookup"><span data-stu-id="cdc45-155">Unsigned data types</span></span>  
  
<span data-ttu-id="cdc45-156">Как правило, рекомендуется использовать `int` вместо беззнаковых типов.</span><span class="sxs-lookup"><span data-stu-id="cdc45-156">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="cdc45-157">В C# обычно используется `int`. Использование `int` упрощает взаимодействие с другими библиотеками.</span><span class="sxs-lookup"><span data-stu-id="cdc45-157">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="cdc45-158">Массивы</span><span class="sxs-lookup"><span data-stu-id="cdc45-158">Arrays</span></span>  
  
<span data-ttu-id="cdc45-159">При инициализации массивов в строке объявления рекомендуется использовать сокращенный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="cdc45-159">Use the concise syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="cdc45-160">В следующем примере видно, что `var` нельзя использовать вместо `string[]`.</span><span class="sxs-lookup"><span data-stu-id="cdc45-160">In the following example, note that you can't use `var` instead of `string[]`.</span></span>  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13a":::

<span data-ttu-id="cdc45-161">Если экземпляр создается явно, можно использовать `var`.</span><span class="sxs-lookup"><span data-stu-id="cdc45-161">If you use explicit instantiation, you can use `var`.</span></span>

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13b":::

<span data-ttu-id="cdc45-162">Если вы указали размер массива, нужно поочередно инициализировать все элементы.</span><span class="sxs-lookup"><span data-stu-id="cdc45-162">If you specify an array size, you have to initialize the elements one at a time.</span></span>
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13c":::
  
### <a name="delegates"></a><span data-ttu-id="cdc45-163">Делегаты</span><span class="sxs-lookup"><span data-stu-id="cdc45-163">Delegates</span></span>  
  
<span data-ttu-id="cdc45-164">Используйте [`Func<>` и `Action<>`](../../../standard/delegates-lambdas.md) вместо определения типов делегатов.</span><span class="sxs-lookup"><span data-stu-id="cdc45-164">Use [`Func<>` and `Action<>`](../../../standard/delegates-lambdas.md) instead of defining delegate types.</span></span> <span data-ttu-id="cdc45-165">В классе определите метод делегата.</span><span class="sxs-lookup"><span data-stu-id="cdc45-165">In a class, define the delegate method.</span></span>  

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14a":::

<span data-ttu-id="cdc45-166">Вызывайте метод с помощью сигнатуры, которую определяет делегат `Func<>` или `Action<>`.</span><span class="sxs-lookup"><span data-stu-id="cdc45-166">Call the method using the signature defined by the `Func<>` or `Action<>` delegate.</span></span>

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15a":::

<span data-ttu-id="cdc45-167">Если вы создаете экземпляры типа делегата, используйте сокращенный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="cdc45-167">If you create instances of a delegate type, use the concise syntax.</span></span> <span data-ttu-id="cdc45-168">В классе определите тип делегата и метод с соответствующей сигнатурой.</span><span class="sxs-lookup"><span data-stu-id="cdc45-168">In a class, define the delegate type and a method that has a matching signature.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14b":::

<span data-ttu-id="cdc45-169">Создайте экземпляр типа делегата и вызовите его.</span><span class="sxs-lookup"><span data-stu-id="cdc45-169">Create an instance of the delegate type and call it.</span></span> <span data-ttu-id="cdc45-170">В следующем объявлении используется сокращенный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="cdc45-170">The following declaration shows the condensed syntax.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15b":::

<span data-ttu-id="cdc45-171">В следующем объявлении используется полный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="cdc45-171">The following declaration uses the full syntax.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15c":::

### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="cdc45-172">Операторы `try`-`catch` и `using` при обработке исключений</span><span class="sxs-lookup"><span data-stu-id="cdc45-172">`try`-`catch` and `using` statements in exception handling</span></span>  
  
- <span data-ttu-id="cdc45-173">Рекомендуется использовать оператор [try-catch](../../language-reference/keywords/try-catch.md) для обработки большей части исключений.</span><span class="sxs-lookup"><span data-stu-id="cdc45-173">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet16":::

- <span data-ttu-id="cdc45-174">Использование [оператора C# using](../../language-reference/keywords/using-statement.md) упрощает код.</span><span class="sxs-lookup"><span data-stu-id="cdc45-174">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="cdc45-175">При наличии оператора [try-finally](../../language-reference/keywords/try-finally.md), код которого в блоке `finally` содержит только вызов метода <xref:System.IDisposable.Dispose%2A>, вместо него рекомендуется использовать оператор `using`.</span><span class="sxs-lookup"><span data-stu-id="cdc45-175">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>

  <span data-ttu-id="cdc45-176">В следующем примере оператор `try`-`finally` вызывает `Dispose` только в блоке `finally`.</span><span class="sxs-lookup"><span data-stu-id="cdc45-176">In the following example, the `try`-`finally` statement only calls `Dispose` in the `finally` block.</span></span>
  
   :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17a":::

  <span data-ttu-id="cdc45-177">То же самое можно сделать с помощью оператора `using`.</span><span class="sxs-lookup"><span data-stu-id="cdc45-177">You can do the same thing with a `using` statement.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17b":::

  <span data-ttu-id="cdc45-178">В C# 8 и более поздних версиях используйте новый [синтаксис `using` ](../../language-reference/keywords/using-statement.md), в котором не требуются скобки:</span><span class="sxs-lookup"><span data-stu-id="cdc45-178">In C# 8 and later versions, use the new [`using` syntax](../../language-reference/keywords/using-statement.md) that doesn't require braces:</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17c":::

### <a name="-and--operators"></a><span data-ttu-id="cdc45-179">Операторы `&&` и `||`</span><span class="sxs-lookup"><span data-stu-id="cdc45-179">`&&` and `||` operators</span></span>  
  
<span data-ttu-id="cdc45-180">Чтобы избежать возникновения исключений и увеличить производительность за счет пропуска необязательных сравнений, используйте [`&&`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) вместо [`&`](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) и [`||`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) вместо [`|`](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) при выполнении сравнений, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="cdc45-180">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [`&&`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [`&`](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [`||`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [`|`](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet18":::

<span data-ttu-id="cdc45-181">Если делитель равен нулю, второе условие в операторе `if` вызовет ошибку времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="cdc45-181">If the divisor is 0, the second clause in the `if` statement would cause a run-time error.</span></span> <span data-ttu-id="cdc45-182">При этом оператор && сразу прекращает выполнение, если первое выражение ложно.</span><span class="sxs-lookup"><span data-stu-id="cdc45-182">But the && operator short-circuits when the first expression is false.</span></span> <span data-ttu-id="cdc45-183">Это означает, что второе выражение не будет вычисляться.</span><span class="sxs-lookup"><span data-stu-id="cdc45-183">That is, it doesn't evaluate the second expression.</span></span> <span data-ttu-id="cdc45-184">Оператор & всегда вычисляет оба выражения, и если значение `divisor` равно 0, возникает ошибка времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="cdc45-184">The & operator would evaluate both, resulting in a run-time error when `divisor` is 0.</span></span>
  
### <a name="new-operator"></a><span data-ttu-id="cdc45-185">Оператор `new`</span><span class="sxs-lookup"><span data-stu-id="cdc45-185">`new` operator</span></span>  
  
- <span data-ttu-id="cdc45-186">Используйте одну из сокращенных форм создания экземпляров объектов, как показано в следующих объявлениях.</span><span class="sxs-lookup"><span data-stu-id="cdc45-186">Use one of the concise forms of object instantiation, as shown in the following declarations.</span></span> <span data-ttu-id="cdc45-187">Во втором примере используется синтаксис, который появился в версии C# 9.</span><span class="sxs-lookup"><span data-stu-id="cdc45-187">The second example shows syntax that is available starting in C# 9.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet19":::
  
  ```csharp
  ExampleClass instance2 = new();
  ```
  
  <span data-ttu-id="cdc45-188">Предыдущие объявления эквивалентны следующему объявлению.</span><span class="sxs-lookup"><span data-stu-id="cdc45-188">The preceding declarations are equivalent to the following declaration.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet20":::

- <span data-ttu-id="cdc45-189">Используйте инициализаторы объектов, чтобы упростить создание объектов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="cdc45-189">Use object initializers to simplify object creation, as shown in the following example.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21a":::

  <span data-ttu-id="cdc45-190">В следующем примере задаются точно такие же свойства, как и в предыдущем, но без использования инициализаторов.</span><span class="sxs-lookup"><span data-stu-id="cdc45-190">The following example sets the same properties as the preceding example but doesn't use initializers.</span></span>
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21b":::

### <a name="event-handling"></a><span data-ttu-id="cdc45-191">Обработка событий</span><span class="sxs-lookup"><span data-stu-id="cdc45-191">Event handling</span></span>  
  
<span data-ttu-id="cdc45-192">Если вы определяете обработчик событий, который не нужно удалять позже, используйте лямбда-выражение.</span><span class="sxs-lookup"><span data-stu-id="cdc45-192">If you're defining an event handler that you don't need to remove later, use a lambda expression.</span></span>  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet22":::

<span data-ttu-id="cdc45-193">Лямбда-выражение сокращает приведенное ниже традиционное определение.</span><span class="sxs-lookup"><span data-stu-id="cdc45-193">The lambda expression shortens the following traditional definition.</span></span>

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet23":::

### <a name="static-members"></a><span data-ttu-id="cdc45-194">Статические члены</span><span class="sxs-lookup"><span data-stu-id="cdc45-194">Static members</span></span>  
  
<span data-ttu-id="cdc45-195">Для вызова [статических](../../language-reference/keywords/static.md) членов следует использовать имя класса: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="cdc45-195">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="cdc45-196">В этом случае код становится более удобочитаемым за счет четкого доступа.</span><span class="sxs-lookup"><span data-stu-id="cdc45-196">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="cdc45-197">Не присваивайте статическому элементу, определенному в базовом классе, имя производного класса.</span><span class="sxs-lookup"><span data-stu-id="cdc45-197">Don't qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="cdc45-198">Во время компиляции кода его читаемость нарушается, и если добавить статический член с тем же именем в производный классе, код может быть поврежден.</span><span class="sxs-lookup"><span data-stu-id="cdc45-198">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="cdc45-199">Запросы LINQ</span><span class="sxs-lookup"><span data-stu-id="cdc45-199">LINQ queries</span></span>  
  
- <span data-ttu-id="cdc45-200">Используйте значимые имена для переменных запроса.</span><span class="sxs-lookup"><span data-stu-id="cdc45-200">Use meaningful names for query variables.</span></span> <span data-ttu-id="cdc45-201">В следующем примере используется `seattleCustomers` для клиентов, находящихся в Сиэтле.</span><span class="sxs-lookup"><span data-stu-id="cdc45-201">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- <span data-ttu-id="cdc45-202">Рекомендуется использовать псевдонимы для уверенности в том, что в именах свойств анонимных типов верно используются прописные буквы при помощи правил использования прописных и строчных букв языка Pascal.</span><span class="sxs-lookup"><span data-stu-id="cdc45-202">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet26":::

- <span data-ttu-id="cdc45-203">Переименуйте свойства, если имена свойств в результате могут быть неоднозначными.</span><span class="sxs-lookup"><span data-stu-id="cdc45-203">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="cdc45-204">Например, если запрос возвращает имя клиента и идентификатор распространителя, не оставляйте имена в виде `Name` и `ID`, а переименуйте их, чтобы было ясно, что `Name` — имя клиента и `ID` — идентификатор распространителя.</span><span class="sxs-lookup"><span data-stu-id="cdc45-204">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet27":::

- <span data-ttu-id="cdc45-205">Рекомендуется использовать неявное типизирование в объявлении переменных запроса и переменных диапазона.</span><span class="sxs-lookup"><span data-stu-id="cdc45-205">Use implicit typing in the declaration of query variables and range variables.</span></span>  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- <span data-ttu-id="cdc45-206">Выравнивайте предложения запроса под предложением [from](../../language-reference/keywords/from-clause.md), как показано в предыдущих примерах.</span><span class="sxs-lookup"><span data-stu-id="cdc45-206">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  

- <span data-ttu-id="cdc45-207">Чтобы гарантировать, что более поздние предложения запроса работают с ограниченным, отфильтрованным набором данных, используйте предложение [where](../../language-reference/keywords/where-clause.md) перед другими предложениями запроса.</span><span class="sxs-lookup"><span data-stu-id="cdc45-207">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet29":::

- <span data-ttu-id="cdc45-208">Используйте несколько предложений `from` для доступа к внутренним коллекциям вместо предложения [join](../../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cdc45-208">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="cdc45-209">Например, коллекция объектов `Student` может содержать коллекцию результатов тестирования.</span><span class="sxs-lookup"><span data-stu-id="cdc45-209">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="cdc45-210">При выполнении следующего запроса возвращаются результаты, превышающие 90 балов, а также фамилии учащихся, получивших такие оценки.</span><span class="sxs-lookup"><span data-stu-id="cdc45-210">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet30":::

## <a name="security"></a><span data-ttu-id="cdc45-211">Безопасность</span><span class="sxs-lookup"><span data-stu-id="cdc45-211">Security</span></span>  

<span data-ttu-id="cdc45-212">Следуйте указаниям, изложенным в [правилах написания безопасного кода](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="cdc45-212">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc45-213">См. также</span><span class="sxs-lookup"><span data-stu-id="cdc45-213">See also</span></span>

- [<span data-ttu-id="cdc45-214">Рекомендации по написанию кода среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="cdc45-214">.NET runtime coding guidelines</span></span>](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)
- [<span data-ttu-id="cdc45-215">Соглашения о написании кода в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cdc45-215">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="cdc45-216">Правила написания безопасного кода</span><span class="sxs-lookup"><span data-stu-id="cdc45-216">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
