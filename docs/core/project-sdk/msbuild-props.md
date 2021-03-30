---
title: Свойства MSBuild для Microsoft.NET.Sdk
description: Справочник по свойствам и элементам MSBuild, распознаваемым пакетом SDK для .NET.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: f6a49a0040bcb38dbaf433f6ea53bb8aad24c65b
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759889"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="651be-103">Справочник по MSBuild для проектов пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="651be-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="651be-104">Эта страница содержит справочные сведения о свойствах и элементах MSBuild, которые вы можете использовать для настройки проектов .NET.</span><span class="sxs-lookup"><span data-stu-id="651be-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="651be-105">Работа над этой страницей еще не завершена, поэтому здесь приведены лишь некоторые полезные свойства MSBuild для пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="651be-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="651be-106">Список стандартных свойств см. в статье [Общие свойства MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="651be-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="651be-107">Свойства платформы</span><span class="sxs-lookup"><span data-stu-id="651be-107">Framework properties</span></span>

<span data-ttu-id="651be-108">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="651be-108">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="651be-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="651be-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="651be-110">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="651be-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="651be-111">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="651be-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="651be-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="651be-112">TargetFramework</span></span>

<span data-ttu-id="651be-113">Свойство `TargetFramework` определяет версию целевой платформы для приложения.</span><span class="sxs-lookup"><span data-stu-id="651be-113">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="651be-114">Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="651be-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="651be-115">Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="651be-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="651be-116">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="651be-116">TargetFrameworks</span></span>

<span data-ttu-id="651be-117">Используйте свойство `TargetFrameworks`, если приложение должно быть предназначено для нескольких платформ.</span><span class="sxs-lookup"><span data-stu-id="651be-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="651be-118">Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="651be-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="651be-119">Это свойство игнорируется, если указано свойство `TargetFramework` (в единственном числе).</span><span class="sxs-lookup"><span data-stu-id="651be-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="651be-120">Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="651be-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="651be-121">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="651be-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="651be-122">Это свойство применяется только к проектам, использующим `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="651be-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="651be-123">Он не применяется к проектам, использующим `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="651be-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="651be-124">Используйте свойство `NetStandardImplicitPackageVersion`, если вам нужно указать версию платформы ниже версии метапакета.</span><span class="sxs-lookup"><span data-stu-id="651be-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="651be-125">Файл проекта, приведенный в следующем примере, предназначен для `netstandard1.3`, но использует `NETStandard.Library` версии 1.6.0.</span><span class="sxs-lookup"><span data-stu-id="651be-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="651be-126">Свойства пакета</span><span class="sxs-lookup"><span data-stu-id="651be-126">Package properties</span></span>

<span data-ttu-id="651be-127">Для описания пакета, созданного из проекта, можно указать такие свойства, как `PackageId`, `PackageVersion`, `PackageIcon`, `Title` и `Description`.</span><span class="sxs-lookup"><span data-stu-id="651be-127">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="651be-128">Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект пакета](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="651be-128">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-related-properties"></a><span data-ttu-id="651be-129">Свойства, связанные с публикацией</span><span class="sxs-lookup"><span data-stu-id="651be-129">Publish-related properties</span></span>

<span data-ttu-id="651be-130">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="651be-130">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="651be-131">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="651be-131">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="651be-132">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="651be-132">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="651be-133">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="651be-133">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="651be-134">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="651be-134">PreserveCompilationContext</span></span>](#preservecompilationcontext)
- [<span data-ttu-id="651be-135">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="651be-135">PreserveCompilationReferences</span></span>](#preservecompilationreferences)
- [<span data-ttu-id="651be-136">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="651be-136">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="651be-137">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="651be-137">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="651be-138">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="651be-138">UseAppHost</span></span>](#useapphost)

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="651be-139">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="651be-139">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="651be-140">Свойство `AppendTargetFrameworkToOutputPath` определяет, добавляется ли [моникер целевой платформы (TFM)](../../standard/frameworks.md) к выходному пути (который определяется свойством [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span><span class="sxs-lookup"><span data-stu-id="651be-140">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="651be-141">Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть).</span><span class="sxs-lookup"><span data-stu-id="651be-141">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="651be-142">При установке значения `false` для свойства `AppendTargetFrameworkToOutputPath` TFM не добавляется к выходному пути.</span><span class="sxs-lookup"><span data-stu-id="651be-142">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="651be-143">Однако при отсутствии TFM в выходном пути несколько артефактов сборки могут перезаписывать друг друга.</span><span class="sxs-lookup"><span data-stu-id="651be-143">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="651be-144">Например, при установке следующего параметра выходной путь для приложения .NET 5.0 изменяется с `bin\Debug\net5.0` на `bin\Debug`:</span><span class="sxs-lookup"><span data-stu-id="651be-144">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="651be-145">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="651be-145">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="651be-146">Свойство `AppendRuntimeIdentifierToOutputPath` определяет, добавляется ли к выходному пути [идентификатор среды выполнения (RID)](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="651be-146">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="651be-147">Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть).</span><span class="sxs-lookup"><span data-stu-id="651be-147">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="651be-148">При установке значения `false` для свойства `AppendRuntimeIdentifierToOutputPath` RID не добавляется к выходному пути.</span><span class="sxs-lookup"><span data-stu-id="651be-148">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="651be-149">Например, при установке следующего параметра выходной путь для приложения .NET 5.0 и идентификатора RID `win10-x64` изменяется с `bin\Debug\net5.0\win10-x64` на `bin\Debug\net5.0`:</span><span class="sxs-lookup"><span data-stu-id="651be-149">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="651be-150">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="651be-150">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="651be-151">Свойство `CopyLocalLockFileAssemblies` полезно для проектов подключаемых модулей, которые имеют зависимости от других библиотек.</span><span class="sxs-lookup"><span data-stu-id="651be-151">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="651be-152">Если для этого свойства задано значение `true`, все зависимости пакета NuGet копируются в выходной каталог.</span><span class="sxs-lookup"><span data-stu-id="651be-152">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="651be-153">Это означает, что вы можете использовать выходные данные `dotnet build` для запуска подключаемого модуля на любом компьютере.</span><span class="sxs-lookup"><span data-stu-id="651be-153">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="651be-154">Кроме того, можно использовать `dotnet publish` для публикации библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="651be-154">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="651be-155">Дополнительные сведения см. в разделе [dotnet publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="651be-155">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="preservecompilationcontext"></a><span data-ttu-id="651be-156">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="651be-156">PreserveCompilationContext</span></span>

<span data-ttu-id="651be-157">Свойство `PreserveCompilationContext` позволяет собранному или опубликованному приложению компилировать дополнительный код во время выполнения с теми же параметрами, которые использовались во время сборки.</span><span class="sxs-lookup"><span data-stu-id="651be-157">The `PreserveCompilationContext` property allows a built or published application to compile more code at run time using the same settings that were used at build time.</span></span> <span data-ttu-id="651be-158">Сборки, ссылки на которые были указаны во время сборки, будут скопированы в подкаталог *ref* выходного каталога.</span><span class="sxs-lookup"><span data-stu-id="651be-158">The assemblies referenced at build time will be copied into the *ref* subdirectory of the output directory.</span></span> <span data-ttu-id="651be-159">Имена базовых сборок хранятся в файле *.deps.json* приложения вместе с параметрами, передаваемыми компилятору.</span><span class="sxs-lookup"><span data-stu-id="651be-159">The names of the reference assemblies are stored in the application's *.deps.json* file along with the options passed to the compiler.</span></span> <span data-ttu-id="651be-160">Эту информацию можно получить с помощью свойств <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> и <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="651be-160">You can retrieve this information using the <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> and <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> properties.</span></span>

<span data-ttu-id="651be-161">Эта функциональность в основном используется внутри системы для поддержки компиляции файлов Razor во время выполнения на страницах MVC и Razor ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="651be-161">This functionality is mostly used internally by ASP.NET Core MVC and Razor pages to support run-time compilation of Razor files.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a><span data-ttu-id="651be-162">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="651be-162">PreserveCompilationReferences</span></span>

<span data-ttu-id="651be-163">Свойство `PreserveCompilationReferences` аналогично свойству [PreserveCompilationContext](#preservecompilationcontext) за исключением того, что при его использовании в каталог публикации копируются только указанные ссылками сборки, но не копируется файл *.deps.json*.</span><span class="sxs-lookup"><span data-stu-id="651be-163">The `PreserveCompilationReferences` property is similar to the [PreserveCompilationContext](#preservecompilationcontext) property, except that it only copies the referenced assemblies to the publish directory, and not the *.deps.json* file.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

<span data-ttu-id="651be-164">Дополнительные сведения см. в разделе [Свойства пакета SDK Razor](/aspnet/core/razor-pages/sdk#properties).</span><span class="sxs-lookup"><span data-stu-id="651be-164">For more information, see [Razor SDK properties](/aspnet/core/razor-pages/sdk#properties).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="651be-165">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="651be-165">RuntimeIdentifier</span></span>

<span data-ttu-id="651be-166">Свойство `RuntimeIdentifier` позволяет указать для проекта один [идентификатор среды выполнения (RID)](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="651be-166">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="651be-167">Идентификатор среды выполнения позволяет опубликовать автономное развертывание.</span><span class="sxs-lookup"><span data-stu-id="651be-167">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="651be-168">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="651be-168">RuntimeIdentifiers</span></span>

<span data-ttu-id="651be-169">Свойство `RuntimeIdentifiers` позволяет указать для проекта список [идентификаторов среды выполнения (RID)](../rid-catalog.md) (в качестве разделителя используется точка с запятой).</span><span class="sxs-lookup"><span data-stu-id="651be-169">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="651be-170">Используйте это свойство, если вам нужна публикация для нескольких сред.</span><span class="sxs-lookup"><span data-stu-id="651be-170">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="651be-171">`RuntimeIdentifiers` используется во время восстановления для обеспечения наличия в графе нужных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="651be-171">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="651be-172">`RuntimeIdentifier` (в единственном числе) может ускорить создание сборок, когда требуется только одна среда выполнения.</span><span class="sxs-lookup"><span data-stu-id="651be-172">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="useapphost"></a><span data-ttu-id="651be-173">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="651be-173">UseAppHost</span></span>

<span data-ttu-id="651be-174">Свойство `UseAppHost` контролирует создание собственного исполняемого файла для развертывания.</span><span class="sxs-lookup"><span data-stu-id="651be-174">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="651be-175">Этот файл требуется для автономных развертываний.</span><span class="sxs-lookup"><span data-stu-id="651be-175">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="651be-176">В .NET Core 3.0 и более поздних версиях зависимый от платформы исполняемый файл создается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="651be-176">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="651be-177">Задайте свойству `UseAppHost` значение `false`, чтобы отключить создание исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="651be-177">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="651be-178">Дополнительные сведения см. в статье о [развертывании приложений .NET](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="651be-178">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compilation-related-properties"></a><span data-ttu-id="651be-179">Свойства, связанные с компиляцией</span><span class="sxs-lookup"><span data-stu-id="651be-179">Compilation-related properties</span></span>

<span data-ttu-id="651be-180">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="651be-180">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="651be-181">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="651be-181">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="651be-182">LangVersion</span><span class="sxs-lookup"><span data-stu-id="651be-182">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="651be-183">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="651be-183">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="651be-184">Свойство `EmbeddedResourceUseDependentUponConvention` определяет, будет ли использоваться информация о типах в исходных файлах, расположенных в одной папке с файлами ресурсов, для создания имен файлов манифеста этих ресурсов.</span><span class="sxs-lookup"><span data-stu-id="651be-184">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="651be-185">Например, если *Form1.resx* находится в той же папке, что и *Form1.cs*, а `EmbeddedResourceUseDependentUponConvention` имеет значение `true`, то созданному файл *.resources* присваивается имя на основе имени первого типа, определенного в файле *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="651be-185">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="651be-186">Например, если первым типом в файле *Form1.cs* является `MyNamespace.Form1`, созданному файлу присваивается имя *MyNamespace.Form1.resources*.</span><span class="sxs-lookup"><span data-stu-id="651be-186">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="651be-187">Если для `EmbeddedResource` элемента заданы метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого файла ресурсов будет создаваться на основе таких метаданных.</span><span class="sxs-lookup"><span data-stu-id="651be-187">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="651be-188">По умолчанию для нового проекта .NET этому свойству задается значение `true`.</span><span class="sxs-lookup"><span data-stu-id="651be-188">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="651be-189">Если задано значение `false` и для элемента `EmbeddedResource` в файле проекта не указаны метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого ресурса будет основано на имени корневого пространства имен проекта и относительном пути к файлу *.resx*.</span><span class="sxs-lookup"><span data-stu-id="651be-189">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="651be-190">Дополнительные сведения об определение имени файла манифеста см. [здесь](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="651be-190">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="651be-191">LangVersion</span><span class="sxs-lookup"><span data-stu-id="651be-191">LangVersion</span></span>

<span data-ttu-id="651be-192">Свойство `LangVersion` позволяет указать конкретную версию языка программирования.</span><span class="sxs-lookup"><span data-stu-id="651be-192">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="651be-193">Например, если требуется доступ к предварительным версиям функций C#, задайте параметру `LangVersion` значение `preview`.</span><span class="sxs-lookup"><span data-stu-id="651be-193">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="651be-194">Дополнительные сведения см. в статье [Управление версиями языка C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="651be-194">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="651be-195">Свойства включения элементов по умолчанию</span><span class="sxs-lookup"><span data-stu-id="651be-195">Default item inclusion properties</span></span>

<span data-ttu-id="651be-196">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="651be-196">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="651be-197">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="651be-197">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="651be-198">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="651be-198">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="651be-199">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="651be-199">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="651be-200">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="651be-200">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="651be-201">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="651be-201">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="651be-202">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="651be-202">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="651be-203">Дополнительные сведения см. в разделе [Включения и исключения по умолчанию](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="651be-203">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="651be-204">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="651be-204">DefaultItemExcludes</span></span>

<span data-ttu-id="651be-205">Используйте свойство `DefaultItemExcludes`, чтобы определить стандартные маски для файлов и папок, которые должны быть исключены из стандартных масок включения, исключения и удаления.</span><span class="sxs-lookup"><span data-stu-id="651be-205">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="651be-206">По умолчанию папки *./bin* и *./obj* исключаются из стандартных масок.</span><span class="sxs-lookup"><span data-stu-id="651be-206">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="651be-207">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="651be-207">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="651be-208">Используйте свойство `DefaultExcludesInProjectFolder`, чтобы определить стандартные маски для файлов и папок в папке проекта, которые должны быть исключены из стандартных масок включения, исключения и удаления.</span><span class="sxs-lookup"><span data-stu-id="651be-208">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="651be-209">По умолчанию папки, начинающиеся с точки (`.`), такие как *.git* и *.vs*, исключаются из стандартных масок.</span><span class="sxs-lookup"><span data-stu-id="651be-209">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="651be-210">Это свойство очень похоже на свойство `DefaultItemExcludes`, за исключением того, что оно учитывает только файлы и папки в папке проекта.</span><span class="sxs-lookup"><span data-stu-id="651be-210">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="651be-211">Если стандартная маска будет случайно соответствовать элементам за пределами папки проекта с относительным путем, используйте свойство `DefaultExcludesInProjectFolder` вместо свойства `DefaultItemExcludes`.</span><span class="sxs-lookup"><span data-stu-id="651be-211">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="651be-212">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="651be-212">EnableDefaultItems</span></span>

<span data-ttu-id="651be-213">Свойство `EnableDefaultItems` определяет, включаются ли в проект неявным образом элементы компиляции, элементы внедренных ресурсов и элементы `None`.</span><span class="sxs-lookup"><span data-stu-id="651be-213">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="651be-214">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="651be-214">The default value is `true`.</span></span> <span data-ttu-id="651be-215">Задайте значение `false` для свойства `EnableDefaultItems`, чтобы отключить все неявные включения файлов.</span><span class="sxs-lookup"><span data-stu-id="651be-215">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="651be-216">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="651be-216">EnableDefaultCompileItems</span></span>

<span data-ttu-id="651be-217">Свойство `EnableDefaultCompileItems` определяет, включаются ли в проект неявным образом элементы компиляции.</span><span class="sxs-lookup"><span data-stu-id="651be-217">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="651be-218">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="651be-218">The default value is `true`.</span></span> <span data-ttu-id="651be-219">Задайте значение `false` для свойства `EnableDefaultCompileItems`, чтобы отключить неявное включение файлов \*.cs и других файлов расширения языка.</span><span class="sxs-lookup"><span data-stu-id="651be-219">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="651be-220">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="651be-220">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="651be-221">Свойство `EnableDefaultEmbeddedResourceItems` определяет, включаются ли в проект неявным образом элементы внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="651be-221">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="651be-222">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="651be-222">The default value is `true`.</span></span> <span data-ttu-id="651be-223">Задайте значение `false` для свойства `EnableDefaultEmbeddedResourceItems`, чтобы отключить неявное включение файлов внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="651be-223">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="651be-224">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="651be-224">EnableDefaultNoneItems</span></span>

<span data-ttu-id="651be-225">Свойство `EnableDefaultNoneItems` определяет, включаются ли в проект неявным образом элементы `None` (файлы, которые не играют никакой роли в процессе сборки).</span><span class="sxs-lookup"><span data-stu-id="651be-225">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="651be-226">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="651be-226">The default value is `true`.</span></span> <span data-ttu-id="651be-227">Задайте значение `false` для свойства `EnableDefaultNoneItems`, чтобы отключить неявное включение элементов `None`.</span><span class="sxs-lookup"><span data-stu-id="651be-227">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="651be-228">Свойства анализа кода</span><span class="sxs-lookup"><span data-stu-id="651be-228">Code analysis properties</span></span>

<span data-ttu-id="651be-229">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="651be-229">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="651be-230">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="651be-230">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="651be-231">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="651be-231">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="651be-232">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="651be-232">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="651be-233">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="651be-233">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="651be-234">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="651be-234">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="651be-235">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="651be-235">AnalysisLevel</span></span>

<span data-ttu-id="651be-236">Свойство `AnalysisLevel` позволяет указать уровень анализа кода.</span><span class="sxs-lookup"><span data-stu-id="651be-236">The `AnalysisLevel` property lets you specify a code-analysis level.</span></span> <span data-ttu-id="651be-237">Например, если требуется доступ к анализаторам кода предварительной версии, задайте для параметра `AnalysisLevel` значение `preview`.</span><span class="sxs-lookup"><span data-stu-id="651be-237">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span>

<span data-ttu-id="651be-238">Значение по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="651be-238">Default value:</span></span>

- <span data-ttu-id="651be-239">Если проект предназначен для .NET 5.0 или более поздней версии или если вы добавили свойство [AnalysisMode](#analysismode), значением по умолчанию будет `latest`.</span><span class="sxs-lookup"><span data-stu-id="651be-239">If your project targets .NET 5.0 or later, or if you've added the [AnalysisMode](#analysismode) property, the default value is `latest`.</span></span>
- <span data-ttu-id="651be-240">В противном случае это свойство не будет учитываться, если оно явно не добавлено в файл проекта.</span><span class="sxs-lookup"><span data-stu-id="651be-240">Otherwise, this property is omitted unless you explicitly add it to the project file.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="651be-241">В следующей таблице приведены доступные параметры.</span><span class="sxs-lookup"><span data-stu-id="651be-241">The following table shows the available options.</span></span>

| <span data-ttu-id="651be-242">Значение</span><span class="sxs-lookup"><span data-stu-id="651be-242">Value</span></span> | <span data-ttu-id="651be-243">Значение</span><span class="sxs-lookup"><span data-stu-id="651be-243">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="651be-244">Используются новейшие анализаторы кода, которые были выпущены.</span><span class="sxs-lookup"><span data-stu-id="651be-244">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="651be-245">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="651be-245">This is the default.</span></span> |
| `preview` | <span data-ttu-id="651be-246">Используются новейшие анализаторы кода, даже если они находятся на этапе предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="651be-246">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="651be-247">Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила.</span><span class="sxs-lookup"><span data-stu-id="651be-247">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="651be-248">Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила.</span><span class="sxs-lookup"><span data-stu-id="651be-248">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

> [!NOTE]
> <span data-ttu-id="651be-249">Это свойство не влияет на анализ кода в проектах, которые не ссылаются на [пакет SDK проекта](overview.md), например, проекты на устаревших платформах .NET Framework, которые ссылаются на пакет NuGet Microsoft.CodeAnalysis.NetAnalyzers.</span><span class="sxs-lookup"><span data-stu-id="651be-249">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="analysismode"></a><span data-ttu-id="651be-250">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="651be-250">AnalysisMode</span></span>

<span data-ttu-id="651be-251">Начиная с .NET 5.0 пакет SDK для .NET поставляется со всеми [правилами качества кода "CA"](../../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="651be-251">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="651be-252">По умолчанию в качестве предупреждений сборки включены только [некоторые правила](../../fundamentals/code-analysis/overview.md#enabled-rules).</span><span class="sxs-lookup"><span data-stu-id="651be-252">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="651be-253">Свойство `AnalysisMode` позволяет настроить набор правил, включенных по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="651be-253">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="651be-254">Можно либо переключиться на более агрессивный (неявный) режим анализа, либо более консервативный (явный) режим анализа.</span><span class="sxs-lookup"><span data-stu-id="651be-254">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="651be-255">Например, если вы хотите включить все правила по умолчанию как предупреждения сборки, установите значение `AllEnabledByDefault`.</span><span class="sxs-lookup"><span data-stu-id="651be-255">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="651be-256">В следующей таблице приведены доступные параметры.</span><span class="sxs-lookup"><span data-stu-id="651be-256">The following table shows the available options.</span></span>

| <span data-ttu-id="651be-257">Значение</span><span class="sxs-lookup"><span data-stu-id="651be-257">Value</span></span> | <span data-ttu-id="651be-258">Значение</span><span class="sxs-lookup"><span data-stu-id="651be-258">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="651be-259">Режим по умолчанию, при котором определенные правила включаются в виде предупреждений сборки, некоторые правила включаются в качестве предложений интегрированной среды разработки Visual Studio, а остальные отключаются.</span><span class="sxs-lookup"><span data-stu-id="651be-259">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="651be-260">Агрессивный или неявный режим означает, что все правила по умолчанию включены как предупреждения сборки.</span><span class="sxs-lookup"><span data-stu-id="651be-260">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="651be-261">Вы можете выборочно [отказаться](../../fundamentals/code-analysis/configuration-options.md) от отдельных правил, чтобы отключить их.</span><span class="sxs-lookup"><span data-stu-id="651be-261">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="651be-262">Консервативный или явный режим означает, что все правила по умолчанию отключены.</span><span class="sxs-lookup"><span data-stu-id="651be-262">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="651be-263">Можно выборочно [принять](../../fundamentals/code-analysis/configuration-options.md) отдельные правила, чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="651be-263">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

> [!NOTE]
> <span data-ttu-id="651be-264">Это свойство не влияет на анализ кода в проектах, которые не ссылаются на [пакет SDK проекта](overview.md), например, проекты на устаревших платформах .NET Framework, которые ссылаются на пакет NuGet Microsoft.CodeAnalysis.NetAnalyzers.</span><span class="sxs-lookup"><span data-stu-id="651be-264">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="651be-265">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="651be-265">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="651be-266">Свойство `CodeAnalysisTreatWarningsAsErrors` позволяет настроить, следует ли обрабатывать предупреждения анализа качества кода (CAxxxx) как предупреждения и прекращать сборку.</span><span class="sxs-lookup"><span data-stu-id="651be-266">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="651be-267">Если при построении проектов используется флаг `-warnaserror`, предупреждения [анализа качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis) также обрабатываются как ошибки.</span><span class="sxs-lookup"><span data-stu-id="651be-267">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="651be-268">Если вы не хотите, чтобы предупреждения качества кода обрабатывались как ошибки, можно задать для свойства MSBuild `CodeAnalysisTreatWarningsAsErrors` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="651be-268">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="651be-269">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="651be-269">EnableNETAnalyzers</span></span>

<span data-ttu-id="651be-270">Для проектов, предназначенных для .NET 5.0 или более поздней версии, по умолчанию включен [анализ качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis).</span><span class="sxs-lookup"><span data-stu-id="651be-270">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="651be-271">Вы можете включить анализ кода .NET для проектов в стиле пакета SDK, предназначенных для более ранних версий .NET, установив для свойства `EnableNETAnalyzers` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="651be-271">You can enable .NET code analysis for SDK-style projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="651be-272">Чтобы отключить анализ кода в любом проекте, присвойте этому свойству значение `false`.</span><span class="sxs-lookup"><span data-stu-id="651be-272">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="651be-273">Это свойство применяется к встроенным анализаторам в пакете SDK для .NET 5+.</span><span class="sxs-lookup"><span data-stu-id="651be-273">This property applies specifically to the built-in analyzers in the .NET 5+ SDK.</span></span> <span data-ttu-id="651be-274">Его не следует использовать при установке пакета NuGet для анализа кода.</span><span class="sxs-lookup"><span data-stu-id="651be-274">It should not be used when you install a NuGet code analysis package.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="651be-275">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="651be-275">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="651be-276">Эта функция в настоящее время является экспериментальной и может измениться в .NET 6 по сравнению с реализацией в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="651be-276">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="651be-277">[Анализ стиля кода .NET](../../fundamentals/code-analysis/overview.md#code-style-analysis) по умолчанию отключен при сборке для всех проектов .NET.</span><span class="sxs-lookup"><span data-stu-id="651be-277">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="651be-278">Можно включить анализ стиля кода для проектов .NET, задав для свойства `EnforceCodeStyleInBuild` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="651be-278">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="651be-279">Все правила стиля кода, которые [настроены](../../fundamentals/code-analysis/overview.md#code-style-analysis) как предупреждения или ошибки, будут выполняться при нарушениях сборки и отчета.</span><span class="sxs-lookup"><span data-stu-id="651be-279">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="651be-280">Свойства конфигурации среды выполнения</span><span class="sxs-lookup"><span data-stu-id="651be-280">Run-time configuration properties</span></span>

<span data-ttu-id="651be-281">Вы можете настроить некоторые варианты поведения среды выполнения, указав свойства MSBuild в файле проекта приложения.</span><span class="sxs-lookup"><span data-stu-id="651be-281">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="651be-282">Сведения о других способах настройки поведения среды выполнения см. в статье о [параметрах конфигурации среды выполнения](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="651be-282">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="651be-283">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="651be-283">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="651be-284">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="651be-284">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="651be-285">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="651be-285">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="651be-286">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="651be-286">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="651be-287">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="651be-287">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="651be-288">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="651be-288">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="651be-289">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="651be-289">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="651be-290">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="651be-290">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="651be-291">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="651be-291">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="651be-292">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="651be-292">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="651be-293">Свойство `ConcurrentGarbageCollection` указывает, включена ли [фоновая (параллельная) сборка мусора](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="651be-293">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="651be-294">Задайте значение `false`, чтобы отключить фоновую сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="651be-294">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="651be-295">Дополнительные сведения см. в разделе [Сборка мусора в фоновом режиме](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="651be-295">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="651be-296">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="651be-296">InvariantGlobalization</span></span>

<span data-ttu-id="651be-297">Свойство `InvariantGlobalization` определяет, выполняется ли приложение в *инвариантном режиме глобализации*, что означает, что у него нет доступа к данным, относящимся к языку и региональным параметрам.</span><span class="sxs-lookup"><span data-stu-id="651be-297">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="651be-298">Установите значение `true` для запуска в инвариантном режиме глобализации.</span><span class="sxs-lookup"><span data-stu-id="651be-298">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="651be-299">Дополнительные сведения см. в разделе [Инвариантный режим](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="651be-299">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="651be-300">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="651be-300">RetainVMGarbageCollection</span></span>

<span data-ttu-id="651be-301">Свойство `RetainVMGarbageCollection` настраивает сборщик мусора для помещения удаленных сегментов памяти в список ожидания для будущего использования или освобождения.</span><span class="sxs-lookup"><span data-stu-id="651be-301">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="651be-302">Значение `true` указывает сборщику мусора разместить сегменты в списке ожидания.</span><span class="sxs-lookup"><span data-stu-id="651be-302">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="651be-303">Дополнительные сведения см. в разделе [Сохранение виртуальной машины](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="651be-303">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="651be-304">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="651be-304">ServerGarbageCollection</span></span>

<span data-ttu-id="651be-305">Свойство `ServerGarbageCollection` указывает, использует ли приложение [сборку мусора рабочей станции или сборку мусора сервера](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="651be-305">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="651be-306">Задайте значение `true`, чтобы использовать сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="651be-306">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="651be-307">Дополнительные сведения см. в разделе [Рабочая станция и сервер](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="651be-307">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="651be-308">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="651be-308">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="651be-309">Свойство `ThreadPoolMaxThreads` указывает максимальное число потоков для пула рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="651be-309">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="651be-310">Дополнительные сведения см. в разделе [Максимальное число потоков](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="651be-310">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="651be-311">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="651be-311">ThreadPoolMinThreads</span></span>

<span data-ttu-id="651be-312">Свойство `ThreadPoolMinThreads` указывает минимальное число потоков для пула рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="651be-312">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="651be-313">Дополнительные сведения см. в разделе [Минимальное число потоков](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="651be-313">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="651be-314">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="651be-314">TieredCompilation</span></span>

<span data-ttu-id="651be-315">Свойство `TieredCompilation` указывает, использует ли JIT-компилятор [многоуровневую компиляцию](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="651be-315">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="651be-316">Задайте значение `false`, чтобы отключить многоуровневую компиляцию.</span><span class="sxs-lookup"><span data-stu-id="651be-316">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="651be-317">Дополнительные сведения см. в разделе [Многоуровневая компиляция](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="651be-317">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="651be-318">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="651be-318">TieredCompilationQuickJit</span></span>

<span data-ttu-id="651be-319">Свойство `TieredCompilationQuickJit` указывает, использует ли JIT-компилятор быструю JIT-компиляцию.</span><span class="sxs-lookup"><span data-stu-id="651be-319">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="651be-320">Задайте значение `false`, чтобы отключить быструю JIT-компиляцию.</span><span class="sxs-lookup"><span data-stu-id="651be-320">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="651be-321">Дополнительные сведения см. в разделе [Быстрая JIT-компиляция](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="651be-321">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="651be-322">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="651be-322">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="651be-323">Свойство `TieredCompilationQuickJitForLoops` указывает, использует ли JIT-компилятор быструю JIT-компиляцию для методов, содержащих циклы.</span><span class="sxs-lookup"><span data-stu-id="651be-323">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="651be-324">Задайте значение `true`, чтобы включить быструю JIT-компиляцию для методов, содержащих циклы.</span><span class="sxs-lookup"><span data-stu-id="651be-324">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="651be-325">Дополнительные сведения см. в разделе [Быстрая JIT-компиляция для циклов](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="651be-325">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="651be-326">Свойства ссылки</span><span class="sxs-lookup"><span data-stu-id="651be-326">Reference properties</span></span>

<span data-ttu-id="651be-327">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="651be-327">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="651be-328">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="651be-328">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="651be-329">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="651be-329">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="651be-330">Свойства, связанные с восстановлением</span><span class="sxs-lookup"><span data-stu-id="651be-330">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="651be-331">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="651be-331">AssetTargetFallback</span></span>

<span data-ttu-id="651be-332">Свойство `AssetTargetFallback` позволяет указать дополнительные совместимые версии платформы для ссылок на проекты и пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="651be-332">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="651be-333">Например, если вы указали зависимость пакета с помощью `PackageReference`, но в этом пакете нет ресурсов, совместимых с `TargetFramework` вашего проекта, тогда пригодится свойство `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="651be-333">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="651be-334">Совместимость пакета, на который указывает ссылка, повторно проверяется с помощью каждой целевой платформы, указанной в свойстве `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="651be-334">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span> <span data-ttu-id="651be-335">Это свойство заменяет устаревшее свойство `PackageTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="651be-335">This property replaces the deprecated property `PackageTargetFallback`.</span></span>

<span data-ttu-id="651be-336">В качестве значения свойства `AssetTargetFallback` можно задать одну [версию целевой платформы](../../standard/frameworks.md#supported-target-frameworks) или несколько.</span><span class="sxs-lookup"><span data-stu-id="651be-336">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="651be-337">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="651be-337">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="651be-338">Свойство `DisableImplicitFrameworkReferences` управляет неявными элементами `FrameworkReference` при разработке для .NET Core 3.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="651be-338">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="651be-339">При использовании .NET Core 2.1 или .NET Standard 2.0 и более ранних версий оно управляет неявными элементами [PackageReference](#packagereference) в пакетах в метапакете.</span><span class="sxs-lookup"><span data-stu-id="651be-339">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="651be-340">(Метапакет — это пакет на основе платформы, который состоит только из зависимостей от других пакетов.) Это свойство также управляет неявными ссылками, такими как `System` и `System.Core`, при разработке для .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="651be-340">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="651be-341">Присвойте этому свойству значение `true`, чтобы отключить неявные элементы `FrameworkReference` или [PackageReference](#packagereference).</span><span class="sxs-lookup"><span data-stu-id="651be-341">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="651be-342">Если этому свойству присвоено значение `true`, можно добавить явные ссылки на только необходимые платформы или пакеты.</span><span class="sxs-lookup"><span data-stu-id="651be-342">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="651be-343">Свойства, связанные с восстановлением</span><span class="sxs-lookup"><span data-stu-id="651be-343">Restore-related properties</span></span>

<span data-ttu-id="651be-344">При восстановлении пакета, на который указывает ссылка, устанавливаются все его прямые зависимости и все зависимости этих зависимостей.</span><span class="sxs-lookup"><span data-stu-id="651be-344">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="651be-345">Можно настроить восстановление пакетов, указав такие свойства, как `RestorePackagesPath` и `RestoreIgnoreFailedSources`.</span><span class="sxs-lookup"><span data-stu-id="651be-345">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="651be-346">Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект восстановления](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="651be-346">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-related-properties"></a><span data-ttu-id="651be-347">Свойства, связанные с запуском</span><span class="sxs-lookup"><span data-stu-id="651be-347">Run-related properties</span></span>

<span data-ttu-id="651be-348">Следующие свойства используются для запуска приложения с помощью команды [`dotnet run`](../tools/dotnet-run.md):</span><span class="sxs-lookup"><span data-stu-id="651be-348">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="651be-349">RunArguments</span><span class="sxs-lookup"><span data-stu-id="651be-349">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="651be-350">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="651be-350">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="651be-351">RunArguments</span><span class="sxs-lookup"><span data-stu-id="651be-351">RunArguments</span></span>

<span data-ttu-id="651be-352">Свойство `RunArguments` определяет аргументы, которые передаются в приложение при его запуске.</span><span class="sxs-lookup"><span data-stu-id="651be-352">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="651be-353">Можно указать дополнительные аргументы для передачи в приложение с помощью параметра [`--` для `dotnet run`](../tools/dotnet-run.md#options).</span><span class="sxs-lookup"><span data-stu-id="651be-353">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="651be-354">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="651be-354">RunWorkingDirectory</span></span>

<span data-ttu-id="651be-355">Свойство `RunWorkingDirectory` определяет рабочий каталог для запуска процесса приложения.</span><span class="sxs-lookup"><span data-stu-id="651be-355">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="651be-356">Это может быть абсолютный путь или путь относительно каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="651be-356">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="651be-357">Если каталог не указан, в качестве рабочего каталога используется `OutDir`.</span><span class="sxs-lookup"><span data-stu-id="651be-357">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-related-properties"></a><span data-ttu-id="651be-358">Свойства, связанные с размещением</span><span class="sxs-lookup"><span data-stu-id="651be-358">Hosting-related properties</span></span>

<span data-ttu-id="651be-359">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="651be-359">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="651be-360">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="651be-360">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="651be-361">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="651be-361">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="651be-362">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="651be-362">EnableComHosting</span></span>

<span data-ttu-id="651be-363">Свойство `EnableComHosting` указывает, что сборка предоставляет сервер COM.</span><span class="sxs-lookup"><span data-stu-id="651be-363">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="651be-364">Установка `EnableComHosting` в `true` также подразумевает, что [EnableDynamicLoading](#enabledynamicloading) — `true`.</span><span class="sxs-lookup"><span data-stu-id="651be-364">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="651be-365">Дополнительные сведения см. в разделе [Предоставление компонентов .NET для COM](../native-interop/expose-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="651be-365">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="651be-366">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="651be-366">EnableDynamicLoading</span></span>

<span data-ttu-id="651be-367">Свойство `EnableDynamicLoading` указывает, что сборка является динамически загружаемым компонентом.</span><span class="sxs-lookup"><span data-stu-id="651be-367">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="651be-368">Компонентом может быть [библиотека COM](/windows/win32/com/the-component-object-model) или библиотека, не относящаяся к COM, которую можно [использовать из собственного узла](../tutorials/netcore-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="651be-368">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="651be-369">Если присвоить этому свойству значения `true`:</span><span class="sxs-lookup"><span data-stu-id="651be-369">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="651be-370">Создается файл *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="651be-370">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="651be-371">[Накат](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) получает значение `LatestMinor`.</span><span class="sxs-lookup"><span data-stu-id="651be-371">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="651be-372">Ссылки NuGet копируются локально.</span><span class="sxs-lookup"><span data-stu-id="651be-372">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="items"></a><span data-ttu-id="651be-373">Элементы</span><span class="sxs-lookup"><span data-stu-id="651be-373">Items</span></span>

<span data-ttu-id="651be-374">[Элементы MSBuild](/visualstudio/msbuild/msbuild-items) — это входные данные для системы сборки.</span><span class="sxs-lookup"><span data-stu-id="651be-374">[MSBuild items](/visualstudio/msbuild/msbuild-items) are inputs into the build system.</span></span> <span data-ttu-id="651be-375">Элементы указываются в соответствии с их типом, который является именем элемента.</span><span class="sxs-lookup"><span data-stu-id="651be-375">Items are specified according to their type, which is the element name.</span></span> <span data-ttu-id="651be-376">Например, `Compile` и `Reference` — [два распространенных типа элементов](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="651be-376">For example, `Compile` and `Reference` are two [common item types](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="651be-377">Пакет SDK для .NET предоставляет следующие дополнительные типы элементов:</span><span class="sxs-lookup"><span data-stu-id="651be-377">The following additional item types are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="651be-378">PackageReference</span><span class="sxs-lookup"><span data-stu-id="651be-378">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="651be-379">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="651be-379">TrimmerRootAssembly</span></span>](#trimmerrootassembly)

<span data-ttu-id="651be-380">Для этих элементов можно использовать любой из стандартных [атрибутов элемента](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), например `Include` и `Update`.</span><span class="sxs-lookup"><span data-stu-id="651be-380">You can use any of the standard [item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), for example, `Include` and `Update`, on these items.</span></span> <span data-ttu-id="651be-381">Чтобы добавить новый элемент, используйте `Include`. Для изменения существующего элемента используйте `Update`.</span><span class="sxs-lookup"><span data-stu-id="651be-381">Use `Include` to add a new item, and use `Update` to modify an existing item.</span></span> <span data-ttu-id="651be-382">Например, `Update` часто используется для изменения элемента, который неявно был добавлен пакетом SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="651be-382">For example, `Update` is often used to modify an item that has implicitly been added by the .NET SDK.</span></span>

### <a name="packagereference"></a><span data-ttu-id="651be-383">PackageReference</span><span class="sxs-lookup"><span data-stu-id="651be-383">PackageReference</span></span>

<span data-ttu-id="651be-384">Элемент `PackageReference` определяет ссылку на пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="651be-384">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="651be-385">Атрибут `Include` указывает идентификатор пакета.</span><span class="sxs-lookup"><span data-stu-id="651be-385">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="651be-386">Атрибут `Version` указывает версию или диапазон версий.</span><span class="sxs-lookup"><span data-stu-id="651be-386">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="651be-387">Сведения о том, как указать минимальную версию, максимальную версию, диапазон или точное соответствие, см. в разделе [Диапазоны версий](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="651be-387">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

<span data-ttu-id="651be-388">Фрагмент файла проекта в следующем примере ссылается на пакет [System.Runtime](https://www.nuget.org/packages/System.Runtime/).</span><span class="sxs-lookup"><span data-stu-id="651be-388">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="651be-389">Также можно [управлять ресурсами зависимостей](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) с помощью таких метаданных, как `PrivateAssets`.</span><span class="sxs-lookup"><span data-stu-id="651be-389">You can also [control dependency assets](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) using metadata such as `PrivateAssets`.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0">
    <PrivateAssets>all</PrivateAssets>
  </PackageReference>
</ItemGroup>
```

<span data-ttu-id="651be-390">Дополнительные сведения см. в статье [Ссылки на пакеты в файлах проекта](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="651be-390">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="trimmerrootassembly"></a><span data-ttu-id="651be-391">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="651be-391">TrimmerRootAssembly</span></span>

<span data-ttu-id="651be-392">Элемент `TrimmerRootAssembly` позволяет исключить сборку из [*обрезки*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="651be-392">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="651be-393">Обрезка — это процесс удаления неиспользуемых частей среды выполнения из упакованного приложения.</span><span class="sxs-lookup"><span data-stu-id="651be-393">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="651be-394">В некоторых случаях при обрезке могут неправильно удаляться необходимые ссылки.</span><span class="sxs-lookup"><span data-stu-id="651be-394">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="651be-395">Следующий код XML исключает сборку `System.Security` из обрезки.</span><span class="sxs-lookup"><span data-stu-id="651be-395">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="item-metadata"></a><span data-ttu-id="651be-396">Метаданные элементов</span><span class="sxs-lookup"><span data-stu-id="651be-396">Item metadata</span></span>

<span data-ttu-id="651be-397">Помимо стандартных [атрибутов элемента MSBuild](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), в пакете SDK для .NET доступны следующие теги метаданных элементов:</span><span class="sxs-lookup"><span data-stu-id="651be-397">In addition to the standard [MSBuild item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), the following item metadata tags are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="651be-398">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="651be-398">CopyToPublishDirectory</span></span>](#copytopublishdirectory)
- [<span data-ttu-id="651be-399">LinkBase</span><span class="sxs-lookup"><span data-stu-id="651be-399">LinkBase</span></span>](#linkbase)

### <a name="copytopublishdirectory"></a><span data-ttu-id="651be-400">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="651be-400">CopyToPublishDirectory</span></span>

<span data-ttu-id="651be-401">Метаданные `CopyToPublishDirectory` в элементах управления MSBuild, когда элемент копируется в каталог публикации.</span><span class="sxs-lookup"><span data-stu-id="651be-401">The `CopyToPublishDirectory` metadata on an MSBuild item controls when the item is copied to the publish directory.</span></span> <span data-ttu-id="651be-402">Допустимые значения: `PreserveNewest`, при котором копируется только элемент, если он был изменен, `Always`, при котором всегда копируется элемент, и `Never`, при котором элемент никогда не копируется.</span><span class="sxs-lookup"><span data-stu-id="651be-402">Allowable values are `PreserveNewest`, which only copies the item if it has changed, `Always`, which always copies the item, and `Never`, which never copies the item.</span></span> <span data-ttu-id="651be-403">С точки зрения производительности `PreserveNewest` предпочтительнее, поскольку включает инкрементную сборку.</span><span class="sxs-lookup"><span data-stu-id="651be-403">From a performance standpoint, `PreserveNewest` is preferable because it enables an incremental build.</span></span>

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a><span data-ttu-id="651be-404">LinkBase</span><span class="sxs-lookup"><span data-stu-id="651be-404">LinkBase</span></span>

<span data-ttu-id="651be-405">Для элемента, находящегося за пределами каталога проекта и его подкаталогов, целевой объект публикации использует [метаданные Link](/visualstudio/msbuild/common-msbuild-item-metadata) элемента, чтобы определить, куда копировать элемент.</span><span class="sxs-lookup"><span data-stu-id="651be-405">For an item that's outside of the project directory and its subdirectories, the publish target uses the item's [Link metadata](/visualstudio/msbuild/common-msbuild-item-metadata) to determine where to copy the item to.</span></span> <span data-ttu-id="651be-406">`Link` также определяет, как элементы за пределами дерева проекта отображаются в окне обозревателя решений Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="651be-406">`Link` also determines how items outside of the project tree are displayed in the Solution Explorer window of Visual Studio.</span></span>

<span data-ttu-id="651be-407">Если для элемента, находящегося за пределами проекта, `Link` не указан, по умолчанию используется `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span><span class="sxs-lookup"><span data-stu-id="651be-407">If `Link` is not specified for an item that's outside of the project cone, it defaults to `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span></span> <span data-ttu-id="651be-408">`LinkBase` позволяет указать допустимую базовую папку для элементов за пределами проекта.</span><span class="sxs-lookup"><span data-stu-id="651be-408">`LinkBase` lets you specify a sensible base folder for items outside of the project cone.</span></span> <span data-ttu-id="651be-409">Иерархия папок в базовой папке обеспечивается с помощью `RecursiveDir`.</span><span class="sxs-lookup"><span data-stu-id="651be-409">The folder hierarchy under the base folder is preserved via `RecursiveDir`.</span></span> <span data-ttu-id="651be-410">Если параметр `LinkBase` не указан, он опускается в пути `Link`.</span><span class="sxs-lookup"><span data-stu-id="651be-410">If `LinkBase` is not specified, it's omitted from the `Link` path.</span></span>

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

<span data-ttu-id="651be-411">На следующем рисунке показано, как файл, который включен с помощью стандартной маски предыдущего элемента `Include`, отображается в обозревателе решений.</span><span class="sxs-lookup"><span data-stu-id="651be-411">The following image shows how a file that's included via the previous item `Include` glob displays in Solution Explorer.</span></span>

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Обозреватель решений: элемент с метаданными LinkBase.":::

## <a name="see-also"></a><span data-ttu-id="651be-413">См. также</span><span class="sxs-lookup"><span data-stu-id="651be-413">See also</span></span>

- [<span data-ttu-id="651be-414">Справочник по схеме MSBuild</span><span class="sxs-lookup"><span data-stu-id="651be-414">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="651be-415">Общие свойства MSBuild</span><span class="sxs-lookup"><span data-stu-id="651be-415">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="651be-416">Свойства MSBuild для целевого объекта pack NuGet</span><span class="sxs-lookup"><span data-stu-id="651be-416">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="651be-417">Свойства MSBuild для целевого объекта restore NuGet</span><span class="sxs-lookup"><span data-stu-id="651be-417">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="651be-418">Настройка сборки</span><span class="sxs-lookup"><span data-stu-id="651be-418">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
