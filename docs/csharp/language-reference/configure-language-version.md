---
title: Управление версиями языка C# — руководство по C#
description: Дополнительные сведения о том, как версия языка C# определяется на основе вашего проекта и какие причины лежат в основе этого решения. Сведения о ручном переопределении значения по умолчанию.
ms.custom: updateeachrelease
ms.date: 08/11/2020
ms.openlocfilehash: e605979c185c476cd908ef4c7b3808f72ded0067
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104652975"
---
# <a name="c-language-versioning"></a><span data-ttu-id="cb895-104">Управление версиями языка C#</span><span class="sxs-lookup"><span data-stu-id="cb895-104">C# language versioning</span></span>

<span data-ttu-id="cb895-105">Компилятор C# последней версии определяет версию языка по умолчанию на основе целевой платформы или платформ проекта.</span><span class="sxs-lookup"><span data-stu-id="cb895-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="cb895-106">Visual Studio не предоставляет пользовательский интерфейс для изменения этого значения, но его можно изменить, отредактировав файл *CSPROJ*.</span><span class="sxs-lookup"><span data-stu-id="cb895-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="cb895-107">Выбор значения по умолчанию гарантирует, что вы используете последнюю версию языка, совместимую с вашей целевой платформой.</span><span class="sxs-lookup"><span data-stu-id="cb895-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="cb895-108">Вы получите преимущество в виде доступа к последним функциям языка, совместимым с целевым объектом проекта.</span><span class="sxs-lookup"><span data-stu-id="cb895-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="cb895-109">Этот вариант по умолчанию также гарантирует, что вы не будете использовать язык, который требует такие типы или поведение во время выполнения, которые недоступны в целевой платформе.</span><span class="sxs-lookup"><span data-stu-id="cb895-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="cb895-110">Выбор более новой версии языка, чем значение по умолчанию, может усложнить диагностику ошибок во время компиляции и выполнения.</span><span class="sxs-lookup"><span data-stu-id="cb895-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="cb895-111">Приведенные в этой статье правила относятся к компилятору, поставляемому с Visual Studio 2019, или к пакету SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="cb895-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET SDK.</span></span> <span data-ttu-id="cb895-112">Компиляторы C#, которые являются частью установки Visual Studio 2017 или более ранних версий пакета SDK для .NET Core предназначены для C# 7.0 по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="cb895-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="cb895-113">C# 8.0 поддерживается только в .NET Core 3.x и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="cb895-113">C# 8.0 is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="cb895-114">Для многих новых функций нужны функции среды выполнения и библиотеки, появившиеся в .NET Core 3. x:</span><span class="sxs-lookup"><span data-stu-id="cb895-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="cb895-115">[Для реализации интерфейса по умолчанию](../whats-new/csharp-8.md#default-interface-methods) требуются новые функции в среде CLR .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="cb895-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="cb895-116">Для [асинхронных потоков](../whats-new/csharp-8.md#asynchronous-streams) требуются новые типы <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> и <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb895-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="cb895-117">Для [индексов и диапазонов](../whats-new/csharp-8.md#indices-and-ranges) требуются новые типы <xref:System.Index?displayProperty=nameWithType> и <xref:System.Range?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb895-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="cb895-118">[Ссылочные типы, допускающие значение NULL](../whats-new/csharp-8.md#nullable-reference-types), используют несколько [атрибутов](attributes/nullable-analysis.md) для предоставления улучшенных предупреждений.</span><span class="sxs-lookup"><span data-stu-id="cb895-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="cb895-119">Эти атрибуты были добавлены в .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="cb895-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="cb895-120">Другие целевые платформы не были помечены ни одним из этих атрибутов.</span><span class="sxs-lookup"><span data-stu-id="cb895-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="cb895-121">Это означает, что предупреждения, допускающие значение NULL, могут неточно отражать потенциальные проблемы.</span><span class="sxs-lookup"><span data-stu-id="cb895-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

<span data-ttu-id="cb895-122">C# 9.0 поддерживается только в .NET 5 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="cb895-122">C# 9.0 is supported only on .NET 5 and newer versions.</span></span>

## <a name="defaults"></a><span data-ttu-id="cb895-123">Значения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="cb895-123">Defaults</span></span>

