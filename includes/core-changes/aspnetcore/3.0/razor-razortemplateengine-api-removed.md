---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032846"
---
### <a name="razor-razortemplateengine-api-removed"></a><span data-ttu-id="39922-101">Razor. Удален API RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="39922-101">Razor: RazorTemplateEngine API removed</span></span>

<span data-ttu-id="39922-102">API [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) был удален и заменен на <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span><span class="sxs-lookup"><span data-stu-id="39922-102">The [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API was removed and replaced with <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span></span>

<span data-ttu-id="39922-103">Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215).</span><span class="sxs-lookup"><span data-stu-id="39922-103">For discussion, see GitHub issue [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="39922-104">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="39922-104">Version introduced</span></span>

<span data-ttu-id="39922-105">3.0</span><span class="sxs-lookup"><span data-stu-id="39922-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="39922-106">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="39922-106">Old behavior</span></span>

<span data-ttu-id="39922-107">Для синтаксического анализа и создания кода для файлов Razor можно создать и использовать обработчик шаблонов.</span><span class="sxs-lookup"><span data-stu-id="39922-107">A template engine can be created and used to parse and generate code for Razor files.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="39922-108">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="39922-108">New behavior</span></span>

<span data-ttu-id="39922-109">Можно создать `RazorProjectEngine` и предоставить сведения того же типа, что и `RazorTemplateEngine` для анализа и создания кода для файлов Razor.</span><span class="sxs-lookup"><span data-stu-id="39922-109">`RazorProjectEngine` can be created and provided the same type of information as `RazorTemplateEngine` to parse and generate code for Razor files.</span></span> <span data-ttu-id="39922-110">`RazorProjectEngine` также предоставляет дополнительные уровни конфигурации.</span><span class="sxs-lookup"><span data-stu-id="39922-110">`RazorProjectEngine` also provides extra levels of configuration.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="39922-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="39922-111">Reason for change</span></span>

<span data-ttu-id="39922-112">`RazorTemplateEngine` был слишком тесно связан с существующими реализациями.</span><span class="sxs-lookup"><span data-stu-id="39922-112">`RazorTemplateEngine` was too tightly coupled to the existing implementations.</span></span> <span data-ttu-id="39922-113">Эта тесная связь приводит к дополнительным вопросам при попытке правильной настройки конвейера анализа и формирования Razor.</span><span class="sxs-lookup"><span data-stu-id="39922-113">This tight coupling led to more questions when trying to properly configure a Razor parsing/generation pipeline.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="39922-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="39922-114">Recommended action</span></span>

<span data-ttu-id="39922-115">Используйте `RazorProjectEngine` вместо `RazorTemplateEngine`.</span><span class="sxs-lookup"><span data-stu-id="39922-115">Use `RazorProjectEngine` instead of `RazorTemplateEngine`.</span></span> <span data-ttu-id="39922-116">Рассмотрим следующие примеры.</span><span class="sxs-lookup"><span data-stu-id="39922-116">Consider the following examples.</span></span>

##### <a name="create-and-configure-the-razorprojectengine"></a><span data-ttu-id="39922-117">Создание и настройка RazorProjectEngine</span><span class="sxs-lookup"><span data-stu-id="39922-117">Create and configure the RazorProjectEngine</span></span>

```csharp
RazorProjectEngine projectEngine =
    RazorProjectEngine.Create(RazorConfiguration.Default,
        RazorProjectFileSystem.Create(@"C:\source\repos\ConsoleApp4\ConsoleApp4"),
        builder =>
        {
            builder.ConfigureClass((document, classNode) =>
            {
                classNode.ClassName = "MyClassName";

                // Can also configure other aspects of the class here.
            });

            // More configuration can go here
        });
```

##### <a name="generate-code-for-a-razor-file"></a><span data-ttu-id="39922-118">Создание кода для файла Razor</span><span class="sxs-lookup"><span data-stu-id="39922-118">Generate code for a Razor file</span></span>

```csharp
RazorProjectItem item = projectEngine.FileSystem.GetItem(
    @"C:\source\repos\ConsoleApp4\ConsoleApp4\Example.cshtml",
    FileKinds.Legacy);
RazorCodeDocument output = projectEngine.Process(item);

// Things available
RazorSyntaxTree syntaxTree = output.GetSyntaxTree();
DocumentIntermediateNode intermediateDocument =
    output.GetDocumentIntermediateNode();
RazorCSharpDocument csharpDocument = output.GetCSharpDocument();
```

#### <a name="category"></a><span data-ttu-id="39922-119">Категория</span><span class="sxs-lookup"><span data-stu-id="39922-119">Category</span></span>

<span data-ttu-id="39922-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39922-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="39922-121">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="39922-121">Affected APIs</span></span>

- [<span data-ttu-id="39922-122">RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="39922-122">RazorTemplateEngine</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [<span data-ttu-id="39922-123">RazorTemplateEngineOptions</span><span class="sxs-lookup"><span data-stu-id="39922-123">RazorTemplateEngineOptions</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
