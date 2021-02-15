---
title: Обзор пакета SDK для проекта .NET
titleSuffix: ''
description: Сведения о пакетах SDK для проектов .NET.
ms.date: 09/17/2020
ms.topic: conceptual
ms.openlocfilehash: d0eb4291f4def9263f37d2d09f09ef43d40dfbac
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506400"
---
# <a name="net-project-sdks"></a><span data-ttu-id="3eccd-103">Пакеты SDK для проектов .NET</span><span class="sxs-lookup"><span data-stu-id="3eccd-103">.NET project SDKs</span></span>

<span data-ttu-id="3eccd-104">Проекты .NET Core и NET 5.0 и более поздних версий связаны с пакетом средств разработки программного обеспечения (SDK).</span><span class="sxs-lookup"><span data-stu-id="3eccd-104">.NET Core and .NET 5.0 and later projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="3eccd-105">Каждый *пакет SDK для проекта* является набором [целевых объектов](/visualstudio/msbuild/msbuild-targets) MSBuild и связанных [задач](/visualstudio/msbuild/msbuild-tasks), которые отвечают за компиляцию, упаковку и публикацию кода.</span><span class="sxs-lookup"><span data-stu-id="3eccd-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="3eccd-106">Проект, который ссылается на пакет SDK для проекта, иногда называется *проектом в стиле пакета SDK*.</span><span class="sxs-lookup"><span data-stu-id="3eccd-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="3eccd-107">Доступные пакеты SDK</span><span class="sxs-lookup"><span data-stu-id="3eccd-107">Available SDKs</span></span>

<span data-ttu-id="3eccd-108">Доступны следующие пакеты SDK:</span><span class="sxs-lookup"><span data-stu-id="3eccd-108">The following SDKs are available:</span></span>

| <span data-ttu-id="3eccd-109">ID</span><span class="sxs-lookup"><span data-stu-id="3eccd-109">ID</span></span> | <span data-ttu-id="3eccd-110">Описание</span><span class="sxs-lookup"><span data-stu-id="3eccd-110">Description</span></span> | <span data-ttu-id="3eccd-111">Репозиторий</span><span class="sxs-lookup"><span data-stu-id="3eccd-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="3eccd-112">Пакет SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="3eccd-112">The .NET SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="3eccd-113">[Веб-пакет SDK](/aspnet/core/razor-pages/web-sdk) для .NET</span><span class="sxs-lookup"><span data-stu-id="3eccd-113">The .NET [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="3eccd-114">[Пакет SDK Razor](/aspnet/core/razor-pages/sdk) для .NET</span><span class="sxs-lookup"><span data-stu-id="3eccd-114">The .NET [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="3eccd-115">Пакет SDK для службы рабочей роли в .NET</span><span class="sxs-lookup"><span data-stu-id="3eccd-115">The .NET Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="3eccd-116">Пакет SDK для WinForms и WPF\*</span><span class="sxs-lookup"><span data-stu-id="3eccd-116">The WinForms and WPF SDK\*</span></span> | <span data-ttu-id="3eccd-117"><https://github.com/dotnet/winforms> и <https://github.com/dotnet/wpf></span><span class="sxs-lookup"><span data-stu-id="3eccd-117"><https://github.com/dotnet/winforms> and <https://github.com/dotnet/wpf></span></span> |

<span data-ttu-id="3eccd-118">Пакет SDK для .NET является базовым пакетом SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="3eccd-118">The .NET SDK is the base SDK for .NET.</span></span> <span data-ttu-id="3eccd-119">Другие пакеты SDK ссылаются на пакет SDK для .NET, а проекты, связанные с другими пакетами SDK, имеют все доступные им свойства пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="3eccd-119">The other SDKs reference the .NET SDK, and projects that are associated with the other SDKs have all the .NET SDK properties available to them.</span></span> <span data-ttu-id="3eccd-120">Например, веб-пакет SDK зависит от пакета SDK для .NET и пакета SDK для Razor.</span><span class="sxs-lookup"><span data-stu-id="3eccd-120">The Web SDK, for example, depends on both the .NET SDK and the Razor SDK.</span></span>

