---
description: 'Дополнительные сведения: выражения C#'
title: Выражения C#
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: ce918bb96164643f1adbc73f749d2b5f88f4eb3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742814"
---
# <a name="c-expressions"></a><span data-ttu-id="2de84-103">Выражения C#</span><span class="sxs-lookup"><span data-stu-id="2de84-103">C# Expressions</span></span>

<span data-ttu-id="2de84-104">Начиная с платформа .NET Framework 4,5, выражения C# поддерживаются в Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="2de84-104">Starting with .NET Framework 4.5, C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="2de84-105">Новые проекты рабочих процессов C#, созданные в Visual Studio 2012, предназначенные для платформа .NET Framework 4,5, используют выражения C#, а проекты рабочих процессов Visual Basic используют выражения Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2de84-105">New C# workflow projects created in Visual Studio 2012 that target .NET Framework 4.5 use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="2de84-106">Существующие проекты рабочих процессов платформа .NET Framework 4, использующие выражения Visual Basic, могут быть перенесены в [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] независимо от языка проекта и поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="2de84-106">Existing .NET Framework 4 workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="2de84-107">В этом разделе приведены общие сведения о выражениях на языке C# в [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2de84-107">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>

## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="2de84-108">Выражения на языке C# в рабочих процессах</span><span class="sxs-lookup"><span data-stu-id="2de84-108">Using C# expressions in workflows</span></span>

