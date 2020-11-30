---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032753"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="e7f99-101">Размещение. Типы IHostingEnvironment и IApplicationLifetime помечены как устаревшие и удалены</span><span class="sxs-lookup"><span data-stu-id="e7f99-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="e7f99-102">Введены новые типы для замены типов `IHostingEnvironment` и `IApplicationLifetime`.</span><span class="sxs-lookup"><span data-stu-id="e7f99-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e7f99-103">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="e7f99-103">Version introduced</span></span>

<span data-ttu-id="e7f99-104">3.0</span><span class="sxs-lookup"><span data-stu-id="e7f99-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e7f99-105">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="e7f99-105">Old behavior</span></span>

<span data-ttu-id="e7f99-106">ранее существовали разные типы `IHostingEnvironment` и `IApplicationLifetime` из `Microsoft.Extensions.Hosting` и `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="e7f99-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e7f99-107">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="e7f99-107">New behavior</span></span>

<span data-ttu-id="e7f99-108">Старые типы помечены как устаревшие и заменены новыми типами.</span><span class="sxs-lookup"><span data-stu-id="e7f99-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e7f99-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="e7f99-109">Reason for change</span></span>

<span data-ttu-id="e7f99-110">Когда `Microsoft.Extensions.Hosting` был введен в ASP.NET Core 2.1, несколько типов, например `IHostingEnvironment` и `IApplicationLifetime`, были скопированы из `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="e7f99-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="e7f99-111">Некоторые изменения в ASP.NET Core 3.0 привели к том, что в приложения одновременно включаются пространства имен `Microsoft.Extensions.Hosting` и `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="e7f99-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="e7f99-112">Любое использование этих дублирующихся типов приводило к ошибке компилятора "двусмысленная ссылка" при использовании обоих пространств имен.</span><span class="sxs-lookup"><span data-stu-id="e7f99-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e7f99-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="e7f99-113">Recommended action</span></span>

<span data-ttu-id="e7f99-114">Замените любые использования старых типов новыми типами, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="e7f99-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="e7f99-115">**Устаревшие типы (предупреждение):**</span><span class="sxs-lookup"><span data-stu-id="e7f99-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="e7f99-116">**Новые типы:**</span><span class="sxs-lookup"><span data-stu-id="e7f99-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="e7f99-117">Новые методы расширения `IHostEnvironment` `IsDevelopment` и `IsProduction` относятся к пространству имен `Microsoft.Extensions.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="e7f99-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="e7f99-118">Возможно, потребуется добавить в проект это пространство имен.</span><span class="sxs-lookup"><span data-stu-id="e7f99-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="e7f99-119">Категория</span><span class="sxs-lookup"><span data-stu-id="e7f99-119">Category</span></span>

<span data-ttu-id="e7f99-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e7f99-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7f99-121">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="e7f99-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