<span data-ttu-id="3eccd-121">Можно также создать собственный пакет SDK и распространять его с помощью NuGet.</span><span class="sxs-lookup"><span data-stu-id="3eccd-121">You can also author your own SDK that can be distributed via NuGet.</span></span>

<span data-ttu-id="3eccd-122">\* Начиная с .NET 5.0, в проектах Windows Forms и Windows Presentation Foundation (WPF) необходимо указывать пакет SDK для .NET (`Microsoft.NET.Sdk`), а не `Microsoft.NET.Sdk.WindowsDesktop`.</span><span class="sxs-lookup"><span data-stu-id="3eccd-122">\* Starting in .NET 5.0, Windows Forms and Windows Presentation Foundation (WPF) projects should specify the .NET SDK (`Microsoft.NET.Sdk`) instead of `Microsoft.NET.Sdk.WindowsDesktop`.</span></span> <span data-ttu-id="3eccd-123">Если для параметра `TargetFramework` в таких проектах установить значение `net5.0-windows`, а для параметра `UseWPF` или `UseWindowsForms` — значение `true`, импорт пакета SDK для Windows Desktop будет выполняться автоматически.</span><span class="sxs-lookup"><span data-stu-id="3eccd-123">For these projects, setting `TargetFramework` to `net5.0-windows` and `UseWPF` or `UseWindowsForms` to `true` will automatically import the Windows desktop SDK.</span></span> <span data-ttu-id="3eccd-124">Если проект предназначен для .NET 5.0 или более поздней версии и в нем указан пакет SDK `Microsoft.NET.Sdk.WindowsDesktop`, при сборке отобразится предупреждение NETSDK1137.</span><span class="sxs-lookup"><span data-stu-id="3eccd-124">If your project targets .NET 5.0 or later and specifies the `Microsoft.NET.Sdk.WindowsDesktop` SDK, you'll get build warning NETSDK1137.</span></span>

## <a name="project-files"></a><span data-ttu-id="3eccd-125">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="3eccd-125">Project files</span></span>