- [<span data-ttu-id="2de84-109">Выражения на языке C# в конструкторе рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="2de84-109">Using C# expressions in the Workflow Designer</span></span>](csharp-expressions.md#WFDesigner)

  - [<span data-ttu-id="2de84-110">обратная совместимость;</span><span class="sxs-lookup"><span data-stu-id="2de84-110">Backwards compatibility</span></span>](csharp-expressions.md#BackwardCompat)

- [<span data-ttu-id="2de84-111">Выражения на языке C# в коде рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="2de84-111">Using C# expressions in code workflows</span></span>](csharp-expressions.md#CodeWorkflows)

- [<span data-ttu-id="2de84-112">Выражения на языке C# в рабочих процессах языка XAML</span><span class="sxs-lookup"><span data-stu-id="2de84-112">Using C# expressions in XAML workflows</span></span>](csharp-expressions.md#XamlWorkflows)

  - [<span data-ttu-id="2de84-113">Скомпилированные файлы Xaml</span><span class="sxs-lookup"><span data-stu-id="2de84-113">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

  - [<span data-ttu-id="2de84-114">Свободный XAML</span><span class="sxs-lookup"><span data-stu-id="2de84-114">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

- [<span data-ttu-id="2de84-115">Выражения на языке C# в службах рабочих процессов XAMLX</span><span class="sxs-lookup"><span data-stu-id="2de84-115">Using C# expressions in XAMLX workflow services</span></span>](csharp-expressions.md#WFServices)

### <a name="using-c-expressions-in-the-workflow-designer"></a><a name="WFDesigner"></a> <span data-ttu-id="2de84-116">Использование выражений C# в конструктор рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="2de84-116">Using C# expressions in the Workflow Designer</span></span>

<span data-ttu-id="2de84-117">Начиная с платформа .NET Framework 4,5, выражения C# поддерживаются в Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="2de84-117">Starting with .NET Framework 4.5, C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="2de84-118">Проекты рабочих процессов C#, созданные в Visual Studio 2012, предназначенные для платформа .NET Framework 4,5, используют выражения C#, а Visual Basic проекты рабочих процессов используют выражения Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2de84-118">C# workflow projects created in Visual Studio 2012 that target .NET Framework 4.5 use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="2de84-119">Чтобы указать нужное выражение C#, введите его в поле с надписью **введите выражение c#**.</span><span class="sxs-lookup"><span data-stu-id="2de84-119">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="2de84-120">Эта метка отображается в окне свойств при выборе действия в конструкторе или при работе в конструкторе рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="2de84-120">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="2de84-121">В следующем примере два действия `WriteLine` содержатся в `Sequence` внутри `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="2de84-121">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>

![Снимок экрана, на котором показано автоматически созданное действие последовательности.](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> <span data-ttu-id="2de84-123">Выражения C# поддерживаются только в Visual Studio и не поддерживаются в конструкторе рабочих процессов, размещенном повторно.</span><span class="sxs-lookup"><span data-stu-id="2de84-123">C# expressions are supported only in Visual Studio, and are not supported in the re-hosted workflow designer.</span></span> <span data-ttu-id="2de84-124">Дополнительные сведения о новых функциях WF45, поддерживаемых в повторно размещенном конструкторе, см. в разделе [Поддержка новых функций Workflow Foundation 4,5 в](wf-features-in-the-rehosted-workflow-designer.md)переразмещенной конструктор рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="2de84-124">For more information about new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](wf-features-in-the-rehosted-workflow-designer.md).</span></span>

#### <a name="backwards-compatibility"></a><a name="BackwardCompat"></a> <span data-ttu-id="2de84-125">Обратная совместимость</span><span class="sxs-lookup"><span data-stu-id="2de84-125">Backwards compatibility</span></span>

<span data-ttu-id="2de84-126">Поддерживаются Visual Basic выражения в существующих проектах рабочих процессов C# платформа .NET Framework 4, которые были перенесены в [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2de84-126">Visual Basic expressions in existing .NET Framework 4 C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="2de84-127">Когда Visual Basic выражения просматриваются в конструкторе рабочих процессов, текст существующего выражения Visual Basic заменяется значением, **установленным в XAML**, если только выражение Visual Basic не является допустимым синтаксисом C#.</span><span class="sxs-lookup"><span data-stu-id="2de84-127">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="2de84-128">Если выражение Visual Basic имеет допустимый синтаксис C#, то отображается выражение.</span><span class="sxs-lookup"><span data-stu-id="2de84-128">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="2de84-129">Чтобы обновить выражение Visual Basic до C#, следует отредактировать его в конструкторе рабочих процессов и указать эквивалентное выражение C#.</span><span class="sxs-lookup"><span data-stu-id="2de84-129">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="2de84-130">Преобразование выражений Visual Basic в C# не является обязательным, но после обновления выражений в конструкторе рабочих процессов они преобразуется в C# и не могут быть восстановлены в виде выражений Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2de84-130">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>

### <a name="using-c-expressions-in-code-workflows"></a><a name="CodeWorkflows"></a> <span data-ttu-id="2de84-131">Использование выражений C# в рабочих процессах кода</span><span class="sxs-lookup"><span data-stu-id="2de84-131">Using C# expressions in code workflows</span></span>

<span data-ttu-id="2de84-132">Выражения на языке C# поддерживаются в рабочих процессах [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] с кодом, но до того, как рабочий процесс может быть вызван, выражения C# необходимо скомпилировать с помощью <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2de84-132">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2de84-133">Авторы рабочих процессов могут использовать `CSharpValue` для представления r-значений выражения и `CSharpReference` для представления l-значений выражения.</span><span class="sxs-lookup"><span data-stu-id="2de84-133">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="2de84-134">В следующем примере рабочий процесс создается с помощью действия `Assign` и действия `WriteLine`, содержащихся в `Sequence`.</span><span class="sxs-lookup"><span data-stu-id="2de84-134">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="2de84-135">`CSharpReference` указывается для аргумента `To` действия `Assign` и представляет l-значение выражения.</span><span class="sxs-lookup"><span data-stu-id="2de84-135">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="2de84-136">`CSharpValue` указывается для аргумента `Value` действия `Assign` и для аргумента `Text` действия `WriteLine` и представляет r-значение для двух этих выражений.</span><span class="sxs-lookup"><span data-stu-id="2de84-136">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>

```csharp
Variable<int> n = new Variable<int>
{
    Name = "n"
};

Activity wf = new Sequence
{
    Variables = { n },
    Activities =
    {
        new Assign<int>
        {
            To = new CSharpReference<int>("n"),
            Value = new CSharpValue<int>("new Random().Next(1, 101)")
        },
        new WriteLine
        {
            Text = new CSharpValue<string>("\"The number is \" + n")
        }
    }
};

CompileExpressions(wf);

WorkflowInvoker.Invoke(wf);
```

<span data-ttu-id="2de84-137">После создания рабочего процесса выражения на языке C# компилируются с помощью вызова вспомогательного метода `CompileExpressions`, а затем уже вызывается рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="2de84-137">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="2de84-138">В следующем примере приведен метод `CompileExpressions`.</span><span class="sxs-lookup"><span data-stu-id="2de84-138">The following example is the `CompileExpressions` method.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```

> [!NOTE]
> <span data-ttu-id="2de84-139">Если выражения C# не компилируются, вызывается <xref:System.NotSupportedException> исключение, если рабочий процесс вызывается с сообщением следующего вида: `Expression Activity type 'CSharpValue` 1 "требуется компиляция для выполнения.</span><span class="sxs-lookup"><span data-stu-id="2de84-139">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="2de84-140">Убедитесь, что рабочий процесс был скомпилирован.</span><span class="sxs-lookup"><span data-stu-id="2de84-140">Please ensure that the workflow has been compiled.\`</span></span>

<span data-ttu-id="2de84-141">Если рабочий процесс на основе пользовательского кода использует `DynamicActivity`, то требуется внести некоторые изменения в методе `CompileExpressions`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="2de84-141">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>

```csharp
static void CompileExpressions(DynamicActivity dynamicActivity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions. For Dynamic Activities this can be retrieved using the
    // name property , which must be in the form Namespace.Type.
    string activityName = dynamicActivity.Name;

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = dynamicActivity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = true
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(
        dynamicActivity, compiledExpressionRoot);
}
```

<span data-ttu-id="2de84-142">Существует несколько различий в перегрузке `CompileExpressions`, которая компилирует выражения C# в динамическом действии.</span><span class="sxs-lookup"><span data-stu-id="2de84-142">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>

- <span data-ttu-id="2de84-143">Параметр в `CompileExpressions` - это `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="2de84-143">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>

- <span data-ttu-id="2de84-144">Имя типа и пространство имен получаются с помощью свойства `DynamicActivity.Name`.</span><span class="sxs-lookup"><span data-stu-id="2de84-144">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>

- <span data-ttu-id="2de84-145">Параметру `TextExpressionCompilerSettings.ForImplementation` задается значение `true`.</span><span class="sxs-lookup"><span data-stu-id="2de84-145">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>

- <span data-ttu-id="2de84-146">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` вызывается вместо `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span><span class="sxs-lookup"><span data-stu-id="2de84-146">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>

<span data-ttu-id="2de84-147">Дополнительные сведения о работе с выражениями в коде см. в разделе [создание рабочих процессов, действий и выражений с помощью императивного кода](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="2de84-147">For more information about working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

### <a name="using-c-expressions-in-xaml-workflows"></a><a name="XamlWorkflows"></a> <span data-ttu-id="2de84-148">Использование выражений C# в рабочих процессах XAML</span><span class="sxs-lookup"><span data-stu-id="2de84-148">Using C# expressions in XAML workflows</span></span>

<span data-ttu-id="2de84-149">Выражения на языке C# поддерживаются в рабочих процессах языка XAML.</span><span class="sxs-lookup"><span data-stu-id="2de84-149">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="2de84-150">Скомпилированные рабочие процессы языка XAML компилируются в тип, свободные рабочие процессы языка XAML загружаются средой выполнения и компилируются в дерево действий при выполнении рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="2de84-150">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>

- [<span data-ttu-id="2de84-151">Скомпилированные файлы Xaml</span><span class="sxs-lookup"><span data-stu-id="2de84-151">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

- [<span data-ttu-id="2de84-152">Свободный XAML</span><span class="sxs-lookup"><span data-stu-id="2de84-152">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

#### <a name="compiled-xaml"></a><a name="CompiledXaml"></a> <span data-ttu-id="2de84-153">Скомпилированный XAML</span><span class="sxs-lookup"><span data-stu-id="2de84-153">Compiled Xaml</span></span>

<span data-ttu-id="2de84-154">Выражения на языке C# поддерживаются в скомпилированных рабочих процессах языка XAML, которые компилируются в тип как часть проекта рабочего процесса C#, целью для которых является [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2de84-154">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="2de84-155">Скомпилированный XAML является типом по умолчанию для создания рабочих процессов в Visual Studio, а проекты рабочих процессов C#, созданные в Visual Studio, предназначены для [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] использования выражений C#.</span><span class="sxs-lookup"><span data-stu-id="2de84-155">Compiled XAML is the default type of workflow authoring in Visual Studio, and C# workflow projects created in Visual Studio that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>

#### <a name="loose-xaml"></a><a name="LooseXaml"></a> <span data-ttu-id="2de84-156">Свободный XAML</span><span class="sxs-lookup"><span data-stu-id="2de84-156">Loose Xaml</span></span>

<span data-ttu-id="2de84-157">Выражения на языке C# поддерживаются в свободных рабочих процессах языка XAML.</span><span class="sxs-lookup"><span data-stu-id="2de84-157">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="2de84-158">Программа размещения рабочего процесса, которая загружает и вызывает свободный рабочий процесс языка XAML, должна иметь целью компиляции [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] и <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> должно быть задано значение `true` (по умолчанию `false`).</span><span class="sxs-lookup"><span data-stu-id="2de84-158">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="2de84-159">Чтобы установить свойству <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> значение `true`, создайте экземпляр <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> со свойством <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A>, установленным в значение `true`, и передайте его как параметр в <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2de84-159">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2de84-160">Если `CompileExpressions` для параметра не задано значение `true` , <xref:System.NotSupportedException> будет создано исключение с сообщением следующего вида: `Expression Activity type 'CSharpValue` 1 ' требуется компиляция для выполнения.</span><span class="sxs-lookup"><span data-stu-id="2de84-160">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="2de84-161">Убедитесь, что рабочий процесс был скомпилирован.</span><span class="sxs-lookup"><span data-stu-id="2de84-161">Please ensure that the workflow has been compiled.\`</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="2de84-162">Дополнительные сведения о работе с рабочими процессами XAML см. [в разделе Сериализация рабочих процессов и действий в XAML и обратно](serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="2de84-162">For more information about working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

### <a name="using-c-expressions-in-xamlx-workflow-services"></a><a name="WFServices"></a> <span data-ttu-id="2de84-163">Использование выражений C# в службах рабочих процессов XAMLX</span><span class="sxs-lookup"><span data-stu-id="2de84-163">Using C# expressions in XAMLX workflow services</span></span>

<span data-ttu-id="2de84-164">Выражения на языке C# поддерживаются в службах рабочих процессов XAMLX.</span><span class="sxs-lookup"><span data-stu-id="2de84-164">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="2de84-165">Если служба рабочего процесса размещается в IIS или WAS, то дополнительные действия не требуются. Но если служба рабочих процессов языка XAML является резидентной, то выражения C# необходимо скомпилировать.</span><span class="sxs-lookup"><span data-stu-id="2de84-165">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="2de84-166">Чтобы скомпилировать выражения C# в локальной службе рабочего процесса XAMLX, сначала загрузите файл XAMLX в `WorkflowService` , а затем передайте в `Body` `WorkflowService` метод, `CompileExpressions` описанный в разделе о предыдущем [использовании выражений C# в рабочих процессах кода](csharp-expressions.md#CodeWorkflows) .</span><span class="sxs-lookup"><span data-stu-id="2de84-166">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="2de84-167">В следующем примере загружается служба рабочих процессов XAMLX, компилируются выражения на языке C#, затем открывается служба рабочих процессов, которая начинает ожидать запросы.</span><span class="sxs-lookup"><span data-stu-id="2de84-167">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>

```csharp
// Load the XAMLX workflow service.
WorkflowService workflow1 =
    (WorkflowService)XamlServices.Load(xamlxPath);

// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.
CompileExpressions(workflow1.Body);

// Initialize the WorkflowServiceHost.
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));

// Enable Metadata publishing/
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
smb.HttpGetEnabled = true;
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;
host.Description.Behaviors.Add(smb);

// Open the WorkflowServiceHost and wait for requests.
host.Open();
Console.WriteLine("Press enter to quit");
Console.ReadLine();
```

<span data-ttu-id="2de84-168">Если выражения C# не скомпилированы, операция `Open` выполняется успешно, но при вызове рабочий процесс завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="2de84-168">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="2de84-169">Следующий метод аналогичен `CompileExpressions` методу из предыдущего раздела [Использование выражений C# в рабочих процессах кода](csharp-expressions.md#CodeWorkflows) .</span><span class="sxs-lookup"><span data-stu-id="2de84-169">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```
