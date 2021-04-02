---
title: Свойства MSBuild для Microsoft.NET.Sdk
description: Справочник по свойствам и элементам MSBuild, распознаваемым пакетом SDK для .NET.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: effcb704056f553b2986ee4a61f73c0dc58af599
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636770"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="aaddf-103">Справочник по MSBuild для проектов пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="aaddf-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="aaddf-104">Эта страница содержит справочные сведения о свойствах и элементах MSBuild, которые вы можете использовать для настройки проектов .NET.</span><span class="sxs-lookup"><span data-stu-id="aaddf-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="aaddf-105">Работа над этой страницей еще не завершена, поэтому здесь приведены лишь некоторые полезные свойства MSBuild для пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="aaddf-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="aaddf-106">Список стандартных свойств см. в статье [Общие свойства MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="aaddf-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="aaddf-107">Свойства платформы</span><span class="sxs-lookup"><span data-stu-id="aaddf-107">Framework properties</span></span>

<span data-ttu-id="aaddf-108">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="aaddf-108">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="aaddf-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="aaddf-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="aaddf-110">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="aaddf-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="aaddf-111">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="aaddf-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="aaddf-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="aaddf-112">TargetFramework</span></span>

<span data-ttu-id="aaddf-113">Свойство `TargetFramework` определяет версию целевой платформы для приложения.</span><span class="sxs-lookup"><span data-stu-id="aaddf-113">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="aaddf-114">Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="aaddf-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="aaddf-115">Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="aaddf-116">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="aaddf-116">TargetFrameworks</span></span>

<span data-ttu-id="aaddf-117">Используйте свойство `TargetFrameworks`, если приложение должно быть предназначено для нескольких платформ.</span><span class="sxs-lookup"><span data-stu-id="aaddf-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="aaddf-118">Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="aaddf-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="aaddf-119">Это свойство игнорируется, если указано свойство `TargetFramework` (в единственном числе).</span><span class="sxs-lookup"><span data-stu-id="aaddf-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="aaddf-120">Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="aaddf-121">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="aaddf-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="aaddf-122">Это свойство применяется только к проектам, использующим `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="aaddf-123">Он не применяется к проектам, использующим `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="aaddf-124">Используйте свойство `NetStandardImplicitPackageVersion`, если вам нужно указать версию платформы ниже версии метапакета.</span><span class="sxs-lookup"><span data-stu-id="aaddf-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="aaddf-125">Файл проекта, приведенный в следующем примере, предназначен для `netstandard1.3`, но использует `NETStandard.Library` версии 1.6.0.</span><span class="sxs-lookup"><span data-stu-id="aaddf-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="assembly-info-generation-properties"></a><span data-ttu-id="aaddf-126">Свойства создания сведений о сборке</span><span class="sxs-lookup"><span data-stu-id="aaddf-126">Assembly info generation properties</span></span>

- [<span data-ttu-id="aaddf-127">GenerateAssemblyCompanyAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-127">GenerateAssemblyCompanyAttribute</span></span>](#generateassemblycompanyattribute)
- [<span data-ttu-id="aaddf-128">GenerateAssemblyConfigurationAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-128">GenerateAssemblyConfigurationAttribute</span></span>](#generateassemblyconfigurationattribute)
- [<span data-ttu-id="aaddf-129">GenerateAssemblyCopyrightAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-129">GenerateAssemblyCopyrightAttribute</span></span>](#generateassemblycopyrightattribute)
- [<span data-ttu-id="aaddf-130">GenerateAssemblyDescriptionAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-130">GenerateAssemblyDescriptionAttribute</span></span>](#generateassemblydescriptionattribute)
- [<span data-ttu-id="aaddf-131">GenerateAssemblyFileVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-131">GenerateAssemblyFileVersionAttribute</span></span>](#generateassemblyfileversionattribute)
- [<span data-ttu-id="aaddf-132">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="aaddf-132">GenerateAssemblyInfo</span></span>](#generateassemblyinfo)
- [<span data-ttu-id="aaddf-133">GenerateAssemblyInformationalVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-133">GenerateAssemblyInformationalVersionAttribute</span></span>](#generateassemblyinformationalversionattribute)
- [<span data-ttu-id="aaddf-134">GenerateAssemblyProductAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-134">GenerateAssemblyProductAttribute</span></span>](#generateassemblyproductattribute)
- [<span data-ttu-id="aaddf-135">GenerateAssemblyTitleAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-135">GenerateAssemblyTitleAttribute</span></span>](#generateassemblytitleattribute)
- [<span data-ttu-id="aaddf-136">GenerateAssemblyVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-136">GenerateAssemblyVersionAttribute</span></span>](#generateassemblyversionattribute)
- [<span data-ttu-id="aaddf-137">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="aaddf-137">GeneratedAssemblyInfoFile</span></span>](#generatedassemblyinfofile)
- [<span data-ttu-id="aaddf-138">GenerateNeutralResourcesLanguageAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-138">GenerateNeutralResourcesLanguageAttribute</span></span>](#generateneutralresourceslanguageattribute)

### <a name="generateassemblycompanyattribute"></a><span data-ttu-id="aaddf-139">GenerateAssemblyCompanyAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-139">GenerateAssemblyCompanyAttribute</span></span>

<span data-ttu-id="aaddf-140">Это свойство определяет, создает ли свойство `Company` атрибут <xref:System.Reflection.AssemblyCompanyAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-140">This property controls whether or not the `Company` property generates the <xref:System.Reflection.AssemblyCompanyAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-141">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-141">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyCompanyAttribute>false</GenerateAssemblyCompanyAttribute>
</PropertyGroup>
```

### <a name="generateassemblyconfigurationattribute"></a><span data-ttu-id="aaddf-142">GenerateAssemblyConfigurationAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-142">GenerateAssemblyConfigurationAttribute</span></span>

<span data-ttu-id="aaddf-143">Это свойство определяет, создает ли свойство `Configuration` атрибут <xref:System.Reflection.AssemblyConfigurationAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-143">This property controls whether or not the `Configuration` property generates the <xref:System.Reflection.AssemblyConfigurationAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-144">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-144">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyConfigurationAttribute>false</GenerateAssemblyConfigurationAttribute>
</PropertyGroup>
```

### <a name="generateassemblycopyrightattribute"></a><span data-ttu-id="aaddf-145">GenerateAssemblyCopyrightAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-145">GenerateAssemblyCopyrightAttribute</span></span>

<span data-ttu-id="aaddf-146">Это свойство определяет, создает ли свойство `Copyright` атрибут <xref:System.Reflection.AssemblyCopyrightAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-146">This property controls whether or not the `Copyright` property generates the <xref:System.Reflection.AssemblyCopyrightAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-147">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-147">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyCopyrightAttribute>false</GenerateAssemblyCopyrightAttribute>
</PropertyGroup>
```

### <a name="generateassemblydescriptionattribute"></a><span data-ttu-id="aaddf-148">GenerateAssemblyDescriptionAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-148">GenerateAssemblyDescriptionAttribute</span></span>

<span data-ttu-id="aaddf-149">Это свойство определяет, создает ли свойство `Description` атрибут <xref:System.Reflection.AssemblyDescriptionAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-149">This property controls whether or not the `Description` property generates the <xref:System.Reflection.AssemblyDescriptionAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-150">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-150">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyDescriptionAttribute>false</GenerateAssemblyDescriptionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyfileversionattribute"></a><span data-ttu-id="aaddf-151">GenerateAssemblyFileVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-151">GenerateAssemblyFileVersionAttribute</span></span>

<span data-ttu-id="aaddf-152">Это свойство определяет, создает ли свойство `FileVersion` атрибут <xref:System.Reflection.AssemblyFileVersionAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-152">This property controls whether or not the `FileVersion` property generates the <xref:System.Reflection.AssemblyFileVersionAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-153">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-153">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyFileVersionAttribute>false</GenerateAssemblyFileVersionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyinfo"></a><span data-ttu-id="aaddf-154">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="aaddf-154">GenerateAssemblyInfo</span></span>

<span data-ttu-id="aaddf-155">Управляет созданием атрибута `AssemblyInfo` для проекта.</span><span class="sxs-lookup"><span data-stu-id="aaddf-155">Controls `AssemblyInfo` attribute generation for the project.</span></span> <span data-ttu-id="aaddf-156">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-156">The default value is `true`.</span></span> <span data-ttu-id="aaddf-157">Используйте `false`, чтобы отключить создание файла:</span><span class="sxs-lookup"><span data-stu-id="aaddf-157">Use `false` to disable generation of the file:</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
</PropertyGroup>
```

<span data-ttu-id="aaddf-158">Параметр [GeneratedAssemblyInfoFile](#generatedassemblyinfofile) определяет имя создаваемого файла.</span><span class="sxs-lookup"><span data-stu-id="aaddf-158">The [GeneratedAssemblyInfoFile](#generatedassemblyinfofile) setting controls the name of the generated file.</span></span>

<span data-ttu-id="aaddf-159">Если значение `GenerateAssemblyInfo` равно `true`, свойства проекта преобразуются в атрибуты `AssemblyInfo`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-159">When the `GenerateAssemblyInfo` value is `true`, project properties are transformed into `AssemblyInfo` attributes.</span></span> <span data-ttu-id="aaddf-160">В следующей таблице перечислены свойства проекта, которые создают атрибуты, а также свойства, которые могут отключить возможность создания:</span><span class="sxs-lookup"><span data-stu-id="aaddf-160">The following table lists the project properties that generate the attributes, and the properties that can disable that generation:</span></span>

| <span data-ttu-id="aaddf-161">Свойство</span><span class="sxs-lookup"><span data-stu-id="aaddf-161">Property</span></span>               | <span data-ttu-id="aaddf-162">attribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-162">Attribute</span></span>                                                      | <span data-ttu-id="aaddf-163">Свойство, используемое для отключения</span><span class="sxs-lookup"><span data-stu-id="aaddf-163">Property to disable</span></span>                                                                               |
|------------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| `Company`              | <xref:System.Reflection.AssemblyCompanyAttribute>              | [`GenerateAssemblyCompanyAttribute`](#generateassemblycompanyattribute)                           |
| `Configuration`        | <xref:System.Reflection.AssemblyConfigurationAttribute>        | [`GenerateAssemblyConfigurationAttribute`](#generateassemblyconfigurationattribute)               |
| `Copyright`            | <xref:System.Reflection.AssemblyCopyrightAttribute>            | [`GenerateAssemblyCopyrightAttribute`](#generateassemblycopyrightattribute)                       |
| `Description`          | <xref:System.Reflection.AssemblyDescriptionAttribute>          | [`GenerateAssemblyDescriptionAttribute`](#generateassemblydescriptionattribute)                   |
| `FileVersion`          | <xref:System.Reflection.AssemblyFileVersionAttribute>          | [`GenerateAssemblyFileVersionAttribute`](#generateassemblyfileversionattribute)                   |
| `InformationalVersion` | <xref:System.Reflection.AssemblyInformationalVersionAttribute> | [`GenerateAssemblyInformationalVersionAttribute`](#generateassemblyinformationalversionattribute) |
| `Product`              | <xref:System.Reflection.AssemblyProductAttribute>              | [`GenerateAssemblyProductAttribute`](#generateassemblyproductattribute)                           |
| `AssemblyTitle`        | <xref:System.Reflection.AssemblyTitleAttribute>                | [`GenerateAssemblyTitleAttribute`](#generateassemblytitleattribute)                               |
| `AssemblyVersion`      | <xref:System.Reflection.AssemblyVersionAttribute>              | [`GenerateAssemblyVersionAttribute`](#generateassemblyversionattribute)                           |
| `NeutralLanguage`      | <xref:System.Resources.NeutralResourcesLanguageAttribute>      | [`GenerateNeutralResourcesLanguageAttribute`](#generateneutralresourceslanguageattribute)         |

<span data-ttu-id="aaddf-164">Примечания об этих параметрах:</span><span class="sxs-lookup"><span data-stu-id="aaddf-164">Notes about these settings:</span></span>

- <span data-ttu-id="aaddf-165">`AssemblyVersion` и `FileVersion` по умолчанию имеют значение `$(Version)` без суффикса.</span><span class="sxs-lookup"><span data-stu-id="aaddf-165">`AssemblyVersion` and `FileVersion` default to the value of `$(Version)` without the suffix.</span></span> <span data-ttu-id="aaddf-166">Например, если для `$(Version)` нужно указать `1.2.3-beta.4`, то значением будет `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-166">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="aaddf-167">По умолчанию для `InformationalVersion` используется значение `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-167">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="aaddf-168">Если имеется свойство `$(SourceRevisionId)`, оно добавляется к `InformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-168">If the `$(SourceRevisionId)` property is present, it's appended to `InformationalVersion`.</span></span> <span data-ttu-id="aaddf-169">Такое поведение можно отключить с помощью `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-169">You can disable this behavior using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="aaddf-170">Свойства `Copyright` и `Description` также используются для метаданных NuGet.</span><span class="sxs-lookup"><span data-stu-id="aaddf-170">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="aaddf-171">Свойство `Configuration`, которое по умолчанию имеет значение `Debug`, является общим для всех целевых объектов MSBuild.</span><span class="sxs-lookup"><span data-stu-id="aaddf-171">`Configuration`, which defaults to `Debug`, is shared with all MSBuild targets.</span></span> <span data-ttu-id="aaddf-172">Его можно задать с помощью параметра `--configuration` команды `dotnet` (например, [dotnet pack](../tools/dotnet-pack.md)).</span><span class="sxs-lookup"><span data-stu-id="aaddf-172">You can set it via the `--configuration` option of `dotnet` commands, for example, [dotnet pack](../tools/dotnet-pack.md).</span></span>
- <span data-ttu-id="aaddf-173">Некоторые свойства используются при создании пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="aaddf-173">Some of the properties are used when creating a NuGet package.</span></span> <span data-ttu-id="aaddf-174">Дополнительные сведения см. в разделе [Свойства пакетов](#package-properties).</span><span class="sxs-lookup"><span data-stu-id="aaddf-174">For more information, see [Package properties](#package-properties).</span></span>

#### <a name="migrating-from-net-framework"></a><span data-ttu-id="aaddf-175">Миграция из .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aaddf-175">Migrating from .NET Framework</span></span>

<span data-ttu-id="aaddf-176">Шаблоны проектов .NET Framework создают файл кода со следующими заданными атрибутами сведений о сборке.</span><span class="sxs-lookup"><span data-stu-id="aaddf-176">.NET Framework project templates create a code file with these assembly info attributes set.</span></span> <span data-ttu-id="aaddf-177">Обычно файл расположен здесь: *.\Properties\AssemblyInfo.cs* или *.\Properties\AssemblyInfo.vb*.</span><span class="sxs-lookup"><span data-stu-id="aaddf-177">The file is typically located at *.\Properties\AssemblyInfo.cs* or *.\Properties\AssemblyInfo.vb*.</span></span> <span data-ttu-id="aaddf-178">Проекты в стиле пакета SDK создают этот файл на основе параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="aaddf-178">SDK-style projects generate this file for you based on the project settings.</span></span> <span data-ttu-id="aaddf-179">**Оба варианта не поддерживаются.**</span><span class="sxs-lookup"><span data-stu-id="aaddf-179">**You can't have both.**</span></span> <span data-ttu-id="aaddf-180">При переносе кода в .NET 5 (и .NET Core 3.1) или более поздней версии выполните одно из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="aaddf-180">When porting your code to .NET 5 (and .NET Core 3.1) or later, do one of the following:</span></span>

- <span data-ttu-id="aaddf-181">Отключите возможность создания временного файла кода, который содержит атрибуты сведений о сборке, задав для `GenerateAssemblyInfo` значение `false`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-181">Disable the generation of the temporary code file that contains the assembly info attributes by setting `GenerateAssemblyInfo` to `false`.</span></span> <span data-ttu-id="aaddf-182">Так вы сохраните свой файл *AssemblyInfo*.</span><span class="sxs-lookup"><span data-stu-id="aaddf-182">This enables you to keep your *AssemblyInfo* file.</span></span>
- <span data-ttu-id="aaddf-183">Перенесите параметры из файла `AssemblyInfo` в файл проекта и удалите файл `AssemblyInfo`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-183">Migrate the settings in the `AssemblyInfo` file to the project file, and delete the `AssemblyInfo` file.</span></span>

### <a name="generateassemblyinformationalversionattribute"></a><span data-ttu-id="aaddf-184">GenerateAssemblyInformationalVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-184">GenerateAssemblyInformationalVersionAttribute</span></span>

<span data-ttu-id="aaddf-185">Это свойство определяет, создает ли свойство `InformationalVersion` атрибут <xref:System.Reflection.AssemblyInformationalVersionAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-185">This property controls whether or not the `InformationalVersion` property generates the <xref:System.Reflection.AssemblyInformationalVersionAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-186">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-186">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyInformationalVersionAttribute>false</GenerateAssemblyInformationalVersionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyproductattribute"></a><span data-ttu-id="aaddf-187">GenerateAssemblyProductAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-187">GenerateAssemblyProductAttribute</span></span>

<span data-ttu-id="aaddf-188">Это свойство определяет, создает ли свойство `Product` атрибут <xref:System.Reflection.AssemblyProductAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-188">This property controls whether or not the `Product` property generates the <xref:System.Reflection.AssemblyProductAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-189">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-189">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyProductAttribute>false</GenerateAssemblyProductAttribute>
</PropertyGroup>
```

### <a name="generateassemblytitleattribute"></a><span data-ttu-id="aaddf-190">GenerateAssemblyTitleAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-190">GenerateAssemblyTitleAttribute</span></span>

<span data-ttu-id="aaddf-191">Это свойство определяет, создает ли свойство `AssemblyTitle` атрибут <xref:System.Reflection.AssemblyTitleAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-191">This property controls whether or not the `AssemblyTitle` property generates the <xref:System.Reflection.AssemblyTitleAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-192">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-192">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyTitleAttribute>false</GenerateAssemblyTitleAttribute>
</PropertyGroup>
```

### <a name="generateassemblyversionattribute"></a><span data-ttu-id="aaddf-193">GenerateAssemblyVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-193">GenerateAssemblyVersionAttribute</span></span>

<span data-ttu-id="aaddf-194">Это свойство определяет, создает ли свойство `AssemblyVersion` атрибут <xref:System.Reflection.AssemblyVersionAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-194">This property controls whether or not the `AssemblyVersion` property generates the <xref:System.Reflection.AssemblyVersionAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-195">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-195">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyVersionAttribute>false</GenerateAssemblyVersionAttribute>
</PropertyGroup>
```

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="aaddf-196">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="aaddf-196">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="aaddf-197">Это свойство определяет относительный или абсолютный путь к файлу сведений о созданной сборке.</span><span class="sxs-lookup"><span data-stu-id="aaddf-197">The property defines the relative or absolute path of the generated assembly info file.</span></span> <span data-ttu-id="aaddf-198">По умолчанию используется файл с именем *[имя_проекта].AssemblyInfo.[cs|vb]* в каталоге `$(IntermediateOutputPath)` (обычно это *obj*).</span><span class="sxs-lookup"><span data-stu-id="aaddf-198">Defaults to a file named *[project-name].AssemblyInfo.[cs|vb]* in the `$(IntermediateOutputPath)` (usually the *obj*) directory.</span></span>

```xml
<PropertyGroup>
  <GeneratedAssemblyInfoFile>assemblyinfo.cs</GeneratedAssemblyInfoFile>
</PropertyGroup>
```

### <a name="generateneutralresourceslanguageattribute"></a><span data-ttu-id="aaddf-199">GenerateNeutralResourcesLanguageAttribute</span><span class="sxs-lookup"><span data-stu-id="aaddf-199">GenerateNeutralResourcesLanguageAttribute</span></span>

<span data-ttu-id="aaddf-200">Это свойство определяет, создает ли свойство `NeutralLanguage` атрибут <xref:System.Resources.NeutralResourcesLanguageAttribute> для сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-200">This property controls whether or not the `NeutralLanguage` property generates the <xref:System.Resources.NeutralResourcesLanguageAttribute> for the assembly.</span></span> <span data-ttu-id="aaddf-201">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-201">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateNeutralResourcesLanguageAttribute>false</GenerateNeutralResourcesLanguageAttribute>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="aaddf-202">Свойства пакета</span><span class="sxs-lookup"><span data-stu-id="aaddf-202">Package properties</span></span>

<span data-ttu-id="aaddf-203">Для описания пакета, созданного из проекта, можно указать такие свойства, как `PackageId`, `PackageVersion`, `PackageIcon`, `Title` и `Description`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-203">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="aaddf-204">Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект пакета](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="aaddf-204">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-related-properties"></a><span data-ttu-id="aaddf-205">Свойства, связанные с публикацией</span><span class="sxs-lookup"><span data-stu-id="aaddf-205">Publish-related properties</span></span>

<span data-ttu-id="aaddf-206">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="aaddf-206">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="aaddf-207">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="aaddf-207">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="aaddf-208">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="aaddf-208">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="aaddf-209">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="aaddf-209">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="aaddf-210">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="aaddf-210">PreserveCompilationContext</span></span>](#preservecompilationcontext)
- [<span data-ttu-id="aaddf-211">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="aaddf-211">PreserveCompilationReferences</span></span>](#preservecompilationreferences)
- [<span data-ttu-id="aaddf-212">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="aaddf-212">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="aaddf-213">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="aaddf-213">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="aaddf-214">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="aaddf-214">UseAppHost</span></span>](#useapphost)

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="aaddf-215">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="aaddf-215">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="aaddf-216">Свойство `AppendTargetFrameworkToOutputPath` определяет, добавляется ли [моникер целевой платформы (TFM)](../../standard/frameworks.md) к выходному пути (который определяется свойством [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span><span class="sxs-lookup"><span data-stu-id="aaddf-216">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="aaddf-217">Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть).</span><span class="sxs-lookup"><span data-stu-id="aaddf-217">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="aaddf-218">При установке значения `false` для свойства `AppendTargetFrameworkToOutputPath` TFM не добавляется к выходному пути.</span><span class="sxs-lookup"><span data-stu-id="aaddf-218">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="aaddf-219">Однако при отсутствии TFM в выходном пути несколько артефактов сборки могут перезаписывать друг друга.</span><span class="sxs-lookup"><span data-stu-id="aaddf-219">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="aaddf-220">Например, при установке следующего параметра выходной путь для приложения .NET 5.0 изменяется с `bin\Debug\net5.0` на `bin\Debug`:</span><span class="sxs-lookup"><span data-stu-id="aaddf-220">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="aaddf-221">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="aaddf-221">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="aaddf-222">Свойство `AppendRuntimeIdentifierToOutputPath` определяет, добавляется ли к выходному пути [идентификатор среды выполнения (RID)](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-222">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="aaddf-223">Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть).</span><span class="sxs-lookup"><span data-stu-id="aaddf-223">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="aaddf-224">При установке значения `false` для свойства `AppendRuntimeIdentifierToOutputPath` RID не добавляется к выходному пути.</span><span class="sxs-lookup"><span data-stu-id="aaddf-224">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="aaddf-225">Например, при установке следующего параметра выходной путь для приложения .NET 5.0 и идентификатора RID `win10-x64` изменяется с `bin\Debug\net5.0\win10-x64` на `bin\Debug\net5.0`:</span><span class="sxs-lookup"><span data-stu-id="aaddf-225">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="aaddf-226">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="aaddf-226">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="aaddf-227">Свойство `CopyLocalLockFileAssemblies` полезно для проектов подключаемых модулей, которые имеют зависимости от других библиотек.</span><span class="sxs-lookup"><span data-stu-id="aaddf-227">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="aaddf-228">Если для этого свойства задано значение `true`, все зависимости пакета NuGet копируются в выходной каталог.</span><span class="sxs-lookup"><span data-stu-id="aaddf-228">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="aaddf-229">Это означает, что вы можете использовать выходные данные `dotnet build` для запуска подключаемого модуля на любом компьютере.</span><span class="sxs-lookup"><span data-stu-id="aaddf-229">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="aaddf-230">Кроме того, можно использовать `dotnet publish` для публикации библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="aaddf-230">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="aaddf-231">Дополнительные сведения см. в разделе [dotnet publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-231">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="preservecompilationcontext"></a><span data-ttu-id="aaddf-232">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="aaddf-232">PreserveCompilationContext</span></span>

<span data-ttu-id="aaddf-233">Свойство `PreserveCompilationContext` позволяет собранному или опубликованному приложению компилировать дополнительный код во время выполнения с теми же параметрами, которые использовались во время сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-233">The `PreserveCompilationContext` property allows a built or published application to compile more code at run time using the same settings that were used at build time.</span></span> <span data-ttu-id="aaddf-234">Сборки, ссылки на которые были указаны во время сборки, будут скопированы в подкаталог *ref* выходного каталога.</span><span class="sxs-lookup"><span data-stu-id="aaddf-234">The assemblies referenced at build time will be copied into the *ref* subdirectory of the output directory.</span></span> <span data-ttu-id="aaddf-235">Имена базовых сборок хранятся в файле *.deps.json* приложения вместе с параметрами, передаваемыми компилятору.</span><span class="sxs-lookup"><span data-stu-id="aaddf-235">The names of the reference assemblies are stored in the application's *.deps.json* file along with the options passed to the compiler.</span></span> <span data-ttu-id="aaddf-236">Эту информацию можно получить с помощью свойств <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> и <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aaddf-236">You can retrieve this information using the <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> and <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> properties.</span></span>

<span data-ttu-id="aaddf-237">Эта функциональность в основном используется внутри системы для поддержки компиляции файлов Razor во время выполнения на страницах MVC и Razor ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="aaddf-237">This functionality is mostly used internally by ASP.NET Core MVC and Razor pages to support run-time compilation of Razor files.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a><span data-ttu-id="aaddf-238">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="aaddf-238">PreserveCompilationReferences</span></span>

<span data-ttu-id="aaddf-239">Свойство `PreserveCompilationReferences` аналогично свойству [PreserveCompilationContext](#preservecompilationcontext) за исключением того, что при его использовании в каталог публикации копируются только указанные ссылками сборки, но не копируется файл *.deps.json*.</span><span class="sxs-lookup"><span data-stu-id="aaddf-239">The `PreserveCompilationReferences` property is similar to the [PreserveCompilationContext](#preservecompilationcontext) property, except that it only copies the referenced assemblies to the publish directory, and not the *.deps.json* file.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

<span data-ttu-id="aaddf-240">Дополнительные сведения см. в разделе [Свойства пакета SDK Razor](/aspnet/core/razor-pages/sdk#properties).</span><span class="sxs-lookup"><span data-stu-id="aaddf-240">For more information, see [Razor SDK properties](/aspnet/core/razor-pages/sdk#properties).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="aaddf-241">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="aaddf-241">RuntimeIdentifier</span></span>

<span data-ttu-id="aaddf-242">Свойство `RuntimeIdentifier` позволяет указать для проекта один [идентификатор среды выполнения (RID)](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-242">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="aaddf-243">Идентификатор среды выполнения позволяет опубликовать автономное развертывание.</span><span class="sxs-lookup"><span data-stu-id="aaddf-243">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="aaddf-244">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="aaddf-244">RuntimeIdentifiers</span></span>

<span data-ttu-id="aaddf-245">Свойство `RuntimeIdentifiers` позволяет указать для проекта список [идентификаторов среды выполнения (RID)](../rid-catalog.md) (в качестве разделителя используется точка с запятой).</span><span class="sxs-lookup"><span data-stu-id="aaddf-245">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="aaddf-246">Используйте это свойство, если вам нужна публикация для нескольких сред.</span><span class="sxs-lookup"><span data-stu-id="aaddf-246">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="aaddf-247">`RuntimeIdentifiers` используется во время восстановления для обеспечения наличия в графе нужных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aaddf-247">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="aaddf-248">`RuntimeIdentifier` (в единственном числе) может ускорить создание сборок, когда требуется только одна среда выполнения.</span><span class="sxs-lookup"><span data-stu-id="aaddf-248">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="useapphost"></a><span data-ttu-id="aaddf-249">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="aaddf-249">UseAppHost</span></span>

<span data-ttu-id="aaddf-250">Свойство `UseAppHost` контролирует создание собственного исполняемого файла для развертывания.</span><span class="sxs-lookup"><span data-stu-id="aaddf-250">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="aaddf-251">Этот файл требуется для автономных развертываний.</span><span class="sxs-lookup"><span data-stu-id="aaddf-251">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="aaddf-252">В .NET Core 3.0 и более поздних версиях зависимый от платформы исполняемый файл создается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aaddf-252">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="aaddf-253">Задайте свойству `UseAppHost` значение `false`, чтобы отключить создание исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="aaddf-253">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="aaddf-254">Дополнительные сведения см. в статье о [развертывании приложений .NET](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-254">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compilation-related-properties"></a><span data-ttu-id="aaddf-255">Свойства, связанные с компиляцией</span><span class="sxs-lookup"><span data-stu-id="aaddf-255">Compilation-related properties</span></span>

<span data-ttu-id="aaddf-256">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="aaddf-256">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="aaddf-257">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="aaddf-257">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="aaddf-258">LangVersion</span><span class="sxs-lookup"><span data-stu-id="aaddf-258">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="aaddf-259">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="aaddf-259">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="aaddf-260">Свойство `EmbeddedResourceUseDependentUponConvention` определяет, будет ли использоваться информация о типах в исходных файлах, расположенных в одной папке с файлами ресурсов, для создания имен файлов манифеста этих ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aaddf-260">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="aaddf-261">Например, если *Form1.resx* находится в той же папке, что и *Form1.cs*, а `EmbeddedResourceUseDependentUponConvention` имеет значение `true`, то созданному файл *.resources* присваивается имя на основе имени первого типа, определенного в файле *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="aaddf-261">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="aaddf-262">Например, если первым типом в файле *Form1.cs* является `MyNamespace.Form1`, созданному файлу присваивается имя *MyNamespace.Form1.resources*.</span><span class="sxs-lookup"><span data-stu-id="aaddf-262">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="aaddf-263">Если для `EmbeddedResource` элемента заданы метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого файла ресурсов будет создаваться на основе таких метаданных.</span><span class="sxs-lookup"><span data-stu-id="aaddf-263">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="aaddf-264">По умолчанию для нового проекта .NET этому свойству задается значение `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-264">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="aaddf-265">Если задано значение `false` и для элемента `EmbeddedResource` в файле проекта не указаны метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого ресурса будет основано на имени корневого пространства имен проекта и относительном пути к файлу *.resx*.</span><span class="sxs-lookup"><span data-stu-id="aaddf-265">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="aaddf-266">Дополнительные сведения об определение имени файла манифеста см. [здесь](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-266">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="aaddf-267">LangVersion</span><span class="sxs-lookup"><span data-stu-id="aaddf-267">LangVersion</span></span>

<span data-ttu-id="aaddf-268">Свойство `LangVersion` позволяет указать конкретную версию языка программирования.</span><span class="sxs-lookup"><span data-stu-id="aaddf-268">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="aaddf-269">Например, если требуется доступ к предварительным версиям функций C#, задайте параметру `LangVersion` значение `preview`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-269">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="aaddf-270">Дополнительные сведения см. в статье [Управление версиями языка C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="aaddf-270">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="aaddf-271">Свойства включения элементов по умолчанию</span><span class="sxs-lookup"><span data-stu-id="aaddf-271">Default item inclusion properties</span></span>

<span data-ttu-id="aaddf-272">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="aaddf-272">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="aaddf-273">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="aaddf-273">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="aaddf-274">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="aaddf-274">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="aaddf-275">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="aaddf-275">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="aaddf-276">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="aaddf-276">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="aaddf-277">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="aaddf-277">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="aaddf-278">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="aaddf-278">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="aaddf-279">Дополнительные сведения см. в разделе [Включения и исключения по умолчанию](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="aaddf-279">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="aaddf-280">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="aaddf-280">DefaultItemExcludes</span></span>

<span data-ttu-id="aaddf-281">Используйте свойство `DefaultItemExcludes`, чтобы определить стандартные маски для файлов и папок, которые должны быть исключены из стандартных масок включения, исключения и удаления.</span><span class="sxs-lookup"><span data-stu-id="aaddf-281">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="aaddf-282">По умолчанию папки *./bin* и *./obj* исключаются из стандартных масок.</span><span class="sxs-lookup"><span data-stu-id="aaddf-282">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="aaddf-283">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="aaddf-283">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="aaddf-284">Используйте свойство `DefaultExcludesInProjectFolder`, чтобы определить стандартные маски для файлов и папок в папке проекта, которые должны быть исключены из стандартных масок включения, исключения и удаления.</span><span class="sxs-lookup"><span data-stu-id="aaddf-284">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="aaddf-285">По умолчанию папки, начинающиеся с точки (`.`), такие как *.git* и *.vs*, исключаются из стандартных масок.</span><span class="sxs-lookup"><span data-stu-id="aaddf-285">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="aaddf-286">Это свойство очень похоже на свойство `DefaultItemExcludes`, за исключением того, что оно учитывает только файлы и папки в папке проекта.</span><span class="sxs-lookup"><span data-stu-id="aaddf-286">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="aaddf-287">Если стандартная маска будет случайно соответствовать элементам за пределами папки проекта с относительным путем, используйте свойство `DefaultExcludesInProjectFolder` вместо свойства `DefaultItemExcludes`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-287">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="aaddf-288">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="aaddf-288">EnableDefaultItems</span></span>

<span data-ttu-id="aaddf-289">Свойство `EnableDefaultItems` определяет, включаются ли в проект неявным образом элементы компиляции, элементы внедренных ресурсов и элементы `None`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-289">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="aaddf-290">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-290">The default value is `true`.</span></span> <span data-ttu-id="aaddf-291">Задайте значение `false` для свойства `EnableDefaultItems`, чтобы отключить все неявные включения файлов.</span><span class="sxs-lookup"><span data-stu-id="aaddf-291">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="aaddf-292">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="aaddf-292">EnableDefaultCompileItems</span></span>

<span data-ttu-id="aaddf-293">Свойство `EnableDefaultCompileItems` определяет, включаются ли в проект неявным образом элементы компиляции.</span><span class="sxs-lookup"><span data-stu-id="aaddf-293">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="aaddf-294">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-294">The default value is `true`.</span></span> <span data-ttu-id="aaddf-295">Задайте значение `false` для свойства `EnableDefaultCompileItems`, чтобы отключить неявное включение файлов \*.cs и других файлов расширения языка.</span><span class="sxs-lookup"><span data-stu-id="aaddf-295">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="aaddf-296">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="aaddf-296">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="aaddf-297">Свойство `EnableDefaultEmbeddedResourceItems` определяет, включаются ли в проект неявным образом элементы внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aaddf-297">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="aaddf-298">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-298">The default value is `true`.</span></span> <span data-ttu-id="aaddf-299">Задайте значение `false` для свойства `EnableDefaultEmbeddedResourceItems`, чтобы отключить неявное включение файлов внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aaddf-299">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="aaddf-300">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="aaddf-300">EnableDefaultNoneItems</span></span>

<span data-ttu-id="aaddf-301">Свойство `EnableDefaultNoneItems` определяет, включаются ли в проект неявным образом элементы `None` (файлы, которые не играют никакой роли в процессе сборки).</span><span class="sxs-lookup"><span data-stu-id="aaddf-301">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="aaddf-302">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-302">The default value is `true`.</span></span> <span data-ttu-id="aaddf-303">Задайте значение `false` для свойства `EnableDefaultNoneItems`, чтобы отключить неявное включение элементов `None`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-303">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="aaddf-304">Свойства анализа кода</span><span class="sxs-lookup"><span data-stu-id="aaddf-304">Code analysis properties</span></span>

<span data-ttu-id="aaddf-305">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="aaddf-305">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="aaddf-306">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="aaddf-306">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="aaddf-307">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="aaddf-307">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="aaddf-308">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="aaddf-308">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="aaddf-309">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="aaddf-309">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="aaddf-310">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="aaddf-310">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="aaddf-311">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="aaddf-311">AnalysisLevel</span></span>

<span data-ttu-id="aaddf-312">Свойство `AnalysisLevel` позволяет указать уровень анализа кода.</span><span class="sxs-lookup"><span data-stu-id="aaddf-312">The `AnalysisLevel` property lets you specify a code-analysis level.</span></span> <span data-ttu-id="aaddf-313">Например, если требуется доступ к анализаторам кода предварительной версии, задайте для параметра `AnalysisLevel` значение `preview`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-313">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span>

<span data-ttu-id="aaddf-314">Значение по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="aaddf-314">Default value:</span></span>

- <span data-ttu-id="aaddf-315">Если проект предназначен для .NET 5.0 или более поздней версии или если вы добавили свойство [AnalysisMode](#analysismode), значением по умолчанию будет `latest`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-315">If your project targets .NET 5.0 or later, or if you've added the [AnalysisMode](#analysismode) property, the default value is `latest`.</span></span>
- <span data-ttu-id="aaddf-316">В противном случае это свойство не будет учитываться, если оно явно не добавлено в файл проекта.</span><span class="sxs-lookup"><span data-stu-id="aaddf-316">Otherwise, this property is omitted unless you explicitly add it to the project file.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="aaddf-317">В следующей таблице приведены доступные параметры.</span><span class="sxs-lookup"><span data-stu-id="aaddf-317">The following table shows the available options.</span></span>

| <span data-ttu-id="aaddf-318">Значение</span><span class="sxs-lookup"><span data-stu-id="aaddf-318">Value</span></span> | <span data-ttu-id="aaddf-319">Значение</span><span class="sxs-lookup"><span data-stu-id="aaddf-319">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="aaddf-320">Используются новейшие анализаторы кода, которые были выпущены.</span><span class="sxs-lookup"><span data-stu-id="aaddf-320">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="aaddf-321">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aaddf-321">This is the default.</span></span> |
| `preview` | <span data-ttu-id="aaddf-322">Используются новейшие анализаторы кода, даже если они находятся на этапе предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="aaddf-322">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="aaddf-323">Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила.</span><span class="sxs-lookup"><span data-stu-id="aaddf-323">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="aaddf-324">Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила.</span><span class="sxs-lookup"><span data-stu-id="aaddf-324">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

> [!NOTE]
> <span data-ttu-id="aaddf-325">Это свойство не влияет на анализ кода в проектах, которые не ссылаются на [пакет SDK проекта](overview.md), например, проекты на устаревших платформах .NET Framework, которые ссылаются на пакет NuGet Microsoft.CodeAnalysis.NetAnalyzers.</span><span class="sxs-lookup"><span data-stu-id="aaddf-325">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="analysismode"></a><span data-ttu-id="aaddf-326">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="aaddf-326">AnalysisMode</span></span>

<span data-ttu-id="aaddf-327">Начиная с .NET 5.0 пакет SDK для .NET поставляется со всеми [правилами качества кода "CA"](../../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-327">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="aaddf-328">По умолчанию в качестве предупреждений сборки включены только [некоторые правила](../../fundamentals/code-analysis/overview.md#enabled-rules).</span><span class="sxs-lookup"><span data-stu-id="aaddf-328">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="aaddf-329">Свойство `AnalysisMode` позволяет настроить набор правил, включенных по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aaddf-329">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="aaddf-330">Можно либо переключиться на более агрессивный (неявный) режим анализа, либо более консервативный (явный) режим анализа.</span><span class="sxs-lookup"><span data-stu-id="aaddf-330">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="aaddf-331">Например, если вы хотите включить все правила по умолчанию как предупреждения сборки, установите значение `AllEnabledByDefault`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-331">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="aaddf-332">В следующей таблице приведены доступные параметры.</span><span class="sxs-lookup"><span data-stu-id="aaddf-332">The following table shows the available options.</span></span>

| <span data-ttu-id="aaddf-333">Значение</span><span class="sxs-lookup"><span data-stu-id="aaddf-333">Value</span></span> | <span data-ttu-id="aaddf-334">Значение</span><span class="sxs-lookup"><span data-stu-id="aaddf-334">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="aaddf-335">Режим по умолчанию, при котором определенные правила включаются в виде предупреждений сборки, некоторые правила включаются в качестве предложений интегрированной среды разработки Visual Studio, а остальные отключаются.</span><span class="sxs-lookup"><span data-stu-id="aaddf-335">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="aaddf-336">Агрессивный или неявный режим означает, что все правила по умолчанию включены как предупреждения сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-336">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="aaddf-337">Вы можете выборочно [отказаться](../../fundamentals/code-analysis/configuration-options.md) от отдельных правил, чтобы отключить их.</span><span class="sxs-lookup"><span data-stu-id="aaddf-337">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="aaddf-338">Консервативный или явный режим означает, что все правила по умолчанию отключены.</span><span class="sxs-lookup"><span data-stu-id="aaddf-338">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="aaddf-339">Можно выборочно [принять](../../fundamentals/code-analysis/configuration-options.md) отдельные правила, чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="aaddf-339">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

> [!NOTE]
> <span data-ttu-id="aaddf-340">Это свойство не влияет на анализ кода в проектах, которые не ссылаются на [пакет SDK проекта](overview.md), например, проекты на устаревших платформах .NET Framework, которые ссылаются на пакет NuGet Microsoft.CodeAnalysis.NetAnalyzers.</span><span class="sxs-lookup"><span data-stu-id="aaddf-340">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="aaddf-341">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="aaddf-341">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="aaddf-342">Свойство `CodeAnalysisTreatWarningsAsErrors` позволяет настроить, следует ли обрабатывать предупреждения анализа качества кода (CAxxxx) как предупреждения и прекращать сборку.</span><span class="sxs-lookup"><span data-stu-id="aaddf-342">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="aaddf-343">Если при построении проектов используется флаг `-warnaserror`, предупреждения [анализа качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis) также обрабатываются как ошибки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-343">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="aaddf-344">Если вы не хотите, чтобы предупреждения качества кода обрабатывались как ошибки, можно задать для свойства MSBuild `CodeAnalysisTreatWarningsAsErrors` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="aaddf-344">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="aaddf-345">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="aaddf-345">EnableNETAnalyzers</span></span>

<span data-ttu-id="aaddf-346">Для проектов, предназначенных для .NET 5.0 или более поздней версии, по умолчанию включен [анализ качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis).</span><span class="sxs-lookup"><span data-stu-id="aaddf-346">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="aaddf-347">Вы можете включить анализ кода .NET для проектов в стиле пакета SDK, предназначенных для более ранних версий .NET, установив для свойства `EnableNETAnalyzers` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-347">You can enable .NET code analysis for SDK-style projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="aaddf-348">Чтобы отключить анализ кода в любом проекте, присвойте этому свойству значение `false`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-348">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="aaddf-349">Это свойство применяется к встроенным анализаторам в пакете SDK для .NET 5+.</span><span class="sxs-lookup"><span data-stu-id="aaddf-349">This property applies specifically to the built-in analyzers in the .NET 5+ SDK.</span></span> <span data-ttu-id="aaddf-350">Его не следует использовать при установке пакета NuGet для анализа кода.</span><span class="sxs-lookup"><span data-stu-id="aaddf-350">It should not be used when you install a NuGet code analysis package.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="aaddf-351">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="aaddf-351">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="aaddf-352">Эта функция в настоящее время является экспериментальной и может измениться в .NET 6 по сравнению с реализацией в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="aaddf-352">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="aaddf-353">[Анализ стиля кода .NET](../../fundamentals/code-analysis/overview.md#code-style-analysis) по умолчанию отключен при сборке для всех проектов .NET.</span><span class="sxs-lookup"><span data-stu-id="aaddf-353">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="aaddf-354">Можно включить анализ стиля кода для проектов .NET, задав для свойства `EnforceCodeStyleInBuild` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-354">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="aaddf-355">Все правила стиля кода, которые [настроены](../../fundamentals/code-analysis/overview.md#code-style-analysis) как предупреждения или ошибки, будут выполняться при нарушениях сборки и отчета.</span><span class="sxs-lookup"><span data-stu-id="aaddf-355">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="aaddf-356">Свойства конфигурации среды выполнения</span><span class="sxs-lookup"><span data-stu-id="aaddf-356">Run-time configuration properties</span></span>

<span data-ttu-id="aaddf-357">Вы можете настроить некоторые варианты поведения среды выполнения, указав свойства MSBuild в файле проекта приложения.</span><span class="sxs-lookup"><span data-stu-id="aaddf-357">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="aaddf-358">Сведения о других способах настройки поведения среды выполнения см. в статье о [параметрах конфигурации среды выполнения](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-358">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="aaddf-359">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aaddf-359">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="aaddf-360">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="aaddf-360">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="aaddf-361">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aaddf-361">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="aaddf-362">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aaddf-362">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="aaddf-363">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="aaddf-363">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="aaddf-364">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="aaddf-364">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="aaddf-365">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="aaddf-365">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="aaddf-366">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="aaddf-366">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="aaddf-367">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="aaddf-367">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="aaddf-368">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aaddf-368">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="aaddf-369">Свойство `ConcurrentGarbageCollection` указывает, включена ли [фоновая (параллельная) сборка мусора](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-369">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="aaddf-370">Задайте значение `false`, чтобы отключить фоновую сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="aaddf-370">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="aaddf-371">Дополнительные сведения см. в разделе [Сборка мусора в фоновом режиме](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="aaddf-371">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="aaddf-372">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="aaddf-372">InvariantGlobalization</span></span>

<span data-ttu-id="aaddf-373">Свойство `InvariantGlobalization` определяет, выполняется ли приложение в *инвариантном режиме глобализации*, что означает, что у него нет доступа к данным, относящимся к языку и региональным параметрам.</span><span class="sxs-lookup"><span data-stu-id="aaddf-373">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="aaddf-374">Установите значение `true` для запуска в инвариантном режиме глобализации.</span><span class="sxs-lookup"><span data-stu-id="aaddf-374">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="aaddf-375">Дополнительные сведения см. в разделе [Инвариантный режим](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="aaddf-375">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="aaddf-376">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aaddf-376">RetainVMGarbageCollection</span></span>

<span data-ttu-id="aaddf-377">Свойство `RetainVMGarbageCollection` настраивает сборщик мусора для помещения удаленных сегментов памяти в список ожидания для будущего использования или освобождения.</span><span class="sxs-lookup"><span data-stu-id="aaddf-377">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="aaddf-378">Значение `true` указывает сборщику мусора разместить сегменты в списке ожидания.</span><span class="sxs-lookup"><span data-stu-id="aaddf-378">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="aaddf-379">Дополнительные сведения см. в разделе [Сохранение виртуальной машины](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="aaddf-379">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="aaddf-380">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aaddf-380">ServerGarbageCollection</span></span>

<span data-ttu-id="aaddf-381">Свойство `ServerGarbageCollection` указывает, использует ли приложение [сборку мусора рабочей станции или сборку мусора сервера](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-381">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="aaddf-382">Задайте значение `true`, чтобы использовать сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="aaddf-382">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="aaddf-383">Дополнительные сведения см. в разделе [Рабочая станция и сервер](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="aaddf-383">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="aaddf-384">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="aaddf-384">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="aaddf-385">Свойство `ThreadPoolMaxThreads` указывает максимальное число потоков для пула рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="aaddf-385">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="aaddf-386">Дополнительные сведения см. в разделе [Максимальное число потоков](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="aaddf-386">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="aaddf-387">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="aaddf-387">ThreadPoolMinThreads</span></span>

<span data-ttu-id="aaddf-388">Свойство `ThreadPoolMinThreads` указывает минимальное число потоков для пула рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="aaddf-388">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="aaddf-389">Дополнительные сведения см. в разделе [Минимальное число потоков](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="aaddf-389">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="aaddf-390">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="aaddf-390">TieredCompilation</span></span>

<span data-ttu-id="aaddf-391">Свойство `TieredCompilation` указывает, использует ли JIT-компилятор [многоуровневую компиляцию](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="aaddf-391">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="aaddf-392">Задайте значение `false`, чтобы отключить многоуровневую компиляцию.</span><span class="sxs-lookup"><span data-stu-id="aaddf-392">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="aaddf-393">Дополнительные сведения см. в разделе [Многоуровневая компиляция](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="aaddf-393">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="aaddf-394">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="aaddf-394">TieredCompilationQuickJit</span></span>

<span data-ttu-id="aaddf-395">Свойство `TieredCompilationQuickJit` указывает, использует ли JIT-компилятор быструю JIT-компиляцию.</span><span class="sxs-lookup"><span data-stu-id="aaddf-395">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="aaddf-396">Задайте значение `false`, чтобы отключить быструю JIT-компиляцию.</span><span class="sxs-lookup"><span data-stu-id="aaddf-396">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="aaddf-397">Дополнительные сведения см. в разделе [Быстрая JIT-компиляция](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="aaddf-397">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="aaddf-398">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="aaddf-398">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="aaddf-399">Свойство `TieredCompilationQuickJitForLoops` указывает, использует ли JIT-компилятор быструю JIT-компиляцию для методов, содержащих циклы.</span><span class="sxs-lookup"><span data-stu-id="aaddf-399">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="aaddf-400">Задайте значение `true`, чтобы включить быструю JIT-компиляцию для методов, содержащих циклы.</span><span class="sxs-lookup"><span data-stu-id="aaddf-400">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="aaddf-401">Дополнительные сведения см. в разделе [Быстрая JIT-компиляция для циклов](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="aaddf-401">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="aaddf-402">Свойства ссылки</span><span class="sxs-lookup"><span data-stu-id="aaddf-402">Reference properties</span></span>

<span data-ttu-id="aaddf-403">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="aaddf-403">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="aaddf-404">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="aaddf-404">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="aaddf-405">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="aaddf-405">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="aaddf-406">Свойства, связанные с восстановлением</span><span class="sxs-lookup"><span data-stu-id="aaddf-406">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="aaddf-407">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="aaddf-407">AssetTargetFallback</span></span>

<span data-ttu-id="aaddf-408">Свойство `AssetTargetFallback` позволяет указать дополнительные совместимые версии платформы для ссылок на проекты и пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="aaddf-408">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="aaddf-409">Например, если вы указали зависимость пакета с помощью `PackageReference`, но в этом пакете нет ресурсов, совместимых с `TargetFramework` вашего проекта, тогда пригодится свойство `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-409">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="aaddf-410">Совместимость пакета, на который указывает ссылка, повторно проверяется с помощью каждой целевой платформы, указанной в свойстве `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-410">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span> <span data-ttu-id="aaddf-411">Это свойство заменяет устаревшее свойство `PackageTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-411">This property replaces the deprecated property `PackageTargetFallback`.</span></span>

<span data-ttu-id="aaddf-412">В качестве значения свойства `AssetTargetFallback` можно задать одну [версию целевой платформы](../../standard/frameworks.md#supported-target-frameworks) или несколько.</span><span class="sxs-lookup"><span data-stu-id="aaddf-412">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="aaddf-413">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="aaddf-413">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="aaddf-414">Свойство `DisableImplicitFrameworkReferences` управляет неявными элементами `FrameworkReference` при разработке для .NET Core 3.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="aaddf-414">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="aaddf-415">При использовании .NET Core 2.1 или .NET Standard 2.0 и более ранних версий оно управляет неявными элементами [PackageReference](#packagereference) в пакетах в метапакете.</span><span class="sxs-lookup"><span data-stu-id="aaddf-415">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="aaddf-416">(Метапакет — это пакет на основе платформы, который состоит только из зависимостей от других пакетов.) Это свойство также управляет неявными ссылками, такими как `System` и `System.Core`, при разработке для .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aaddf-416">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="aaddf-417">Присвойте этому свойству значение `true`, чтобы отключить неявные элементы `FrameworkReference` или [PackageReference](#packagereference).</span><span class="sxs-lookup"><span data-stu-id="aaddf-417">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="aaddf-418">Если этому свойству присвоено значение `true`, можно добавить явные ссылки на только необходимые платформы или пакеты.</span><span class="sxs-lookup"><span data-stu-id="aaddf-418">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="aaddf-419">Свойства, связанные с восстановлением</span><span class="sxs-lookup"><span data-stu-id="aaddf-419">Restore-related properties</span></span>

<span data-ttu-id="aaddf-420">При восстановлении пакета, на который указывает ссылка, устанавливаются все его прямые зависимости и все зависимости этих зависимостей.</span><span class="sxs-lookup"><span data-stu-id="aaddf-420">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="aaddf-421">Можно настроить восстановление пакетов, указав такие свойства, как `RestorePackagesPath` и `RestoreIgnoreFailedSources`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-421">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="aaddf-422">Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект восстановления](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="aaddf-422">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-related-properties"></a><span data-ttu-id="aaddf-423">Свойства, связанные с запуском</span><span class="sxs-lookup"><span data-stu-id="aaddf-423">Run-related properties</span></span>

<span data-ttu-id="aaddf-424">Следующие свойства используются для запуска приложения с помощью команды [`dotnet run`](../tools/dotnet-run.md):</span><span class="sxs-lookup"><span data-stu-id="aaddf-424">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="aaddf-425">RunArguments</span><span class="sxs-lookup"><span data-stu-id="aaddf-425">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="aaddf-426">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="aaddf-426">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="aaddf-427">RunArguments</span><span class="sxs-lookup"><span data-stu-id="aaddf-427">RunArguments</span></span>

<span data-ttu-id="aaddf-428">Свойство `RunArguments` определяет аргументы, которые передаются в приложение при его запуске.</span><span class="sxs-lookup"><span data-stu-id="aaddf-428">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="aaddf-429">Можно указать дополнительные аргументы для передачи в приложение с помощью параметра [`--` для `dotnet run`](../tools/dotnet-run.md#options).</span><span class="sxs-lookup"><span data-stu-id="aaddf-429">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="aaddf-430">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="aaddf-430">RunWorkingDirectory</span></span>

<span data-ttu-id="aaddf-431">Свойство `RunWorkingDirectory` определяет рабочий каталог для запуска процесса приложения.</span><span class="sxs-lookup"><span data-stu-id="aaddf-431">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="aaddf-432">Это может быть абсолютный путь или путь относительно каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="aaddf-432">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="aaddf-433">Если каталог не указан, в качестве рабочего каталога используется `OutDir`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-433">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-related-properties"></a><span data-ttu-id="aaddf-434">Свойства, связанные с размещением</span><span class="sxs-lookup"><span data-stu-id="aaddf-434">Hosting-related properties</span></span>

<span data-ttu-id="aaddf-435">В этом разделе описаны следующие свойства MSBuild:</span><span class="sxs-lookup"><span data-stu-id="aaddf-435">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="aaddf-436">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="aaddf-436">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="aaddf-437">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="aaddf-437">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="aaddf-438">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="aaddf-438">EnableComHosting</span></span>

<span data-ttu-id="aaddf-439">Свойство `EnableComHosting` указывает, что сборка предоставляет сервер COM.</span><span class="sxs-lookup"><span data-stu-id="aaddf-439">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="aaddf-440">Установка `EnableComHosting` в `true` также подразумевает, что [EnableDynamicLoading](#enabledynamicloading) — `true`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-440">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="aaddf-441">Дополнительные сведения см. в разделе [Предоставление компонентов .NET для COM](../native-interop/expose-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-441">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="aaddf-442">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="aaddf-442">EnableDynamicLoading</span></span>

<span data-ttu-id="aaddf-443">Свойство `EnableDynamicLoading` указывает, что сборка является динамически загружаемым компонентом.</span><span class="sxs-lookup"><span data-stu-id="aaddf-443">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="aaddf-444">Компонентом может быть [библиотека COM](/windows/win32/com/the-component-object-model) или библиотека, не относящаяся к COM, которую можно [использовать из собственного узла](../tutorials/netcore-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-444">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="aaddf-445">Если присвоить этому свойству значения `true`:</span><span class="sxs-lookup"><span data-stu-id="aaddf-445">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="aaddf-446">Создается файл *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="aaddf-446">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="aaddf-447">[Накат](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) получает значение `LatestMinor`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-447">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="aaddf-448">Ссылки NuGet копируются локально.</span><span class="sxs-lookup"><span data-stu-id="aaddf-448">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="items"></a><span data-ttu-id="aaddf-449">Элементы</span><span class="sxs-lookup"><span data-stu-id="aaddf-449">Items</span></span>

<span data-ttu-id="aaddf-450">[Элементы MSBuild](/visualstudio/msbuild/msbuild-items) — это входные данные для системы сборки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-450">[MSBuild items](/visualstudio/msbuild/msbuild-items) are inputs into the build system.</span></span> <span data-ttu-id="aaddf-451">Элементы указываются в соответствии с их типом, который является именем элемента.</span><span class="sxs-lookup"><span data-stu-id="aaddf-451">Items are specified according to their type, which is the element name.</span></span> <span data-ttu-id="aaddf-452">Например, `Compile` и `Reference` — [два распространенных типа элементов](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="aaddf-452">For example, `Compile` and `Reference` are two [common item types](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="aaddf-453">Пакет SDK для .NET предоставляет следующие дополнительные типы элементов:</span><span class="sxs-lookup"><span data-stu-id="aaddf-453">The following additional item types are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="aaddf-454">PackageReference</span><span class="sxs-lookup"><span data-stu-id="aaddf-454">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="aaddf-455">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="aaddf-455">TrimmerRootAssembly</span></span>](#trimmerrootassembly)

<span data-ttu-id="aaddf-456">Для этих элементов можно использовать любой из стандартных [атрибутов элемента](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), например `Include` и `Update`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-456">You can use any of the standard [item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), for example, `Include` and `Update`, on these items.</span></span> <span data-ttu-id="aaddf-457">Чтобы добавить новый элемент, используйте `Include`. Для изменения существующего элемента используйте `Update`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-457">Use `Include` to add a new item, and use `Update` to modify an existing item.</span></span> <span data-ttu-id="aaddf-458">Например, `Update` часто используется для изменения элемента, который неявно был добавлен пакетом SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="aaddf-458">For example, `Update` is often used to modify an item that has implicitly been added by the .NET SDK.</span></span>

### <a name="packagereference"></a><span data-ttu-id="aaddf-459">PackageReference</span><span class="sxs-lookup"><span data-stu-id="aaddf-459">PackageReference</span></span>

<span data-ttu-id="aaddf-460">Элемент `PackageReference` определяет ссылку на пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="aaddf-460">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="aaddf-461">Атрибут `Include` указывает идентификатор пакета.</span><span class="sxs-lookup"><span data-stu-id="aaddf-461">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="aaddf-462">Атрибут `Version` указывает версию или диапазон версий.</span><span class="sxs-lookup"><span data-stu-id="aaddf-462">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="aaddf-463">Сведения о том, как указать минимальную версию, максимальную версию, диапазон или точное соответствие, см. в разделе [Диапазоны версий](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="aaddf-463">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

<span data-ttu-id="aaddf-464">Фрагмент файла проекта в следующем примере ссылается на пакет [System.Runtime](https://www.nuget.org/packages/System.Runtime/).</span><span class="sxs-lookup"><span data-stu-id="aaddf-464">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="aaddf-465">Также можно [управлять ресурсами зависимостей](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) с помощью таких метаданных, как `PrivateAssets`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-465">You can also [control dependency assets](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) using metadata such as `PrivateAssets`.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0">
    <PrivateAssets>all</PrivateAssets>
  </PackageReference>
</ItemGroup>
```

<span data-ttu-id="aaddf-466">Дополнительные сведения см. в статье [Ссылки на пакеты в файлах проекта](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="aaddf-466">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="trimmerrootassembly"></a><span data-ttu-id="aaddf-467">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="aaddf-467">TrimmerRootAssembly</span></span>

<span data-ttu-id="aaddf-468">Элемент `TrimmerRootAssembly` позволяет исключить сборку из [*обрезки*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="aaddf-468">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="aaddf-469">Обрезка — это процесс удаления неиспользуемых частей среды выполнения из упакованного приложения.</span><span class="sxs-lookup"><span data-stu-id="aaddf-469">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="aaddf-470">В некоторых случаях при обрезке могут неправильно удаляться необходимые ссылки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-470">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="aaddf-471">Следующий код XML исключает сборку `System.Security` из обрезки.</span><span class="sxs-lookup"><span data-stu-id="aaddf-471">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="item-metadata"></a><span data-ttu-id="aaddf-472">Метаданные элементов</span><span class="sxs-lookup"><span data-stu-id="aaddf-472">Item metadata</span></span>

<span data-ttu-id="aaddf-473">Помимо стандартных [атрибутов элемента MSBuild](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), в пакете SDK для .NET доступны следующие теги метаданных элементов:</span><span class="sxs-lookup"><span data-stu-id="aaddf-473">In addition to the standard [MSBuild item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), the following item metadata tags are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="aaddf-474">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="aaddf-474">CopyToPublishDirectory</span></span>](#copytopublishdirectory)
- [<span data-ttu-id="aaddf-475">LinkBase</span><span class="sxs-lookup"><span data-stu-id="aaddf-475">LinkBase</span></span>](#linkbase)

### <a name="copytopublishdirectory"></a><span data-ttu-id="aaddf-476">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="aaddf-476">CopyToPublishDirectory</span></span>

<span data-ttu-id="aaddf-477">Метаданные `CopyToPublishDirectory` в элементах управления MSBuild, когда элемент копируется в каталог публикации.</span><span class="sxs-lookup"><span data-stu-id="aaddf-477">The `CopyToPublishDirectory` metadata on an MSBuild item controls when the item is copied to the publish directory.</span></span> <span data-ttu-id="aaddf-478">Допустимые значения: `PreserveNewest`, при котором копируется только элемент, если он был изменен, `Always`, при котором всегда копируется элемент, и `Never`, при котором элемент никогда не копируется.</span><span class="sxs-lookup"><span data-stu-id="aaddf-478">Allowable values are `PreserveNewest`, which only copies the item if it has changed, `Always`, which always copies the item, and `Never`, which never copies the item.</span></span> <span data-ttu-id="aaddf-479">С точки зрения производительности `PreserveNewest` предпочтительнее, поскольку включает инкрементную сборку.</span><span class="sxs-lookup"><span data-stu-id="aaddf-479">From a performance standpoint, `PreserveNewest` is preferable because it enables an incremental build.</span></span>

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a><span data-ttu-id="aaddf-480">LinkBase</span><span class="sxs-lookup"><span data-stu-id="aaddf-480">LinkBase</span></span>

<span data-ttu-id="aaddf-481">Для элемента, находящегося за пределами каталога проекта и его подкаталогов, целевой объект публикации использует [метаданные Link](/visualstudio/msbuild/common-msbuild-item-metadata) элемента, чтобы определить, куда копировать элемент.</span><span class="sxs-lookup"><span data-stu-id="aaddf-481">For an item that's outside of the project directory and its subdirectories, the publish target uses the item's [Link metadata](/visualstudio/msbuild/common-msbuild-item-metadata) to determine where to copy the item to.</span></span> <span data-ttu-id="aaddf-482">`Link` также определяет, как элементы за пределами дерева проекта отображаются в окне обозревателя решений Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aaddf-482">`Link` also determines how items outside of the project tree are displayed in the Solution Explorer window of Visual Studio.</span></span>

<span data-ttu-id="aaddf-483">Если для элемента, находящегося за пределами проекта, `Link` не указан, по умолчанию используется `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-483">If `Link` is not specified for an item that's outside of the project cone, it defaults to `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span></span> <span data-ttu-id="aaddf-484">`LinkBase` позволяет указать допустимую базовую папку для элементов за пределами проекта.</span><span class="sxs-lookup"><span data-stu-id="aaddf-484">`LinkBase` lets you specify a sensible base folder for items outside of the project cone.</span></span> <span data-ttu-id="aaddf-485">Иерархия папок в базовой папке обеспечивается с помощью `RecursiveDir`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-485">The folder hierarchy under the base folder is preserved via `RecursiveDir`.</span></span> <span data-ttu-id="aaddf-486">Если параметр `LinkBase` не указан, он опускается в пути `Link`.</span><span class="sxs-lookup"><span data-stu-id="aaddf-486">If `LinkBase` is not specified, it's omitted from the `Link` path.</span></span>

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

<span data-ttu-id="aaddf-487">На следующем рисунке показано, как файл, который включен с помощью стандартной маски предыдущего элемента `Include`, отображается в обозревателе решений.</span><span class="sxs-lookup"><span data-stu-id="aaddf-487">The following image shows how a file that's included via the previous item `Include` glob displays in Solution Explorer.</span></span>

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Обозреватель решений: элемент с метаданными LinkBase.":::

## <a name="see-also"></a><span data-ttu-id="aaddf-489">См. также</span><span class="sxs-lookup"><span data-stu-id="aaddf-489">See also</span></span>

- [<span data-ttu-id="aaddf-490">Справочник по схеме MSBuild</span><span class="sxs-lookup"><span data-stu-id="aaddf-490">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="aaddf-491">Общие свойства MSBuild</span><span class="sxs-lookup"><span data-stu-id="aaddf-491">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="aaddf-492">Свойства MSBuild для целевого объекта pack NuGet</span><span class="sxs-lookup"><span data-stu-id="aaddf-492">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="aaddf-493">Свойства MSBuild для целевого объекта restore NuGet</span><span class="sxs-lookup"><span data-stu-id="aaddf-493">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="aaddf-494">Настройка сборки</span><span class="sxs-lookup"><span data-stu-id="aaddf-494">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