<span data-ttu-id="3eccd-126">В основе проектов .NET лежит формат [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="3eccd-126">.NET projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="3eccd-127">Файлы проекта с такими расширениями, как *CPROJ* для проектов C# и *FPROJ* для проектов F#, имеют формат XML.</span><span class="sxs-lookup"><span data-stu-id="3eccd-127">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="3eccd-128">Корневым элементом файла проекта MSBuild является элемент [Project](/visualstudio/msbuild/project-element-msbuild).</span><span class="sxs-lookup"><span data-stu-id="3eccd-128">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="3eccd-129">Элемент `Project` имеет необязательный атрибут `Sdk`, указывающий, какой пакет SDK (и версию) следует использовать.</span><span class="sxs-lookup"><span data-stu-id="3eccd-129">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="3eccd-130">Чтобы использовать средства .NET и выполнить сборку кода, задайте в качестве значения атрибута `Sdk` один из идентификаторов, указанных в таблице[Доступные пакеты SDK](#available-sdks).</span><span class="sxs-lookup"><span data-stu-id="3eccd-130">To use the .NET tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="3eccd-131">Чтобы указать пакет SDK, который содержится в NuGet, добавьте версию в конец имени или укажите имя и версию в файле *global.json*.</span><span class="sxs-lookup"><span data-stu-id="3eccd-131">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="3eccd-132">Другим способом указания пакета SDK является элемент [Sdk](/visualstudio/msbuild/sdk-element-msbuild) верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="3eccd-132">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="3eccd-133">Указание пакета SDK одним из этих способов значительно упрощает файлы проекта для .NET.</span><span class="sxs-lookup"><span data-stu-id="3eccd-133">Referencing an SDK in one of these ways greatly simplifies project files for .NET.</span></span> <span data-ttu-id="3eccd-134">На этапе оценки проекта MSBuild добавляет неявные директивы импорта для `Sdk.props` в начале и для `Sdk.targets` в конце файла проекта.</span><span class="sxs-lookup"><span data-stu-id="3eccd-134">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="3eccd-135">На компьютере Windows файлы *Sdk.props* и *Sdk.targets* можно найти в папке *%ProgramFiles%\dotnet\sdk\\[версия]\Sdks\Microsoft.NET.Sdk\Sdk*.</span><span class="sxs-lookup"><span data-stu-id="3eccd-135">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="3eccd-136">Предварительная обработка файла проекта</span><span class="sxs-lookup"><span data-stu-id="3eccd-136">Preprocess the project file</span></span>

<span data-ttu-id="3eccd-137">Увидеть полностью развернутый проект так, как он отображается в MSBuild, можно после включения пакета SDK и его целевых объектов с помощью команды `dotnet msbuild -preprocess`.</span><span class="sxs-lookup"><span data-stu-id="3eccd-137">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="3eccd-138">Включите параметр [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) в команду [`dotnet msbuild`](../tools/dotnet-msbuild.md), чтобы просмотреть сведения об импортированных файлах, их источниках, вкладе в сборку без фактического создания проекта.</span><span class="sxs-lookup"><span data-stu-id="3eccd-138">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="3eccd-139">Если проект имеет несколько требуемых версий .NET Framework, результаты выполнения команды должны касаться только одной из них. Эту версию следует указать в качестве свойства MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3eccd-139">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="3eccd-140">Пример:</span><span class="sxs-lookup"><span data-stu-id="3eccd-140">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

## <a name="default-includes-and-excludes"></a><span data-ttu-id="3eccd-141">Включения и исключения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="3eccd-141">Default includes and excludes</span></span>

<span data-ttu-id="3eccd-142">В пакете SDK определены стандартные включения и исключения для [элементов `Compile`](/visualstudio/msbuild/common-msbuild-project-items#compile), [внедренных ресурсов](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource) и [элементов `None`](/visualstudio/msbuild/common-msbuild-project-items#none).</span><span class="sxs-lookup"><span data-stu-id="3eccd-142">The default includes and excludes for [`Compile` items](/visualstudio/msbuild/common-msbuild-project-items#compile), [embedded resources](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource), and [`None` items](/visualstudio/msbuild/common-msbuild-project-items#none) are defined in the SDK.</span></span> <span data-ttu-id="3eccd-143">В отличие от проектов .NET Framework без пакетов SDK в файле проекта не нужно указывать эти элементы, так как для наиболее распространенных вариантов использования действуют значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3eccd-143">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="3eccd-144">Такой подход позволяет уменьшить файлы проекта и без труда понимать их, а при необходимости даже вносить правки вручную.</span><span class="sxs-lookup"><span data-stu-id="3eccd-144">This behavior makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="3eccd-145">В следующей таблице показано, какие элементы и [стандартные маски](https://en.wikipedia.org/wiki/Glob_(programming)) включены в пакет SDK для .NET и исключены из него:</span><span class="sxs-lookup"><span data-stu-id="3eccd-145">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET SDK:</span></span>

| <span data-ttu-id="3eccd-146">Элемент</span><span class="sxs-lookup"><span data-stu-id="3eccd-146">Element</span></span>           | <span data-ttu-id="3eccd-147">Стандартная маска включения</span><span class="sxs-lookup"><span data-stu-id="3eccd-147">Include glob</span></span>                              | <span data-ttu-id="3eccd-148">Стандартная маска исключения</span><span class="sxs-lookup"><span data-stu-id="3eccd-148">Exclude glob</span></span>                                                  | <span data-ttu-id="3eccd-149">Стандартная маска удаления</span><span class="sxs-lookup"><span data-stu-id="3eccd-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="3eccd-150">Компилятор</span><span class="sxs-lookup"><span data-stu-id="3eccd-150">Compile</span></span>           | <span data-ttu-id="3eccd-151">\*\*/\*.cs (или другие расширения языка)</span><span class="sxs-lookup"><span data-stu-id="3eccd-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="3eccd-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="3eccd-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="3eccd-153">Н/Д</span><span class="sxs-lookup"><span data-stu-id="3eccd-153">N/A</span></span>                      |
| <span data-ttu-id="3eccd-154">ВнедренныйРесурс</span><span class="sxs-lookup"><span data-stu-id="3eccd-154">EmbeddedResource</span></span>  | <span data-ttu-id="3eccd-155">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="3eccd-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="3eccd-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="3eccd-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="3eccd-157">Н/Д</span><span class="sxs-lookup"><span data-stu-id="3eccd-157">N/A</span></span>                      |
| <span data-ttu-id="3eccd-158">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="3eccd-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="3eccd-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="3eccd-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="3eccd-160">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="3eccd-160">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="3eccd-161">Папки `./bin` и `./obj`, которые представлены свойствами MSBuild `$(BaseOutputPath)` и `$(BaseIntermediateOutputPath)`, исключаются из стандартных масок исключения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3eccd-161">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="3eccd-162">Исключения представлены свойством [DefaultItemExcludes](msbuild-props.md#defaultitemexcludes).</span><span class="sxs-lookup"><span data-stu-id="3eccd-162">Excludes are represented by the [DefaultItemExcludes property](msbuild-props.md#defaultitemexcludes).</span></span>

### <a name="build-errors"></a><span data-ttu-id="3eccd-163">Ошибки сборки</span><span class="sxs-lookup"><span data-stu-id="3eccd-163">Build errors</span></span>

<span data-ttu-id="3eccd-164">Если вы явным образом определите любой из этих элементов в файле проекта, скорее всего, произойдет ошибка сборки NETSDK1022 с примерно таким сообщением:</span><span class="sxs-lookup"><span data-stu-id="3eccd-164">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="3eccd-165">"Duplicate 'Compile' items were included.</span><span class="sxs-lookup"><span data-stu-id="3eccd-165">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="3eccd-166">The .NET SDK includes Compile items from your project directory by default.</span><span class="sxs-lookup"><span data-stu-id="3eccd-166">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="3eccd-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file. (Включены повторяющиеся элементы Compile. По умолчанию пакет SDK для .NET включает элементы Compile из каталога проекта. Можно удалить эти элементы из файла проекта или задать для свойства "EnableDefaultCompileItems" значение "false", чтобы явно включить их в файл проекта.)</span><span class="sxs-lookup"><span data-stu-id="3eccd-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="3eccd-168">"Duplicate 'EmbeddedResource' items were included.</span><span class="sxs-lookup"><span data-stu-id="3eccd-168">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="3eccd-169">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span><span class="sxs-lookup"><span data-stu-id="3eccd-169">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="3eccd-170">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file" (Включены повторяющиеся элементы EmbeddedResource. По умолчанию пакет SDK для .NET включает элементы EmbeddedResource из каталога проекта. Можно удалить эти элементы из файла проекта или задать для свойства EnableDefaultEmbeddedResourceItems значение false, чтобы явно включить их в файл проекта).</span><span class="sxs-lookup"><span data-stu-id="3eccd-170">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="3eccd-171">Чтобы устранить такую проблему, выполните любое из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="3eccd-171">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="3eccd-172">Удалите явно заданные элементы `Compile`, `EmbeddedResource` или `None`, которые совпадают с неявно заданными параметрами из предыдущей таблицы.</span><span class="sxs-lookup"><span data-stu-id="3eccd-172">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="3eccd-173">Присвойте [свойству EnableDefaultItems](msbuild-props.md#enabledefaultitems) значение `false`, чтобы отключить все неявные включения файлов:</span><span class="sxs-lookup"><span data-stu-id="3eccd-173">Set the [EnableDefaultItems property](msbuild-props.md#enabledefaultitems) to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="3eccd-174">Если вы хотите указать файлы, которые нужно публиковать вместе с приложением, для этого можно по-прежнему использовать привычные механизмы MSBuild (например, элемент `Content`).</span><span class="sxs-lookup"><span data-stu-id="3eccd-174">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="3eccd-175">Выборочно отключите только стандартные маски `Compile`, `EmbeddedResource` или `None`, присвоив свойствам [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems), [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems) или [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) значение `false`:</span><span class="sxs-lookup"><span data-stu-id="3eccd-175">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems), [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems), or [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="3eccd-176">Если вы отключите только стандартные маски `Compile`, обозреватель решений в Visual Studio будет по-прежнему отображать элементы \*.cs в составе проекта, включая их в виде элементов `None`.</span><span class="sxs-lookup"><span data-stu-id="3eccd-176">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="3eccd-177">Чтобы отключить неявную стандартную маску `None`, задайте свойству `EnableDefaultNoneItems` значение `false`.</span><span class="sxs-lookup"><span data-stu-id="3eccd-177">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="3eccd-178">Неявные ссылки на пакет</span><span class="sxs-lookup"><span data-stu-id="3eccd-178">Implicit package references</span></span>

<span data-ttu-id="3eccd-179">При использовании .NET Core 1.0–2.2 или .NET Standard 1.0–2.0 пакет SDK для .NET добавляет неявные ссылки на определенные *метапакеты*.</span><span class="sxs-lookup"><span data-stu-id="3eccd-179">When targeting .NET Core 1.0 - 2.2 or .NET Standard 1.0 - 2.0, the .NET SDK adds implicit references to certain *metapackages*.</span></span> <span data-ttu-id="3eccd-180">Метапакет — это пакет на основе платформы, который состоит только из зависимостей от других пакетов.</span><span class="sxs-lookup"><span data-stu-id="3eccd-180">A metapackage is a framework-based package that consists only of dependencies on other packages.</span></span> <span data-ttu-id="3eccd-181">Теперь неявные ссылки на метапакеты указываются в зависимости от целевой платформы, указанной в свойстве [TargetFramework](msbuild-props.md#targetframework) или [TargetFrameworks](msbuild-props.md#targetframeworks) файла проекта.</span><span class="sxs-lookup"><span data-stu-id="3eccd-181">Metapackages are implicitly referenced based on the target framework(s) specified in the [TargetFramework](msbuild-props.md#targetframework) or [TargetFrameworks](msbuild-props.md#targetframeworks) property of your project file.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp2.1</TargetFramework>
</PropertyGroup>
```

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="3eccd-182">При необходимости можно отключить неявные ссылки на пакеты с помощью свойства [DisableImplicitFrameworkReferences](msbuild-props.md#disableimplicitframeworkreferences) и добавить явные ссылки только на необходимые платформы или пакеты.</span><span class="sxs-lookup"><span data-stu-id="3eccd-182">If needed, you can disable implicit package references using the [DisableImplicitFrameworkReferences](msbuild-props.md#disableimplicitframeworkreferences) property, and add explicit references to just the frameworks or packages you need.</span></span>

<span data-ttu-id="3eccd-183">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="3eccd-183">Recommendations:</span></span>

- <span data-ttu-id="3eccd-184">При использовании .NET Framework, .NET Core 1.0–2.2 или .NET Standard 1.0–2.0 не добавляйте явную ссылку на метапакеты `Microsoft.NETCore.App` или `NETStandard.Library` через элемент `<PackageReference>` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="3eccd-184">When targeting .NET Framework, .NET Core 1.0 - 2.2, or .NET Standard 1.0 - 2.0, don't add an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span> <span data-ttu-id="3eccd-185">Для проектов .NET Core 1.0–2.2 и .NET Standard 1.0–2.0 ссылка на эти метапакеты неявно присутствует.</span><span class="sxs-lookup"><span data-stu-id="3eccd-185">For .NET Core 1.0 - 2.2 and .NET Standard 1.0 - 2.0 projects, these metapackages are implicitly referenced.</span></span> <span data-ttu-id="3eccd-186">Если при использовании проектов .NET Framework и пакета NuGet на основе .NET Standard требуется любая версия `NETStandard.Library`, NuGet автоматически устанавливает ее.</span><span class="sxs-lookup"><span data-stu-id="3eccd-186">For .NET Framework projects, if any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>
- <span data-ttu-id="3eccd-187">Если при использовании .NET Core 1.0–2.2 нужна определенная версия среды выполнения, вместо ссылки на метапакет следует использовать свойство `<RuntimeFrameworkVersion>` в проекте (например, `1.0.4`).</span><span class="sxs-lookup"><span data-stu-id="3eccd-187">If you need a specific version of the runtime when targeting .NET Core 1.0 - 2.2, use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span> <span data-ttu-id="3eccd-188">Например, может потребоваться специальная версия LTS среды выполнения 1.0.0, если вы используете [автономные развертывания](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="3eccd-188">For example, you might need a specific patch version of 1.0.0 LTS runtime if you're using [self-contained deployments](../deploying/index.md#publish-self-contained).</span></span>
- <span data-ttu-id="3eccd-189">Если при использовании .NET Standard 1.0–2.0 вам нужна конкретная версия метапакета `NETStandard.Library`, можно использовать свойство `<NetStandardImplicitPackageVersion>` и установить требуемую версию.</span><span class="sxs-lookup"><span data-stu-id="3eccd-189">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard 1.0 - 2.0, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>

## <a name="build-events"></a><span data-ttu-id="3eccd-190">События сборки</span><span class="sxs-lookup"><span data-stu-id="3eccd-190">Build events</span></span>

<span data-ttu-id="3eccd-191">Для проектов в стиле пакета SDK используйте целевой объект MSBuild с именем `PreBuild` или `PostBuild` и задайте свойство `BeforeTargets` для `PreBuild` или свойство `AfterTargets` для `PostBuild`.</span><span class="sxs-lookup"><span data-stu-id="3eccd-191">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>
> - <span data-ttu-id="3eccd-192">Для целевых объектов MSBuild можно использовать любые имена.</span><span class="sxs-lookup"><span data-stu-id="3eccd-192">You can use any name for the MSBuild targets.</span></span> <span data-ttu-id="3eccd-193">Однако интегрированная среда разработки Visual Studio распознает целевые объекты `PreBuild` и `PostBuild`, поэтому с помощью этих имен можно изменять команды в интегрированной среде разработки.</span><span class="sxs-lookup"><span data-stu-id="3eccd-193">However, the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so by using those names, you can edit the commands in the IDE.</span></span>
> - <span data-ttu-id="3eccd-194">Свойства `PreBuildEvent` и `PostBuildEvent` не рекомендуется использовать в проектах в стиле пакета SDK, поскольку такие макросы, как `$(ProjectDir)`, не разрешены.</span><span class="sxs-lookup"><span data-stu-id="3eccd-194">The properties `PreBuildEvent` and `PostBuildEvent` are not recommended in SDK-style projects, because macros such as `$(ProjectDir)` aren't resolved.</span></span> <span data-ttu-id="3eccd-195">Например, приведенный ниже код не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="3eccd-195">For example, the following code is not supported:</span></span>
>
> ```xml
> <PropertyGroup>
>   <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
> </PropertyGroup>
> ```

## <a name="customize-the-build"></a><span data-ttu-id="3eccd-196">Настройка сборки</span><span class="sxs-lookup"><span data-stu-id="3eccd-196">Customize the build</span></span>

<span data-ttu-id="3eccd-197">Существует несколько способов [настройки сборки](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="3eccd-197">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="3eccd-198">Может потребоваться переопределить свойство, передав его в качестве аргумента в команду [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) или [dotnet](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="3eccd-198">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="3eccd-199">Можно также добавить свойство в файл проекта или в файл *Directory.Build.props*.</span><span class="sxs-lookup"><span data-stu-id="3eccd-199">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="3eccd-200">Список полезных свойств для проектов .NET см. в статье [Справочник по MSBuild для проектов пакета SDK для .NET](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="3eccd-200">For a list of useful properties for .NET projects, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="3eccd-201">Пользовательские целевые объекты</span><span class="sxs-lookup"><span data-stu-id="3eccd-201">Custom targets</span></span>

<span data-ttu-id="3eccd-202">В проектах .NET доступна возможность упаковки пользовательских целевых объектов MSBuild и свойств для использования в проектах, применяющих этот пакет.</span><span class="sxs-lookup"><span data-stu-id="3eccd-202">.NET projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="3eccd-203">Используйте этот тип расширяемости, если нужно выполнить следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="3eccd-203">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="3eccd-204">расширить процесс сборки;</span><span class="sxs-lookup"><span data-stu-id="3eccd-204">Extend the build process.</span></span>
- <span data-ttu-id="3eccd-205">получить доступ к артефактам процесса сборки, таким как созданные файлы;</span><span class="sxs-lookup"><span data-stu-id="3eccd-205">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="3eccd-206">проверить конфигурацию, с которой была запущена сборка.</span><span class="sxs-lookup"><span data-stu-id="3eccd-206">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="3eccd-207">Чтобы добавить пользовательские целевые объекты или свойства сборки, нужно поместить файлы в форме `<package_id>.targets` или `<package_id>.props` (например, `Contoso.Utility.UsefulStuff.targets`) в папку *build* проекта.</span><span class="sxs-lookup"><span data-stu-id="3eccd-207">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="3eccd-208">Следующий XML-код является фрагментом из файла *CPROJ*, который указывает команде [`dotnet pack`](../tools/dotnet-pack.md), что именно нужно упаковать.</span><span class="sxs-lookup"><span data-stu-id="3eccd-208">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="3eccd-209">Элемент `<ItemGroup Label="dotnet pack instructions">` помещает файлы целевых объектов в папку *build* в пакете.</span><span class="sxs-lookup"><span data-stu-id="3eccd-209">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="3eccd-210">Элемент `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` помещает сборки и файлы *JSON* в папку *build*.</span><span class="sxs-lookup"><span data-stu-id="3eccd-210">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...

</Project>
```

<span data-ttu-id="3eccd-211">Чтобы использовать пользовательский целевой объект в проекте, добавьте элемент `PackageReference`, указывающий на пакет и его версию.</span><span class="sxs-lookup"><span data-stu-id="3eccd-211">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="3eccd-212">В отличие от средств пакет пользовательских целевых объектов входит в замыкание зависимостей исходного проекта.</span><span class="sxs-lookup"><span data-stu-id="3eccd-212">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="3eccd-213">Вы можете настроить способ использования пользовательского целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="3eccd-213">You can configure how to use the custom target.</span></span> <span data-ttu-id="3eccd-214">Так как это целевой объект MSBuild, он может зависеть от заданного целевого объекта, запускаться после другого целевого объекта или быть вызван вручную с помощью команды `dotnet msbuild -t:<target-name>`.</span><span class="sxs-lookup"><span data-stu-id="3eccd-214">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="3eccd-215">Однако для удобства пользователей можно объединить средства для отдельных проектов и пользовательские целевые объекты.</span><span class="sxs-lookup"><span data-stu-id="3eccd-215">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="3eccd-216">В этом сценарии средство для отдельного проекта принимает необходимые параметры и преобразует их в требуемый вызов [`dotnet msbuild`](../tools/dotnet-msbuild.md), который выполняет целевой объект.</span><span class="sxs-lookup"><span data-stu-id="3eccd-216">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="3eccd-217">Пример подобного типа синергии можно увидеть в репозитории [примеров хакатона MVP Summit 2016](https://github.com/dotnet/MVPSummitHackathon2016) в проекте [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).</span><span class="sxs-lookup"><span data-stu-id="3eccd-217">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="3eccd-218">См. также</span><span class="sxs-lookup"><span data-stu-id="3eccd-218">See also</span></span>

- <span data-ttu-id="3eccd-219">[установите .NET Core](../install/index.yml).</span><span class="sxs-lookup"><span data-stu-id="3eccd-219">[Install .NET Core](../install/index.yml)</span></span>
- [<span data-ttu-id="3eccd-220">Использование пакетов SDK проекта MSBuild</span><span class="sxs-lookup"><span data-stu-id="3eccd-220">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="3eccd-221">Упаковка пользовательских целевых объектов и свойств MSBuild с помощью NuGet</span><span class="sxs-lookup"><span data-stu-id="3eccd-221">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
