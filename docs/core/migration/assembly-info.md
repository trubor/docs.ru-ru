---
title: Свойства AssemblyInfo
description: Сведения о атрибутах сборки и о том, как они соответствуют свойствам MSBuild в .NET Core 2.1 и более поздних версий.
ms.topic: reference
ms.date: 01/08/2021
ms.openlocfilehash: a2c431b3fe3da428f21582624ca5f357887e2815
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192878"
---
# <a name="map-assemblyinfo-attributes-to-properties"></a><span data-ttu-id="e4e7c-103">Сопоставление со свойствами для атрибутов AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="e4e7c-103">Map AssemblyInfo attributes to properties</span></span>

<span data-ttu-id="e4e7c-104">[Атрибуты сборки](../../standard/assembly/set-attributes.md), которые обычно присутствовали в файле *AssemblyInfo* в .NET Core 2.0 и более ранних версий, создаются автоматически из свойств MSBuild, начиная с .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-104">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file in .NET Core 2.0 and earlier versions are automatically generated from MSBuild properties, starting in .NET Core 2.1.</span></span>

## <a name="properties-per-attribute"></a><span data-ttu-id="e4e7c-105">Свойства каждого атрибута</span><span class="sxs-lookup"><span data-stu-id="e4e7c-105">Properties per attribute</span></span>

<span data-ttu-id="e4e7c-106">Как показано в следующей таблице, каждый атрибут имеет два соответствующих свойства: одно управляет содержимым атрибута, а второе отключает его создание.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-106">As shown in the following table, each attribute has a corresponding property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="e4e7c-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e4e7c-107">Attribute</span></span>                                                      | <span data-ttu-id="e4e7c-108">Свойство.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-108">Property</span></span>               | <span data-ttu-id="e4e7c-109">Свойство, используемое для отключения</span><span class="sxs-lookup"><span data-stu-id="e4e7c-109">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="e4e7c-110">Примечания.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-110">Notes:</span></span>

- <span data-ttu-id="e4e7c-111">`AssemblyVersion` и `FileVersion` по умолчанию имеют значение `$(Version)` без суффикса.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-111">`AssemblyVersion` and `FileVersion` default to the value of `$(Version)` without the suffix.</span></span> <span data-ttu-id="e4e7c-112">Например, если для `$(Version)` нужно указать `1.2.3-beta.4`, то значением будет `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-112">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="e4e7c-113">По умолчанию для `InformationalVersion` используется значение `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-113">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="e4e7c-114">Если имеется свойство `$(SourceRevisionId)`, оно добавляется к `InformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-114">If the `$(SourceRevisionId)` property is present, it's appended to `InformationalVersion`.</span></span> <span data-ttu-id="e4e7c-115">Такое поведение можно отключить с помощью `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-115">You can disable this behavior using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="e4e7c-116">Свойства `Copyright` и `Description` также используются для метаданных NuGet.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-116">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="e4e7c-117">Свойство `Configuration`, которое по умолчанию имеет значение `Debug`, является общим для всех целевых объектов MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-117">`Configuration`, which defaults to `Debug`, is shared with all MSBuild targets.</span></span> <span data-ttu-id="e4e7c-118">Его можно задать с помощью параметра `--configuration` команды `dotnet` (например, [dotnet pack](../tools/dotnet-pack.md)).</span><span class="sxs-lookup"><span data-stu-id="e4e7c-118">You can set it via the `--configuration` option of `dotnet` commands, for example, [dotnet pack](../tools/dotnet-pack.md).</span></span>

## <a name="generateassemblyinfo"></a><span data-ttu-id="e4e7c-119">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="e4e7c-119">GenerateAssemblyInfo</span></span>

<span data-ttu-id="e4e7c-120">Логическое свойство, которое позволяет включить или отключить создание свойств AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-120">A Boolean that enables or disables the AssemblyInfo generation.</span></span> <span data-ttu-id="e4e7c-121">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-121">The default value is `true`.</span></span>

## <a name="generatedassemblyinfofile"></a><span data-ttu-id="e4e7c-122">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="e4e7c-122">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="e4e7c-123">Относительный или абсолютный путь к файлу сведений о созданной сборке.</span><span class="sxs-lookup"><span data-stu-id="e4e7c-123">The relative or absolute path of the generated assembly info file.</span></span> <span data-ttu-id="e4e7c-124">По умолчанию используется файл с именем *[имя_проекта].AssemblyInfo.[cs|vb]* в каталоге `$(IntermediateOutputPath)` (*obj*).</span><span class="sxs-lookup"><span data-stu-id="e4e7c-124">Defaults to a file named *[project-name].AssemblyInfo.[cs|vb]* in the `$(IntermediateOutputPath)` (*obj*) directory.</span></span>