<span data-ttu-id="cb895-124">Компилятор определяет значение по умолчанию на основе следующих правил:</span><span class="sxs-lookup"><span data-stu-id="cb895-124">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="cb895-125">Целевая платформа</span><span class="sxs-lookup"><span data-stu-id="cb895-125">Target framework</span></span> | <span data-ttu-id="cb895-126">version</span><span class="sxs-lookup"><span data-stu-id="cb895-126">version</span></span> | <span data-ttu-id="cb895-127">Версия языка C# по умолчанию</span><span class="sxs-lookup"><span data-stu-id="cb895-127">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="cb895-128">.NET</span><span class="sxs-lookup"><span data-stu-id="cb895-128">.NET</span></span>             | <span data-ttu-id="cb895-129">5.x</span><span class="sxs-lookup"><span data-stu-id="cb895-129">5.x</span></span>     | <span data-ttu-id="cb895-130">C# 9.0</span><span class="sxs-lookup"><span data-stu-id="cb895-130">C# 9.0</span></span>                      |
| <span data-ttu-id="cb895-131">.NET Core</span><span class="sxs-lookup"><span data-stu-id="cb895-131">.NET Core</span></span>        | <span data-ttu-id="cb895-132">3.x</span><span class="sxs-lookup"><span data-stu-id="cb895-132">3.x</span></span>     | <span data-ttu-id="cb895-133">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="cb895-133">C# 8.0</span></span>                      |
| <span data-ttu-id="cb895-134">.NET Core</span><span class="sxs-lookup"><span data-stu-id="cb895-134">.NET Core</span></span>        | <span data-ttu-id="cb895-135">2.x</span><span class="sxs-lookup"><span data-stu-id="cb895-135">2.x</span></span>     | <span data-ttu-id="cb895-136">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="cb895-136">C# 7.3</span></span>                      |
| <span data-ttu-id="cb895-137">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="cb895-137">.NET Standard</span></span>    | <span data-ttu-id="cb895-138">2.1</span><span class="sxs-lookup"><span data-stu-id="cb895-138">2.1</span></span>     | <span data-ttu-id="cb895-139">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="cb895-139">C# 8.0</span></span>                      |
| <span data-ttu-id="cb895-140">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="cb895-140">.NET Standard</span></span>    | <span data-ttu-id="cb895-141">2.0</span><span class="sxs-lookup"><span data-stu-id="cb895-141">2.0</span></span>     | <span data-ttu-id="cb895-142">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="cb895-142">C# 7.3</span></span>                      |
| <span data-ttu-id="cb895-143">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="cb895-143">.NET Standard</span></span>    | <span data-ttu-id="cb895-144">1.x</span><span class="sxs-lookup"><span data-stu-id="cb895-144">1.x</span></span>     | <span data-ttu-id="cb895-145">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="cb895-145">C# 7.3</span></span>                      |
| <span data-ttu-id="cb895-146">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="cb895-146">.NET Framework</span></span>   | <span data-ttu-id="cb895-147">все</span><span class="sxs-lookup"><span data-stu-id="cb895-147">all</span></span>     | <span data-ttu-id="cb895-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="cb895-148">C# 7.3</span></span>                      |

<span data-ttu-id="cb895-149">Если проект предназначен для платформы в предварительной версии с поддержкой соответствующего языка в предварительной версии, будет использоваться язык, поддерживаемый в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="cb895-149">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="cb895-150">Вы можете использовать новейшие возможности в этой предварительной версии в любой среде, не затрагивая проекты, предназначенные для выпущенной версии .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb895-150">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb895-151">В Visual Studio 2017 во все создаваемые файлы проектов добавлялась запись `<LangVersion>latest</LangVersion>`.</span><span class="sxs-lookup"><span data-stu-id="cb895-151">Visual Studio 2017 added a `<LangVersion>latest</LangVersion>` entry to any project files it created.</span></span> <span data-ttu-id="cb895-152">На момент добавления последней считалась версия *C# 7.0*.</span><span class="sxs-lookup"><span data-stu-id="cb895-152">That meant *C# 7.0* when it was added.</span></span> <span data-ttu-id="cb895-153">Но после обновления до Visual Studio 2019 эта запись указывает на последнюю выпущенную версию, независимо от целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="cb895-153">However, once you upgrade to Visual Studio 2019, that means the latest released version, regardless of the target framework.</span></span> <span data-ttu-id="cb895-154">Теперь для этих проектов [переопределяется поведение по умолчанию](#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="cb895-154">These projects now [override the default behavior](#override-a-default).</span></span> <span data-ttu-id="cb895-155">Вам нужно изменить файл проекта и удалить этот узел.</span><span class="sxs-lookup"><span data-stu-id="cb895-155">You should edit the project file and remove that node.</span></span> <span data-ttu-id="cb895-156">После этого проект будет использовать версию компилятора, рекомендованную для вашей целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="cb895-156">Then, your project will use the compiler version recommended for your target framework.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="cb895-157">Переопределение значения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="cb895-157">Override a default</span></span>

