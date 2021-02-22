---
title: Команда dotnet new
description: Команда dotnet new создает проекты .NET на основе указанного шаблона.
no-loc:
- Blazor
- WebAssembly
ms.date: 09/04/2020
ms.openlocfilehash: acaaf025555c46f720452b8c9d4f875b8656125a
ms.sourcegitcommit: b924ade6426cf61a4604c4e2ee54cb3592c29317
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2021
ms.locfileid: "101096811"
---
# <a name="dotnet-new"></a><span data-ttu-id="e15c4-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="e15c4-103">dotnet new</span></span>

<span data-ttu-id="e15c4-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="e15c4-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e15c4-105">name</span><span class="sxs-lookup"><span data-stu-id="e15c4-105">Name</span></span>

<span data-ttu-id="e15c4-106">`dotnet new` - создает проект, файл конфигурации или решений на основе указанного шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e15c4-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="e15c4-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="e15c4-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e15c4-108">Description</span></span>

<span data-ttu-id="e15c4-109">Команда `dotnet new` создает проект .NET или другие артефакты на основе шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-109">The `dotnet new` command creates a .NET project or other artifacts based on a template.</span></span>

<span data-ttu-id="e15c4-110">Она вызывает [подсистему шаблонов](https://github.com/dotnet/templating), чтобы создать артефакты на диске на основе заданных параметров и шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="e15c4-111">Неявное восстановление</span><span class="sxs-lookup"><span data-stu-id="e15c4-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="e15c4-112">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e15c4-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="e15c4-113">Шаблон для создания экземпляров при вызове команды.</span><span class="sxs-lookup"><span data-stu-id="e15c4-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="e15c4-114">Каждый шаблон может иметь отдельные параметры, доступные для передачи.</span><span class="sxs-lookup"><span data-stu-id="e15c4-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="e15c4-115">Дополнительные сведения см. в разделе [Параметры шаблона](#template-options).</span><span class="sxs-lookup"><span data-stu-id="e15c4-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="e15c4-116">Вы можете запустить `dotnet new --list` или `dotnet new -l`, чтобы просмотреть список всех установленных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="e15c4-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="e15c4-117">Если значение `TEMPLATE` не совпадает в точности с текстом в столбце **Шаблоны** или **Короткое имя** из возвращаемой таблицы, для этих двух столбцов выполняется поиск совпадений в подстроках.</span><span class="sxs-lookup"><span data-stu-id="e15c4-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="e15c4-118">Начиная с пакета SDK для .NET Core 3.0, интерфейс командной строки выполняет поиск шаблонов в NuGet.org при вызове команды `dotnet new` в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="e15c4-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="e15c4-119">если CLI не может найти совпадение шаблона при вызове `dotnet new`, даже частичное;</span><span class="sxs-lookup"><span data-stu-id="e15c4-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="e15c4-120">если доступна более новая версия шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="e15c4-121">В этом случае проект или артефакт создается, но CLI предупреждает об обновленной версии шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="e15c4-122">В следующей таблице представлены шаблоны, которые устанавливаются вместе с пакетом SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="e15c4-122">The following table shows the templates that come pre-installed with the .NET SDK.</span></span> <span data-ttu-id="e15c4-123">Язык по умолчанию для шаблона указан внутри квадратных скобок.</span><span class="sxs-lookup"><span data-stu-id="e15c4-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="e15c4-124">Нажмите на ссылку с коротким названием, чтобы увидеть конкретные параметры шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="e15c4-125">Шаблоны</span><span class="sxs-lookup"><span data-stu-id="e15c4-125">Templates</span></span>                                    | <span data-ttu-id="e15c4-126">короткое имя;</span><span class="sxs-lookup"><span data-stu-id="e15c4-126">Short name</span></span>                        | <span data-ttu-id="e15c4-127">Язык</span><span class="sxs-lookup"><span data-stu-id="e15c4-127">Language</span></span>     | <span data-ttu-id="e15c4-128">Tags</span><span class="sxs-lookup"><span data-stu-id="e15c4-128">Tags</span></span>                                  | <span data-ttu-id="e15c4-129">Введенный</span><span class="sxs-lookup"><span data-stu-id="e15c4-129">Introduced</span></span> |
|----------------------------------------------|-----------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="e15c4-130">Консольное приложение</span><span class="sxs-lookup"><span data-stu-id="e15c4-130">Console Application</span></span>                          | [`console`](#console)             | <span data-ttu-id="e15c4-131">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-131">[C#], F#, VB</span></span> | <span data-ttu-id="e15c4-132">Общее/консоль</span><span class="sxs-lookup"><span data-stu-id="e15c4-132">Common/Console</span></span>                        | <span data-ttu-id="e15c4-133">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-133">1.0</span></span>        |
| <span data-ttu-id="e15c4-134">Библиотека классов</span><span class="sxs-lookup"><span data-stu-id="e15c4-134">Class library</span></span>                                | [`classlib`](#classlib)           | <span data-ttu-id="e15c4-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-135">[C#], F#, VB</span></span> | <span data-ttu-id="e15c4-136">Общее/библиотека</span><span class="sxs-lookup"><span data-stu-id="e15c4-136">Common/Library</span></span>                        | <span data-ttu-id="e15c4-137">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-137">1.0</span></span>        |
| <span data-ttu-id="e15c4-138">Приложение WPF</span><span class="sxs-lookup"><span data-stu-id="e15c4-138">WPF Application</span></span>                              | [`wpf`](#wpf)                     | <span data-ttu-id="e15c4-139">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-139">[C#], VB</span></span>     | <span data-ttu-id="e15c4-140">Общее/WPF</span><span class="sxs-lookup"><span data-stu-id="e15c4-140">Common/WPF</span></span>                            | <span data-ttu-id="e15c4-141">3.0 (5.0 для VB)</span><span class="sxs-lookup"><span data-stu-id="e15c4-141">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e15c4-142">Библиотека классов WPF</span><span class="sxs-lookup"><span data-stu-id="e15c4-142">WPF Class library</span></span>                            | [`wpflib`](#wpf)                  | <span data-ttu-id="e15c4-143">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-143">[C#], VB</span></span>     | <span data-ttu-id="e15c4-144">Общее/WPF</span><span class="sxs-lookup"><span data-stu-id="e15c4-144">Common/WPF</span></span>                            | <span data-ttu-id="e15c4-145">3.0 (5.0 для VB)</span><span class="sxs-lookup"><span data-stu-id="e15c4-145">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e15c4-146">Библиотека настраиваемых элементов управления WPF</span><span class="sxs-lookup"><span data-stu-id="e15c4-146">WPF Custom Control Library</span></span>                   | [`wpfcustomcontrollib`](#wpf)     | <span data-ttu-id="e15c4-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-147">[C#], VB</span></span>     | <span data-ttu-id="e15c4-148">Общее/WPF</span><span class="sxs-lookup"><span data-stu-id="e15c4-148">Common/WPF</span></span>                            | <span data-ttu-id="e15c4-149">3.0 (5.0 для VB)</span><span class="sxs-lookup"><span data-stu-id="e15c4-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e15c4-150">Библиотека пользовательских элементов управления WPF</span><span class="sxs-lookup"><span data-stu-id="e15c4-150">WPF User Control Library</span></span>                     | [`wpfusercontrollib`](#wpf)       | <span data-ttu-id="e15c4-151">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-151">[C#], VB</span></span>     | <span data-ttu-id="e15c4-152">Общее/WPF</span><span class="sxs-lookup"><span data-stu-id="e15c4-152">Common/WPF</span></span>                            | <span data-ttu-id="e15c4-153">3.0 (5.0 для VB)</span><span class="sxs-lookup"><span data-stu-id="e15c4-153">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e15c4-154">Приложение Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e15c4-154">Windows Forms (WinForms) Application</span></span>         | [`winforms`](#winforms)           | <span data-ttu-id="e15c4-155">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-155">[C#], VB</span></span>     | <span data-ttu-id="e15c4-156">Общее (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e15c4-156">Common/WinForms</span></span>                       | <span data-ttu-id="e15c4-157">3.0 (5.0 для VB)</span><span class="sxs-lookup"><span data-stu-id="e15c4-157">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e15c4-158">Библиотека классов для Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e15c4-158">Windows Forms (WinForms) Class library</span></span>       | [`winformslib`](#winforms)        | <span data-ttu-id="e15c4-159">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-159">[C#], VB</span></span>     | <span data-ttu-id="e15c4-160">Общее (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e15c4-160">Common/WinForms</span></span>                       | <span data-ttu-id="e15c4-161">3.0 (5.0 для VB)</span><span class="sxs-lookup"><span data-stu-id="e15c4-161">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e15c4-162">Служба Worker Service</span><span class="sxs-lookup"><span data-stu-id="e15c4-162">Worker Service</span></span>                               | [`worker`](#web-others)           | <span data-ttu-id="e15c4-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-163">[C#]</span></span>         | <span data-ttu-id="e15c4-164">Общее/Рабочая роль/Веб</span><span class="sxs-lookup"><span data-stu-id="e15c4-164">Common/Worker/Web</span></span>                     | <span data-ttu-id="e15c4-165">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-165">3.0</span></span>        |
| <span data-ttu-id="e15c4-166">Проект модульного теста</span><span class="sxs-lookup"><span data-stu-id="e15c4-166">Unit Test Project</span></span>                            | [`mstest`](#test)                 | <span data-ttu-id="e15c4-167">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-167">[C#], F#, VB</span></span> | <span data-ttu-id="e15c4-168">Тест/MSTest</span><span class="sxs-lookup"><span data-stu-id="e15c4-168">Test/MSTest</span></span>                           | <span data-ttu-id="e15c4-169">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-169">1.0</span></span>        |
| <span data-ttu-id="e15c4-170">Тестовый проект NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e15c4-170">NUnit 3 Test Project</span></span>                         | [`nunit`](#nunit)                 | <span data-ttu-id="e15c4-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-171">[C#], F#, VB</span></span> | <span data-ttu-id="e15c4-172">Тест/NUnit</span><span class="sxs-lookup"><span data-stu-id="e15c4-172">Test/NUnit</span></span>                            | <span data-ttu-id="e15c4-173">2.1.400</span><span class="sxs-lookup"><span data-stu-id="e15c4-173">2.1.400</span></span>    |
| <span data-ttu-id="e15c4-174">Элемент теста NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e15c4-174">NUnit 3 Test Item</span></span>                            | `nunit-test`                      | <span data-ttu-id="e15c4-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-175">[C#], F#, VB</span></span> | <span data-ttu-id="e15c4-176">Тест/NUnit</span><span class="sxs-lookup"><span data-stu-id="e15c4-176">Test/NUnit</span></span>                            | <span data-ttu-id="e15c4-177">2.2</span><span class="sxs-lookup"><span data-stu-id="e15c4-177">2.2</span></span>        |
| <span data-ttu-id="e15c4-178">Тестовый проект xUnit</span><span class="sxs-lookup"><span data-stu-id="e15c4-178">xUnit Test Project</span></span>                           | [`xunit`](#test)                  | <span data-ttu-id="e15c4-179">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e15c4-179">[C#], F#, VB</span></span> | <span data-ttu-id="e15c4-180">Тест/xUnit</span><span class="sxs-lookup"><span data-stu-id="e15c4-180">Test/xUnit</span></span>                            | <span data-ttu-id="e15c4-181">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-181">1.0</span></span>        |
| <span data-ttu-id="e15c4-182">Компонент Razor</span><span class="sxs-lookup"><span data-stu-id="e15c4-182">Razor Component</span></span>                              | `razorcomponent`                  | <span data-ttu-id="e15c4-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-183">[C#]</span></span>         | <span data-ttu-id="e15c4-184">Веб/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e15c4-184">Web/ASP.NET</span></span>                           | <span data-ttu-id="e15c4-185">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-185">3.0</span></span>        |
| <span data-ttu-id="e15c4-186">Страница Razor</span><span class="sxs-lookup"><span data-stu-id="e15c4-186">Razor Page</span></span>                                   | [`page`](#page)                   | <span data-ttu-id="e15c4-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-187">[C#]</span></span>         | <span data-ttu-id="e15c4-188">Веб/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e15c4-188">Web/ASP.NET</span></span>                           | <span data-ttu-id="e15c4-189">2.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-189">2.0</span></span>        |
| <span data-ttu-id="e15c4-190">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="e15c4-190">MVC ViewImports</span></span>                              | [`viewimports`](#namespace)       | <span data-ttu-id="e15c4-191">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-191">[C#]</span></span>         | <span data-ttu-id="e15c4-192">Веб/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e15c4-192">Web/ASP.NET</span></span>                           | <span data-ttu-id="e15c4-193">2.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-193">2.0</span></span>        |
| <span data-ttu-id="e15c4-194">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="e15c4-194">MVC ViewStart</span></span>                                | `viewstart`                       | <span data-ttu-id="e15c4-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-195">[C#]</span></span>         | <span data-ttu-id="e15c4-196">Веб/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e15c4-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="e15c4-197">2.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-197">2.0</span></span>        |
| <span data-ttu-id="e15c4-198">Серверное приложение Blazor</span><span class="sxs-lookup"><span data-stu-id="e15c4-198">Blazor Server App</span></span>                            | [`blazorserver`](#blazorserver)   | <span data-ttu-id="e15c4-199">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-199">[C#]</span></span>         | <span data-ttu-id="e15c4-200">Веб/Blazor</span><span class="sxs-lookup"><span data-stu-id="e15c4-200">Web/Blazor</span></span>                            | <span data-ttu-id="e15c4-201">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-201">3.0</span></span>        |
| <span data-ttu-id="e15c4-202">Приложение WebAssembly Blazor</span><span class="sxs-lookup"><span data-stu-id="e15c4-202">Blazor WebAssembly App</span></span>                       | [`blazorwasm`](#blazorwasm)       | <span data-ttu-id="e15c4-203">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-203">[C#]</span></span>         | <span data-ttu-id="e15c4-204">Веб/Blazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="e15c4-204">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="e15c4-205">3.1.300</span><span class="sxs-lookup"><span data-stu-id="e15c4-205">3.1.300</span></span>    |
| <span data-ttu-id="e15c4-206">Пустой ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e15c4-206">ASP.NET Core Empty</span></span>                           | [`web`](#web)                     | <span data-ttu-id="e15c4-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e15c4-207">[C#], F#</span></span>     | <span data-ttu-id="e15c4-208">Веб/пусто</span><span class="sxs-lookup"><span data-stu-id="e15c4-208">Web/Empty</span></span>                             | <span data-ttu-id="e15c4-209">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-209">1.0</span></span>        |
| <span data-ttu-id="e15c4-210">Веб-приложение ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="e15c4-210">ASP.NET Core Web App (Model-View-Controller)</span></span> | [`mvc`](#web-options)             | <span data-ttu-id="e15c4-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e15c4-211">[C#], F#</span></span>     | <span data-ttu-id="e15c4-212">Веб/MVC</span><span class="sxs-lookup"><span data-stu-id="e15c4-212">Web/MVC</span></span>                               | <span data-ttu-id="e15c4-213">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-213">1.0</span></span>        |
| <span data-ttu-id="e15c4-214">Веб-приложение ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e15c4-214">ASP.NET Core Web App</span></span>                         | [`webapp, razor`](#web-options)   | <span data-ttu-id="e15c4-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-215">[C#]</span></span>         | <span data-ttu-id="e15c4-216">Веб/MVC и Razor Pages</span><span class="sxs-lookup"><span data-stu-id="e15c4-216">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="e15c4-217">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-217">2.2, 2.0</span></span>   |
| <span data-ttu-id="e15c4-218">ASP.NET Core с Angular</span><span class="sxs-lookup"><span data-stu-id="e15c4-218">ASP.NET Core with Angular</span></span>                    | [`angular`](#spa)                 | <span data-ttu-id="e15c4-219">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-219">[C#]</span></span>         | <span data-ttu-id="e15c4-220">MVC/Веб/SPA</span><span class="sxs-lookup"><span data-stu-id="e15c4-220">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e15c4-221">2.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-221">2.0</span></span>        |
| <span data-ttu-id="e15c4-222">ASP.NET Core с React.js</span><span class="sxs-lookup"><span data-stu-id="e15c4-222">ASP.NET Core with React.js</span></span>                   | [`react`](#spa)                   | <span data-ttu-id="e15c4-223">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-223">[C#]</span></span>         | <span data-ttu-id="e15c4-224">MVC/Веб/SPA</span><span class="sxs-lookup"><span data-stu-id="e15c4-224">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e15c4-225">2.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-225">2.0</span></span>        |
| <span data-ttu-id="e15c4-226">ASP.NET Core с React.js и Redux</span><span class="sxs-lookup"><span data-stu-id="e15c4-226">ASP.NET Core with React.js and Redux</span></span>         | [`reactredux`](#reactredux)       | <span data-ttu-id="e15c4-227">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-227">[C#]</span></span>         | <span data-ttu-id="e15c4-228">MVC/Веб/SPA</span><span class="sxs-lookup"><span data-stu-id="e15c4-228">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e15c4-229">2.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-229">2.0</span></span>        |
| <span data-ttu-id="e15c4-230">Библиотека классов Razor</span><span class="sxs-lookup"><span data-stu-id="e15c4-230">Razor Class Library</span></span>                          | [`razorclasslib`](#razorclasslib) | <span data-ttu-id="e15c4-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-231">[C#]</span></span>         | <span data-ttu-id="e15c4-232">Веб/Razor/Библиотека/Библиотека классов Razor</span><span class="sxs-lookup"><span data-stu-id="e15c4-232">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="e15c4-233">2.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-233">2.1</span></span>        |
| <span data-ttu-id="e15c4-234">Веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e15c4-234">ASP.NET Core Web API</span></span>                         | [`webapi`](#webapi)               | <span data-ttu-id="e15c4-235">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e15c4-235">[C#], F#</span></span>     | <span data-ttu-id="e15c4-236">Веб/веб-API</span><span class="sxs-lookup"><span data-stu-id="e15c4-236">Web/WebAPI</span></span>                            | <span data-ttu-id="e15c4-237">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-237">1.0</span></span>        |
| <span data-ttu-id="e15c4-238">Служба ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="e15c4-238">ASP.NET Core gRPC Service</span></span>                    | [`grpc`](#web-others)             | <span data-ttu-id="e15c4-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="e15c4-239">[C#]</span></span>         | <span data-ttu-id="e15c4-240">Веб/gRPC</span><span class="sxs-lookup"><span data-stu-id="e15c4-240">Web/gRPC</span></span>                              | <span data-ttu-id="e15c4-241">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-241">3.0</span></span>        |
| <span data-ttu-id="e15c4-242">Файл dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="e15c4-242">dotnet gitignore file</span></span>                        | `gitignore`                       |              | <span data-ttu-id="e15c4-243">Config</span><span class="sxs-lookup"><span data-stu-id="e15c4-243">Config</span></span>                                | <span data-ttu-id="e15c4-244">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-244">3.0</span></span>        |
| <span data-ttu-id="e15c4-245">Файл global.json</span><span class="sxs-lookup"><span data-stu-id="e15c4-245">global.json file</span></span>                             | [`globaljson`](#globaljson)       |              | <span data-ttu-id="e15c4-246">Config</span><span class="sxs-lookup"><span data-stu-id="e15c4-246">Config</span></span>                                | <span data-ttu-id="e15c4-247">2.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-247">2.0</span></span>        |
| <span data-ttu-id="e15c4-248">Конфигурация NuGet</span><span class="sxs-lookup"><span data-stu-id="e15c4-248">NuGet Config</span></span>                                 | `nugetconfig`                     |              | <span data-ttu-id="e15c4-249">Config</span><span class="sxs-lookup"><span data-stu-id="e15c4-249">Config</span></span>                                | <span data-ttu-id="e15c4-250">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-250">1.0</span></span>        |
| <span data-ttu-id="e15c4-251">Локальное средство файла манифеста dotnet</span><span class="sxs-lookup"><span data-stu-id="e15c4-251">Dotnet local tool manifest file</span></span>              | `tool-manifest`                   |              | <span data-ttu-id="e15c4-252">Config</span><span class="sxs-lookup"><span data-stu-id="e15c4-252">Config</span></span>                                | <span data-ttu-id="e15c4-253">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-253">3.0</span></span>        |
| <span data-ttu-id="e15c4-254">Файл веб-конфигурации</span><span class="sxs-lookup"><span data-stu-id="e15c4-254">Web Config</span></span>                                   | `webconfig`                       |              | <span data-ttu-id="e15c4-255">Config</span><span class="sxs-lookup"><span data-stu-id="e15c4-255">Config</span></span>                                | <span data-ttu-id="e15c4-256">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-256">1.0</span></span>        |
| <span data-ttu-id="e15c4-257">Файл решения</span><span class="sxs-lookup"><span data-stu-id="e15c4-257">Solution File</span></span>                                | `sln`                             |              | <span data-ttu-id="e15c4-258">Решение</span><span class="sxs-lookup"><span data-stu-id="e15c4-258">Solution</span></span>                              | <span data-ttu-id="e15c4-259">1.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-259">1.0</span></span>        |
| <span data-ttu-id="e15c4-260">Файл буфера протокола</span><span class="sxs-lookup"><span data-stu-id="e15c4-260">Protocol Buffer File</span></span>                         | [`proto`](#namespace)             |              | <span data-ttu-id="e15c4-261">Веб/gRPC</span><span class="sxs-lookup"><span data-stu-id="e15c4-261">Web/gRPC</span></span>                              | <span data-ttu-id="e15c4-262">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-262">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="e15c4-263">Параметры</span><span class="sxs-lookup"><span data-stu-id="e15c4-263">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="e15c4-264">Отображает сводку того, что произойдет, если выполнить команду и это приведет к созданию шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-264">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="e15c4-265">Доступно начиная с пакета SDK для .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="e15c4-265">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="e15c4-266">Принудительное создание содержимого, даже если при этом изменяются существующие файлы.</span><span class="sxs-lookup"><span data-stu-id="e15c4-266">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="e15c4-267">Это необходимо, когда выбранный шаблон переопределяет существующие файлы в выходном каталоге.</span><span class="sxs-lookup"><span data-stu-id="e15c4-267">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e15c4-268">Распечатывает справку для команды.</span><span class="sxs-lookup"><span data-stu-id="e15c4-268">Prints out help for the command.</span></span> <span data-ttu-id="e15c4-269">Его можно вызвать для самой команды `dotnet new` или для любого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-269">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="e15c4-270">Например, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-270">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="e15c4-271">Устанавливает пакет шаблона из указанного пути `PATH` или по указанному идентификатору `NUGET_ID`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-271">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e15c4-272">Если вы хотите установить предварительную версию пакета шаблонов, необходимо указать версию в формате `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-272">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="e15c4-273">По умолчанию `dotnet new` передает \* для версии, что указывает на последнюю стабильную версию пакета.</span><span class="sxs-lookup"><span data-stu-id="e15c4-273">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="e15c4-274">См. пример в разделе [Примеры](#examples).</span><span class="sxs-lookup"><span data-stu-id="e15c4-274">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="e15c4-275">Если при выполнении этой команды версия шаблона уже была установлена, шаблон будет обновлен до указанной версии или до последней стабильной версии, если версию не указано.</span><span class="sxs-lookup"><span data-stu-id="e15c4-275">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="e15c4-276">Сведения о создании пользовательских шаблонов см. в статье [Пользовательские шаблоны для команды dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-276">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="e15c4-277">Перечисляет шаблоны с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="e15c4-277">Lists templates containing the specified name.</span></span> <span data-ttu-id="e15c4-278">Если имя не указано, перечисляются все шаблоны.</span><span class="sxs-lookup"><span data-stu-id="e15c4-278">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="e15c4-279">Язык создаваемого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-279">The language of the template to create.</span></span> <span data-ttu-id="e15c4-280">Допустимый язык зависит от шаблона (см. значения по умолчанию в разделе об [аргументах](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="e15c4-280">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="e15c4-281">Не является допустимым для некоторых шаблонов.</span><span class="sxs-lookup"><span data-stu-id="e15c4-281">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e15c4-282">Некоторые оболочки интерпретируют `#` как специальный символ.</span><span class="sxs-lookup"><span data-stu-id="e15c4-282">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="e15c4-283">В этих случаях заключите значение языкового параметра в кавычки.</span><span class="sxs-lookup"><span data-stu-id="e15c4-283">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="e15c4-284">Например, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-284">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="e15c4-285">Имя создаваемых выходных данных.</span><span class="sxs-lookup"><span data-stu-id="e15c4-285">The name for the created output.</span></span> <span data-ttu-id="e15c4-286">Если имя не указано, используется имя текущего каталога.</span><span class="sxs-lookup"><span data-stu-id="e15c4-286">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="e15c4-287">Задает источник пакетов NuGet для использования во время установки.</span><span class="sxs-lookup"><span data-stu-id="e15c4-287">Specifies a NuGet source to use during install.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e15c4-288">Расположение, в котором размещаются созданные выходные данные.</span><span class="sxs-lookup"><span data-stu-id="e15c4-288">Location to place the generated output.</span></span> <span data-ttu-id="e15c4-289">Значением по умолчанию является текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="e15c4-289">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="e15c4-290">Фильтрует шаблоны по доступным типам.</span><span class="sxs-lookup"><span data-stu-id="e15c4-290">Filters templates based on available types.</span></span> <span data-ttu-id="e15c4-291">Предопределенные значения: `project` и `item`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-291">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="e15c4-292">Удаляет пакет шаблона из указанного пути `PATH` или по указанному идентификатору `NUGET_ID`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-292">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e15c4-293">Если значение `<PATH|NUGET_ID>` не указано, отображаются все установленные пакеты шаблонов и связанные с ними шаблоны.</span><span class="sxs-lookup"><span data-stu-id="e15c4-293">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="e15c4-294">Не указывайте номер версии, если задаете `NUGET_ID`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-294">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="e15c4-295">Если вы не указываете параметр в этой опции, команда перечисляет установленные шаблоны и подробные сведения о них.</span><span class="sxs-lookup"><span data-stu-id="e15c4-295">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e15c4-296">Чтобы удалить шаблон с помощью `PATH`, вам необходимо указать полный путь.</span><span class="sxs-lookup"><span data-stu-id="e15c4-296">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="e15c4-297">Например, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* будет работать, а *./GarciaSoftware.ConsoleTemplate.CSharp* — нет.</span><span class="sxs-lookup"><span data-stu-id="e15c4-297">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="e15c4-298">Путь к шаблону не должен содержать конечную косую черту закрытия каталога.</span><span class="sxs-lookup"><span data-stu-id="e15c4-298">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="e15c4-299">Проверяет наличие обновлений для установленных в настоящее время пакетов шаблонов и устанавливает их.</span><span class="sxs-lookup"><span data-stu-id="e15c4-299">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="e15c4-300">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e15c4-300">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="e15c4-301">Проверяет наличие обновлений для установленных в настоящее время пакетов шаблонов.</span><span class="sxs-lookup"><span data-stu-id="e15c4-301">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="e15c4-302">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e15c4-302">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="e15c4-303">Параметры шаблона</span><span class="sxs-lookup"><span data-stu-id="e15c4-303">Template options</span></span>

<span data-ttu-id="e15c4-304">Каждый шаблон проекта может содержать дополнительные доступные параметры.</span><span class="sxs-lookup"><span data-stu-id="e15c4-304">Each project template may have additional options available.</span></span> <span data-ttu-id="e15c4-305">Основные шаблоны имеют следующие дополнительные параметры:</span><span class="sxs-lookup"><span data-stu-id="e15c4-305">The core templates have the following additional options:</span></span>

### `console`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-306">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-306">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-307">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e15c4-307">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e15c4-308">В следующей таблице приведены значения по умолчанию в соответствии с версией пакета SDK, которую вы используете:</span><span class="sxs-lookup"><span data-stu-id="e15c4-308">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e15c4-309">Версия пакета SDK</span><span class="sxs-lookup"><span data-stu-id="e15c4-309">SDK version</span></span> | <span data-ttu-id="e15c4-310">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e15c4-310">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e15c4-311">5,0</span><span class="sxs-lookup"><span data-stu-id="e15c4-311">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e15c4-312">3.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-312">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e15c4-313">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-313">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e15c4-314">Задает свойство `LangVersion` в созданном файле проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-314">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e15c4-315">Например, вам требуется `--langVersion 7.3`, чтобы использовать C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e15c4-315">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="e15c4-316">Не поддерживается для F#.</span><span class="sxs-lookup"><span data-stu-id="e15c4-316">Not supported for F#.</span></span> <span data-ttu-id="e15c4-317">Доступно начиная с пакета SDK для .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="e15c4-317">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e15c4-318">Список версий C# по умолчанию см. в разделе [Значения по умолчанию](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e15c4-318">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e15c4-319">Если указано — во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-319">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="e15c4-320">Доступно начиная с пакета SDK для .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="e15c4-320">Available since .NET Core 2.2 SDK.</span></span>

***

### `classlib`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-321">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-321">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-322">Значения: `net5.0` или `netcoreapp<version>` для создания библиотеки классов .NET Core или `netstandard<version>` для создания стандартной библиотеки классов .NET.</span><span class="sxs-lookup"><span data-stu-id="e15c4-322">Values: `net5.0` or `netcoreapp<version>` to create a .NET Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="e15c4-323">Значение по умолчанию для пакета SDK для .NET 5.0 — `net5.0`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-323">The default value for .NET 5.0 SDK is `net5.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e15c4-324">Задает свойство `LangVersion` в созданном файле проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-324">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e15c4-325">Например, вам требуется `--langVersion 7.3`, чтобы использовать C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e15c4-325">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="e15c4-326">Не поддерживается для F#.</span><span class="sxs-lookup"><span data-stu-id="e15c4-326">Not supported for F#.</span></span> <span data-ttu-id="e15c4-327">Доступно начиная с пакета SDK для .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="e15c4-327">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e15c4-328">Список версий C# по умолчанию см. в разделе [Значения по умолчанию](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e15c4-328">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e15c4-329">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-329">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="e15c4-330">`wpf`, `wpflib`, `wpfcustomcontrollib`, `wpfusercontrollib`</span><span class="sxs-lookup"><span data-stu-id="e15c4-330">`wpf`, `wpflib`, `wpfcustomcontrollib`, `wpfusercontrollib`</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-331">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-332">Значение по умолчанию — `net5.0`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-332">The default value is `net5.0`.</span></span> <span data-ttu-id="e15c4-333">Доступно, начиная с пакета SDK для .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="e15c4-333">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e15c4-334">Задает свойство `LangVersion` в созданном файле проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-334">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e15c4-335">Например, вам требуется `--langVersion 7.3`, чтобы использовать C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e15c4-335">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="e15c4-336">Список версий C# по умолчанию см. в разделе [Значения по умолчанию](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e15c4-336">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e15c4-337">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-337">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="e15c4-338">`winforms`, `winformslib`</span><span class="sxs-lookup"><span data-stu-id="e15c4-338">`winforms`, `winformslib`</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e15c4-339">Задает свойство `LangVersion` в созданном файле проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-339">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e15c4-340">Например, вам требуется `--langVersion 7.3`, чтобы использовать C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e15c4-340">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="e15c4-341">Список версий C# по умолчанию см. в разделе [Значения по умолчанию](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e15c4-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e15c4-342">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-342">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="e15c4-343">`worker`, `grpc`</span><span class="sxs-lookup"><span data-stu-id="e15c4-343">`worker`, `grpc`</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-344">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-344">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-345">Значение по умолчанию — `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-345">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="e15c4-346">Доступно, начиная с пакета SDK для .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="e15c4-346">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e15c4-347">Исключает файл *launchSettings.json* из создаваемого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-347">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e15c4-348">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-348">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="e15c4-349">`mstest`, `xunit`</span><span class="sxs-lookup"><span data-stu-id="e15c4-349">`mstest`, `xunit`</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-350">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-350">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-351">Параметр доступен, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e15c4-351">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e15c4-352">В следующей таблице приведены значения по умолчанию в соответствии с версией пакета SDK, которую вы используете:</span><span class="sxs-lookup"><span data-stu-id="e15c4-352">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e15c4-353">Версия пакета SDK</span><span class="sxs-lookup"><span data-stu-id="e15c4-353">SDK version</span></span> | <span data-ttu-id="e15c4-354">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e15c4-354">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e15c4-355">5,0</span><span class="sxs-lookup"><span data-stu-id="e15c4-355">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e15c4-356">3.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-356">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e15c4-357">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-357">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="e15c4-358">Включает упаковку проекта с помощью команды [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-358">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e15c4-359">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-359">Doesn't execute an implicit restore during project creation.</span></span>

***

### `nunit`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-360">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-360">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="e15c4-361">В следующей таблице приведены значения по умолчанию в соответствии с версией пакета SDK, которую вы используете:</span><span class="sxs-lookup"><span data-stu-id="e15c4-361">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e15c4-362">Версия пакета SDK</span><span class="sxs-lookup"><span data-stu-id="e15c4-362">SDK version</span></span> | <span data-ttu-id="e15c4-363">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e15c4-363">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e15c4-364">5,0</span><span class="sxs-lookup"><span data-stu-id="e15c4-364">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e15c4-365">3.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-365">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e15c4-366">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-366">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e15c4-367">2.2</span><span class="sxs-lookup"><span data-stu-id="e15c4-367">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="e15c4-368">2.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-368">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="e15c4-369">Включает упаковку проекта с помощью команды [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-369">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e15c4-370">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### `page`

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="e15c4-371">Пространство имен для сформированного кода.</span><span class="sxs-lookup"><span data-stu-id="e15c4-371">Namespace for the generated code.</span></span> <span data-ttu-id="e15c4-372">Значение по умолчанию — `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-372">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="e15c4-373">Создает страницу без PageModel.</span><span class="sxs-lookup"><span data-stu-id="e15c4-373">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="e15c4-374">`viewimports`, `proto`</span><span class="sxs-lookup"><span data-stu-id="e15c4-374">`viewimports`, `proto`</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="e15c4-375">Пространство имен для сформированного кода.</span><span class="sxs-lookup"><span data-stu-id="e15c4-375">Namespace for the generated code.</span></span> <span data-ttu-id="e15c4-376">Значение по умолчанию — `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-376">The default value is `MyApp.Namespace`.</span></span>

***

### `blazorserver`

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="e15c4-377">Тип проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-377">The type of authentication to use.</span></span> <span data-ttu-id="e15c4-378">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="e15c4-378">The possible values are:</span></span>

  - <span data-ttu-id="e15c4-379">`None` — без проверки подлинности (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="e15c4-379">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e15c4-380">`Individual` — индивидуальная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-380">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e15c4-381">`IndividualB2C` — индивидуальная проверка подлинности с помощью Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e15c4-381">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e15c4-382">`SingleOrg` — проверка подлинности организации для отдельного клиента.</span><span class="sxs-lookup"><span data-stu-id="e15c4-382">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e15c4-383">`MultiOrg` — проверка подлинности организации для нескольких клиентов.</span><span class="sxs-lookup"><span data-stu-id="e15c4-383">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="e15c4-384">`Windows` — проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="e15c4-384">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e15c4-385">Экземпляр Azure Active Directory B2C, к которому выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-385">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e15c4-386">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-386">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-387">Значение по умолчанию — `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-387">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e15c4-388">Идентификатор политики входа и регистрации для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-388">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e15c4-389">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-389">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="e15c4-390">Идентификатор политики сброса паролей для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-390">The reset password policy ID for this project.</span></span> <span data-ttu-id="e15c4-391">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-391">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="e15c4-392">Идентификатор политики изменения профилей для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-392">The edit profile policy ID for this project.</span></span> <span data-ttu-id="e15c4-393">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-393">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e15c4-394">Экземпляр Azure Active Directory, к которому выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-394">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e15c4-395">Используется с проверкой подлинности `SingleOrg` или `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-395">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e15c4-396">Значение по умолчанию — `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-396">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e15c4-397">Идентификатор клиента для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-397">The Client ID for this project.</span></span> <span data-ttu-id="e15c4-398">Используется с проверкой подлинности `IndividualB2C`, `SingleOrg` или `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-398">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e15c4-399">Значение по умолчанию — `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-399">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e15c4-400">Домен клиента каталога.</span><span class="sxs-lookup"><span data-stu-id="e15c4-400">The domain for the directory tenant.</span></span> <span data-ttu-id="e15c4-401">Используется с проверкой подлинности `SingleOrg` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-401">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-402">Значение по умолчанию — `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-402">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e15c4-403">Идентификатор TenantId каталога, к которому устанавливается подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-403">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e15c4-404">Используется с проверкой подлинности `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-404">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e15c4-405">Значение по умолчанию — `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-405">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="e15c4-406">Путь запроса по базовому пути кода URI перенаправления для приложения.</span><span class="sxs-lookup"><span data-stu-id="e15c4-406">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e15c4-407">Используется с проверкой подлинности `SingleOrg` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-407">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-408">Значение по умолчанию — `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-408">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e15c4-409">Предоставляет приложению доступ к каталогу для чтения.</span><span class="sxs-lookup"><span data-stu-id="e15c4-409">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e15c4-410">Применяется только при проверке подлинности `SingleOrg` или `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-410">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e15c4-411">Исключает файл *launchSettings.json* из создаваемого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-411">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e15c4-412">Отключает протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e15c4-412">Turns off HTTPS.</span></span> <span data-ttu-id="e15c4-413">Этот параметр применяется, только если `Individual`, `IndividualB2C`, `SingleOrg` или `MultiOrg` не используются для `--auth`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-413">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e15c4-414">Указывает, что вместо SQLite следует использовать LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e15c4-414">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e15c4-415">Применяется только при проверке подлинности `Individual` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-415">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e15c4-416">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-416">Doesn't execute an implicit restore during project creation.</span></span>

***

### `blazorwasm`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-417">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-417">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="e15c4-418">В следующей таблице приведены значения по умолчанию в соответствии с версией пакета SDK, которую вы используете:</span><span class="sxs-lookup"><span data-stu-id="e15c4-418">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e15c4-419">Версия пакета SDK</span><span class="sxs-lookup"><span data-stu-id="e15c4-419">SDK version</span></span> | <span data-ttu-id="e15c4-420">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e15c4-420">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e15c4-421">5,0</span><span class="sxs-lookup"><span data-stu-id="e15c4-421">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e15c4-422">3.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-422">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="e15c4-423">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-423">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="e15c4-424">Включает узел ASP.NET Core для приложения Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="e15c4-424">Includes an ASP.NET Core host for the Blazor WebAssembly app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="e15c4-425">Тип проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-425">The type of authentication to use.</span></span> <span data-ttu-id="e15c4-426">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="e15c4-426">The possible values are:</span></span>

  - <span data-ttu-id="e15c4-427">`None` — без проверки подлинности (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="e15c4-427">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e15c4-428">`Individual` — индивидуальная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-428">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e15c4-429">`IndividualB2C` — индивидуальная проверка подлинности с помощью Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e15c4-429">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e15c4-430">`SingleOrg` — проверка подлинности организации для отдельного клиента.</span><span class="sxs-lookup"><span data-stu-id="e15c4-430">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="e15c4-431">Центр поставщика OIDC.</span><span class="sxs-lookup"><span data-stu-id="e15c4-431">The authority of the OIDC provider.</span></span> <span data-ttu-id="e15c4-432">Используется с проверкой подлинности `Individual`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-432">Use with `Individual` authentication.</span></span> <span data-ttu-id="e15c4-433">Значение по умолчанию — `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-433">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e15c4-434">Экземпляр Azure Active Directory B2C, к которому выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-434">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e15c4-435">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-435">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-436">Значение по умолчанию — `https://aadB2CInstance.b2clogin.com/`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-436">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e15c4-437">Идентификатор политики входа и регистрации для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-437">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e15c4-438">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-438">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e15c4-439">Экземпляр Azure Active Directory, к которому выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-439">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e15c4-440">Используется с проверкой подлинности `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e15c4-441">Значение по умолчанию — `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-441">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e15c4-442">Идентификатор клиента для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-442">The Client ID for this project.</span></span> <span data-ttu-id="e15c4-443">Используйте для проверки подлинности `IndividualB2C`, `SingleOrg` или `Individual` в автономных сценариях.</span><span class="sxs-lookup"><span data-stu-id="e15c4-443">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="e15c4-444">Значение по умолчанию — `33333333-3333-3333-33333333333333333`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-444">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e15c4-445">Домен клиента каталога.</span><span class="sxs-lookup"><span data-stu-id="e15c4-445">The domain for the directory tenant.</span></span> <span data-ttu-id="e15c4-446">Используется с проверкой подлинности `SingleOrg` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-446">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-447">Значение по умолчанию — `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-447">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="e15c4-448">URI идентификатора приложения для серверного API-интерфейса, который требуется вызвать.</span><span class="sxs-lookup"><span data-stu-id="e15c4-448">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="e15c4-449">Используется с проверкой подлинности `SingleOrg` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-449">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-450">Значение по умолчанию — `api.id.uri`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-450">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="e15c4-451">Идентификатор клиента для API, размещенного на сервере.</span><span class="sxs-lookup"><span data-stu-id="e15c4-451">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="e15c4-452">Используется с проверкой подлинности `SingleOrg` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-452">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-453">Значение по умолчанию — `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-453">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="e15c4-454">Область API, которую клиент должен запросить для подготовки маркера доступа.</span><span class="sxs-lookup"><span data-stu-id="e15c4-454">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="e15c4-455">Используется с проверкой подлинности `SingleOrg` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-455">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-456">Значение по умолчанию — `user_impersonation`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-456">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e15c4-457">Идентификатор TenantId каталога, к которому устанавливается подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-457">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e15c4-458">Используется с проверкой подлинности `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-458">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e15c4-459">Значение по умолчанию — `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-459">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e15c4-460">Предоставляет приложению доступ к каталогу для чтения.</span><span class="sxs-lookup"><span data-stu-id="e15c4-460">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e15c4-461">Применяется только при проверке подлинности `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-461">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e15c4-462">Исключает файл *launchSettings.json* из создаваемого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-462">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="e15c4-463">Создает прогрессивное веб-приложение (PWA), поддерживающее установку и автономное использование.</span><span class="sxs-lookup"><span data-stu-id="e15c4-463">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="e15c4-464">Отключает протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e15c4-464">Turns off HTTPS.</span></span> <span data-ttu-id="e15c4-465">Этот параметр применяется, только если `Individual`, `IndividualB2C` или `SingleOrg` не используются для `--auth`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-465">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e15c4-466">Указывает, что вместо SQLite следует использовать LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e15c4-466">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e15c4-467">Применяется только при проверке подлинности `Individual` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-467">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="e15c4-468">URL-адрес API для вызова из веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="e15c4-468">URL of the API to call from the web app.</span></span> <span data-ttu-id="e15c4-469">Применяется только при проверке подлинности `SingleOrg` или `IndividualB2C` без указания узла ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e15c4-469">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="e15c4-470">Значение по умолчанию — `https://graph.microsoft.com/v1.0/me`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-470">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="e15c4-471">Указывает, вызывает ли веб-приложение Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="e15c4-471">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="e15c4-472">Применяется только при проверке подлинности `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-472">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="e15c4-473">Области для запроса вызова API из веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="e15c4-473">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="e15c4-474">Применяется только при проверке подлинности `SingleOrg` или `IndividualB2C` без указания узла ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e15c4-474">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="e15c4-475">Значение по умолчанию — `user.read`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-475">The default is `user.read`.</span></span>

***

### `web`

- **`--exclude-launch-settings`**

  <span data-ttu-id="e15c4-476">Исключает файл *launchSettings.json* из создаваемого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-476">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-477">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-477">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-478">Опция не доступна в .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="e15c4-478">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e15c4-479">В следующей таблице приведены значения по умолчанию в соответствии с версией пакета SDK, которую вы используете:</span><span class="sxs-lookup"><span data-stu-id="e15c4-479">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e15c4-480">Версия пакета SDK</span><span class="sxs-lookup"><span data-stu-id="e15c4-480">SDK version</span></span> | <span data-ttu-id="e15c4-481">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e15c4-481">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e15c4-482">5,0</span><span class="sxs-lookup"><span data-stu-id="e15c4-482">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e15c4-483">3.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-483">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e15c4-484">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-484">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e15c4-485">2.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-485">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="e15c4-486">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-486">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e15c4-487">Отключает протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e15c4-487">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="e15c4-488">`mvc`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="e15c4-488">`mvc`, `webapp`</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="e15c4-489">Тип проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-489">The type of authentication to use.</span></span> <span data-ttu-id="e15c4-490">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="e15c4-490">The possible values are:</span></span>

  - <span data-ttu-id="e15c4-491">`None` — без проверки подлинности (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="e15c4-491">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e15c4-492">`Individual` — индивидуальная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-492">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e15c4-493">`IndividualB2C` — индивидуальная проверка подлинности с помощью Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e15c4-493">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e15c4-494">`SingleOrg` — проверка подлинности организации для отдельного клиента.</span><span class="sxs-lookup"><span data-stu-id="e15c4-494">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e15c4-495">`MultiOrg` — проверка подлинности организации для нескольких клиентов.</span><span class="sxs-lookup"><span data-stu-id="e15c4-495">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="e15c4-496">`Windows` — проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="e15c4-496">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e15c4-497">Экземпляр Azure Active Directory B2C, к которому выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-497">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e15c4-498">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-498">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-499">Значение по умолчанию — `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-499">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e15c4-500">Идентификатор политики входа и регистрации для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-500">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e15c4-501">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-501">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="e15c4-502">Идентификатор политики сброса паролей для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-502">The reset password policy ID for this project.</span></span> <span data-ttu-id="e15c4-503">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-503">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="e15c4-504">Идентификатор политики изменения профилей для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-504">The edit profile policy ID for this project.</span></span> <span data-ttu-id="e15c4-505">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-505">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e15c4-506">Экземпляр Azure Active Directory, к которому выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-506">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e15c4-507">Используется с проверкой подлинности `SingleOrg` или `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-507">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e15c4-508">Значение по умолчанию — `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-508">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e15c4-509">Идентификатор клиента для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-509">The Client ID for this project.</span></span> <span data-ttu-id="e15c4-510">Используется с проверкой подлинности `IndividualB2C`, `SingleOrg` или `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-510">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e15c4-511">Значение по умолчанию — `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-511">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e15c4-512">Домен клиента каталога.</span><span class="sxs-lookup"><span data-stu-id="e15c4-512">The domain for the directory tenant.</span></span> <span data-ttu-id="e15c4-513">Используется с проверкой подлинности `SingleOrg` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-513">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-514">Значение по умолчанию — `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-514">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e15c4-515">Идентификатор TenantId каталога, к которому устанавливается подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-515">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e15c4-516">Используется с проверкой подлинности `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-516">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e15c4-517">Значение по умолчанию — `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-517">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="e15c4-518">Путь запроса по базовому пути кода URI перенаправления для приложения.</span><span class="sxs-lookup"><span data-stu-id="e15c4-518">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e15c4-519">Используется с проверкой подлинности `SingleOrg` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-520">Значение по умолчанию — `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-520">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e15c4-521">Предоставляет приложению доступ к каталогу для чтения.</span><span class="sxs-lookup"><span data-stu-id="e15c4-521">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e15c4-522">Применяется только при проверке подлинности `SingleOrg` или `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-522">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e15c4-523">Исключает файл *launchSettings.json* из создаваемого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-523">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e15c4-524">Отключает протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e15c4-524">Turns off HTTPS.</span></span> <span data-ttu-id="e15c4-525">Этот параметр применяется, только если `Individual`, `IndividualB2C`, `SingleOrg` или `MultiOrg` не используются.</span><span class="sxs-lookup"><span data-stu-id="e15c4-525">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e15c4-526">Указывает, что вместо SQLite следует использовать LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e15c4-526">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e15c4-527">Применяется только при проверке подлинности `Individual` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-527">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-528">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-529">Параметр доступен, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e15c4-529">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e15c4-530">В следующей таблице приведены значения по умолчанию в соответствии с версией пакета SDK, которую вы используете:</span><span class="sxs-lookup"><span data-stu-id="e15c4-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e15c4-531">Версия пакета SDK</span><span class="sxs-lookup"><span data-stu-id="e15c4-531">SDK version</span></span> | <span data-ttu-id="e15c4-532">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e15c4-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e15c4-533">5,0</span><span class="sxs-lookup"><span data-stu-id="e15c4-533">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e15c4-534">3.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e15c4-535">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-535">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="e15c4-536">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="e15c4-537">Включает BrowserLink в проект.</span><span class="sxs-lookup"><span data-stu-id="e15c4-537">Includes BrowserLink in the project.</span></span> <span data-ttu-id="e15c4-538">Опция не доступна в .NET Core 2.2 и 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="e15c4-538">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="e15c4-539">Определяет, настроен ли проект для использования [компиляции среды выполнения Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) в отладочных сборках.</span><span class="sxs-lookup"><span data-stu-id="e15c4-539">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="e15c4-540">Параметр доступен начиная с пакета SDK для .NET Core 3.1.201.</span><span class="sxs-lookup"><span data-stu-id="e15c4-540">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="e15c4-541">`angular`, `react`</span><span class="sxs-lookup"><span data-stu-id="e15c4-541">`angular`, `react`</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="e15c4-542">Тип проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-542">The type of authentication to use.</span></span> <span data-ttu-id="e15c4-543">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e15c4-543">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="e15c4-544">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="e15c4-544">The possible values are:</span></span>

  - <span data-ttu-id="e15c4-545">`None` — без проверки подлинности (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="e15c4-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e15c4-546">`Individual` — индивидуальная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-546">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e15c4-547">Исключает файл *launchSettings.json* из создаваемого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-547">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e15c4-548">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-548">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e15c4-549">Отключает протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e15c4-549">Turns off HTTPS.</span></span> <span data-ttu-id="e15c4-550">Данная опция применяется только в том случае, если проверкой подлинности является `None`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-550">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e15c4-551">Указывает, что вместо SQLite следует использовать LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e15c4-551">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e15c4-552">Применяется только при проверке подлинности `Individual` или `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-552">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-553">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e15c4-553">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-554">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-554">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-555">Опция не доступна в .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="e15c4-555">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e15c4-556">В следующей таблице приведены значения по умолчанию в соответствии с версией пакета SDK, которую вы используете:</span><span class="sxs-lookup"><span data-stu-id="e15c4-556">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e15c4-557">Версия пакета SDK</span><span class="sxs-lookup"><span data-stu-id="e15c4-557">SDK version</span></span> | <span data-ttu-id="e15c4-558">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e15c4-558">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e15c4-559">5,0</span><span class="sxs-lookup"><span data-stu-id="e15c4-559">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e15c4-560">3.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-560">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e15c4-561">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-561">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e15c4-562">2.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-562">2.1</span></span>         | `netcoreapp2.0` |

***

### `reactredux`

- **`--exclude-launch-settings`**

  <span data-ttu-id="e15c4-563">Исключает файл *launchSettings.json* из создаваемого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-563">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-564">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-564">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-565">Опция не доступна в .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="e15c4-565">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e15c4-566">В следующей таблице приведены значения по умолчанию в соответствии с версией пакета SDK, которую вы используете:</span><span class="sxs-lookup"><span data-stu-id="e15c4-566">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e15c4-567">Версия пакета SDK</span><span class="sxs-lookup"><span data-stu-id="e15c4-567">SDK version</span></span> | <span data-ttu-id="e15c4-568">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e15c4-568">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e15c4-569">5,0</span><span class="sxs-lookup"><span data-stu-id="e15c4-569">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e15c4-570">3.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-570">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e15c4-571">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-571">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e15c4-572">2.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-572">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="e15c4-573">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-573">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e15c4-574">Отключает протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e15c4-574">Turns off HTTPS.</span></span>

***

### `razorclasslib`

- **`--no-restore`**

  <span data-ttu-id="e15c4-575">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-575">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="e15c4-576">Поддерживает добавление традиционных страниц Razor и представлений в дополнение к компонентам этой библиотеки.</span><span class="sxs-lookup"><span data-stu-id="e15c4-576">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="e15c4-577">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e15c4-577">Available since .NET Core 3.0 SDK.</span></span>

***
  
### `webapi`

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="e15c4-578">Тип проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-578">The type of authentication to use.</span></span> <span data-ttu-id="e15c4-579">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="e15c4-579">The possible values are:</span></span>

  - <span data-ttu-id="e15c4-580">`None` — без проверки подлинности (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="e15c4-580">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e15c4-581">`IndividualB2C` — индивидуальная проверка подлинности с помощью Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e15c4-581">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e15c4-582">`SingleOrg` — проверка подлинности организации для отдельного клиента.</span><span class="sxs-lookup"><span data-stu-id="e15c4-582">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e15c4-583">`Windows` — проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="e15c4-583">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e15c4-584">Экземпляр Azure Active Directory B2C, к которому выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-584">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e15c4-585">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-585">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e15c4-586">Значение по умолчанию — `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-586">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e15c4-587">Идентификатор политики входа и регистрации для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-587">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e15c4-588">Используется с проверкой подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-588">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e15c4-589">Экземпляр Azure Active Directory, к которому выполняется подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-589">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e15c4-590">Используется с проверкой подлинности `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-590">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e15c4-591">Значение по умолчанию — `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-591">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e15c4-592">Идентификатор клиента для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="e15c4-592">The Client ID for this project.</span></span> <span data-ttu-id="e15c4-593">Используется с проверкой подлинности `IndividualB2C` или `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-593">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e15c4-594">Значение по умолчанию — `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-594">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e15c4-595">Домен клиента каталога.</span><span class="sxs-lookup"><span data-stu-id="e15c4-595">The domain for the directory tenant.</span></span> <span data-ttu-id="e15c4-596">Используется с проверкой подлинности `IndividualB2C` или `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-596">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e15c4-597">Значение по умолчанию — `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-597">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e15c4-598">Идентификатор TenantId каталога, к которому устанавливается подключение.</span><span class="sxs-lookup"><span data-stu-id="e15c4-598">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e15c4-599">Используется с проверкой подлинности `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-599">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e15c4-600">Значение по умолчанию — `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-600">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e15c4-601">Предоставляет приложению доступ к каталогу для чтения.</span><span class="sxs-lookup"><span data-stu-id="e15c4-601">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e15c4-602">Применяется только при проверке подлинности `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-602">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e15c4-603">Исключает файл *launchSettings.json* из создаваемого шаблона.</span><span class="sxs-lookup"><span data-stu-id="e15c4-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e15c4-604">Отключает протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e15c4-604">Turns off HTTPS.</span></span> <span data-ttu-id="e15c4-605">`app.UseHsts` и `app.UseHttpsRedirection` не добавляются к `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-605">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="e15c4-606">Этот параметр применяется, только если `IndividualB2C` или `SingleOrg` не используются для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="e15c4-606">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e15c4-607">Указывает, что вместо SQLite следует использовать LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e15c4-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e15c4-608">Применяется только при проверке подлинности `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e15c4-608">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e15c4-609">Указывает целевую [платформу](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-609">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e15c4-610">Опция не доступна в .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="e15c4-610">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e15c4-611">В следующей таблице приведены значения по умолчанию в соответствии с версией пакета SDK, которую вы используете:</span><span class="sxs-lookup"><span data-stu-id="e15c4-611">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e15c4-612">Версия пакета SDK</span><span class="sxs-lookup"><span data-stu-id="e15c4-612">SDK version</span></span> | <span data-ttu-id="e15c4-613">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e15c4-613">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e15c4-614">5,0</span><span class="sxs-lookup"><span data-stu-id="e15c4-614">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e15c4-615">3.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-615">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e15c4-616">3.0</span><span class="sxs-lookup"><span data-stu-id="e15c4-616">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e15c4-617">2.1</span><span class="sxs-lookup"><span data-stu-id="e15c4-617">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="e15c4-618">Во время создания проекта не выполняется неявное восстановление.</span><span class="sxs-lookup"><span data-stu-id="e15c4-618">Doesn't execute an implicit restore during project creation.</span></span>

***

### `globaljson`

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="e15c4-619">Задает версию пакета SDK для .NET, используемую в файле *global.json*.</span><span class="sxs-lookup"><span data-stu-id="e15c4-619">Specifies the version of the .NET SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="e15c4-620">Примеры</span><span class="sxs-lookup"><span data-stu-id="e15c4-620">Examples</span></span>

- <span data-ttu-id="e15c4-621">Создайте проект консольного приложения на C#, указав имя шаблона:</span><span class="sxs-lookup"><span data-stu-id="e15c4-621">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="e15c4-622">Создание проекта консольного приложения F# в текущем каталоге:</span><span class="sxs-lookup"><span data-stu-id="e15c4-622">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="e15c4-623">Создайте проект библиотеки классов .NET Standard в указанном каталоге:</span><span class="sxs-lookup"><span data-stu-id="e15c4-623">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="e15c4-624">Создайте новый проект MVC ASP.NET Core C# в текущем каталоге без проверки подлинности:</span><span class="sxs-lookup"><span data-stu-id="e15c4-624">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="e15c4-625">Создайте новый проект xUnit:</span><span class="sxs-lookup"><span data-stu-id="e15c4-625">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="e15c4-626">Перечислите все шаблоны, доступные для одностраничных приложений (SPA):</span><span class="sxs-lookup"><span data-stu-id="e15c4-626">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="e15c4-627">Список всех шаблонов, соответствующих подстроке *we*.</span><span class="sxs-lookup"><span data-stu-id="e15c4-627">List all templates matching the *we* substring.</span></span> <span data-ttu-id="e15c4-628">Точное совпадение не найдено, поэтому сравнение подстрок выполняется по короткому имени и столбцам имен.</span><span class="sxs-lookup"><span data-stu-id="e15c4-628">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="e15c4-629">Попытайтесь вызвать шаблон, соответствующий *ng*.</span><span class="sxs-lookup"><span data-stu-id="e15c4-629">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="e15c4-630">Если точное совпадение не найдено, выведите шаблоны с частичным совпадением.</span><span class="sxs-lookup"><span data-stu-id="e15c4-630">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="e15c4-631">Установите версию 2.0 шаблонов SPA для ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="e15c4-631">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="e15c4-632">Перечислите установленные шаблоны и подробную информацию о них, в том числе и о том, как их удалить:</span><span class="sxs-lookup"><span data-stu-id="e15c4-632">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="e15c4-633">Создайте *global.json* в текущем каталоге, установив версию SDK на 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="e15c4-633">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="e15c4-634">См. также</span><span class="sxs-lookup"><span data-stu-id="e15c4-634">See also</span></span>

- [<span data-ttu-id="e15c4-635">Пользовательские шаблоны для команды dotnet new</span><span class="sxs-lookup"><span data-stu-id="e15c4-635">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="e15c4-636">Создание пользовательского шаблона для dotnet</span><span class="sxs-lookup"><span data-stu-id="e15c4-636">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="e15c4-637">Репозиторий dotnet/dotnet-template-samples в GitHub</span><span class="sxs-lookup"><span data-stu-id="e15c4-637">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="e15c4-638">Доступные шаблоны для команды dotnet new</span><span class="sxs-lookup"><span data-stu-id="e15c4-638">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
