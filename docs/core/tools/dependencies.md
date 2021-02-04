---
title: Управление зависимостями в .NET
description: Сведения об управлении зависимостями проекта для приложения .NET.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.topic: how-to
ms.date: 01/28/2021
ms.openlocfilehash: 9f5f814d0b4dc7aa3ff1a938c172475169a55bf2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216132"
---
# <a name="manage-dependencies-in-net-applications"></a><span data-ttu-id="0c48b-103">Управление зависимостями в приложениях .NET</span><span class="sxs-lookup"><span data-stu-id="0c48b-103">Manage dependencies in .NET applications</span></span>

<span data-ttu-id="0c48b-104">Эта статья описывает, как добавлять и удалять зависимости путем изменения файла проекта или с помощью интерфейса командной строки.</span><span class="sxs-lookup"><span data-stu-id="0c48b-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="0c48b-105">элемент \<PackageReference>;</span><span class="sxs-lookup"><span data-stu-id="0c48b-105">The \<PackageReference> element</span></span>

<span data-ttu-id="0c48b-106">Элемент файла проекта `<PackageReference>` имеет следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="0c48b-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="0c48b-107">Атрибут `Include` указывает идентификатор пакета, добавляемого в проект.</span><span class="sxs-lookup"><span data-stu-id="0c48b-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="0c48b-108">Атрибут `Version` указывает версию, которую необходимо получить.</span><span class="sxs-lookup"><span data-stu-id="0c48b-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="0c48b-109">Версии указываются в соответствии с [правилами версий NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="0c48b-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="0c48b-110">Если вы не знакомы с синтаксисом файла проекта, см. дополнительные сведения в [справочной документации по проектам MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).</span><span class="sxs-lookup"><span data-stu-id="0c48b-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="0c48b-111">Зависимость, доступная только в конкретном целевом объекте, добавляется с использованием условий, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0c48b-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="0c48b-112">Зависимость в предыдущем примере будет допустимой только при сборке для указанного целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="0c48b-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="0c48b-113">Элемент `$(TargetFramework)` в этом условии представляет собой задаваемое в проекте свойство MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0c48b-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="0c48b-114">Для наиболее распространенных приложений .NET это не требуется.</span><span class="sxs-lookup"><span data-stu-id="0c48b-114">For most common .NET applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="0c48b-115">Добавление зависимости путем изменения файла проекта</span><span class="sxs-lookup"><span data-stu-id="0c48b-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="0c48b-116">Чтобы добавить зависимость, добавьте элемент `<PackageReference>` внутрь элемента `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="0c48b-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="0c48b-117">Можно добавить существующий элемент `<ItemGroup>` или создать новый.</span><span class="sxs-lookup"><span data-stu-id="0c48b-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="0c48b-118">В следующем примере используется проект консольного приложения по умолчанию, созданный с помощью `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="0c48b-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="0c48b-119">Добавление зависимости с помощью интерфейса командной строки</span><span class="sxs-lookup"><span data-stu-id="0c48b-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="0c48b-120">Чтобы добавить зависимость, выполните команду [dotnet add package](dotnet-add-package.md), как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0c48b-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="0c48b-121">Удаление зависимости путем изменения файла проекта</span><span class="sxs-lookup"><span data-stu-id="0c48b-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="0c48b-122">Чтобы удалить зависимость, удалите ее элемент `<PackageReference>` из файла проекта.</span><span class="sxs-lookup"><span data-stu-id="0c48b-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="0c48b-123">Удаление зависимости с помощью интерфейса командной строки</span><span class="sxs-lookup"><span data-stu-id="0c48b-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="0c48b-124">Чтобы удалить зависимость, выполните команду [dotnet remove package](dotnet-remove-package.md), как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0c48b-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="0c48b-125">См. также</span><span class="sxs-lookup"><span data-stu-id="0c48b-125">See also</span></span>

* [<span data-ttu-id="0c48b-126">Ссылки на пакеты в файлах проекта</span><span class="sxs-lookup"><span data-stu-id="0c48b-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [<span data-ttu-id="0c48b-127">Команда dotnet list package</span><span class="sxs-lookup"><span data-stu-id="0c48b-127">dotnet list package command</span></span>](dotnet-list-package.md)
