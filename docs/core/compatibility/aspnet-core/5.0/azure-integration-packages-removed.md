---
title: 'Критическое изменение. Azure: Пакеты интеграции Azure с префиксом Майкрософт удалены'
description: 'Сведения о критическом изменении в ASP.NET Core 5.0 под названием Azure: Пакеты интеграции Azure с префиксом Майкрософт удалены'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: be7b2eeb6b12d033517c15ecb29e0d5364d64817
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498234"
---
# <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="8d93d-103">Azure Пакеты интеграции Azure с префиксом Майкрософт удалены</span><span class="sxs-lookup"><span data-stu-id="8d93d-103">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="8d93d-104">Следующие пакеты `Microsoft.*`, обеспечивающие интеграцию между ASP.NET Core и пакетами SDK для Azure, не входят в ASP.NET Core 5.0:</span><span class="sxs-lookup"><span data-stu-id="8d93d-104">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="8d93d-105">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), который интегрирует [Azure Key Vault](/azure/key-vault/) в [систему конфигурации](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="8d93d-105">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="8d93d-106">[Microsoft.AspNetCore.Data Protection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), который интегрирует Azure Key Vault в [систему защиты данных ASP.NET Core](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="8d93d-106">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="8d93d-107">[Microsoft.AspNetCore.Data Protection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), который интегрирует [хранилище BLOB-объектов Azure](/azure/storage/blobs/) в систему защиты данных ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d93d-107">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="8d93d-108">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="8d93d-108">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8d93d-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="8d93d-109">Version introduced</span></span>

<span data-ttu-id="8d93d-110">5.0 Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="8d93d-110">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="8d93d-111">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="8d93d-111">Old behavior</span></span>

<span data-ttu-id="8d93d-112">Пакеты `Microsoft.*` интегрированных служб Azure с API конфигурации и защиты данных.</span><span class="sxs-lookup"><span data-stu-id="8d93d-112">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="8d93d-113">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="8d93d-113">New behavior</span></span>

<span data-ttu-id="8d93d-114">Новые пакеты `Azure.*` интегрируют службы Azure с API конфигурации и защиты данных.</span><span class="sxs-lookup"><span data-stu-id="8d93d-114">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="8d93d-115">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="8d93d-115">Reason for change</span></span>

<span data-ttu-id="8d93d-116">Изменение внесено, поскольку `Microsoft.*` пакеты:</span><span class="sxs-lookup"><span data-stu-id="8d93d-116">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="8d93d-117">использовали устаревшие версии пакета SDK Azure;</span><span class="sxs-lookup"><span data-stu-id="8d93d-117">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="8d93d-118">Простые обновления не были доступны, поскольку новые версии пакета SDK для Azure включали критические изменения.</span><span class="sxs-lookup"><span data-stu-id="8d93d-118">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="8d93d-119">связаны с расписанием выпуска .NET Core;</span><span class="sxs-lookup"><span data-stu-id="8d93d-119">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="8d93d-120">Передача прав владения пакетами в группу пакета SDK Azure позволяет обновлять пакеты при обновлении пакета SDK для Azure.</span><span class="sxs-lookup"><span data-stu-id="8d93d-120">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8d93d-121">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="8d93d-121">Recommended action</span></span>

<span data-ttu-id="8d93d-122">В проектах ASP.NET Core 2.1 или более поздней версии замените старые `Microsoft.*` на новые пакеты `Azure.*`.</span><span class="sxs-lookup"><span data-stu-id="8d93d-122">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="8d93d-123">Прежний вариант</span><span class="sxs-lookup"><span data-stu-id="8d93d-123">Old</span></span> | <span data-ttu-id="8d93d-124">Оператор new</span><span class="sxs-lookup"><span data-stu-id="8d93d-124">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="8d93d-125">Azure.Extensions.AspNetCore.DataProtection.Keys</span><span class="sxs-lookup"><span data-stu-id="8d93d-125">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="8d93d-126">Azure.Extensions.AspNetCore.DataProtection.Blobs</span><span class="sxs-lookup"><span data-stu-id="8d93d-126">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="8d93d-127">Azure.Extensions.AspNetCore.Configuration.Secrets</span><span class="sxs-lookup"><span data-stu-id="8d93d-127">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="8d93d-128">Новые пакеты используют новую версию пакета SDK для Azure, включающую критические изменения.</span><span class="sxs-lookup"><span data-stu-id="8d93d-128">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="8d93d-129">Шаблоны общего использования не изменяются.</span><span class="sxs-lookup"><span data-stu-id="8d93d-129">The general usage patterns are unchanged.</span></span> <span data-ttu-id="8d93d-130">Некоторые перегрузки и параметры могут отличаться для адаптации к изменениям в базовых API пакета SDK для Azure.</span><span class="sxs-lookup"><span data-stu-id="8d93d-130">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="8d93d-131">Старые пакеты будут:</span><span class="sxs-lookup"><span data-stu-id="8d93d-131">The old packages will:</span></span>

* <span data-ttu-id="8d93d-132">поддерживаться командой ASP.NET Core в течение времени существования версий .NET Core 2.1 и 3.1;</span><span class="sxs-lookup"><span data-stu-id="8d93d-132">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="8d93d-133">исключены в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="8d93d-133">Not be included in .NET 5.</span></span>

<span data-ttu-id="8d93d-134">Для поддержки при обновлении проекта до версии .NET 5 переходите к пакетам `Azure.*`.</span><span class="sxs-lookup"><span data-stu-id="8d93d-134">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8d93d-135">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="8d93d-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
