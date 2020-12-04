---
title: 'NETSDK1071: PackageReference для "{0}" указывает версию `{1}`.'
description: Как устранить проблему с PackageReference для метапакета, включенного в состав платформы с версией.
author: Forgind
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1071
ms.openlocfilehash: 1381fc63941ec04efb31035d13913620a195c236
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713084"
---
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a><span data-ttu-id="e189e-103">NETSDK1071: Явное управление версиями PackageReference для метапакета, который будет включаться в состав платформы.</span><span class="sxs-lookup"><span data-stu-id="e189e-103">NETSDK1071: Explicitly versioned PackageReference to a metapackage that would be included with the framework.</span></span>

<span data-ttu-id="e189e-104">**Эта статья относится к:** ✔️ пакету SDK для .NET 5.0.100 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="e189e-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="e189e-105">Когда пакет SDK для .NET выдает предупреждение NETSDK1071, это означает, что в будущем может возникнуть конфликт версий между версией метапакета, указанной в PackageReference, и версией того же метапакета, неявно заданной в свойстве TargetFramework:</span><span class="sxs-lookup"><span data-stu-id="e189e-105">When the .NET SDK issues warning NETSDK1071, it suggests there may be a version conflict in the future between the version of a metapackage specified in a PackageReference and the version of that metapackage as implicitly referenced via a TargetFramework property:</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="e189e-106">Так как TargetFramework автоматически переносит версию метапакета, эти версии, если они различны, будут конфликтовать.</span><span class="sxs-lookup"><span data-stu-id="e189e-106">Since the TargetFramework automatically brings in a version of the metapackage, the versions will conflict should they ever differ.</span></span>

<span data-ttu-id="e189e-107">Чтобы устранить эту проблему:</span><span class="sxs-lookup"><span data-stu-id="e189e-107">To resolve this:</span></span>

1. <span data-ttu-id="e189e-108">При использовании .NET Core или .NET Standard следует избегать явных ссылок на `Microsoft.NETCore.App` или `NETStandard.Library` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="e189e-108">Consider, when targeting .NET Core or .NET Standard, avoiding explicit references to `Microsoft.NETCore.App` or `NETStandard.Library` in your project file.</span></span>
2. <span data-ttu-id="e189e-109">Если при ориентации на .NET Core нужна определенная версия среды выполнения, вместо прямой ссылки на метапакет используйте свойство `<RuntimeFrameworkVersion>`.</span><span class="sxs-lookup"><span data-stu-id="e189e-109">If you need a specific version of the runtime when targeting .NET Core, use the `<RuntimeFrameworkVersion>`property instead of referencing the metapackage directly.</span></span> <span data-ttu-id="e189e-110">Это может произойти, например, когда вы используете [автономные развертывания](../../deploying/index.md#publish-self-contained) и нуждаетесь в определенной версии исправления 1.0.0 LTS для среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e189e-110">As an example, this could happen if you're using [self-contained deployments](../../deploying/index.md#publish-self-contained) and need a specific patch of the 1.0.0 LTS runtime.</span></span>
3. <span data-ttu-id="e189e-111">Если при ориентации на .NET Standard вам нужна конкретная версия `NetStandard.Library`, можно использовать свойство `<NetStandardImplicitPackageVersion>` и установить требуемую версию.</span><span class="sxs-lookup"><span data-stu-id="e189e-111">If you need a specific version of `NetStandard.Library` when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set it to the version you need.</span></span>
4. <span data-ttu-id="e189e-112">Не добавляйте и не обновляйте ссылки на `Microsoft.NETCore.App` или `NETSTandard.Library` явным образом в проектах .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e189e-112">Don't explicitly add or update references to either `Microsoft.NETCore.App` or `NETSTandard.Library` in .NET Framework projects.</span></span> <span data-ttu-id="e189e-113">Если при использовании пакета NuGet на основе .NET Standard требуется любая версия `NETStandard.Library`, NuGet автоматически устанавливает ее.</span><span class="sxs-lookup"><span data-stu-id="e189e-113">NuGet automatically installs any version of `NETStandard.Library` you need when using a .NET Standard-based NuGet package.</span></span>
5. <span data-ttu-id="e189e-114">Не указывайте версию для `Microsoft.AspNetCore.App` или `Microsoft.AspNetCore.All` при использовании .NET Core 2.1+, так как пакет SDK для .NET Core автоматически выбирает соответствующую версию.</span><span class="sxs-lookup"><span data-stu-id="e189e-114">Do not specify a version for `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` when using .NET Core 2.1+, as the .NET Core SDK automatically selects the appropriate version.</span></span> <span data-ttu-id="e189e-115">(Примечание: Это работает только при нацеливании на .NET Core 2.1, если проект также использует `Microsoft.NET.Sdk.Web`.</span><span class="sxs-lookup"><span data-stu-id="e189e-115">(Note: This only works when targeting .NET Core 2.1 if the project also uses `Microsoft.NET.Sdk.Web`.</span></span> <span data-ttu-id="e189e-116">Эта проблема устранена в пакете SDK для .NET Core 2.2.)</span><span class="sxs-lookup"><span data-stu-id="e189e-116">This problem was resolved in the .NET Core 2.2 SDK.)</span></span>
6. <span data-ttu-id="e189e-117">Если вы не хотите получать это предупреждение, вы можете отключить его:</span><span class="sxs-lookup"><span data-stu-id="e189e-117">If you want the warning to go away, you can also disable it:</span></span>

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
