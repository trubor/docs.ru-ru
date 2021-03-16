---
title: 'NETSDK1080: элемент PackageReference для Microsoft.AspNetCore.App не обязателен'
description: Сведения об ошибке NETSDK1080 пакета SDK для .NET, которая предупреждает о необязательной записи в файле проекта.
ms.topic: error-reference
ms.date: 02/25/2021
f1_keywords:
- NETSDK1080
ms.openlocfilehash: ebf9484e4a358597a1177f95e92f68330180cd35
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206793"
---
# <a name="netsdk1080-packagereference-to-microsoftaspnetcoreapp-is-not-necessary"></a><span data-ttu-id="29914-103">NETSDK1080: элемент PackageReference для Microsoft.AspNetCore.App не обязателен</span><span class="sxs-lookup"><span data-stu-id="29914-103">NETSDK1080: PackageReference to Microsoft.AspNetCore.App is not necessary</span></span>

<span data-ttu-id="29914-104">NETSDK1080 предупреждает, что элемент `PackageReference` для `Microsoft.AspNetCore.App` в файле проекта не является обязательным.</span><span class="sxs-lookup"><span data-stu-id="29914-104">NETSDK1080 warns you that the `PackageReference` element for `Microsoft.AspNetCore.App` in your project file is not necessary.</span></span> <span data-ttu-id="29914-105">Полный текст сообщения об ошибке подобен приведенному ниже.</span><span class="sxs-lookup"><span data-stu-id="29914-105">The full error message is similar to the following example:</span></span>

> <span data-ttu-id="29914-106">Предупреждение NETSDK1080: PackageReference для Microsoft.AspNetCore.App не является обязательным при нацеливании на .NET Core 3.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="29914-106">warning NETSDK1080: A PackageReference to Microsoft.AspNetCore.App is not necessary when targeting .NET Core 3.0 or higher.</span></span> <span data-ttu-id="29914-107">Если используется Microsoft.NET.Sdk.Web, ссылка на общую платформу будет выполняться автоматически.</span><span class="sxs-lookup"><span data-stu-id="29914-107">If Microsoft.NET.Sdk.Web is used, the shared framework will be referenced automatically.</span></span> <span data-ttu-id="29914-108">В противном случае PackageReference следует заменить на FrameworkReference.</span><span class="sxs-lookup"><span data-stu-id="29914-108">Otherwise, the PackageReference should be replaced with a FrameworkReference.</span></span>

<span data-ttu-id="29914-109">Эта ошибка обычно возникает после обновления проекта до .NET Core 3.0 или более поздней версии с более ранней версии, которая требовала записи `PackageReference` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="29914-109">This error typically occurs after you've upgraded a project to .NET Core 3.0 or later, from an earlier version that required `PackageReference` entries in the project file.</span></span>

## <a name="aspnet-core-project-files"></a><span data-ttu-id="29914-110">Файлы проекта ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="29914-110">ASP.NET Core project files</span></span>

<span data-ttu-id="29914-111">Например, исходный файл проекта может выглядеть, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="29914-111">For example, your original project file might look like this example:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp2.2</TargetFramework>
    <AspNetCoreHostingModel>InProcess</AspNetCoreHostingModel>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.App"/>
    <PackageReference Include="Microsoft.AspNetCore.Razor.Design" Version="2.2.0" PrivateAssets="All" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="29914-112">После обновления до .NET Core 3.1 файл проекта для того же проекта должен выглядеть, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="29914-112">After updating to .NET Core 3.1 the project file for the same project should look like the following example:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="29914-113">Внесите эти изменения, в частности, удалите элемент `PackageReference`, чтобы устранить предупреждение.</span><span class="sxs-lookup"><span data-stu-id="29914-113">Make these changes, in particular delete the `PackageReference` element, to eliminate the warning.</span></span> <span data-ttu-id="29914-114">Дополнительные сведения см. в разделе [Удаление устаревших ссылок на пакеты](/aspnet/core/migration/22-to-30#remove-obsolete-package-references).</span><span class="sxs-lookup"><span data-stu-id="29914-114">For more information, see [Remove obsolete package references](/aspnet/core/migration/22-to-30#remove-obsolete-package-references).</span></span>

## <a name="class-library-project"></a><span data-ttu-id="29914-115">Проект библиотеки классов</span><span class="sxs-lookup"><span data-stu-id="29914-115">Class library project</span></span>

<span data-ttu-id="29914-116">В проекте библиотеки классов, использующем API ASP.NET Core, замените `PackageReference` на `FrameworkReference`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="29914-116">In a class library project that uses ASP.NET Core APIs, replace the `PackageReference` with a `FrameworkReference`, as shown in the following example:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <FrameworkReference Include="Microsoft.AspNetCore.App" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="29914-117">Дополнительные сведения см. в разделе [Использование API ASP.NET Core в библиотеке классов](/aspnet/core/fundamentals/target-aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="29914-117">For more information, see [Use ASP.NET Core APIs in a class library](/aspnet/core/fundamentals/target-aspnetcore).</span></span>
