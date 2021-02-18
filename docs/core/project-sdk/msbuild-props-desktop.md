---
title: Свойства MSBuild для Microsoft.NET.Sdk.Desktop
description: Справочник по свойствам и элементам MSBuild, распознаваемым пакетом SDK для классических приложений .NET, который включает WPF и WinForms.
ms.date: 02/04/2021
ms.topic: reference
author: adegeo
ms.author: adegeo
ms.custom: updateeachrelease
no-loc:
- App.xaml
- Application.xaml
- ApplicationDefinition
- Page
- EmbeddedResource
- Compile
- None
ms.openlocfilehash: 6d1903558dd03776a72eb6ee56ddae09fb66615b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488271"
---
# <a name="msbuild-reference-for-net-desktop-sdk-projects"></a><span data-ttu-id="0b499-103">Справочник по MSBuild для проектов пакета SDK для классических приложений .NET</span><span class="sxs-lookup"><span data-stu-id="0b499-103">MSBuild reference for .NET Desktop SDK projects</span></span>

<span data-ttu-id="0b499-104">На этой странице приведена ссылка на свойства и элементы MSBuild, используемые для настройки проектов Windows Forms (WinForms) и Windows Presentation Foundation (WPF) с помощью пакета SDK для классических приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="0b499-104">This page is a reference for the MSBuild properties and items that you use to configure Windows Forms (WinForms) and Windows Presentation Foundation (WPF) projects with the .NET Desktop SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="0b499-105">В этой статье приведено подмножество свойств MSBuild для пакета SDK для .NET, поскольку он связан с классическими приложениями.</span><span class="sxs-lookup"><span data-stu-id="0b499-105">This article documents a subset of the MSBuild properties for the .NET SDK as it relates to desktop apps.</span></span> <span data-ttu-id="0b499-106">Список полезных свойств для проектов .NET см. в статье [Справочник по MSBuild для проектов пакета SDK для .NET](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="0b499-106">For a list of common .NET SDK-specific MSBuild properties, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span> <span data-ttu-id="0b499-107">Список стандартных свойств см. в статье [Общие свойства MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="0b499-107">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="enable-net-desktop-sdk"></a><span data-ttu-id="0b499-108">Включение пакета SDK для классических приложений .NET</span><span class="sxs-lookup"><span data-stu-id="0b499-108">Enable .NET Desktop SDK</span></span>

<span data-ttu-id="0b499-109">Чтобы использовать WinForms или WPF, настройте файл проекта.</span><span class="sxs-lookup"><span data-stu-id="0b499-109">To use WinForms or WPF, configure your project file.</span></span>

### <a name="net-50"></a><span data-ttu-id="0b499-110">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0b499-110">.NET 5.0</span></span>

<span data-ttu-id="0b499-111">Укажите следующие параметры в файле проекта для WinForms или проекта WPF:</span><span class="sxs-lookup"><span data-stu-id="0b499-111">Specify the following settings in the project file of your WinForms or WPF project:</span></span>

- <span data-ttu-id="0b499-112">Выполните нацеливание для `Microsoft.NET.Sdk` пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="0b499-112">Target the .NET SDK `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="0b499-113">Дополнительные сведения см. в разделе [Файлы проекта](overview.md#project-files).</span><span class="sxs-lookup"><span data-stu-id="0b499-113">For more information, see [Project files](overview.md#project-files).</span></span>
- <span data-ttu-id="0b499-114">Присвойте параметру [`TargetFramework`](msbuild-props.md#targetframework) значение `net5.0-windows`.</span><span class="sxs-lookup"><span data-stu-id="0b499-114">Set [`TargetFramework`](msbuild-props.md#targetframework) to `net5.0-windows`.</span></span>
- <span data-ttu-id="0b499-115">При необходимости добавьте свойство платформы пользовательского интерфейса (или и то, и другое):</span><span class="sxs-lookup"><span data-stu-id="0b499-115">Add a UI framework property (or both, if necessary):</span></span>
  - <span data-ttu-id="0b499-116">Присвойте параметру [`UseWPF`](#usewpf) значение `true`, чтобы импортировать и использовать WPF.</span><span class="sxs-lookup"><span data-stu-id="0b499-116">Set [`UseWPF`](#usewpf) to `true` to import and use WPF.</span></span>
  - <span data-ttu-id="0b499-117">Присвойте параметру [`UseWindowsForms`](#usewindowsforms) значение `true`, чтобы импортировать и использовать WinForms.</span><span class="sxs-lookup"><span data-stu-id="0b499-117">Set [`UseWindowsForms`](#usewindowsforms) to `true` to import and use WinForms.</span></span>
- <span data-ttu-id="0b499-118">(Необязательно) Присвойте параметру `OutputType` значение `WinExe`.</span><span class="sxs-lookup"><span data-stu-id="0b499-118">(Optional) Set `OutputType` to `WinExe`.</span></span> <span data-ttu-id="0b499-119">При этом создается приложение, а не библиотека.</span><span class="sxs-lookup"><span data-stu-id="0b499-119">This produces an app as opposed to a library.</span></span> <span data-ttu-id="0b499-120">Чтобы создать библиотеку, опустите это свойство.</span><span class="sxs-lookup"><span data-stu-id="0b499-120">To produce a library, omit this property.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

### <a name="net-core-31"></a><span data-ttu-id="0b499-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="0b499-121">.NET Core 3.1</span></span>

<span data-ttu-id="0b499-122">Укажите следующие параметры в файле проекта для WinForms или проекта WPF:</span><span class="sxs-lookup"><span data-stu-id="0b499-122">Specify the following settings in the project file of your WinForms or WPF project:</span></span>

- <span data-ttu-id="0b499-123">Выполните нацеливание для `Microsoft.NET.Sdk.WindowsDesktop` пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="0b499-123">Target the .NET SDK `Microsoft.NET.Sdk.WindowsDesktop`.</span></span> <span data-ttu-id="0b499-124">Дополнительные сведения см. в разделе [Файлы проекта](overview.md#project-files).</span><span class="sxs-lookup"><span data-stu-id="0b499-124">For more information, see [Project files](overview.md#project-files).</span></span>
- <span data-ttu-id="0b499-125">Присвойте параметру [`TargetFramework`](msbuild-props.md#targetframework) значение `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="0b499-125">Set [`TargetFramework`](msbuild-props.md#targetframework) to `netcoreapp3.1`.</span></span>
- <span data-ttu-id="0b499-126">При необходимости добавьте свойство платформы пользовательского интерфейса (или и то, и другое):</span><span class="sxs-lookup"><span data-stu-id="0b499-126">Add a UI framework property (or both, if necessary):</span></span>
  - <span data-ttu-id="0b499-127">Присвойте параметру [`UseWPF`](#usewpf) значение `true`, чтобы импортировать и использовать WPF.</span><span class="sxs-lookup"><span data-stu-id="0b499-127">Set [`UseWPF`](#usewpf) to `true` to import and use WPF.</span></span>
  - <span data-ttu-id="0b499-128">Присвойте параметру [`UseWindowsForms`](#usewindowsforms) значение `true`, чтобы импортировать и использовать WinForms.</span><span class="sxs-lookup"><span data-stu-id="0b499-128">Set [`UseWindowsForms`](#usewindowsforms) to `true` to import and use WinForms.</span></span>
- <span data-ttu-id="0b499-129">(Необязательно) Присвойте параметру `OutputType` значение `WinExe`.</span><span class="sxs-lookup"><span data-stu-id="0b499-129">(Optional) Set `OutputType` to `WinExe`.</span></span> <span data-ttu-id="0b499-130">При этом создается приложение, а не библиотека.</span><span class="sxs-lookup"><span data-stu-id="0b499-130">This produces an app as opposed to a library.</span></span> <span data-ttu-id="0b499-131">Чтобы создать библиотеку, опустите это свойство.</span><span class="sxs-lookup"><span data-stu-id="0b499-131">To produce a library, omit this property.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

## <a name="wpf-default-includes-and-excludes"></a><span data-ttu-id="0b499-132">Включения и исключения WPF по умолчанию</span><span class="sxs-lookup"><span data-stu-id="0b499-132">WPF default includes and excludes</span></span>

<span data-ttu-id="0b499-133">Проекты SDK определяют набор правил для неявного включения или исключения файлов из проекта.</span><span class="sxs-lookup"><span data-stu-id="0b499-133">SDK projects define a set of rules to implicitly include or exclude files from the project.</span></span> <span data-ttu-id="0b499-134">Эти правила также автоматически устанавливают действие сборки файла.</span><span class="sxs-lookup"><span data-stu-id="0b499-134">These rules also automatically set the file's build action.</span></span> <span data-ttu-id="0b499-135">Это отличается от старых проектов .NET Framework, не использующих пакет SDK, которые не имеют правил включения или исключения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b499-135">This is unlike the older non-SDK .NET Framework projects, which have no default include or exclude rules.</span></span> <span data-ttu-id="0b499-136">В проектах .NET Framework требуется явное объявление того, какие файлы следует включить в проект.</span><span class="sxs-lookup"><span data-stu-id="0b499-136">.NET Framework projects require you to explicitly declare which files to include in the project.</span></span>

<span data-ttu-id="0b499-137">Файлы проектов .NET включают [стандартный набор правил](overview.md#default-includes-and-excludes) для автоматической обработки файлов.</span><span class="sxs-lookup"><span data-stu-id="0b499-137">.NET project files include a [standard set of rules](overview.md#default-includes-and-excludes) for automatically processing files.</span></span> <span data-ttu-id="0b499-138">Проекты WPF добавляют дополнительные правила.</span><span class="sxs-lookup"><span data-stu-id="0b499-138">WPF projects add additional rules.</span></span>

<span data-ttu-id="0b499-139">В следующей таблице показано, какие элементы и [стандартные маски](https://en.wikipedia.org/wiki/Glob_(programming)) включены в пакет SDK для классических приложений .NET и исключены из него, когда свойству проекта [`UseWPF`](#usewpf) задано значение `true`:</span><span class="sxs-lookup"><span data-stu-id="0b499-139">The following table shows which elements and [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Desktop SDK when the [`UseWPF`](#usewpf) project property is set to `true`:</span></span>

| <span data-ttu-id="0b499-140">Элемент</span><span class="sxs-lookup"><span data-stu-id="0b499-140">Element</span></span>               | <span data-ttu-id="0b499-141">Стандартная маска включения</span><span class="sxs-lookup"><span data-stu-id="0b499-141">Include glob</span></span>                 | <span data-ttu-id="0b499-142">Стандартная маска исключения</span><span class="sxs-lookup"><span data-stu-id="0b499-142">Exclude glob</span></span>                                                                                           | <span data-ttu-id="0b499-143">Стандартная маска удаления</span><span class="sxs-lookup"><span data-stu-id="0b499-143">Remove glob</span></span>  |
|-----------------------|------------------------------|--------------------------------------------------------------------|--------------|
| ApplicationDefinition | <span data-ttu-id="0b499-144">App.xaml или Application.xaml</span><span class="sxs-lookup"><span data-stu-id="0b499-144">App.xaml or Application.xaml</span></span> | <span data-ttu-id="0b499-145">Н/Д</span><span class="sxs-lookup"><span data-stu-id="0b499-145">N/A</span></span>                                                                | <span data-ttu-id="0b499-146">Н/Д</span><span class="sxs-lookup"><span data-stu-id="0b499-146">N/A</span></span>          |
| Page                  | <span data-ttu-id="0b499-147">\*\*/\*.xaml</span><span class="sxs-lookup"><span data-stu-id="0b499-147">\*\*/\*.xaml</span></span>                 | <span data-ttu-id="0b499-148">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0b499-148">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span><br><span data-ttu-id="0b499-149">Любой XAML, определенный *ApplicationDefinition*</span><span class="sxs-lookup"><span data-stu-id="0b499-149">Any XAML defined by *ApplicationDefinition*</span></span> | <span data-ttu-id="0b499-150">Н/Д</span><span class="sxs-lookup"><span data-stu-id="0b499-150">N/A</span></span>          |
| None                  | <span data-ttu-id="0b499-151">Н/Д</span><span class="sxs-lookup"><span data-stu-id="0b499-151">N/A</span></span>                          | <span data-ttu-id="0b499-152">Н/Д</span><span class="sxs-lookup"><span data-stu-id="0b499-152">N/A</span></span>                                                                | <span data-ttu-id="0b499-153">\*\*/\*.xaml</span><span class="sxs-lookup"><span data-stu-id="0b499-153">\*\*/\*.xaml</span></span> |

<span data-ttu-id="0b499-154">Ниже приведены параметры включения и исключения по умолчанию для всех типов проектов.</span><span class="sxs-lookup"><span data-stu-id="0b499-154">Here are the default include and exclude settings for all project types.</span></span> <span data-ttu-id="0b499-155">Дополнительные сведения см. в разделе [Включения и исключения по умолчанию](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="0b499-155">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

| <span data-ttu-id="0b499-156">Элемент</span><span class="sxs-lookup"><span data-stu-id="0b499-156">Element</span></span>           | <span data-ttu-id="0b499-157">Стандартная маска включения</span><span class="sxs-lookup"><span data-stu-id="0b499-157">Include glob</span></span>                              | <span data-ttu-id="0b499-158">Стандартная маска исключения</span><span class="sxs-lookup"><span data-stu-id="0b499-158">Exclude glob</span></span>                                                  | <span data-ttu-id="0b499-159">Стандартная маска удаления</span><span class="sxs-lookup"><span data-stu-id="0b499-159">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compile           | <span data-ttu-id="0b499-160">\*\*/\*.cs; \*\*/\*.vb (или другие расширения языка)</span><span class="sxs-lookup"><span data-stu-id="0b499-160">\*\*/\*.cs; \*\*/\*.vb (or other language extensions)</span></span> | <span data-ttu-id="0b499-161">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0b499-161">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="0b499-162">Н/Д</span><span class="sxs-lookup"><span data-stu-id="0b499-162">N/A</span></span>          |
| EmbeddedResource  | <span data-ttu-id="0b499-163">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="0b499-163">\*\*/\*.resx</span></span>                              | <span data-ttu-id="0b499-164">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0b499-164">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0b499-165">Н/Д</span><span class="sxs-lookup"><span data-stu-id="0b499-165">N/A</span></span>                      |
| None              | \*\*/\*                                   | <span data-ttu-id="0b499-166">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0b499-166">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0b499-167">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="0b499-167">\*\*/\*.cs; \*\*/\*.resx</span></span> |

### <a name="errors-related-to-duplicate-items"></a><span data-ttu-id="0b499-168">Ошибки, связанные с повторяющимися элементами</span><span class="sxs-lookup"><span data-stu-id="0b499-168">Errors related to "duplicate" items</span></span>

<span data-ttu-id="0b499-169">Если вы явно добавили файлы в проект или используете стандартные маски XAML для автоматического включения файлов в проект, может возникать одна из следующих ошибок:</span><span class="sxs-lookup"><span data-stu-id="0b499-169">If you explicitly added files to your project, or have XAML globs to automatically include files in your project, you might get one of the following errors:</span></span>

* <span data-ttu-id="0b499-170">Включены дублирующиеся элементы "ApplicationDefinition".</span><span class="sxs-lookup"><span data-stu-id="0b499-170">Duplicate 'ApplicationDefinition' items were included.</span></span>
* <span data-ttu-id="0b499-171">Включены дублирующиеся элементы "Page".</span><span class="sxs-lookup"><span data-stu-id="0b499-171">Duplicate 'Page' items were included.</span></span>

<span data-ttu-id="0b499-172">Эти ошибки являются результатом неявного *включения* стандартных масок, конфликтующих с вашими настройками.</span><span class="sxs-lookup"><span data-stu-id="0b499-172">These errors are a result of the implicit *Include* globs conflicting with your settings.</span></span> <span data-ttu-id="0b499-173">Чтобы обойти эту проблему, задайте параметру [`EnableDefaultApplicationDefinition`](#enabledefaultapplicationdefinition) или [`EnableDefaultPageItems`](#enabledefaultpageitems) значение `false`.</span><span class="sxs-lookup"><span data-stu-id="0b499-173">To work around this problem, set either [`EnableDefaultApplicationDefinition`](#enabledefaultapplicationdefinition) or [`EnableDefaultPageItems`](#enabledefaultpageitems) to `false`.</span></span> <span data-ttu-id="0b499-174">При установке этих значений в `false` возвращается поведение предыдущих пакетов SDK, где необходимо явно определить стандартные маски по умолчанию в проекте или явно определить файлы для включения в проект.</span><span class="sxs-lookup"><span data-stu-id="0b499-174">Setting these values to `false` reverts to the behavior of previous SDKs where you had to explicitly define the default globs in your project, or explicitly define the files to include in the project.</span></span>

<span data-ttu-id="0b499-175">Все неявные включения можно полностью отключить, установив для свойства [`EnableDefaultItems` ](msbuild-props.md#enabledefaultitems)значение `false`.</span><span class="sxs-lookup"><span data-stu-id="0b499-175">You can completely disable all implicit includes by setting the [`EnableDefaultItems` property](msbuild-props.md#enabledefaultitems) to `false`.</span></span>

## <a name="wpf-settings"></a><span data-ttu-id="0b499-176">Параметры WPF</span><span class="sxs-lookup"><span data-stu-id="0b499-176">WPF settings</span></span>

- [<span data-ttu-id="0b499-177">UseWPF</span><span class="sxs-lookup"><span data-stu-id="0b499-177">UseWPF</span></span>](#usewpf)
- [<span data-ttu-id="0b499-178">EnableDefaultApplicationDefinition</span><span class="sxs-lookup"><span data-stu-id="0b499-178">EnableDefaultApplicationDefinition</span></span>](#enabledefaultapplicationdefinition)
- [<span data-ttu-id="0b499-179">EnableDefaultPageItems</span><span class="sxs-lookup"><span data-stu-id="0b499-179">EnableDefaultPageItems</span></span>](#enabledefaultpageitems)

<span data-ttu-id="0b499-180">Дополнительные сведения о параметрах проектов, отличных от WPF, см. в разделе [Справочник по MSBuild для проектов пакета SDK для .NET](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="0b499-180">For information about non-WPF-specific project settings, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="usewpf"></a><span data-ttu-id="0b499-181">UseWPF</span><span class="sxs-lookup"><span data-stu-id="0b499-181">UseWPF</span></span>

<span data-ttu-id="0b499-182">Свойство `UseWPF` определяет, следует ли включать ссылки на библиотеки WPF.</span><span class="sxs-lookup"><span data-stu-id="0b499-182">The `UseWPF` property controls whether or not to include references to WPF libraries.</span></span> <span data-ttu-id="0b499-183">Это также приводит к соответствующему изменению конвейера MSBuild для правильной обработки проекта WPF и связанных файлов.</span><span class="sxs-lookup"><span data-stu-id="0b499-183">This also alters the MSBuild pipeline to correctly process a WPF project and related files.</span></span> <span data-ttu-id="0b499-184">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="0b499-184">The default value is `false`.</span></span> <span data-ttu-id="0b499-185">Задайте для свойства `UseWPF` значение `true`, чтобы включить поддержку WPF.</span><span class="sxs-lookup"><span data-stu-id="0b499-185">Set the `UseWPF` property to `true` to enable WPF support.</span></span> <span data-ttu-id="0b499-186">Выполнить нацеливание на платформу Windows можно только в том случае, если это свойство включено.</span><span class="sxs-lookup"><span data-stu-id="0b499-186">You can only target the Windows platform when this property is enabled.</span></span>

```xml
<PropertyGroup>
  <UseWPF>true</UseWPF>
</PropertyGroup>
```

<span data-ttu-id="0b499-187">Если это свойство имеет значение `true`, проекты .NET 5.0+ автоматически импортируют [пакет SDK для классических приложений .NET](#enable-net-desktop-sdk).</span><span class="sxs-lookup"><span data-stu-id="0b499-187">When this property is set to `true`, .NET 5.0+ projects will automatically import the [.NET Desktop SDK](#enable-net-desktop-sdk).</span></span>

<span data-ttu-id="0b499-188">Для использования этого свойства проекты .NET Core 3.1 должны быть явно предназначены для [пакета SDK для классических приложений.NET](#enable-net-desktop-sdk).</span><span class="sxs-lookup"><span data-stu-id="0b499-188">.NET Core 3.1 projects need to explicitly target the [.NET Desktop SDK](#enable-net-desktop-sdk) to use this property.</span></span>

### <a name="enabledefaultapplicationdefinition"></a><span data-ttu-id="0b499-189">EnableDefaultApplicationDefinition</span><span class="sxs-lookup"><span data-stu-id="0b499-189">EnableDefaultApplicationDefinition</span></span>

<span data-ttu-id="0b499-190">Свойство `EnableDefaultApplicationDefinition` определяет, включаются ли в проект неявным образом элементы `ApplicationDefinition`.</span><span class="sxs-lookup"><span data-stu-id="0b499-190">The `EnableDefaultApplicationDefinition` property controls whether `ApplicationDefinition` items are implicitly included in the project.</span></span> <span data-ttu-id="0b499-191">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="0b499-191">The default value is `true`.</span></span> <span data-ttu-id="0b499-192">Задайте значение `false` для свойства `EnableDefaultApplicationDefinition`, чтобы отключить неявные включения файлов.</span><span class="sxs-lookup"><span data-stu-id="0b499-192">Set the `EnableDefaultApplicationDefinition` property to `false` to disable the implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultApplicationDefinition>false</EnableDefaultApplicationDefinition>
</PropertyGroup>
```

<span data-ttu-id="0b499-193">Для этого свойства необходимо, чтобы свойство [`EnableDefaultItems` ](msbuild-props.md#enabledefaultitems) имело значение `true`, которое является значением по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b499-193">This property requires that the [`EnableDefaultItems` property](msbuild-props.md#enabledefaultitems) property is set to `true`, which is the default setting.</span></span>

### <a name="enabledefaultpageitems"></a><span data-ttu-id="0b499-194">EnableDefaultPageItems</span><span class="sxs-lookup"><span data-stu-id="0b499-194">EnableDefaultPageItems</span></span>

<span data-ttu-id="0b499-195">Свойство `EnableDefaultPageItems` определяет, включаются ли в проект неявным образом элементы `Page`, которые являются файлами _.xaml_.</span><span class="sxs-lookup"><span data-stu-id="0b499-195">The `EnableDefaultPageItems` property controls whether `Page` items, which are _.xaml_ files, are implicitly included in the project.</span></span> <span data-ttu-id="0b499-196">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="0b499-196">The default value is `true`.</span></span> <span data-ttu-id="0b499-197">Задайте значение `false` для свойства `EnableDefaultPageItems`, чтобы отключить неявные включения файлов.</span><span class="sxs-lookup"><span data-stu-id="0b499-197">Set the `EnableDefaultPageItems` property to `false` to disable the implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultPageItems>false</EnableDefaultPageItems>
</PropertyGroup>
```

<span data-ttu-id="0b499-198">Для этого свойства необходимо, чтобы свойство [`EnableDefaultItems` ](msbuild-props.md#enabledefaultitems) имело значение `true`, которое является значением по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b499-198">This property requires that the [`EnableDefaultItems` property](msbuild-props.md#enabledefaultitems) property is set to `true`, which is the default setting.</span></span>

## <a name="windows-forms-settings"></a><span data-ttu-id="0b499-199">Параметры Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b499-199">Windows Forms settings</span></span>

- [<span data-ttu-id="0b499-200">UseWindowsForms</span><span class="sxs-lookup"><span data-stu-id="0b499-200">UseWindowsForms</span></span>](#usewindowsforms)

<span data-ttu-id="0b499-201">Дополнительные сведения о свойствах проектов, отличных от WinForms, см. в разделе [Справочник по MSBuild для проектов пакета SDK для .NET](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="0b499-201">For information about non-WinForms-specific project properties, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="usewindowsforms"></a><span data-ttu-id="0b499-202">UseWindowsForms</span><span class="sxs-lookup"><span data-stu-id="0b499-202">UseWindowsForms</span></span>

<span data-ttu-id="0b499-203">Свойство `UseWindowsForms` определяет, предназначено ли приложение для Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0b499-203">The `UseWindowsForms` property controls whether or not your application is built to target Windows Forms.</span></span> <span data-ttu-id="0b499-204">Это свойство изменяет конвейер MSBuild соответствующим образом для правильной обработки Windows Forms проекта и связанных файлов.</span><span class="sxs-lookup"><span data-stu-id="0b499-204">This property alters the MSBuild pipeline to correctly process a Windows Forms project and related files.</span></span> <span data-ttu-id="0b499-205">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="0b499-205">The default value is `false`.</span></span> <span data-ttu-id="0b499-206">Задайте для свойства `UseWindowsForms` значение `true`, чтобы включить поддержку Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0b499-206">Set the `UseWindowsForms` property to `true` to enable Windows Forms support.</span></span> <span data-ttu-id="0b499-207">Выполнить нацеливание на платформу Windows можно только в том случае, если этот параметр включен.</span><span class="sxs-lookup"><span data-stu-id="0b499-207">You can only target the Windows platform when this setting is enabled.</span></span>

```xml
<PropertyGroup>
  <UseWindowsForms>true</UseWindowsForms>
</PropertyGroup>
```

<span data-ttu-id="0b499-208">Если это свойство имеет значение `true`, проекты .NET 5.0+ автоматически импортируют [пакет SDK для классических приложений .NET](#enable-net-desktop-sdk).</span><span class="sxs-lookup"><span data-stu-id="0b499-208">When this property is set to `true`, .NET 5.0+ projects will automatically import the [.NET Desktop SDK](#enable-net-desktop-sdk).</span></span>

<span data-ttu-id="0b499-209">Для использования этого свойства проекты .NET Core 3.1 должны быть явно предназначены для [пакета SDK для классических приложений.NET](#enable-net-desktop-sdk).</span><span class="sxs-lookup"><span data-stu-id="0b499-209">.NET Core 3.1 projects need to explicitly target the [.NET Desktop SDK](#enable-net-desktop-sdk) to use this property.</span></span>

## <a name="shared-settings"></a><span data-ttu-id="0b499-210">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="0b499-210">Shared settings</span></span>

- [<span data-ttu-id="0b499-211">DisableWinExeOutputInference</span><span class="sxs-lookup"><span data-stu-id="0b499-211">DisableWinExeOutputInference</span></span>](#disablewinexeoutputinference)

### <a name="disablewinexeoutputinference"></a><span data-ttu-id="0b499-212">DisableWinExeOutputInference</span><span class="sxs-lookup"><span data-stu-id="0b499-212">DisableWinExeOutputInference</span></span>

<span data-ttu-id="0b499-213">Применимо к пакету SDK для .NET 5.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="0b499-213">Applies to .NET 5.0 SDK and later.</span></span>

<span data-ttu-id="0b499-214">Если в приложении свойству `OutputType` присвоено значение `Exe`, создается окно консоли, если приложение не запускается из консоли.</span><span class="sxs-lookup"><span data-stu-id="0b499-214">When an app has the `Exe` value set for the `OutputType` property, a console window is created if the app isn't running from a console.</span></span> <span data-ttu-id="0b499-215">Обычно это не является необходимым поведением классического приложения Windows.</span><span class="sxs-lookup"><span data-stu-id="0b499-215">This is generally not the desired behavior of a Windows Desktop app.</span></span> <span data-ttu-id="0b499-216">Если присвоено значение `WinExe`, окно консоли не создается.</span><span class="sxs-lookup"><span data-stu-id="0b499-216">With the `WinExe` value, a console window isn't created.</span></span> <span data-ttu-id="0b499-217">Начиная с пакета SDK для .NET 5.0, значение `Exe` автоматически преобразуется в `WinExe`.</span><span class="sxs-lookup"><span data-stu-id="0b499-217">Starting with the .NET 5.0 SDK, the `Exe` value is automatically transformed to `WinExe`.</span></span>

<span data-ttu-id="0b499-218">Свойство `DisableWinExeOutputInference` возвращает поведение при обработке `Exe` как `WinExe`.</span><span class="sxs-lookup"><span data-stu-id="0b499-218">The `DisableWinExeOutputInference` property reverts the behavior of treating `Exe` as `WinExe`.</span></span> <span data-ttu-id="0b499-219">Присвойте этому параметру значение `true`, чтобы восстановить поведение значения свойства `OutputType` для `Exe`.</span><span class="sxs-lookup"><span data-stu-id="0b499-219">Set this value to `true` to restore the behavior of the `OutputType` property value of `Exe`.</span></span> <span data-ttu-id="0b499-220">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="0b499-220">The default value is `false`.</span></span>

```xml
<PropertyGroup>
  <DisableWinExeOutputInference>true</DisableWinExeOutputInference>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="0b499-221">См. также</span><span class="sxs-lookup"><span data-stu-id="0b499-221">See also</span></span>

- [<span data-ttu-id="0b499-222">Пакеты SDK для проектов .NET</span><span class="sxs-lookup"><span data-stu-id="0b499-222">.NET project SDKs</span></span>](overview.md)
- [<span data-ttu-id="0b499-223">Справочник по MSBuild для проектов пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="0b499-223">MSBuild reference for .NET SDK projects</span></span>](msbuild-props.md)
- [<span data-ttu-id="0b499-224">Справочник по схеме MSBuild</span><span class="sxs-lookup"><span data-stu-id="0b499-224">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="0b499-225">Общие свойства MSBuild</span><span class="sxs-lookup"><span data-stu-id="0b499-225">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="0b499-226">Настройка сборки</span><span class="sxs-lookup"><span data-stu-id="0b499-226">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