<span data-ttu-id="cb895-158">Если необходимо явно указать версию C#, это можно сделать несколькими способами:</span><span class="sxs-lookup"><span data-stu-id="cb895-158">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="cb895-159">Вручную изменить [файл проекта](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="cb895-159">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="cb895-160">Задать версию языка [для нескольких проектов в подкаталоге](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="cb895-160">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="cb895-161">Настроить [параметр компилятора **LangVersion**](compiler-options/language.md#langversion).</span><span class="sxs-lookup"><span data-stu-id="cb895-161">Configure the [**LangVersion** compiler option](compiler-options/language.md#langversion).</span></span>

> [!TIP]
> <span data-ttu-id="cb895-162">Чтобы узнать, какую версию языка вы используете в данный момент, поставьте `#error version` (с учетом регистра) в коде.</span><span class="sxs-lookup"><span data-stu-id="cb895-162">To know what language version you're currently using, put `#error version` (case sensitive) in your code.</span></span> <span data-ttu-id="cb895-163">Это позволяет компилятору вывести ошибку CS8304 с сообщением, содержащим сведения об используемой версии компилятора и текущей выбранной версии языка.</span><span class="sxs-lookup"><span data-stu-id="cb895-163">This makes the compiler report a compiler error, CS8304, with a message containing the compiler version being used and the current selected language version.</span></span> <span data-ttu-id="cb895-164">Дополнительные сведения см. в статье [#error (справочник по C#)](preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="cb895-164">See [#error (C# Reference)](preprocessor-directives/preprocessor-error.md) for more information.</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="cb895-165">Изменение файла проекта</span><span class="sxs-lookup"><span data-stu-id="cb895-165">Edit the project file</span></span>

<span data-ttu-id="cb895-166">Версию языка можно задать в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="cb895-166">You can set the language version in your project file.</span></span> <span data-ttu-id="cb895-167">Например, если доступ к предварительной версии функций должен быть задан явным образом, можно добавить следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="cb895-167">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="cb895-168">Значение `preview` использует последнюю предварительную версию языка C#, которую поддерживает компилятор.</span><span class="sxs-lookup"><span data-stu-id="cb895-168">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="cb895-169">Настройка нескольких проектов</span><span class="sxs-lookup"><span data-stu-id="cb895-169">Configure multiple projects</span></span>

<span data-ttu-id="cb895-170">Чтобы настроить несколько проектов, вы можете создать файл **Directory.Build.props**, содержащий элемент `<LangVersion>`.</span><span class="sxs-lookup"><span data-stu-id="cb895-170">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="cb895-171">Обычно это делается в каталоге решения.</span><span class="sxs-lookup"><span data-stu-id="cb895-171">You typically do that in your solution directory.</span></span> <span data-ttu-id="cb895-172">Добавьте следующий код в файл **Directory.Build.props** в каталоге решения:</span><span class="sxs-lookup"><span data-stu-id="cb895-172">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="cb895-173">Сборки во всех подкаталогах каталога, который содержит этот файл, будут использовать предварительную версию C#.</span><span class="sxs-lookup"><span data-stu-id="cb895-173">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="cb895-174">Дополнительные сведения см. в статье [Настройка сборки](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="cb895-174">For more information, see [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="cb895-175">Справочник по версиям языка C#</span><span class="sxs-lookup"><span data-stu-id="cb895-175">C# language version reference</span></span>

<span data-ttu-id="cb895-176">В следующей таблице показаны все текущие версии языка C#.</span><span class="sxs-lookup"><span data-stu-id="cb895-176">The following table shows all current C# language versions.</span></span> <span data-ttu-id="cb895-177">Ваш компилятор может не распознавать все значения, если имеет более раннюю версию.</span><span class="sxs-lookup"><span data-stu-id="cb895-177">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="cb895-178">При установке .последней версии пакета SDK для .NET вы получаете доступ ко всем значениям в таблице.</span><span class="sxs-lookup"><span data-stu-id="cb895-178">If you install the latest .NET SDK, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="cb895-179">Откройте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell) и выполните следующую команду, чтобы просмотреть список версий языка, доступных на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="cb895-179">Open [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="cb895-180">В ответ на запрос параметра компиляции [\*\*LangVersion](compiler-options/language.md#langversion) такого типа выводится примерно следующее:</span><span class="sxs-lookup"><span data-stu-id="cb895-180">Querying the [\*\*LangVersion](compiler-options/language.md#langversion) compile option like this prints something similar to the following:</span></span>
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0
> 9.0 (default)
> latestmajor
> preview
> latest
> ```
