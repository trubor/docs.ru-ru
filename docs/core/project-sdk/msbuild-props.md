---
title: Свойства MSBuild для Microsoft.NET.Sdk
description: Справочник по свойствам и элементам MSBuild, распознаваемым пакетом SDK для .NET.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: e7deb8c32fd01452524122e41f758ab037020ee4
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970711"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="8276a-103">Справочник по MSBuild для проектов пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="8276a-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="8276a-104">Эта страница содержит справочные сведения о свойствах и элементах MSBuild, которые вы можете использовать для настройки проектов .NET.</span><span class="sxs-lookup"><span data-stu-id="8276a-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="8276a-105">Работа над этой страницей еще не завершена, поэтому здесь приведены лишь некоторые полезные свойства MSBuild для пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="8276a-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="8276a-106">Список стандартных свойств см. в статье [Общие свойства MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="8276a-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="8276a-107">Свойства платформы</span><span class="sxs-lookup"><span data-stu-id="8276a-107">Framework properties</span></span>

- [<span data-ttu-id="8276a-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="8276a-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="8276a-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="8276a-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="8276a-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="8276a-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="8276a-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="8276a-111">TargetFramework</span></span>

<span data-ttu-id="8276a-112">Свойство `TargetFramework` определяет версию целевой платформы для приложения.</span><span class="sxs-lookup"><span data-stu-id="8276a-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="8276a-113">Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="8276a-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="8276a-114">Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="8276a-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="8276a-115">TargetFrameworks</span></span>

<span data-ttu-id="8276a-116">Используйте свойство `TargetFrameworks`, если приложение должно быть предназначено для нескольких платформ.</span><span class="sxs-lookup"><span data-stu-id="8276a-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="8276a-117">Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="8276a-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="8276a-118">Это свойство игнорируется, если указано свойство `TargetFramework` (в единственном числе).</span><span class="sxs-lookup"><span data-stu-id="8276a-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="8276a-119">Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="8276a-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="8276a-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="8276a-121">Это свойство применяется только к проектам, использующим `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="8276a-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="8276a-122">Он не применяется к проектам, использующим `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="8276a-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="8276a-123">Используйте свойство `NetStandardImplicitPackageVersion`, если вам нужно указать версию платформы ниже версии метапакета.</span><span class="sxs-lookup"><span data-stu-id="8276a-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="8276a-124">Файл проекта, приведенный в следующем примере, предназначен для `netstandard1.3`, но использует `NETStandard.Library` версии 1.6.0.</span><span class="sxs-lookup"><span data-stu-id="8276a-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="8276a-125">Свойства пакета</span><span class="sxs-lookup"><span data-stu-id="8276a-125">Package properties</span></span>

<span data-ttu-id="8276a-126">Для описания пакета, созданного из проекта, можно указать такие свойства, как `PackageId`, `PackageVersion`, `PackageIcon`, `Title` и `Description`.</span><span class="sxs-lookup"><span data-stu-id="8276a-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="8276a-127">Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект пакета](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="8276a-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="8276a-128">Публикация свойств и элементов</span><span class="sxs-lookup"><span data-stu-id="8276a-128">Publish properties and items</span></span>

- [<span data-ttu-id="8276a-129">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="8276a-129">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="8276a-130">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="8276a-130">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="8276a-131">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="8276a-131">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="8276a-132">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="8276a-132">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="8276a-133">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="8276a-133">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="8276a-134">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="8276a-134">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="8276a-135">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="8276a-135">UseAppHost</span></span>](#useapphost)

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="8276a-136">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="8276a-136">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="8276a-137">Свойство `AppendTargetFrameworkToOutputPath` определяет, добавляется ли [моникер целевой платформы (TFM)](../../standard/frameworks.md) к выходному пути (который определяется свойством [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span><span class="sxs-lookup"><span data-stu-id="8276a-137">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="8276a-138">Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть).</span><span class="sxs-lookup"><span data-stu-id="8276a-138">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="8276a-139">При установке значения `false` для свойства `AppendTargetFrameworkToOutputPath` TFM не добавляется к выходному пути.</span><span class="sxs-lookup"><span data-stu-id="8276a-139">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="8276a-140">Однако при отсутствии TFM в выходном пути несколько артефактов сборки могут перезаписывать друг друга.</span><span class="sxs-lookup"><span data-stu-id="8276a-140">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="8276a-141">Например, при установке следующего параметра выходной путь для приложения .NET 5.0 изменяется с `bin\Debug\net5.0` на `bin\Debug`:</span><span class="sxs-lookup"><span data-stu-id="8276a-141">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="8276a-142">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="8276a-142">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="8276a-143">Свойство `AppendRuntimeIdentifierToOutputPath` определяет, добавляется ли к выходному пути [идентификатор среды выполнения (RID)](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-143">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="8276a-144">Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть).</span><span class="sxs-lookup"><span data-stu-id="8276a-144">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="8276a-145">При установке значения `false` для свойства `AppendRuntimeIdentifierToOutputPath` RID не добавляется к выходному пути.</span><span class="sxs-lookup"><span data-stu-id="8276a-145">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="8276a-146">Например, при установке следующего параметра выходной путь для приложения .NET 5.0 и идентификатора RID `win10-x64` изменяется с `bin\Debug\net5.0\win10-x64` на `bin\Debug\net5.0`:</span><span class="sxs-lookup"><span data-stu-id="8276a-146">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="8276a-147">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="8276a-147">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="8276a-148">Свойство `CopyLocalLockFileAssemblies` полезно для проектов подключаемых модулей, которые имеют зависимости от других библиотек.</span><span class="sxs-lookup"><span data-stu-id="8276a-148">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="8276a-149">Если для этого свойства задано значение `true`, все зависимости пакета NuGet копируются в выходной каталог.</span><span class="sxs-lookup"><span data-stu-id="8276a-149">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="8276a-150">Это означает, что вы можете использовать выходные данные `dotnet build` для запуска подключаемого модуля на любом компьютере.</span><span class="sxs-lookup"><span data-stu-id="8276a-150">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="8276a-151">Кроме того, можно использовать `dotnet publish` для публикации библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="8276a-151">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="8276a-152">Дополнительные сведения см. в разделе [dotnet publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-152">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="8276a-153">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="8276a-153">RuntimeIdentifier</span></span>

<span data-ttu-id="8276a-154">Свойство `RuntimeIdentifier` позволяет указать для проекта один [идентификатор среды выполнения (RID)](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-154">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="8276a-155">Идентификатор среды выполнения позволяет опубликовать автономное развертывание.</span><span class="sxs-lookup"><span data-stu-id="8276a-155">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="8276a-156">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="8276a-156">RuntimeIdentifiers</span></span>

<span data-ttu-id="8276a-157">Свойство `RuntimeIdentifiers` позволяет указать для проекта список [идентификаторов среды выполнения (RID)](../rid-catalog.md) (в качестве разделителя используется точка с запятой).</span><span class="sxs-lookup"><span data-stu-id="8276a-157">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="8276a-158">Используйте это свойство, если вам нужна публикация для нескольких сред.</span><span class="sxs-lookup"><span data-stu-id="8276a-158">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="8276a-159">`RuntimeIdentifiers` используется во время восстановления для обеспечения наличия в графе нужных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8276a-159">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="8276a-160">`RuntimeIdentifier` (в единственном числе) может ускорить создание сборок, когда требуется только одна среда выполнения.</span><span class="sxs-lookup"><span data-stu-id="8276a-160">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="8276a-161">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="8276a-161">TrimmerRootAssembly</span></span>

<span data-ttu-id="8276a-162">Элемент `TrimmerRootAssembly` позволяет исключить сборку из [*обрезки*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-162">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="8276a-163">Обрезка — это процесс удаления неиспользуемых частей среды выполнения из упакованного приложения.</span><span class="sxs-lookup"><span data-stu-id="8276a-163">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="8276a-164">В некоторых случаях при обрезке могут неправильно удаляться необходимые ссылки.</span><span class="sxs-lookup"><span data-stu-id="8276a-164">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="8276a-165">Следующий код XML исключает сборку `System.Security` из обрезки.</span><span class="sxs-lookup"><span data-stu-id="8276a-165">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="8276a-166">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="8276a-166">UseAppHost</span></span>

<span data-ttu-id="8276a-167">Свойство `UseAppHost` контролирует создание собственного исполняемого файла для развертывания.</span><span class="sxs-lookup"><span data-stu-id="8276a-167">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="8276a-168">Этот файл требуется для автономных развертываний.</span><span class="sxs-lookup"><span data-stu-id="8276a-168">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="8276a-169">В .NET Core 3.0 и более поздних версиях зависимый от платформы исполняемый файл создается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8276a-169">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="8276a-170">Задайте свойству `UseAppHost` значение `false`, чтобы отключить создание исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="8276a-170">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="8276a-171">Дополнительные сведения см. в статье о [развертывании приложений .NET](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-171">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="8276a-172">Свойства компиляции</span><span class="sxs-lookup"><span data-stu-id="8276a-172">Compile properties</span></span>

- [<span data-ttu-id="8276a-173">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="8276a-173">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="8276a-174">LangVersion</span><span class="sxs-lookup"><span data-stu-id="8276a-174">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="8276a-175">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="8276a-175">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="8276a-176">Свойство `EmbeddedResourceUseDependentUponConvention` определяет, будет ли использоваться информация о типах в исходных файлах, расположенных в одной папке с файлами ресурсов, для создания имен файлов манифеста этих ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8276a-176">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="8276a-177">Например, если *Form1.resx* находится в той же папке, что и *Form1.cs*, а `EmbeddedResourceUseDependentUponConvention` имеет значение `true`, то созданному файл *.resources* присваивается имя на основе имени первого типа, определенного в файле *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="8276a-177">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="8276a-178">Например, если первым типом в файле *Form1.cs* является `MyNamespace.Form1`, созданному файлу присваивается имя *MyNamespace.Form1.resources*.</span><span class="sxs-lookup"><span data-stu-id="8276a-178">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="8276a-179">Если для `EmbeddedResource` элемента заданы метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого файла ресурсов будет создаваться на основе таких метаданных.</span><span class="sxs-lookup"><span data-stu-id="8276a-179">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="8276a-180">По умолчанию для нового проекта .NET этому свойству задается значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8276a-180">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="8276a-181">Если задано значение `false` и для элемента `EmbeddedResource` в файле проекта не указаны метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого ресурса будет основано на имени корневого пространства имен проекта и относительном пути к файлу *.resx*.</span><span class="sxs-lookup"><span data-stu-id="8276a-181">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="8276a-182">Дополнительные сведения об определение имени файла манифеста см. [здесь](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-182">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="8276a-183">LangVersion</span><span class="sxs-lookup"><span data-stu-id="8276a-183">LangVersion</span></span>

<span data-ttu-id="8276a-184">Свойство `LangVersion` позволяет указать конкретную версию языка программирования.</span><span class="sxs-lookup"><span data-stu-id="8276a-184">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="8276a-185">Например, если требуется доступ к предварительным версиям функций C#, задайте параметру `LangVersion` значение `preview`.</span><span class="sxs-lookup"><span data-stu-id="8276a-185">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="8276a-186">Дополнительные сведения см. в статье [Управление версиями языка C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="8276a-186">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="8276a-187">Свойства включения элементов по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8276a-187">Default item inclusion properties</span></span>

- [<span data-ttu-id="8276a-188">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="8276a-188">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="8276a-189">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="8276a-189">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="8276a-190">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="8276a-190">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="8276a-191">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="8276a-191">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="8276a-192">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="8276a-192">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="8276a-193">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="8276a-193">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="8276a-194">Дополнительные сведения см. в разделе [Включения и исключения по умолчанию](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="8276a-194">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="8276a-195">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="8276a-195">DefaultItemExcludes</span></span>

<span data-ttu-id="8276a-196">Используйте свойство `DefaultItemExcludes`, чтобы определить стандартные маски для файлов и папок, которые должны быть исключены из стандартных масок включения, исключения и удаления.</span><span class="sxs-lookup"><span data-stu-id="8276a-196">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="8276a-197">По умолчанию папки *./bin* и *./obj* исключаются из стандартных масок.</span><span class="sxs-lookup"><span data-stu-id="8276a-197">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="8276a-198">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="8276a-198">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="8276a-199">Используйте свойство `DefaultExcludesInProjectFolder`, чтобы определить стандартные маски для файлов и папок в папке проекта, которые должны быть исключены из стандартных масок включения, исключения и удаления.</span><span class="sxs-lookup"><span data-stu-id="8276a-199">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="8276a-200">По умолчанию папки, начинающиеся с точки (`.`), такие как *.git* и *.vs*, исключаются из стандартных масок.</span><span class="sxs-lookup"><span data-stu-id="8276a-200">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="8276a-201">Это свойство очень похоже на свойство `DefaultItemExcludes`, за исключением того, что оно учитывает только файлы и папки в папке проекта.</span><span class="sxs-lookup"><span data-stu-id="8276a-201">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="8276a-202">Если стандартная маска будет случайно соответствовать элементам за пределами папки проекта с относительным путем, используйте свойство `DefaultExcludesInProjectFolder` вместо свойства `DefaultItemExcludes`.</span><span class="sxs-lookup"><span data-stu-id="8276a-202">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="8276a-203">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="8276a-203">EnableDefaultItems</span></span>

<span data-ttu-id="8276a-204">Свойство `EnableDefaultItems` определяет, включаются ли в проект неявным образом элементы компиляции, элементы внедренных ресурсов и элементы `None`.</span><span class="sxs-lookup"><span data-stu-id="8276a-204">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="8276a-205">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="8276a-205">The default value is `true`.</span></span> <span data-ttu-id="8276a-206">Задайте значение `false` для свойства `EnableDefaultItems`, чтобы отключить все неявные включения файлов.</span><span class="sxs-lookup"><span data-stu-id="8276a-206">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="8276a-207">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="8276a-207">EnableDefaultCompileItems</span></span>

<span data-ttu-id="8276a-208">Свойство `EnableDefaultCompileItems` определяет, включаются ли в проект неявным образом элементы компиляции.</span><span class="sxs-lookup"><span data-stu-id="8276a-208">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="8276a-209">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="8276a-209">The default value is `true`.</span></span> <span data-ttu-id="8276a-210">Задайте значение `false` для свойства `EnableDefaultCompileItems`, чтобы отключить неявное включение файлов \*.cs и других файлов расширения языка.</span><span class="sxs-lookup"><span data-stu-id="8276a-210">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="8276a-211">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="8276a-211">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="8276a-212">Свойство `EnableDefaultEmbeddedResourceItems` определяет, включаются ли в проект неявным образом элементы внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8276a-212">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="8276a-213">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="8276a-213">The default value is `true`.</span></span> <span data-ttu-id="8276a-214">Задайте значение `false` для свойства `EnableDefaultEmbeddedResourceItems`, чтобы отключить неявное включение файлов внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8276a-214">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="8276a-215">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="8276a-215">EnableDefaultNoneItems</span></span>

<span data-ttu-id="8276a-216">Свойство `EnableDefaultNoneItems` определяет, включаются ли в проект неявным образом элементы `None` (файлы, которые не играют никакой роли в процессе сборки).</span><span class="sxs-lookup"><span data-stu-id="8276a-216">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="8276a-217">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="8276a-217">The default value is `true`.</span></span> <span data-ttu-id="8276a-218">Задайте значение `false` для свойства `EnableDefaultNoneItems`, чтобы отключить неявное включение элементов `None`.</span><span class="sxs-lookup"><span data-stu-id="8276a-218">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="8276a-219">Свойства анализа кода</span><span class="sxs-lookup"><span data-stu-id="8276a-219">Code analysis properties</span></span>

- [<span data-ttu-id="8276a-220">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="8276a-220">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="8276a-221">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="8276a-221">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="8276a-222">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="8276a-222">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="8276a-223">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="8276a-223">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="8276a-224">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="8276a-224">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="8276a-225">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="8276a-225">AnalysisLevel</span></span>

<span data-ttu-id="8276a-226">Свойство `AnalysisLevel` позволяет указать уровень анализа кода.</span><span class="sxs-lookup"><span data-stu-id="8276a-226">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="8276a-227">Например, если требуется доступ к анализаторам кода предварительной версии, задайте для параметра `AnalysisLevel` значение `preview`.</span><span class="sxs-lookup"><span data-stu-id="8276a-227">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="8276a-228">Значение по умолчанию — `latest`.</span><span class="sxs-lookup"><span data-stu-id="8276a-228">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="8276a-229">В следующей таблице приведены доступные параметры.</span><span class="sxs-lookup"><span data-stu-id="8276a-229">The following table shows the available options.</span></span>

| <span data-ttu-id="8276a-230">Значение</span><span class="sxs-lookup"><span data-stu-id="8276a-230">Value</span></span> | <span data-ttu-id="8276a-231">Значение</span><span class="sxs-lookup"><span data-stu-id="8276a-231">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="8276a-232">Используются новейшие анализаторы кода, которые были выпущены.</span><span class="sxs-lookup"><span data-stu-id="8276a-232">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="8276a-233">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8276a-233">This is the default.</span></span> |
| `preview` | <span data-ttu-id="8276a-234">Используются новейшие анализаторы кода, даже если они находятся на этапе предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="8276a-234">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="8276a-235">Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила.</span><span class="sxs-lookup"><span data-stu-id="8276a-235">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="8276a-236">Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила.</span><span class="sxs-lookup"><span data-stu-id="8276a-236">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="8276a-237">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="8276a-237">AnalysisMode</span></span>

<span data-ttu-id="8276a-238">Начиная с .NET 5.0 пакет SDK для .NET поставляется со всеми [правилами качества кода "CA"](../../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-238">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="8276a-239">По умолчанию в качестве предупреждений сборки включены только [некоторые правила](../../fundamentals/code-analysis/overview.md#enabled-rules).</span><span class="sxs-lookup"><span data-stu-id="8276a-239">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="8276a-240">Свойство `AnalysisMode` позволяет настроить набор правил, включенных по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8276a-240">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="8276a-241">Можно либо переключиться на более агрессивный (неявный) режим анализа, либо более консервативный (явный) режим анализа.</span><span class="sxs-lookup"><span data-stu-id="8276a-241">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="8276a-242">Например, если вы хотите включить все правила по умолчанию как предупреждения сборки, установите значение `AllEnabledByDefault`.</span><span class="sxs-lookup"><span data-stu-id="8276a-242">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="8276a-243">В следующей таблице приведены доступные параметры.</span><span class="sxs-lookup"><span data-stu-id="8276a-243">The following table shows the available options.</span></span>

| <span data-ttu-id="8276a-244">Значение</span><span class="sxs-lookup"><span data-stu-id="8276a-244">Value</span></span> | <span data-ttu-id="8276a-245">Значение</span><span class="sxs-lookup"><span data-stu-id="8276a-245">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="8276a-246">Режим по умолчанию, при котором определенные правила включаются в виде предупреждений сборки, некоторые правила включаются в качестве предложений интегрированной среды разработки Visual Studio, а остальные отключаются.</span><span class="sxs-lookup"><span data-stu-id="8276a-246">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="8276a-247">Агрессивный или неявный режим означает, что все правила по умолчанию включены как предупреждения сборки.</span><span class="sxs-lookup"><span data-stu-id="8276a-247">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="8276a-248">Вы можете выборочно [отказаться](../../fundamentals/code-analysis/configuration-options.md) от отдельных правил, чтобы отключить их.</span><span class="sxs-lookup"><span data-stu-id="8276a-248">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="8276a-249">Консервативный или явный режим означает, что все правила по умолчанию отключены.</span><span class="sxs-lookup"><span data-stu-id="8276a-249">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="8276a-250">Можно выборочно [принять](../../fundamentals/code-analysis/configuration-options.md) отдельные правила, чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="8276a-250">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="8276a-251">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="8276a-251">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="8276a-252">Свойство `CodeAnalysisTreatWarningsAsErrors` позволяет настроить, следует ли обрабатывать предупреждения анализа качества кода (CAxxxx) как предупреждения и прекращать сборку.</span><span class="sxs-lookup"><span data-stu-id="8276a-252">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="8276a-253">Если при построении проектов используется флаг `-warnaserror`, предупреждения [анализа качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis) также обрабатываются как ошибки.</span><span class="sxs-lookup"><span data-stu-id="8276a-253">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="8276a-254">Если вы не хотите, чтобы предупреждения качества кода обрабатывались как ошибки, можно задать для свойства MSBuild `CodeAnalysisTreatWarningsAsErrors` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="8276a-254">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="8276a-255">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="8276a-255">EnableNETAnalyzers</span></span>

<span data-ttu-id="8276a-256">Для проектов, предназначенных для .NET 5.0 или более поздней версии, по умолчанию включен [анализ качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis).</span><span class="sxs-lookup"><span data-stu-id="8276a-256">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="8276a-257">Вы можете включить анализ кода .NET для проектов, предназначенных для более ранних версий .NET, установив для свойства `EnableNETAnalyzers` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8276a-257">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="8276a-258">Чтобы отключить анализ кода в любом проекте, присвойте этому свойству значение `false`.</span><span class="sxs-lookup"><span data-stu-id="8276a-258">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="8276a-259">Другой способ включить анализ кода .NET для проектов, предназначенных для версий .NET до .NET 5.0, — задать для свойства [AnalysisLevel](#analysislevel) значение `latest`.</span><span class="sxs-lookup"><span data-stu-id="8276a-259">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="8276a-260">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="8276a-260">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="8276a-261">Эта функция в настоящее время является экспериментальной и может измениться в .NET 6 по сравнению с реализацией в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="8276a-261">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="8276a-262">[Анализ стиля кода .NET](../../fundamentals/code-analysis/overview.md#code-style-analysis) по умолчанию отключен при сборке для всех проектов .NET.</span><span class="sxs-lookup"><span data-stu-id="8276a-262">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="8276a-263">Можно включить анализ стиля кода для проектов .NET, задав для свойства `EnforceCodeStyleInBuild` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8276a-263">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="8276a-264">Все правила стиля кода, которые [настроены](../../fundamentals/code-analysis/overview.md#code-style-analysis) как предупреждения или ошибки, будут выполняться при нарушениях сборки и отчета.</span><span class="sxs-lookup"><span data-stu-id="8276a-264">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="8276a-265">Свойства конфигурации среды выполнения</span><span class="sxs-lookup"><span data-stu-id="8276a-265">Run-time configuration properties</span></span>

<span data-ttu-id="8276a-266">Вы можете настроить некоторые варианты поведения среды выполнения, указав свойства MSBuild в файле проекта приложения.</span><span class="sxs-lookup"><span data-stu-id="8276a-266">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="8276a-267">Сведения о других способах настройки поведения среды выполнения см. в статье о [параметрах конфигурации среды выполнения](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-267">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="8276a-268">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="8276a-268">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="8276a-269">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="8276a-269">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="8276a-270">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="8276a-270">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="8276a-271">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="8276a-271">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="8276a-272">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="8276a-272">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="8276a-273">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="8276a-273">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="8276a-274">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="8276a-274">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="8276a-275">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="8276a-275">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="8276a-276">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="8276a-276">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="8276a-277">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="8276a-277">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="8276a-278">Свойство `ConcurrentGarbageCollection` указывает, включена ли [фоновая (параллельная) сборка мусора](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-278">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="8276a-279">Задайте значение `false`, чтобы отключить фоновую сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="8276a-279">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="8276a-280">Дополнительные сведения см. в разделе [Сборка мусора в фоновом режиме](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="8276a-280">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="8276a-281">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="8276a-281">InvariantGlobalization</span></span>

<span data-ttu-id="8276a-282">Свойство `InvariantGlobalization` определяет, выполняется ли приложение в *инвариантном режиме глобализации*, что означает, что у него нет доступа к данным, относящимся к языку и региональным параметрам.</span><span class="sxs-lookup"><span data-stu-id="8276a-282">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="8276a-283">Установите значение `true` для запуска в инвариантном режиме глобализации.</span><span class="sxs-lookup"><span data-stu-id="8276a-283">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="8276a-284">Дополнительные сведения см. в разделе [Инвариантный режим](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="8276a-284">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="8276a-285">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="8276a-285">RetainVMGarbageCollection</span></span>

<span data-ttu-id="8276a-286">Свойство `RetainVMGarbageCollection` настраивает сборщик мусора для помещения удаленных сегментов памяти в список ожидания для будущего использования или освобождения.</span><span class="sxs-lookup"><span data-stu-id="8276a-286">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="8276a-287">Значение `true` указывает сборщику мусора разместить сегменты в списке ожидания.</span><span class="sxs-lookup"><span data-stu-id="8276a-287">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="8276a-288">Дополнительные сведения см. в разделе [Сохранение виртуальной машины](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="8276a-288">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="8276a-289">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="8276a-289">ServerGarbageCollection</span></span>

<span data-ttu-id="8276a-290">Свойство `ServerGarbageCollection` указывает, использует ли приложение [сборку мусора рабочей станции или сборку мусора сервера](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-290">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="8276a-291">Задайте значение `true`, чтобы использовать сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="8276a-291">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="8276a-292">Дополнительные сведения см. в разделе [Рабочая станция и сервер](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="8276a-292">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="8276a-293">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="8276a-293">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="8276a-294">Свойство `ThreadPoolMaxThreads` указывает максимальное число потоков для пула рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="8276a-294">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="8276a-295">Дополнительные сведения см. в разделе [Максимальное число потоков](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="8276a-295">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="8276a-296">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="8276a-296">ThreadPoolMinThreads</span></span>

<span data-ttu-id="8276a-297">Свойство `ThreadPoolMinThreads` указывает минимальное число потоков для пула рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="8276a-297">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="8276a-298">Дополнительные сведения см. в разделе [Минимальное число потоков](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="8276a-298">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="8276a-299">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="8276a-299">TieredCompilation</span></span>

<span data-ttu-id="8276a-300">Свойство `TieredCompilation` указывает, использует ли JIT-компилятор [многоуровневую компиляцию](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="8276a-300">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="8276a-301">Задайте значение `false`, чтобы отключить многоуровневую компиляцию.</span><span class="sxs-lookup"><span data-stu-id="8276a-301">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="8276a-302">Дополнительные сведения см. в разделе [Многоуровневая компиляция](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="8276a-302">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="8276a-303">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="8276a-303">TieredCompilationQuickJit</span></span>

<span data-ttu-id="8276a-304">Свойство `TieredCompilationQuickJit` указывает, использует ли JIT-компилятор быструю JIT-компиляцию.</span><span class="sxs-lookup"><span data-stu-id="8276a-304">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="8276a-305">Задайте значение `false`, чтобы отключить быструю JIT-компиляцию.</span><span class="sxs-lookup"><span data-stu-id="8276a-305">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="8276a-306">Дополнительные сведения см. в разделе [Быстрая JIT-компиляция](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="8276a-306">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="8276a-307">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="8276a-307">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="8276a-308">Свойство `TieredCompilationQuickJitForLoops` указывает, использует ли JIT-компилятор быструю JIT-компиляцию для методов, содержащих циклы.</span><span class="sxs-lookup"><span data-stu-id="8276a-308">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="8276a-309">Задайте значение `true`, чтобы включить быструю JIT-компиляцию для методов, содержащих циклы.</span><span class="sxs-lookup"><span data-stu-id="8276a-309">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="8276a-310">Дополнительные сведения см. в разделе [Быстрая JIT-компиляция для циклов](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="8276a-310">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="8276a-311">Справочники по свойствам и элементам</span><span class="sxs-lookup"><span data-stu-id="8276a-311">Reference properties and items</span></span>

- [<span data-ttu-id="8276a-312">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="8276a-312">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="8276a-313">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="8276a-313">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="8276a-314">PackageReference</span><span class="sxs-lookup"><span data-stu-id="8276a-314">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="8276a-315">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="8276a-315">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="8276a-316">Ссылки</span><span class="sxs-lookup"><span data-stu-id="8276a-316">Reference</span></span>](#reference)
- [<span data-ttu-id="8276a-317">Свойства, связанные с восстановлением</span><span class="sxs-lookup"><span data-stu-id="8276a-317">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="8276a-318">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="8276a-318">AssetTargetFallback</span></span>

<span data-ttu-id="8276a-319">Свойство `AssetTargetFallback` позволяет указать дополнительные совместимые версии платформы для ссылок на проекты и пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="8276a-319">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="8276a-320">Например, если вы указали зависимость пакета с помощью `PackageReference`, но в этом пакете нет ресурсов, совместимых с `TargetFramework` вашего проекта, тогда пригодится свойство `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="8276a-320">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="8276a-321">Совместимость пакета, на который указывает ссылка, повторно проверяется с помощью каждой целевой платформы, указанной в свойстве `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="8276a-321">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="8276a-322">В качестве значения свойства `AssetTargetFallback` можно задать одну [версию целевой платформы](../../standard/frameworks.md#supported-target-frameworks) или несколько.</span><span class="sxs-lookup"><span data-stu-id="8276a-322">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="8276a-323">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="8276a-323">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="8276a-324">Свойство `DisableImplicitFrameworkReferences` управляет неявными элементами `FrameworkReference` при разработке для .NET Core 3.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="8276a-324">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="8276a-325">При использовании .NET Core 2.1 или .NET Standard 2.0 и более ранних версий оно управляет неявными элементами [PackageReference](#packagereference) в пакетах в метапакете.</span><span class="sxs-lookup"><span data-stu-id="8276a-325">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="8276a-326">(Метапакет — это пакет на основе платформы, который состоит только из зависимостей от других пакетов.) Это свойство также управляет неявными ссылками, такими как `System` и `System.Core`, при разработке для .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8276a-326">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="8276a-327">Присвойте этому свойству значение `true`, чтобы отключить неявные элементы `FrameworkReference` или [PackageReference](#packagereference).</span><span class="sxs-lookup"><span data-stu-id="8276a-327">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="8276a-328">Если этому свойству присвоено значение `true`, можно добавить явные ссылки на только необходимые платформы или пакеты.</span><span class="sxs-lookup"><span data-stu-id="8276a-328">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="8276a-329">PackageReference</span><span class="sxs-lookup"><span data-stu-id="8276a-329">PackageReference</span></span>

<span data-ttu-id="8276a-330">Элемент `PackageReference` определяет ссылку на пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="8276a-330">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="8276a-331">Атрибут `Include` указывает идентификатор пакета.</span><span class="sxs-lookup"><span data-stu-id="8276a-331">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="8276a-332">Атрибут `Version` указывает версию или диапазон версий.</span><span class="sxs-lookup"><span data-stu-id="8276a-332">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="8276a-333">Сведения о том, как указать минимальную версию, максимальную версию, диапазон или точное соответствие, см. в разделе [Диапазоны версий](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="8276a-333">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="8276a-334">Вы также можете добавить в ссылку на проект следующие метаданные: `IncludeAssets`, `ExcludeAssets` и `PrivateAssets`.</span><span class="sxs-lookup"><span data-stu-id="8276a-334">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="8276a-335">Фрагмент файла проекта в следующем примере ссылается на пакет [System.Runtime](https://www.nuget.org/packages/System.Runtime/).</span><span class="sxs-lookup"><span data-stu-id="8276a-335">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="8276a-336">Дополнительные сведения см. в статье [Ссылки на пакеты в файлах проекта](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="8276a-336">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="8276a-337">СсылкаНаПроект</span><span class="sxs-lookup"><span data-stu-id="8276a-337">ProjectReference</span></span>

<span data-ttu-id="8276a-338">Элемент `ProjectReference` определяет ссылку на другой проект.</span><span class="sxs-lookup"><span data-stu-id="8276a-338">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="8276a-339">Проект, на который указывает ссылка, добавляется как зависимость пакета NuGet, то есть обрабатывается так же, как `PackageReference`.</span><span class="sxs-lookup"><span data-stu-id="8276a-339">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="8276a-340">Атрибут `Include` задает путь к проекту.</span><span class="sxs-lookup"><span data-stu-id="8276a-340">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="8276a-341">Вы также можете добавить в ссылку на проект следующие метаданные: `IncludeAssets`, `ExcludeAssets` и `PrivateAssets`.</span><span class="sxs-lookup"><span data-stu-id="8276a-341">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="8276a-342">Фрагмент файла проекта в следующем примере ссылается на проект `Project2`.</span><span class="sxs-lookup"><span data-stu-id="8276a-342">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="8276a-343">Справочник</span><span class="sxs-lookup"><span data-stu-id="8276a-343">Reference</span></span>

<span data-ttu-id="8276a-344">Элемент `Reference` определяет ссылку на файл сборки.</span><span class="sxs-lookup"><span data-stu-id="8276a-344">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="8276a-345">Атрибут `Include` задает имя файла, а метаданные `HintPath` указывают путь к этой сборке.</span><span class="sxs-lookup"><span data-stu-id="8276a-345">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="8276a-346">Свойства, связанные с восстановлением</span><span class="sxs-lookup"><span data-stu-id="8276a-346">Restore-related properties</span></span>

<span data-ttu-id="8276a-347">При восстановлении пакета, на который указывает ссылка, устанавливаются все его прямые зависимости и все зависимости этих зависимостей.</span><span class="sxs-lookup"><span data-stu-id="8276a-347">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="8276a-348">Можно настроить восстановление пакетов, указав такие свойства, как `RestorePackagesPath` и `RestoreIgnoreFailedSources`.</span><span class="sxs-lookup"><span data-stu-id="8276a-348">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="8276a-349">Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект восстановления](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="8276a-349">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a><span data-ttu-id="8276a-350">Свойства запуска</span><span class="sxs-lookup"><span data-stu-id="8276a-350">Run properties</span></span>

<span data-ttu-id="8276a-351">Следующие свойства используются для запуска приложения с помощью команды [`dotnet run`](../tools/dotnet-run.md):</span><span class="sxs-lookup"><span data-stu-id="8276a-351">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="8276a-352">RunArguments</span><span class="sxs-lookup"><span data-stu-id="8276a-352">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="8276a-353">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="8276a-353">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="8276a-354">RunArguments</span><span class="sxs-lookup"><span data-stu-id="8276a-354">RunArguments</span></span>

<span data-ttu-id="8276a-355">Свойство `RunArguments` определяет аргументы, которые передаются в приложение при его запуске.</span><span class="sxs-lookup"><span data-stu-id="8276a-355">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="8276a-356">Можно указать дополнительные аргументы для передачи в приложение с помощью параметра [`--` для `dotnet run`](../tools/dotnet-run.md#options).</span><span class="sxs-lookup"><span data-stu-id="8276a-356">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="8276a-357">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="8276a-357">RunWorkingDirectory</span></span>

<span data-ttu-id="8276a-358">Свойство `RunWorkingDirectory` определяет рабочий каталог для запуска процесса приложения.</span><span class="sxs-lookup"><span data-stu-id="8276a-358">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="8276a-359">Это может быть абсолютный путь или путь относительно каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="8276a-359">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="8276a-360">Если каталог не указан, в качестве рабочего каталога используется `OutDir`.</span><span class="sxs-lookup"><span data-stu-id="8276a-360">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties"></a><span data-ttu-id="8276a-361">Свойства размещения</span><span class="sxs-lookup"><span data-stu-id="8276a-361">Hosting properties</span></span>

- [<span data-ttu-id="8276a-362">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="8276a-362">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="8276a-363">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="8276a-363">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="8276a-364">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="8276a-364">EnableComHosting</span></span>

<span data-ttu-id="8276a-365">Свойство `EnableComHosting` указывает, что сборка предоставляет сервер COM.</span><span class="sxs-lookup"><span data-stu-id="8276a-365">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="8276a-366">Установка `EnableComHosting` в `true` также подразумевает, что [EnableDynamicLoading](#enabledynamicloading) — `true`.</span><span class="sxs-lookup"><span data-stu-id="8276a-366">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="8276a-367">Дополнительные сведения см. в разделе [Предоставление компонентов .NET для COM](../native-interop/expose-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-367">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="8276a-368">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="8276a-368">EnableDynamicLoading</span></span>

<span data-ttu-id="8276a-369">Свойство `EnableDynamicLoading` указывает, что сборка является динамически загружаемым компонентом.</span><span class="sxs-lookup"><span data-stu-id="8276a-369">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="8276a-370">Компонентом может быть [библиотека COM](/windows/win32/com/the-component-object-model) или библиотека, не относящаяся к COM, которую можно [использовать из собственного узла](../tutorials/netcore-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="8276a-370">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="8276a-371">Если присвоить этому свойству значения `true`:</span><span class="sxs-lookup"><span data-stu-id="8276a-371">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="8276a-372">Создается файл *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="8276a-372">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="8276a-373">[Накат](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) получает значение `LatestMinor`.</span><span class="sxs-lookup"><span data-stu-id="8276a-373">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="8276a-374">Ссылки NuGet копируются локально.</span><span class="sxs-lookup"><span data-stu-id="8276a-374">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="8276a-375">См. также</span><span class="sxs-lookup"><span data-stu-id="8276a-375">See also</span></span>

- [<span data-ttu-id="8276a-376">Справочник по схеме MSBuild</span><span class="sxs-lookup"><span data-stu-id="8276a-376">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="8276a-377">Общие свойства MSBuild</span><span class="sxs-lookup"><span data-stu-id="8276a-377">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="8276a-378">Свойства MSBuild для целевого объекта pack NuGet</span><span class="sxs-lookup"><span data-stu-id="8276a-378">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="8276a-379">Свойства MSBuild для целевого объекта restore NuGet</span><span class="sxs-lookup"><span data-stu-id="8276a-379">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="8276a-380">Настройка сборки</span><span class="sxs-lookup"><span data-stu-id="8276a-380">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
