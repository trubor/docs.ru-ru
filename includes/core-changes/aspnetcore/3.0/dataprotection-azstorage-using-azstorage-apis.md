---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032737"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a><span data-ttu-id="a0d9c-101">Защита данных. DataProtection.Blobs использует новые API службы хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="a0d9c-101">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>

<span data-ttu-id="a0d9c-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` зависит от [библиотек службы хранилища Azure](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="a0d9c-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="a0d9c-103">Эти библиотеки переименовали свои сборки, пакеты и пространства имен.</span><span class="sxs-lookup"><span data-stu-id="a0d9c-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="a0d9c-104">Начиная с ASP.NET Core 3.0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` использует новые API и пакеты с префиксом `Azure.Storage.`.</span><span class="sxs-lookup"><span data-stu-id="a0d9c-104">Starting in ASP.NET Core 3.0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` uses the new `Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="a0d9c-105">Если у вас возникли вопросы об API службы хранилища Azure, см. страницу <https://github.com/Azure/azure-storage-net>.</span><span class="sxs-lookup"><span data-stu-id="a0d9c-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="a0d9c-106">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="a0d9c-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a0d9c-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a0d9c-107">Version introduced</span></span>

<span data-ttu-id="a0d9c-108">3.0</span><span class="sxs-lookup"><span data-stu-id="a0d9c-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a0d9c-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="a0d9c-109">Old behavior</span></span>

<span data-ttu-id="a0d9c-110">Пакет ссылался на пакет `WindowsAzure.Storage` NuGet.</span><span class="sxs-lookup"><span data-stu-id="a0d9c-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>
<span data-ttu-id="a0d9c-111">Пакет ссылается на пакет `Microsoft.Azure.Storage.Blob` NuGet.</span><span class="sxs-lookup"><span data-stu-id="a0d9c-111">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a0d9c-112">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="a0d9c-112">New behavior</span></span>

<span data-ttu-id="a0d9c-113">Пакет ссылается на пакет `Azure.Storage.Blob` NuGet.</span><span class="sxs-lookup"><span data-stu-id="a0d9c-113">The package references the `Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a0d9c-114">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="a0d9c-114">Reason for change</span></span>

<span data-ttu-id="a0d9c-115">Это изменение позволяет `Azure.Extensions.AspNetCore.DataProtection.Blobs` переходить к рекомендуемым пакетам службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="a0d9c-115">This change allows `Azure.Extensions.AspNetCore.DataProtection.Blobs` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a0d9c-116">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a0d9c-116">Recommended action</span></span>

<span data-ttu-id="a0d9c-117">Если вам по-прежнему нужно использовать старые API службы хранилища Azure с ASP.NET Core 3.0, добавьте прямую зависимость в пакет [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) или [Microsoft.Azure.Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/).</span><span class="sxs-lookup"><span data-stu-id="a0d9c-117">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the package [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) or [Microsoft.Azure.Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/).</span></span> <span data-ttu-id="a0d9c-118">Этот пакет можно установить вместе с новыми API `Azure.Storage`.</span><span class="sxs-lookup"><span data-stu-id="a0d9c-118">This package can be installed alongside the new `Azure.Storage` APIs.</span></span>

<span data-ttu-id="a0d9c-119">Во многих случаях обновление включает только изменение инструкций `using` для использования новых пространств имен:</span><span class="sxs-lookup"><span data-stu-id="a0d9c-119">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a><span data-ttu-id="a0d9c-120">Категория</span><span class="sxs-lookup"><span data-stu-id="a0d9c-120">Category</span></span>

<span data-ttu-id="a0d9c-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a0d9c-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a0d9c-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a0d9c-122">Affected APIs</span></span>

<span data-ttu-id="a0d9c-123">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="a0d9c-123">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
