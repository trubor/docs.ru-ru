---
title: Свойства MSBuild для Microsoft.NET.Sdk
description: Справочник по свойствам и элементам MSBuild, распознаваемым пакетом SDK для .NET.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: e140491c694291438fe1db7fd60d581ffed0319d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802675"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="a1841-103">Справочник по MSBuild для проектов пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="a1841-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="a1841-104">Эта страница содержит справочные сведения о свойствах и элементах MSBuild, которые вы можете использовать для настройки проектов .NET.</span><span class="sxs-lookup"><span data-stu-id="a1841-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="a1841-105">Работа над этой страницей еще не завершена, поэтому здесь приведены лишь некоторые полезные свойства MSBuild для пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="a1841-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="a1841-106">Список стандартных свойств см. в статье [Общие свойства MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="a1841-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="a1841-107">Свойства платформы</span><span class="sxs-lookup"><span data-stu-id="a1841-107">Framework properties</span></span>

- [<span data-ttu-id="a1841-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="a1841-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="a1841-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="a1841-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="a1841-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="a1841-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="a1841-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="a1841-111">TargetFramework</span></span>

<span data-ttu-id="a1841-112">Свойство `TargetFramework` определяет версию целевой платформы для приложения.</span><span class="sxs-lookup"><span data-stu-id="a1841-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="a1841-113">Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="a1841-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="a1841-114">Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="a1841-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="a1841-115">TargetFrameworks</span></span>

<span data-ttu-id="a1841-116">Используйте свойство `TargetFrameworks`, если приложение должно быть предназначено для нескольких платформ.</span><span class="sxs-lookup"><span data-stu-id="a1841-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="a1841-117">Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="a1841-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="a1841-118">Это свойство игнорируется, если указано свойство `TargetFramework` (в единственном числе).</span><span class="sxs-lookup"><span data-stu-id="a1841-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="a1841-119">Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="a1841-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="a1841-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="a1841-121">Это свойство применяется только к проектам, использующим `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="a1841-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="a1841-122">Он не применяется к проектам, использующим `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="a1841-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="a1841-123">Используйте свойство `NetStandardImplicitPackageVersion`, если вам нужно указать версию платформы ниже версии метапакета.</span><span class="sxs-lookup"><span data-stu-id="a1841-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="a1841-124">Файл проекта, приведенный в следующем примере, предназначен для `netstandard1.3`, но использует `NETStandard.Library` версии 1.6.0.</span><span class="sxs-lookup"><span data-stu-id="a1841-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="a1841-125">Свойства пакета</span><span class="sxs-lookup"><span data-stu-id="a1841-125">Package properties</span></span>

<span data-ttu-id="a1841-126">Для описания пакета, созданного из проекта, можно указать такие свойства, как `PackageId`, `PackageVersion`, `PackageIcon`, `Title` и `Description`.</span><span class="sxs-lookup"><span data-stu-id="a1841-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="a1841-127">Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект пакета](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="a1841-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-items-and-metadata"></a><span data-ttu-id="a1841-128">Публикация свойств, элементов и метаданных</span><span class="sxs-lookup"><span data-stu-id="a1841-128">Publish properties, items, and metadata</span></span>

- [<span data-ttu-id="a1841-129">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="a1841-129">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="a1841-130">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="a1841-130">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="a1841-131">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="a1841-131">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="a1841-132">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="a1841-132">CopyToPublishDirectory</span></span>](#copytopublishdirectory)
- [<span data-ttu-id="a1841-133">LinkBase</span><span class="sxs-lookup"><span data-stu-id="a1841-133">LinkBase</span></span>](#linkbase)
- [<span data-ttu-id="a1841-134">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="a1841-134">PreserveCompilationContext</span></span>](#preservecompilationcontext)
- [<span data-ttu-id="a1841-135">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="a1841-135">PreserveCompilationReferences</span></span>](#preservecompilationreferences)
- [<span data-ttu-id="a1841-136">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="a1841-136">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="a1841-137">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="a1841-137">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="a1841-138">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="a1841-138">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="a1841-139">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="a1841-139">UseAppHost</span></span>](#useapphost)

### <a name="copytopublishdirectory"></a><span data-ttu-id="a1841-140">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="a1841-140">CopyToPublishDirectory</span></span>

<span data-ttu-id="a1841-141">Метаданные `CopyToPublishDirectory` в элементах управления MSBuild, когда элемент копируется в каталог публикации.</span><span class="sxs-lookup"><span data-stu-id="a1841-141">The `CopyToPublishDirectory` metadata on an MSBuild item controls when the item is copied to the publish directory.</span></span> <span data-ttu-id="a1841-142">Допустимые значения: `PreserveNewest`, при котором копируется только элемент, если он был изменен, `Always`, при котором всегда копируется элемент, и `Never`, при котором элемент никогда не копируется.</span><span class="sxs-lookup"><span data-stu-id="a1841-142">Allowable values are `PreserveNewest`, which only copies the item if it has changed, `Always`, which always copies the item, and `Never`, which never copies the item.</span></span> <span data-ttu-id="a1841-143">С точки зрения производительности `PreserveNewest` предпочтительнее, поскольку включает инкрементную сборку.</span><span class="sxs-lookup"><span data-stu-id="a1841-143">From a performance standpoint, `PreserveNewest` is preferable because it enables an incremental build.</span></span>

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a><span data-ttu-id="a1841-144">LinkBase</span><span class="sxs-lookup"><span data-stu-id="a1841-144">LinkBase</span></span>

<span data-ttu-id="a1841-145">Для элемента, находящегося за пределами каталога проекта и его подкаталогов, целевой объект публикации использует [метаданные Link](/visualstudio/msbuild/common-msbuild-item-metadata) элемента, чтобы определить, куда копировать элемент.</span><span class="sxs-lookup"><span data-stu-id="a1841-145">For an item that's outside of the project directory and its subdirectories, the publish target uses the item's [Link metadata](/visualstudio/msbuild/common-msbuild-item-metadata) to determine where to copy the item to.</span></span> <span data-ttu-id="a1841-146">`Link` также определяет, как элементы за пределами дерева проекта отображаются в окне обозревателя решений Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1841-146">`Link` also determines how items outside of the project tree are displayed in the Solution Explorer window of Visual Studio.</span></span>

<span data-ttu-id="a1841-147">Если для элемента, находящегося за пределами проекта, `Link` не указан, по умолчанию используется `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span><span class="sxs-lookup"><span data-stu-id="a1841-147">If `Link` is not specified for an item that's outside of the project cone, it defaults to `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span></span> <span data-ttu-id="a1841-148">`LinkBase` позволяет указать допустимую базовую папку для элементов за пределами проекта.</span><span class="sxs-lookup"><span data-stu-id="a1841-148">`LinkBase` lets you specify a sensible base folder for items outside of the project cone.</span></span> <span data-ttu-id="a1841-149">Иерархия папок в базовой папке обеспечивается с помощью `RecursiveDir`.</span><span class="sxs-lookup"><span data-stu-id="a1841-149">The folder hierarchy under the base folder is preserved via `RecursiveDir`.</span></span> <span data-ttu-id="a1841-150">Если параметр `LinkBase` не указан, он опускается в пути `Link`.</span><span class="sxs-lookup"><span data-stu-id="a1841-150">If `LinkBase` is not specified, it's omitted from the `Link` path.</span></span>

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

<span data-ttu-id="a1841-151">На следующем рисунке показано, как файл, который включен с помощью стандартной маски предыдущего элемента `Include`, отображается в обозревателе решений.</span><span class="sxs-lookup"><span data-stu-id="a1841-151">The following image shows how a file that's included via the previous item `Include` glob displays in Solution Explorer.</span></span>

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Обозреватель решений: элемент с метаданными LinkBase.":::

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="a1841-153">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="a1841-153">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="a1841-154">Свойство `AppendTargetFrameworkToOutputPath` определяет, добавляется ли [моникер целевой платформы (TFM)](../../standard/frameworks.md) к выходному пути (который определяется свойством [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span><span class="sxs-lookup"><span data-stu-id="a1841-154">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="a1841-155">Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть).</span><span class="sxs-lookup"><span data-stu-id="a1841-155">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="a1841-156">При установке значения `false` для свойства `AppendTargetFrameworkToOutputPath` TFM не добавляется к выходному пути.</span><span class="sxs-lookup"><span data-stu-id="a1841-156">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="a1841-157">Однако при отсутствии TFM в выходном пути несколько артефактов сборки могут перезаписывать друг друга.</span><span class="sxs-lookup"><span data-stu-id="a1841-157">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="a1841-158">Например, при установке следующего параметра выходной путь для приложения .NET 5.0 изменяется с `bin\Debug\net5.0` на `bin\Debug`:</span><span class="sxs-lookup"><span data-stu-id="a1841-158">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="a1841-159">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="a1841-159">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="a1841-160">Свойство `AppendRuntimeIdentifierToOutputPath` определяет, добавляется ли к выходному пути [идентификатор среды выполнения (RID)](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-160">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="a1841-161">Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть).</span><span class="sxs-lookup"><span data-stu-id="a1841-161">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="a1841-162">При установке значения `false` для свойства `AppendRuntimeIdentifierToOutputPath` RID не добавляется к выходному пути.</span><span class="sxs-lookup"><span data-stu-id="a1841-162">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="a1841-163">Например, при установке следующего параметра выходной путь для приложения .NET 5.0 и идентификатора RID `win10-x64` изменяется с `bin\Debug\net5.0\win10-x64` на `bin\Debug\net5.0`:</span><span class="sxs-lookup"><span data-stu-id="a1841-163">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="a1841-164">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="a1841-164">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="a1841-165">Свойство `CopyLocalLockFileAssemblies` полезно для проектов подключаемых модулей, которые имеют зависимости от других библиотек.</span><span class="sxs-lookup"><span data-stu-id="a1841-165">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="a1841-166">Если для этого свойства задано значение `true`, все зависимости пакета NuGet копируются в выходной каталог.</span><span class="sxs-lookup"><span data-stu-id="a1841-166">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="a1841-167">Это означает, что вы можете использовать выходные данные `dotnet build` для запуска подключаемого модуля на любом компьютере.</span><span class="sxs-lookup"><span data-stu-id="a1841-167">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="a1841-168">Кроме того, можно использовать `dotnet publish` для публикации библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="a1841-168">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="a1841-169">Дополнительные сведения см. в разделе [dotnet publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-169">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="preservecompilationcontext"></a><span data-ttu-id="a1841-170">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="a1841-170">PreserveCompilationContext</span></span>

<span data-ttu-id="a1841-171">Свойство `PreserveCompilationContext` позволяет собранному или опубликованному приложению компилировать дополнительный код во время выполнения с теми же параметрами, которые использовались во время сборки.</span><span class="sxs-lookup"><span data-stu-id="a1841-171">The `PreserveCompilationContext` property allows a built or published application to compile more code at run time using the same settings that were used at build time.</span></span> <span data-ttu-id="a1841-172">Сборки, ссылки на которые были указаны во время сборки, будут скопированы в подкаталог *ref* выходного каталога.</span><span class="sxs-lookup"><span data-stu-id="a1841-172">The assemblies referenced at build time will be copied into the *ref* subdirectory of the output directory.</span></span> <span data-ttu-id="a1841-173">Имена базовых сборок хранятся в файле *.deps.json* приложения вместе с параметрами, передаваемыми компилятору.</span><span class="sxs-lookup"><span data-stu-id="a1841-173">The names of the reference assemblies are stored in the application's *.deps.json* file along with the options passed to the compiler.</span></span> <span data-ttu-id="a1841-174">Эту информацию можно получить с помощью свойств <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> и <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a1841-174">You can retrieve this information using the <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> and <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> properties.</span></span>

<span data-ttu-id="a1841-175">Эта функциональность в основном используется внутри системы для поддержки компиляции файлов Razor во время выполнения на страницах MVC и Razor ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1841-175">This functionality is mostly used internally by ASP.NET Core MVC and Razor pages to support run-time compilation of Razor files.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a><span data-ttu-id="a1841-176">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="a1841-176">PreserveCompilationReferences</span></span>

<span data-ttu-id="a1841-177">Свойство `PreserveCompilationReferences` аналогично свойству [PreserveCompilationContext](#preservecompilationcontext) за исключением того, что при его использовании в каталог публикации копируются только указанные ссылками сборки, но не копируется файл *.deps.json*.</span><span class="sxs-lookup"><span data-stu-id="a1841-177">The `PreserveCompilationReferences` property is similar to the [PreserveCompilationContext](#preservecompilationcontext) property, except that it only copies the referenced assemblies to the publish directory, and not the *.deps.json* file.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

<span data-ttu-id="a1841-178">Дополнительные сведения см. в разделе [Свойства пакета SDK Razor](/aspnet/core/razor-pages/sdk#properties).</span><span class="sxs-lookup"><span data-stu-id="a1841-178">For more information, see [Razor SDK properties](/aspnet/core/razor-pages/sdk#properties).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="a1841-179">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="a1841-179">RuntimeIdentifier</span></span>

<span data-ttu-id="a1841-180">Свойство `RuntimeIdentifier` позволяет указать для проекта один [идентификатор среды выполнения (RID)](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-180">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a1841-181">Идентификатор среды выполнения позволяет опубликовать автономное развертывание.</span><span class="sxs-lookup"><span data-stu-id="a1841-181">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="a1841-182">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="a1841-182">RuntimeIdentifiers</span></span>

<span data-ttu-id="a1841-183">Свойство `RuntimeIdentifiers` позволяет указать для проекта список [идентификаторов среды выполнения (RID)](../rid-catalog.md) (в качестве разделителя используется точка с запятой).</span><span class="sxs-lookup"><span data-stu-id="a1841-183">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a1841-184">Используйте это свойство, если вам нужна публикация для нескольких сред.</span><span class="sxs-lookup"><span data-stu-id="a1841-184">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="a1841-185">`RuntimeIdentifiers` используется во время восстановления для обеспечения наличия в графе нужных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a1841-185">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="a1841-186">`RuntimeIdentifier` (в единственном числе) может ускорить создание сборок, когда требуется только одна среда выполнения.</span><span class="sxs-lookup"><span data-stu-id="a1841-186">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="a1841-187">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="a1841-187">TrimmerRootAssembly</span></span>

<span data-ttu-id="a1841-188">Элемент `TrimmerRootAssembly` позволяет исключить сборку из [*обрезки*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-188">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="a1841-189">Обрезка — это процесс удаления неиспользуемых частей среды выполнения из упакованного приложения.</span><span class="sxs-lookup"><span data-stu-id="a1841-189">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="a1841-190">В некоторых случаях при обрезке могут неправильно удаляться необходимые ссылки.</span><span class="sxs-lookup"><span data-stu-id="a1841-190">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="a1841-191">Следующий код XML исключает сборку `System.Security` из обрезки.</span><span class="sxs-lookup"><span data-stu-id="a1841-191">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="a1841-192">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="a1841-192">UseAppHost</span></span>

<span data-ttu-id="a1841-193">Свойство `UseAppHost` контролирует создание собственного исполняемого файла для развертывания.</span><span class="sxs-lookup"><span data-stu-id="a1841-193">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="a1841-194">Этот файл требуется для автономных развертываний.</span><span class="sxs-lookup"><span data-stu-id="a1841-194">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="a1841-195">В .NET Core 3.0 и более поздних версиях зависимый от платформы исполняемый файл создается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a1841-195">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="a1841-196">Задайте свойству `UseAppHost` значение `false`, чтобы отключить создание исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="a1841-196">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="a1841-197">Дополнительные сведения см. в статье о [развертывании приложений .NET](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-197">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="a1841-198">Свойства компиляции</span><span class="sxs-lookup"><span data-stu-id="a1841-198">Compile properties</span></span>

- [<span data-ttu-id="a1841-199">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="a1841-199">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="a1841-200">LangVersion</span><span class="sxs-lookup"><span data-stu-id="a1841-200">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="a1841-201">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="a1841-201">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="a1841-202">Свойство `EmbeddedResourceUseDependentUponConvention` определяет, будет ли использоваться информация о типах в исходных файлах, расположенных в одной папке с файлами ресурсов, для создания имен файлов манифеста этих ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a1841-202">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="a1841-203">Например, если *Form1.resx* находится в той же папке, что и *Form1.cs*, а `EmbeddedResourceUseDependentUponConvention` имеет значение `true`, то созданному файл *.resources* присваивается имя на основе имени первого типа, определенного в файле *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="a1841-203">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="a1841-204">Например, если первым типом в файле *Form1.cs* является `MyNamespace.Form1`, созданному файлу присваивается имя *MyNamespace.Form1.resources*.</span><span class="sxs-lookup"><span data-stu-id="a1841-204">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="a1841-205">Если для `EmbeddedResource` элемента заданы метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого файла ресурсов будет создаваться на основе таких метаданных.</span><span class="sxs-lookup"><span data-stu-id="a1841-205">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="a1841-206">По умолчанию для нового проекта .NET этому свойству задается значение `true`.</span><span class="sxs-lookup"><span data-stu-id="a1841-206">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="a1841-207">Если задано значение `false` и для элемента `EmbeddedResource` в файле проекта не указаны метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого ресурса будет основано на имени корневого пространства имен проекта и относительном пути к файлу *.resx*.</span><span class="sxs-lookup"><span data-stu-id="a1841-207">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="a1841-208">Дополнительные сведения об определение имени файла манифеста см. [здесь](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-208">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="a1841-209">LangVersion</span><span class="sxs-lookup"><span data-stu-id="a1841-209">LangVersion</span></span>

<span data-ttu-id="a1841-210">Свойство `LangVersion` позволяет указать конкретную версию языка программирования.</span><span class="sxs-lookup"><span data-stu-id="a1841-210">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="a1841-211">Например, если требуется доступ к предварительным версиям функций C#, задайте параметру `LangVersion` значение `preview`.</span><span class="sxs-lookup"><span data-stu-id="a1841-211">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="a1841-212">Дополнительные сведения см. в статье [Управление версиями языка C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="a1841-212">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="a1841-213">Свойства включения элементов по умолчанию</span><span class="sxs-lookup"><span data-stu-id="a1841-213">Default item inclusion properties</span></span>

- [<span data-ttu-id="a1841-214">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="a1841-214">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="a1841-215">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="a1841-215">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="a1841-216">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="a1841-216">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="a1841-217">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="a1841-217">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="a1841-218">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="a1841-218">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="a1841-219">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="a1841-219">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="a1841-220">Дополнительные сведения см. в разделе [Включения и исключения по умолчанию](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="a1841-220">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="a1841-221">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="a1841-221">DefaultItemExcludes</span></span>

<span data-ttu-id="a1841-222">Используйте свойство `DefaultItemExcludes`, чтобы определить стандартные маски для файлов и папок, которые должны быть исключены из стандартных масок включения, исключения и удаления.</span><span class="sxs-lookup"><span data-stu-id="a1841-222">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="a1841-223">По умолчанию папки *./bin* и *./obj* исключаются из стандартных масок.</span><span class="sxs-lookup"><span data-stu-id="a1841-223">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="a1841-224">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="a1841-224">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="a1841-225">Используйте свойство `DefaultExcludesInProjectFolder`, чтобы определить стандартные маски для файлов и папок в папке проекта, которые должны быть исключены из стандартных масок включения, исключения и удаления.</span><span class="sxs-lookup"><span data-stu-id="a1841-225">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="a1841-226">По умолчанию папки, начинающиеся с точки (`.`), такие как *.git* и *.vs*, исключаются из стандартных масок.</span><span class="sxs-lookup"><span data-stu-id="a1841-226">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="a1841-227">Это свойство очень похоже на свойство `DefaultItemExcludes`, за исключением того, что оно учитывает только файлы и папки в папке проекта.</span><span class="sxs-lookup"><span data-stu-id="a1841-227">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="a1841-228">Если стандартная маска будет случайно соответствовать элементам за пределами папки проекта с относительным путем, используйте свойство `DefaultExcludesInProjectFolder` вместо свойства `DefaultItemExcludes`.</span><span class="sxs-lookup"><span data-stu-id="a1841-228">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="a1841-229">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="a1841-229">EnableDefaultItems</span></span>

<span data-ttu-id="a1841-230">Свойство `EnableDefaultItems` определяет, включаются ли в проект неявным образом элементы компиляции, элементы внедренных ресурсов и элементы `None`.</span><span class="sxs-lookup"><span data-stu-id="a1841-230">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="a1841-231">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="a1841-231">The default value is `true`.</span></span> <span data-ttu-id="a1841-232">Задайте значение `false` для свойства `EnableDefaultItems`, чтобы отключить все неявные включения файлов.</span><span class="sxs-lookup"><span data-stu-id="a1841-232">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="a1841-233">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="a1841-233">EnableDefaultCompileItems</span></span>

<span data-ttu-id="a1841-234">Свойство `EnableDefaultCompileItems` определяет, включаются ли в проект неявным образом элементы компиляции.</span><span class="sxs-lookup"><span data-stu-id="a1841-234">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="a1841-235">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="a1841-235">The default value is `true`.</span></span> <span data-ttu-id="a1841-236">Задайте значение `false` для свойства `EnableDefaultCompileItems`, чтобы отключить неявное включение файлов \*.cs и других файлов расширения языка.</span><span class="sxs-lookup"><span data-stu-id="a1841-236">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="a1841-237">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="a1841-237">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="a1841-238">Свойство `EnableDefaultEmbeddedResourceItems` определяет, включаются ли в проект неявным образом элементы внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a1841-238">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="a1841-239">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="a1841-239">The default value is `true`.</span></span> <span data-ttu-id="a1841-240">Задайте значение `false` для свойства `EnableDefaultEmbeddedResourceItems`, чтобы отключить неявное включение файлов внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a1841-240">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="a1841-241">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="a1841-241">EnableDefaultNoneItems</span></span>

<span data-ttu-id="a1841-242">Свойство `EnableDefaultNoneItems` определяет, включаются ли в проект неявным образом элементы `None` (файлы, которые не играют никакой роли в процессе сборки).</span><span class="sxs-lookup"><span data-stu-id="a1841-242">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="a1841-243">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="a1841-243">The default value is `true`.</span></span> <span data-ttu-id="a1841-244">Задайте значение `false` для свойства `EnableDefaultNoneItems`, чтобы отключить неявное включение элементов `None`.</span><span class="sxs-lookup"><span data-stu-id="a1841-244">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="a1841-245">Свойства анализа кода</span><span class="sxs-lookup"><span data-stu-id="a1841-245">Code analysis properties</span></span>

- [<span data-ttu-id="a1841-246">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="a1841-246">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="a1841-247">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="a1841-247">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="a1841-248">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="a1841-248">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="a1841-249">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="a1841-249">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="a1841-250">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="a1841-250">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="a1841-251">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="a1841-251">AnalysisLevel</span></span>

<span data-ttu-id="a1841-252">Свойство `AnalysisLevel` позволяет указать уровень анализа кода.</span><span class="sxs-lookup"><span data-stu-id="a1841-252">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="a1841-253">Например, если требуется доступ к анализаторам кода предварительной версии, задайте для параметра `AnalysisLevel` значение `preview`.</span><span class="sxs-lookup"><span data-stu-id="a1841-253">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span>

<span data-ttu-id="a1841-254">Значение по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="a1841-254">Default value:</span></span>

- <span data-ttu-id="a1841-255">Если проект предназначен для .NET 5.0 или более поздней версии или если вы добавили свойство [AnalysisMode](#analysismode), значением по умолчанию будет `latest`.</span><span class="sxs-lookup"><span data-stu-id="a1841-255">If your project targets .NET 5.0 or later, or if you've added the [AnalysisMode](#analysismode) property, the default value is `latest`.</span></span>
- <span data-ttu-id="a1841-256">В противном случае это свойство не будет учитываться, если оно явно не добавлено в файл проекта.</span><span class="sxs-lookup"><span data-stu-id="a1841-256">Otherwise, this property is omitted unless you explicitly add it to the project file.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="a1841-257">В следующей таблице приведены доступные параметры.</span><span class="sxs-lookup"><span data-stu-id="a1841-257">The following table shows the available options.</span></span>

| <span data-ttu-id="a1841-258">Значение</span><span class="sxs-lookup"><span data-stu-id="a1841-258">Value</span></span> | <span data-ttu-id="a1841-259">Значение</span><span class="sxs-lookup"><span data-stu-id="a1841-259">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="a1841-260">Используются новейшие анализаторы кода, которые были выпущены.</span><span class="sxs-lookup"><span data-stu-id="a1841-260">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="a1841-261">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a1841-261">This is the default.</span></span> |
| `preview` | <span data-ttu-id="a1841-262">Используются новейшие анализаторы кода, даже если они находятся на этапе предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="a1841-262">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="a1841-263">Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила.</span><span class="sxs-lookup"><span data-stu-id="a1841-263">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="a1841-264">Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила.</span><span class="sxs-lookup"><span data-stu-id="a1841-264">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="a1841-265">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="a1841-265">AnalysisMode</span></span>

<span data-ttu-id="a1841-266">Начиная с .NET 5.0 пакет SDK для .NET поставляется со всеми [правилами качества кода "CA"](../../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-266">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="a1841-267">По умолчанию в качестве предупреждений сборки включены только [некоторые правила](../../fundamentals/code-analysis/overview.md#enabled-rules).</span><span class="sxs-lookup"><span data-stu-id="a1841-267">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="a1841-268">Свойство `AnalysisMode` позволяет настроить набор правил, включенных по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a1841-268">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="a1841-269">Можно либо переключиться на более агрессивный (неявный) режим анализа, либо более консервативный (явный) режим анализа.</span><span class="sxs-lookup"><span data-stu-id="a1841-269">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="a1841-270">Например, если вы хотите включить все правила по умолчанию как предупреждения сборки, установите значение `AllEnabledByDefault`.</span><span class="sxs-lookup"><span data-stu-id="a1841-270">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="a1841-271">В следующей таблице приведены доступные параметры.</span><span class="sxs-lookup"><span data-stu-id="a1841-271">The following table shows the available options.</span></span>

| <span data-ttu-id="a1841-272">Значение</span><span class="sxs-lookup"><span data-stu-id="a1841-272">Value</span></span> | <span data-ttu-id="a1841-273">Значение</span><span class="sxs-lookup"><span data-stu-id="a1841-273">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="a1841-274">Режим по умолчанию, при котором определенные правила включаются в виде предупреждений сборки, некоторые правила включаются в качестве предложений интегрированной среды разработки Visual Studio, а остальные отключаются.</span><span class="sxs-lookup"><span data-stu-id="a1841-274">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="a1841-275">Агрессивный или неявный режим означает, что все правила по умолчанию включены как предупреждения сборки.</span><span class="sxs-lookup"><span data-stu-id="a1841-275">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="a1841-276">Вы можете выборочно [отказаться](../../fundamentals/code-analysis/configuration-options.md) от отдельных правил, чтобы отключить их.</span><span class="sxs-lookup"><span data-stu-id="a1841-276">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="a1841-277">Консервативный или явный режим означает, что все правила по умолчанию отключены.</span><span class="sxs-lookup"><span data-stu-id="a1841-277">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="a1841-278">Можно выборочно [принять](../../fundamentals/code-analysis/configuration-options.md) отдельные правила, чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="a1841-278">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="a1841-279">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="a1841-279">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="a1841-280">Свойство `CodeAnalysisTreatWarningsAsErrors` позволяет настроить, следует ли обрабатывать предупреждения анализа качества кода (CAxxxx) как предупреждения и прекращать сборку.</span><span class="sxs-lookup"><span data-stu-id="a1841-280">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="a1841-281">Если при построении проектов используется флаг `-warnaserror`, предупреждения [анализа качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis) также обрабатываются как ошибки.</span><span class="sxs-lookup"><span data-stu-id="a1841-281">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="a1841-282">Если вы не хотите, чтобы предупреждения качества кода обрабатывались как ошибки, можно задать для свойства MSBuild `CodeAnalysisTreatWarningsAsErrors` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="a1841-282">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="a1841-283">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="a1841-283">EnableNETAnalyzers</span></span>

<span data-ttu-id="a1841-284">Для проектов, предназначенных для .NET 5.0 или более поздней версии, по умолчанию включен [анализ качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis).</span><span class="sxs-lookup"><span data-stu-id="a1841-284">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="a1841-285">Вы можете включить анализ кода .NET для проектов, предназначенных для более ранних версий .NET, установив для свойства `EnableNETAnalyzers` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="a1841-285">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="a1841-286">Чтобы отключить анализ кода в любом проекте, присвойте этому свойству значение `false`.</span><span class="sxs-lookup"><span data-stu-id="a1841-286">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="a1841-287">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="a1841-287">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="a1841-288">Эта функция в настоящее время является экспериментальной и может измениться в .NET 6 по сравнению с реализацией в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="a1841-288">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="a1841-289">[Анализ стиля кода .NET](../../fundamentals/code-analysis/overview.md#code-style-analysis) по умолчанию отключен при сборке для всех проектов .NET.</span><span class="sxs-lookup"><span data-stu-id="a1841-289">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="a1841-290">Можно включить анализ стиля кода для проектов .NET, задав для свойства `EnforceCodeStyleInBuild` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="a1841-290">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="a1841-291">Все правила стиля кода, которые [настроены](../../fundamentals/code-analysis/overview.md#code-style-analysis) как предупреждения или ошибки, будут выполняться при нарушениях сборки и отчета.</span><span class="sxs-lookup"><span data-stu-id="a1841-291">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="a1841-292">Свойства конфигурации среды выполнения</span><span class="sxs-lookup"><span data-stu-id="a1841-292">Run-time configuration properties</span></span>

<span data-ttu-id="a1841-293">Вы можете настроить некоторые варианты поведения среды выполнения, указав свойства MSBuild в файле проекта приложения.</span><span class="sxs-lookup"><span data-stu-id="a1841-293">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="a1841-294">Сведения о других способах настройки поведения среды выполнения см. в статье о [параметрах конфигурации среды выполнения](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-294">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="a1841-295">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1841-295">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="a1841-296">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="a1841-296">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="a1841-297">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1841-297">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="a1841-298">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1841-298">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="a1841-299">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a1841-299">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="a1841-300">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="a1841-300">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="a1841-301">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="a1841-301">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="a1841-302">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="a1841-302">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="a1841-303">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="a1841-303">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="a1841-304">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1841-304">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="a1841-305">Свойство `ConcurrentGarbageCollection` указывает, включена ли [фоновая (параллельная) сборка мусора](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-305">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="a1841-306">Задайте значение `false`, чтобы отключить фоновую сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="a1841-306">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="a1841-307">Дополнительные сведения см. в разделе [Сборка мусора в фоновом режиме](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="a1841-307">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="a1841-308">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="a1841-308">InvariantGlobalization</span></span>

<span data-ttu-id="a1841-309">Свойство `InvariantGlobalization` определяет, выполняется ли приложение в *инвариантном режиме глобализации*, что означает, что у него нет доступа к данным, относящимся к языку и региональным параметрам.</span><span class="sxs-lookup"><span data-stu-id="a1841-309">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="a1841-310">Установите значение `true` для запуска в инвариантном режиме глобализации.</span><span class="sxs-lookup"><span data-stu-id="a1841-310">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="a1841-311">Дополнительные сведения см. в разделе [Инвариантный режим](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="a1841-311">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="a1841-312">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1841-312">RetainVMGarbageCollection</span></span>

<span data-ttu-id="a1841-313">Свойство `RetainVMGarbageCollection` настраивает сборщик мусора для помещения удаленных сегментов памяти в список ожидания для будущего использования или освобождения.</span><span class="sxs-lookup"><span data-stu-id="a1841-313">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="a1841-314">Значение `true` указывает сборщику мусора разместить сегменты в списке ожидания.</span><span class="sxs-lookup"><span data-stu-id="a1841-314">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="a1841-315">Дополнительные сведения см. в разделе [Сохранение виртуальной машины](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="a1841-315">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="a1841-316">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1841-316">ServerGarbageCollection</span></span>

<span data-ttu-id="a1841-317">Свойство `ServerGarbageCollection` указывает, использует ли приложение [сборку мусора рабочей станции или сборку мусора сервера](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-317">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="a1841-318">Задайте значение `true`, чтобы использовать сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="a1841-318">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="a1841-319">Дополнительные сведения см. в разделе [Рабочая станция и сервер](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="a1841-319">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="a1841-320">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a1841-320">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="a1841-321">Свойство `ThreadPoolMaxThreads` указывает максимальное число потоков для пула рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="a1841-321">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="a1841-322">Дополнительные сведения см. в разделе [Максимальное число потоков](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="a1841-322">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="a1841-323">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="a1841-323">ThreadPoolMinThreads</span></span>

<span data-ttu-id="a1841-324">Свойство `ThreadPoolMinThreads` указывает минимальное число потоков для пула рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="a1841-324">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="a1841-325">Дополнительные сведения см. в разделе [Минимальное число потоков](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="a1841-325">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="a1841-326">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="a1841-326">TieredCompilation</span></span>

<span data-ttu-id="a1841-327">Свойство `TieredCompilation` указывает, использует ли JIT-компилятор [многоуровневую компиляцию](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="a1841-327">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="a1841-328">Задайте значение `false`, чтобы отключить многоуровневую компиляцию.</span><span class="sxs-lookup"><span data-stu-id="a1841-328">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="a1841-329">Дополнительные сведения см. в разделе [Многоуровневая компиляция](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="a1841-329">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="a1841-330">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="a1841-330">TieredCompilationQuickJit</span></span>

<span data-ttu-id="a1841-331">Свойство `TieredCompilationQuickJit` указывает, использует ли JIT-компилятор быструю JIT-компиляцию.</span><span class="sxs-lookup"><span data-stu-id="a1841-331">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="a1841-332">Задайте значение `false`, чтобы отключить быструю JIT-компиляцию.</span><span class="sxs-lookup"><span data-stu-id="a1841-332">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="a1841-333">Дополнительные сведения см. в разделе [Быстрая JIT-компиляция](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="a1841-333">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="a1841-334">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="a1841-334">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="a1841-335">Свойство `TieredCompilationQuickJitForLoops` указывает, использует ли JIT-компилятор быструю JIT-компиляцию для методов, содержащих циклы.</span><span class="sxs-lookup"><span data-stu-id="a1841-335">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="a1841-336">Задайте значение `true`, чтобы включить быструю JIT-компиляцию для методов, содержащих циклы.</span><span class="sxs-lookup"><span data-stu-id="a1841-336">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="a1841-337">Дополнительные сведения см. в разделе [Быстрая JIT-компиляция для циклов](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="a1841-337">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="a1841-338">Справочники по свойствам и элементам</span><span class="sxs-lookup"><span data-stu-id="a1841-338">Reference properties and items</span></span>

- [<span data-ttu-id="a1841-339">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="a1841-339">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="a1841-340">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="a1841-340">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="a1841-341">PackageReference</span><span class="sxs-lookup"><span data-stu-id="a1841-341">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="a1841-342">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="a1841-342">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="a1841-343">Ссылки</span><span class="sxs-lookup"><span data-stu-id="a1841-343">Reference</span></span>](#reference)
- [<span data-ttu-id="a1841-344">Свойства, связанные с восстановлением</span><span class="sxs-lookup"><span data-stu-id="a1841-344">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="a1841-345">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="a1841-345">AssetTargetFallback</span></span>

<span data-ttu-id="a1841-346">Свойство `AssetTargetFallback` позволяет указать дополнительные совместимые версии платформы для ссылок на проекты и пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="a1841-346">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="a1841-347">Например, если вы указали зависимость пакета с помощью `PackageReference`, но в этом пакете нет ресурсов, совместимых с `TargetFramework` вашего проекта, тогда пригодится свойство `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="a1841-347">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="a1841-348">Совместимость пакета, на который указывает ссылка, повторно проверяется с помощью каждой целевой платформы, указанной в свойстве `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="a1841-348">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span> <span data-ttu-id="a1841-349">Это свойство заменяет устаревшее свойство `PackageTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="a1841-349">This property replaces the deprecated property `PackageTargetFallback`.</span></span>

<span data-ttu-id="a1841-350">В качестве значения свойства `AssetTargetFallback` можно задать одну [версию целевой платформы](../../standard/frameworks.md#supported-target-frameworks) или несколько.</span><span class="sxs-lookup"><span data-stu-id="a1841-350">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="a1841-351">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="a1841-351">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="a1841-352">Свойство `DisableImplicitFrameworkReferences` управляет неявными элементами `FrameworkReference` при разработке для .NET Core 3.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="a1841-352">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="a1841-353">При использовании .NET Core 2.1 или .NET Standard 2.0 и более ранних версий оно управляет неявными элементами [PackageReference](#packagereference) в пакетах в метапакете.</span><span class="sxs-lookup"><span data-stu-id="a1841-353">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="a1841-354">(Метапакет — это пакет на основе платформы, который состоит только из зависимостей от других пакетов.) Это свойство также управляет неявными ссылками, такими как `System` и `System.Core`, при разработке для .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1841-354">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="a1841-355">Присвойте этому свойству значение `true`, чтобы отключить неявные элементы `FrameworkReference` или [PackageReference](#packagereference).</span><span class="sxs-lookup"><span data-stu-id="a1841-355">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="a1841-356">Если этому свойству присвоено значение `true`, можно добавить явные ссылки на только необходимые платформы или пакеты.</span><span class="sxs-lookup"><span data-stu-id="a1841-356">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="a1841-357">PackageReference</span><span class="sxs-lookup"><span data-stu-id="a1841-357">PackageReference</span></span>

<span data-ttu-id="a1841-358">Элемент `PackageReference` определяет ссылку на пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="a1841-358">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="a1841-359">Атрибут `Include` указывает идентификатор пакета.</span><span class="sxs-lookup"><span data-stu-id="a1841-359">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="a1841-360">Атрибут `Version` указывает версию или диапазон версий.</span><span class="sxs-lookup"><span data-stu-id="a1841-360">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="a1841-361">Сведения о том, как указать минимальную версию, максимальную версию, диапазон или точное соответствие, см. в разделе [Диапазоны версий](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="a1841-361">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="a1841-362">[Атрибуты ресурса](#asset-attributes) можно также добавить в ссылку на пакет.</span><span class="sxs-lookup"><span data-stu-id="a1841-362">You can also add [asset attributes](#asset-attributes) to a package reference.</span></span>

<span data-ttu-id="a1841-363">Фрагмент файла проекта в следующем примере ссылается на пакет [System.Runtime](https://www.nuget.org/packages/System.Runtime/).</span><span class="sxs-lookup"><span data-stu-id="a1841-363">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="a1841-364">Дополнительные сведения см. в статье [Ссылки на пакеты в файлах проекта](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="a1841-364">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

#### <a name="asset-attributes"></a><span data-ttu-id="a1841-365">Атрибуты ресурса</span><span class="sxs-lookup"><span data-stu-id="a1841-365">Asset attributes</span></span>

<span data-ttu-id="a1841-366">Метаданные `IncludeAssets`, `ExcludeAssets` и `PrivateAssets` можно добавить в ссылку на пакет.</span><span class="sxs-lookup"><span data-stu-id="a1841-366">The `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets` metadata can be added to a package reference.</span></span>

| <span data-ttu-id="a1841-367">attribute</span><span class="sxs-lookup"><span data-stu-id="a1841-367">Attribute</span></span> | <span data-ttu-id="a1841-368">Описание</span><span class="sxs-lookup"><span data-stu-id="a1841-368">Description</span></span> |
| - | - |
| `IncludeAssets` | <span data-ttu-id="a1841-369">Указывает, какие ресурсы пакета, указанные `<PackageReference>`, следует использовать.</span><span class="sxs-lookup"><span data-stu-id="a1841-369">Specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="a1841-370">По умолчанию включаются все ресурсы пакета.</span><span class="sxs-lookup"><span data-stu-id="a1841-370">By default, all package assets are included.</span></span> |
| `ExcludeAssets`| <span data-ttu-id="a1841-371">Указывает, какие ресурсы пакета, указанные `<PackageReference>`, не следует использовать.</span><span class="sxs-lookup"><span data-stu-id="a1841-371">Specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span> |
| `PrivateAssets` | <span data-ttu-id="a1841-372">Указывает, какие ресурсы пакета, указанные `<PackageReference>`, следует использовать, но не следует передавать в следующий проект.</span><span class="sxs-lookup"><span data-stu-id="a1841-372">Specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="a1841-373">Если этот атрибут отсутствует, ресурсы `Analyzers`, `Build` и `ContentFiles` по умолчанию являются частными.</span><span class="sxs-lookup"><span data-stu-id="a1841-373">The `Analyzers`, `Build`, and `ContentFiles` assets are private by default when this attribute is not present.</span></span> |

<span data-ttu-id="a1841-374">Эти атрибуты могут содержать один или несколько следующих элементов (если их больше одного, они разделяются точкой с запятой `;`):</span><span class="sxs-lookup"><span data-stu-id="a1841-374">These attributes can contain one or more of the following items, separated by a semicolon `;` if more than one is listed:</span></span>

- <span data-ttu-id="a1841-375">`Compile` — содержимое папки *lib* доступно для компиляции.</span><span class="sxs-lookup"><span data-stu-id="a1841-375">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="a1841-376">`Runtime` — содержимое папки *runtime* распределяется.</span><span class="sxs-lookup"><span data-stu-id="a1841-376">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="a1841-377">`ContentFiles` — используется содержимое папки *contentfiles*.</span><span class="sxs-lookup"><span data-stu-id="a1841-377">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="a1841-378">`Build` — используются свойства и целевые объекты в папке *build*.</span><span class="sxs-lookup"><span data-stu-id="a1841-378">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="a1841-379">`Native` — содержимое копируется из основных ресурсов в папку *output* среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="a1841-379">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="a1841-380">`Analyzers` — используются анализаторы.</span><span class="sxs-lookup"><span data-stu-id="a1841-380">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="a1841-381">Кроме того, атрибут может содержать следующие значения.</span><span class="sxs-lookup"><span data-stu-id="a1841-381">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="a1841-382">`None` — не используется ни один ресурс.</span><span class="sxs-lookup"><span data-stu-id="a1841-382">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="a1841-383">`All` — используются все ресурсы.</span><span class="sxs-lookup"><span data-stu-id="a1841-383">`All` – all assets are used.</span></span>

### <a name="projectreference"></a><span data-ttu-id="a1841-384">СсылкаНаПроект</span><span class="sxs-lookup"><span data-stu-id="a1841-384">ProjectReference</span></span>

<span data-ttu-id="a1841-385">Элемент `ProjectReference` определяет ссылку на другой проект.</span><span class="sxs-lookup"><span data-stu-id="a1841-385">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="a1841-386">Проект, на который указывает ссылка, добавляется как зависимость пакета NuGet, то есть обрабатывается так же, как `PackageReference`.</span><span class="sxs-lookup"><span data-stu-id="a1841-386">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="a1841-387">Атрибут `Include` задает путь к проекту.</span><span class="sxs-lookup"><span data-stu-id="a1841-387">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="a1841-388">Вы также можете добавить в ссылку на проект следующие метаданные: `IncludeAssets`, `ExcludeAssets` и `PrivateAssets`.</span><span class="sxs-lookup"><span data-stu-id="a1841-388">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="a1841-389">Фрагмент файла проекта в следующем примере ссылается на проект `Project2`.</span><span class="sxs-lookup"><span data-stu-id="a1841-389">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="a1841-390">Справочник</span><span class="sxs-lookup"><span data-stu-id="a1841-390">Reference</span></span>

<span data-ttu-id="a1841-391">Элемент `Reference` определяет ссылку на файл сборки.</span><span class="sxs-lookup"><span data-stu-id="a1841-391">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="a1841-392">Атрибут `Include` задает имя файла, а метаданные `HintPath` указывают путь к этой сборке.</span><span class="sxs-lookup"><span data-stu-id="a1841-392">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="a1841-393">Свойства, связанные с восстановлением</span><span class="sxs-lookup"><span data-stu-id="a1841-393">Restore-related properties</span></span>

<span data-ttu-id="a1841-394">При восстановлении пакета, на который указывает ссылка, устанавливаются все его прямые зависимости и все зависимости этих зависимостей.</span><span class="sxs-lookup"><span data-stu-id="a1841-394">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="a1841-395">Можно настроить восстановление пакетов, указав такие свойства, как `RestorePackagesPath` и `RestoreIgnoreFailedSources`.</span><span class="sxs-lookup"><span data-stu-id="a1841-395">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="a1841-396">Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект восстановления](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="a1841-396">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a><span data-ttu-id="a1841-397">Свойства запуска</span><span class="sxs-lookup"><span data-stu-id="a1841-397">Run properties</span></span>

<span data-ttu-id="a1841-398">Следующие свойства используются для запуска приложения с помощью команды [`dotnet run`](../tools/dotnet-run.md):</span><span class="sxs-lookup"><span data-stu-id="a1841-398">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="a1841-399">RunArguments</span><span class="sxs-lookup"><span data-stu-id="a1841-399">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="a1841-400">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="a1841-400">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="a1841-401">RunArguments</span><span class="sxs-lookup"><span data-stu-id="a1841-401">RunArguments</span></span>

<span data-ttu-id="a1841-402">Свойство `RunArguments` определяет аргументы, которые передаются в приложение при его запуске.</span><span class="sxs-lookup"><span data-stu-id="a1841-402">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="a1841-403">Можно указать дополнительные аргументы для передачи в приложение с помощью параметра [`--` для `dotnet run`](../tools/dotnet-run.md#options).</span><span class="sxs-lookup"><span data-stu-id="a1841-403">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="a1841-404">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="a1841-404">RunWorkingDirectory</span></span>

<span data-ttu-id="a1841-405">Свойство `RunWorkingDirectory` определяет рабочий каталог для запуска процесса приложения.</span><span class="sxs-lookup"><span data-stu-id="a1841-405">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="a1841-406">Это может быть абсолютный путь или путь относительно каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="a1841-406">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="a1841-407">Если каталог не указан, в качестве рабочего каталога используется `OutDir`.</span><span class="sxs-lookup"><span data-stu-id="a1841-407">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties"></a><span data-ttu-id="a1841-408">Свойства размещения</span><span class="sxs-lookup"><span data-stu-id="a1841-408">Hosting properties</span></span>

- [<span data-ttu-id="a1841-409">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="a1841-409">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="a1841-410">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="a1841-410">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="a1841-411">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="a1841-411">EnableComHosting</span></span>

<span data-ttu-id="a1841-412">Свойство `EnableComHosting` указывает, что сборка предоставляет сервер COM.</span><span class="sxs-lookup"><span data-stu-id="a1841-412">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="a1841-413">Установка `EnableComHosting` в `true` также подразумевает, что [EnableDynamicLoading](#enabledynamicloading) — `true`.</span><span class="sxs-lookup"><span data-stu-id="a1841-413">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="a1841-414">Дополнительные сведения см. в разделе [Предоставление компонентов .NET для COM](../native-interop/expose-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-414">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="a1841-415">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="a1841-415">EnableDynamicLoading</span></span>

<span data-ttu-id="a1841-416">Свойство `EnableDynamicLoading` указывает, что сборка является динамически загружаемым компонентом.</span><span class="sxs-lookup"><span data-stu-id="a1841-416">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="a1841-417">Компонентом может быть [библиотека COM](/windows/win32/com/the-component-object-model) или библиотека, не относящаяся к COM, которую можно [использовать из собственного узла](../tutorials/netcore-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="a1841-417">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="a1841-418">Если присвоить этому свойству значения `true`:</span><span class="sxs-lookup"><span data-stu-id="a1841-418">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="a1841-419">Создается файл *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="a1841-419">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="a1841-420">[Накат](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) получает значение `LatestMinor`.</span><span class="sxs-lookup"><span data-stu-id="a1841-420">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="a1841-421">Ссылки NuGet копируются локально.</span><span class="sxs-lookup"><span data-stu-id="a1841-421">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="a1841-422">См. также</span><span class="sxs-lookup"><span data-stu-id="a1841-422">See also</span></span>

- [<span data-ttu-id="a1841-423">Справочник по схеме MSBuild</span><span class="sxs-lookup"><span data-stu-id="a1841-423">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="a1841-424">Общие свойства MSBuild</span><span class="sxs-lookup"><span data-stu-id="a1841-424">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="a1841-425">Свойства MSBuild для целевого объекта pack NuGet</span><span class="sxs-lookup"><span data-stu-id="a1841-425">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="a1841-426">Свойства MSBuild для целевого объекта restore NuGet</span><span class="sxs-lookup"><span data-stu-id="a1841-426">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="a1841-427">Настройка сборки</span><span class="sxs-lookup"><span data-stu-id="a1841-427">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
