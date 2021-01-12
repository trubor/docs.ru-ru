---
title: Сравнение project.json и CSPROJ
description: См. сопоставление между элементами project.json и CSPROJ.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: 7de9f623a57a6a094debd3e018edc1560d837fc2
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970880"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="f085f-103">Сопоставление между свойствами project.json и CSPROJ</span><span class="sxs-lookup"><span data-stu-id="f085f-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="f085f-104">Автор: [Nate McMaster](https://github.com/natemcmaster) (Нейт Макмастер)</span><span class="sxs-lookup"><span data-stu-id="f085f-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="f085f-105">При разработке инструментария .NET Core были внесены важные структурные изменения, направленные на прекращение поддержки файлов *project.json* и перенос проектов .NET Core на формат MSBuild/CSPROJ.</span><span class="sxs-lookup"><span data-stu-id="f085f-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="f085f-106">Эта статья показывает, как параметры из *project.json* представлены в формате MSBuild/CSPROJ. Это поможет вам научиться использовать новый формат и узнать об изменениях, вносимых средствами миграции при обновлении проекта до последней версии инструментария.</span><span class="sxs-lookup"><span data-stu-id="f085f-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span>

## <a name="the-csproj-format"></a><span data-ttu-id="f085f-107">Формат CSPROJ</span><span class="sxs-lookup"><span data-stu-id="f085f-107">The csproj format</span></span>

<span data-ttu-id="f085f-108">Новый формат \*.csproj основан на XML.</span><span class="sxs-lookup"><span data-stu-id="f085f-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="f085f-109">В следующем примере показан корневой узел проекта .NET Core с использованием `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="f085f-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="f085f-110">Для веб-проектов используется пакет SDK `Microsoft.NET.Sdk.Web`.</span><span class="sxs-lookup"><span data-stu-id="f085f-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="f085f-111">Общие свойства верхнего уровня</span><span class="sxs-lookup"><span data-stu-id="f085f-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="f085f-112">name</span><span class="sxs-lookup"><span data-stu-id="f085f-112">name</span></span>

```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="f085f-113">Больше не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f085f-113">No longer supported.</span></span> <span data-ttu-id="f085f-114">В CSPROJ-файле это свойство определяется именем файла проекта, которое обычно соответствует имени каталога.</span><span class="sxs-lookup"><span data-stu-id="f085f-114">In csproj, this is determined by the project filename, which usually matches the directory name.</span></span> <span data-ttu-id="f085f-115">Например, `MyProjectName.csproj`.</span><span class="sxs-lookup"><span data-stu-id="f085f-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="f085f-116">По умолчанию имя файла проекта также определяет значение свойств `<AssemblyName>` и `<PackageId>`.</span><span class="sxs-lookup"><span data-stu-id="f085f-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span>

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="f085f-117">Значение `<AssemblyName>` будет отличаться от значения `<PackageId>`, если свойство `buildOptions\outputName` было определено в project.json.</span><span class="sxs-lookup"><span data-stu-id="f085f-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span>
<span data-ttu-id="f085f-118">Дополнительные сведения см. в разделе [Другие общие параметры сборки](#other-common-build-options).</span><span class="sxs-lookup"><span data-stu-id="f085f-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="f085f-119">version</span><span class="sxs-lookup"><span data-stu-id="f085f-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```

<span data-ttu-id="f085f-120">Используйте свойства `VersionPrefix` и `VersionSuffix`:</span><span class="sxs-lookup"><span data-stu-id="f085f-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="f085f-121">Можно также использовать свойство `Version`, но это может переопределить параметры версии во время упаковки:</span><span class="sxs-lookup"><span data-stu-id="f085f-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="f085f-122">Другие общие параметры корневого уровня</span><span class="sxs-lookup"><span data-stu-id="f085f-122">Other common root-level options</span></span>

```json
{
  "authors": [ "Anne", "Bob" ],
  "company": "Contoso",
  "language": "en-US",
  "title": "My library",
  "description": "This is my library.\r\nAnd it's really great!",
  "copyright": "Nugetizer 3000",
  "userSecretsId": "xyz123"
}
```

```xml
<PropertyGroup>
  <Authors>Anne;Bob</Authors>
  <Company>Contoso</Company>
  <NeutralLanguage>en-US</NeutralLanguage>
  <AssemblyTitle>My library</AssemblyTitle>
  <Description>This is my library.
And it's really great!</Description>
  <Copyright>Nugetizer 3000</Copyright>
  <UserSecretsId>xyz123</UserSecretsId>
</PropertyGroup>
```

## <a name="frameworks"></a><span data-ttu-id="f085f-123">Инфраструктуры</span><span class="sxs-lookup"><span data-stu-id="f085f-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="f085f-124">Одна целевая платформа</span><span class="sxs-lookup"><span data-stu-id="f085f-124">One target framework</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp1.0</TargetFramework>
</PropertyGroup>
```

### <a name="multiple-target-frameworks"></a><span data-ttu-id="f085f-125">Несколько целевых платформ</span><span class="sxs-lookup"><span data-stu-id="f085f-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="f085f-126">Используйте свойство `TargetFrameworks`, чтобы определить список целевых платформ.</span><span class="sxs-lookup"><span data-stu-id="f085f-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="f085f-127">Для разделения нескольких значений платформы используйте точку с запятой.</span><span class="sxs-lookup"><span data-stu-id="f085f-127">Use semi-colon to separate multiple framework values.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="f085f-128">зависимости</span><span class="sxs-lookup"><span data-stu-id="f085f-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f085f-129">Если зависимостью является **проект**, а не пакет, то формат будет отличаться.</span><span class="sxs-lookup"><span data-stu-id="f085f-129">If the dependency is a **project** and not a package, the format is different.</span></span>
> <span data-ttu-id="f085f-130">Дополнительные сведения см. в разделе [Тип dependency](#dependency-type).</span><span class="sxs-lookup"><span data-stu-id="f085f-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="f085f-131">Метапакет NETStandard.Library</span><span class="sxs-lookup"><span data-stu-id="f085f-131">NETStandard.Library metapackage</span></span>

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  }
}
```

```xml
<PropertyGroup>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="f085f-132">Метапакет Microsoft.NETCore.App</span><span class="sxs-lookup"><span data-stu-id="f085f-132">Microsoft.NETCore.App metapackage</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  }
}
```

```xml
<PropertyGroup>
  <RuntimeFrameworkVersion>1.0.3</RuntimeFrameworkVersion>
</PropertyGroup>
```

<span data-ttu-id="f085f-133">Значение `<RuntimeFrameworkVersion>` в перенесенном проекте определяется версией установленного пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="f085f-133">The `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of SDK that's installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="f085f-134">Высокоуровневые зависимости</span><span class="sxs-lookup"><span data-stu-id="f085f-134">Top-level dependencies</span></span>

```json
{
  "dependencies": {
    "Microsoft.AspNetCore": "1.1.0"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

### <a name="per-framework-dependencies"></a><span data-ttu-id="f085f-135">Зависимости отдельных платформ</span><span class="sxs-lookup"><span data-stu-id="f085f-135">Per-framework dependencies</span></span>

```json
{
  "framework": {
    "net451": {
      "dependencies": {
        "System.Collections.Immutable": "1.3.1"
      }
    },
    "netstandard1.5": {
      "dependencies": {
        "Newtonsoft.Json": "9.0.1"
      }
    }
  }
}
```

```xml
<ItemGroup Condition="'$(TargetFramework)'=='net451'">
  <PackageReference Include="System.Collections.Immutable" Version="1.3.1" />
</ItemGroup>

<ItemGroup Condition="'$(TargetFramework)'=='netstandard1.5'">
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
</ItemGroup>
```

### <a name="imports"></a><span data-ttu-id="f085f-136">импорт</span><span class="sxs-lookup"><span data-stu-id="f085f-136">imports</span></span>

```json
{
  "dependencies": {
    "YamlDotNet": "4.0.1-pre309"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "dotnet"
      ]
    }
  }
}
```

```xml
<PropertyGroup>
  <PackageTargetFallback>dnxcore50;dotnet</PackageTargetFallback>
</PropertyGroup>
<ItemGroup>
  <PackageReference Include="YamlDotNet" Version="4.0.1-pre309" />
</ItemGroup>
```

### <a name="dependency-type"></a><span data-ttu-id="f085f-137">Тип dependency</span><span class="sxs-lookup"><span data-stu-id="f085f-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="f085f-138">type: project</span><span class="sxs-lookup"><span data-stu-id="f085f-138">type: project</span></span>

```json
{
  "dependencies": {
    "MyOtherProject": "1.0.0-*",
    "AnotherProject": {
      "type": "project"
    }
  }
}
```

```xml
<ItemGroup>
  <ProjectReference Include="..\MyOtherProject\MyOtherProject.csproj" />
  <ProjectReference Include="..\AnotherProject\AnotherProject.csproj" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="f085f-139">Нарушает процедуру, по которой `dotnet pack --version-suffix $suffix` определяет версию зависимости для ссылки на проект.</span><span class="sxs-lookup"><span data-stu-id="f085f-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>

#### <a name="type-build"></a><span data-ttu-id="f085f-140">type: build</span><span class="sxs-lookup"><span data-stu-id="f085f-140">type: build</span></span>

```json
{
  "dependencies": {
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.0" PrivateAssets="All" />
</ItemGroup>
```

#### <a name="type-platform"></a><span data-ttu-id="f085f-141">type: platform</span><span class="sxs-lookup"><span data-stu-id="f085f-141">type: platform</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": {
      "version": "1.1.0",
      "type": "platform"
    }
  }
}
```

<span data-ttu-id="f085f-142">Не имеет эквивалента в CSPROJ.</span><span class="sxs-lookup"><span data-stu-id="f085f-142">There is no equivalent in csproj.</span></span>

## <a name="runtimes"></a><span data-ttu-id="f085f-143">runtimes</span><span class="sxs-lookup"><span data-stu-id="f085f-143">runtimes</span></span>

```json
{
  "runtimes": {
    "win7-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
  }
}
```

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win7-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="f085f-144">Автономные приложения (автономное развертывание)</span><span class="sxs-lookup"><span data-stu-id="f085f-144">Standalone apps (self-contained deployment)</span></span>

<span data-ttu-id="f085f-145">В project.json определение раздела `runtimes` означает, что приложение было автономным во время сборки и публикации.</span><span class="sxs-lookup"><span data-stu-id="f085f-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="f085f-146">В MSBuild все проекты являются *портативными* во время сборки, но могут быть опубликованы как автономные.</span><span class="sxs-lookup"><span data-stu-id="f085f-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="f085f-147">Дополнительные сведения см. в статье [Автономные развертывания (SCD)](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="f085f-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#publish-self-contained).</span></span>

## <a name="tools"></a><span data-ttu-id="f085f-148">средства</span><span class="sxs-lookup"><span data-stu-id="f085f-148">tools</span></span>

```json
{
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.0.0-*"
  }
}
```

```xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.0" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="f085f-149">`imports` для tools не поддерживаются в CSPROJ.</span><span class="sxs-lookup"><span data-stu-id="f085f-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="f085f-150">Tools, которым требуются imports, не будут работать с новым `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="f085f-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="f085f-151">buildOptions</span><span class="sxs-lookup"><span data-stu-id="f085f-151">buildOptions</span></span>

<span data-ttu-id="f085f-152">См. также раздел [Файлы](#files).</span><span class="sxs-lookup"><span data-stu-id="f085f-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="f085f-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="f085f-153">emitEntryPoint</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": true
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="f085f-154">Если `emitEntryPoint` имело значение `false`, значение `OutputType` преобразуется в `Library`, которое используется по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="f085f-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": false
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Library</OutputType>
  <!-- or, omit altogether. It defaults to 'Library' -->
</PropertyGroup>
```

### <a name="keyfile"></a><span data-ttu-id="f085f-155">keyFile</span><span class="sxs-lookup"><span data-stu-id="f085f-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="f085f-156">Элемент `keyFile` развертывается в три свойства в MSBuild:</span><span class="sxs-lookup"><span data-stu-id="f085f-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="f085f-157">Другие общие параметры сборки</span><span class="sxs-lookup"><span data-stu-id="f085f-157">Other common build options</span></span>

```json
{
  "buildOptions": {
    "warningsAsErrors": true,
    "nowarn": ["CS0168", "CS0219"],
    "xmlDoc": true,
    "preserveCompilationContext": true,
    "outputName": "Different.AssemblyName",
    "debugType": "portable",
    "allowUnsafe": true,
    "define": ["TEST", "OTHERCONDITION"]
  }
}
```

```xml
<PropertyGroup>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
  <NoWarn>$(NoWarn);CS0168;CS0219</NoWarn>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <PreserveCompilationContext>true</PreserveCompilationContext>
  <AssemblyName>Different.AssemblyName</AssemblyName>
  <DebugType>portable</DebugType>
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  <DefineConstants>$(DefineConstants);TEST;OTHERCONDITION</DefineConstants>
</PropertyGroup>
```

## <a name="packoptions"></a><span data-ttu-id="f085f-158">packOptions</span><span class="sxs-lookup"><span data-stu-id="f085f-158">packOptions</span></span>

<span data-ttu-id="f085f-159">См. также раздел [Файлы](#files).</span><span class="sxs-lookup"><span data-stu-id="f085f-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="f085f-160">Общие параметры пакета</span><span class="sxs-lookup"><span data-stu-id="f085f-160">Common pack options</span></span>

```json
{
  "packOptions": {
    "summary": "numl is a machine learning library intended to ease the use of using standard modeling techniques for both prediction and clustering.",
    "tags": ["machine learning", "framework"],
    "releaseNotes": "Version 0.9.12-beta",
    "iconUrl": "http://numl.net/images/ico.png",
    "projectUrl": "http://numl.net",
    "licenseUrl": "https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md",
    "requireLicenseAcceptance": false,
    "repository": {
      "type": "git",
      "url": "https://raw.githubusercontent.com/sethjuarez/numl"
    },
    "owners": ["Seth Juarez"]
  }
}
```

```xml
<PropertyGroup>
  <!-- summary is not migrated from project.json, but you can use the <Description> property for that if needed. -->
  <PackageTags>machine learning;framework</PackageTags>
  <PackageReleaseNotes>Version 0.9.12-beta</PackageReleaseNotes>
  <PackageIcon>ico.png</PackageIcon>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

<span data-ttu-id="f085f-161">В MSBuild нет эквивалента для элемента `owners`.</span><span class="sxs-lookup"><span data-stu-id="f085f-161">There is no equivalent for the `owners` element in MSBuild.</span></span> <span data-ttu-id="f085f-162">Для `summary` вы можете использовать свойство `<Description>` MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f085f-162">For `summary`, you can use the MSBuild `<Description>` property.</span></span> <span data-ttu-id="f085f-163">Значение `summary` не переносится в это свойство автоматически, так как это оно сопоставляется с элементом [`description`](#other-common-root-level-options).</span><span class="sxs-lookup"><span data-stu-id="f085f-163">The value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#other-common-root-level-options) element.</span></span>  <span data-ttu-id="f085f-164">[Элемент PackageIconUrl объявлен устаревшим](/nuget/reference/msbuild-targets#packageiconurl). Вместо него следует использовать PackageIcon.</span><span class="sxs-lookup"><span data-stu-id="f085f-164">[PackageIconUrl is deprecated](/nuget/reference/msbuild-targets#packageiconurl) in favor of PackageIcon.</span></span>

## <a name="scripts"></a><span data-ttu-id="f085f-165">scripts</span><span class="sxs-lookup"><span data-stu-id="f085f-165">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="f085f-166">Эквивалентом в MSBuild являются [целевые объекты](/visualstudio/msbuild/msbuild-targets):</span><span class="sxs-lookup"><span data-stu-id="f085f-166">Their equivalents in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a><span data-ttu-id="f085f-167">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="f085f-167">runtimeOptions</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "System.GC.Server": true,
      "System.GC.Concurrent": true,
      "System.GC.RetainVM": true,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

<span data-ttu-id="f085f-168">Все параметры в этой группе, кроме свойства `System.GC.Server`, помещаются в файл *runtimeconfig.template.json* в папке проекта, при этом параметры переносятся в корневой объект в ходе миграции:</span><span class="sxs-lookup"><span data-stu-id="f085f-168">All settings in this group, except for the `System.GC.Server` property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": true,
    "System.GC.RetainVM": true,
    "System.Threading.ThreadPool.MinThreads": 4,
    "System.Threading.ThreadPool.MaxThreads": 25
  }
}
```

<span data-ttu-id="f085f-169">Свойство `System.GC.Server` переносится в файл .csproj:</span><span class="sxs-lookup"><span data-stu-id="f085f-169">The `System.GC.Server` property is migrated into the csproj file:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="f085f-170">Но все эти значения можно задать в CSPROJ, а также в свойствах MSBuild:</span><span class="sxs-lookup"><span data-stu-id="f085f-170">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="f085f-171">общие</span><span class="sxs-lookup"><span data-stu-id="f085f-171">shared</span></span>

```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="f085f-172">Не поддерживается в CSPROJ.</span><span class="sxs-lookup"><span data-stu-id="f085f-172">Not supported in csproj.</span></span> <span data-ttu-id="f085f-173">Вместо этого создайте файлы для включения содержимого в ваш файл *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="f085f-173">Instead, create include content files in your *.nuspec* file.</span></span>
<span data-ttu-id="f085f-174">Дополнительные сведения см. в разделе [Включение файлов содержимого](/nuget/schema/nuspec#including-content-files).</span><span class="sxs-lookup"><span data-stu-id="f085f-174">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="f085f-175">файлы</span><span class="sxs-lookup"><span data-stu-id="f085f-175">files</span></span>

<span data-ttu-id="f085f-176">В *project.json* сборку и упаковку можно расширить для компиляции и внедрения из разных папок.</span><span class="sxs-lookup"><span data-stu-id="f085f-176">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="f085f-177">В MSBuild это делается с помощью [элементов](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="f085f-177">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="f085f-178">Следующий пример описывает типичное преобразование:</span><span class="sxs-lookup"><span data-stu-id="f085f-178">The following example is a common conversion:</span></span>

```json
{
  "buildOptions": {
    "compile": {
      "copyToOutput": "notes.txt",
      "include": "../Shared/*.cs",
      "exclude": "../Shared/Not/*.cs"
    },
    "embed": {
      "include": "../Shared/*.resx"
    }
  },
  "packOptions": {
    "include": "Views/",
    "mappings": {
      "some/path/in/project.txt": "in/package.txt"
    }
  },
  "publishOptions": {
    "include": [
      "files/",
      "publishnotes.txt"
    ]
  }
}
```

```xml
<ItemGroup>
  <Compile Include="..\Shared\*.cs" Exclude="..\Shared\Not\*.cs" />
  <EmbeddedResource Include="..\Shared\*.resx" />
  <Content Include="Views\**\*" PackagePath="%(Identity)" />
  <None Include="some/path/in/project.txt" Pack="true" PackagePath="in/package.txt" />
  
  <None Include="notes.txt" CopyToOutputDirectory="Always" />
  <!-- CopyToOutputDirectory = { Always, PreserveNewest, Never } -->

  <Content Include="files\**\*" CopyToPublishDirectory="PreserveNewest" />
  <None Include="publishnotes.txt" CopyToPublishDirectory="Always" />
  <!-- CopyToPublishDirectory = { Always, PreserveNewest, Never } -->
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="f085f-179">Многие из [стандартных масок](https://en.wikipedia.org/wiki/Glob_(programming)) по умолчанию добавляются автоматически с помощью пакета SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f085f-179">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span> <span data-ttu-id="f085f-180">См. сведения о том, [что включает компиляция по умолчанию](../project-sdk/overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="f085f-180">For more information, see [Default compilation includes](../project-sdk/overview.md#default-includes-and-excludes).</span></span>

<span data-ttu-id="f085f-181">Все элементы `ItemGroup` MSBuild поддерживают `Include`, `Exclude` и `Remove`.</span><span class="sxs-lookup"><span data-stu-id="f085f-181">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="f085f-182">Макет пакета внутри NUPKG можно изменить с помощью `PackagePath="path"`.</span><span class="sxs-lookup"><span data-stu-id="f085f-182">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="f085f-183">Кроме `Content`, для большинства групп элементов требуется явное добавление `Pack="true"` для включения в пакет.</span><span class="sxs-lookup"><span data-stu-id="f085f-183">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="f085f-184">`Content` помещается в папку *content* пакета, так как для свойства `<IncludeContentInPack>` MSBuild по умолчанию задано значение `true`.</span><span class="sxs-lookup"><span data-stu-id="f085f-184">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span>
<span data-ttu-id="f085f-185">Дополнительные сведения см. в статье [Включение содержимого в пакет](/nuget/schema/msbuild-targets#including-content-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="f085f-185">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="f085f-186">`PackagePath="%(Identity)"` позволяет быстро настроить относительный путь к файлу проекта в качестве пути к пакету.</span><span class="sxs-lookup"><span data-stu-id="f085f-186">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="f085f-187">testRunner</span><span class="sxs-lookup"><span data-stu-id="f085f-187">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="f085f-188">xUnit</span><span class="sxs-lookup"><span data-stu-id="f085f-188">xUnit</span></span>

```json
{
  "testRunner": "xunit",
  "dependencies": {
    "dotnet-test-xunit": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="xunit" Version="2.2.0-*" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-*" />
</ItemGroup>
```

### <a name="mstest"></a><span data-ttu-id="f085f-189">MSTest</span><span class="sxs-lookup"><span data-stu-id="f085f-189">MSTest</span></span>

```json
{
  "testRunner": "mstest",
  "dependencies": {
    "dotnet-test-mstest": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.12-*" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11-*" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="f085f-190">См. также</span><span class="sxs-lookup"><span data-stu-id="f085f-190">See also</span></span>

- [<span data-ttu-id="f085f-191">Краткий обзор изменений в интерфейсе командной строки</span><span class="sxs-lookup"><span data-stu-id="f085f-191">High-level overview of changes in CLI</span></span>](cli-msbuild-architecture.md)
