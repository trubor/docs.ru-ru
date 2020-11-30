---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032718"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="88e90-101">Кэширование: свойство CompactOnMemoryPressure удалено</span><span class="sxs-lookup"><span data-stu-id="88e90-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="88e90-102">В выпуске ASP.NET Core 3.0 недоступны [устаревшие API MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span><span class="sxs-lookup"><span data-stu-id="88e90-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="88e90-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="88e90-103">Change description</span></span>

<span data-ttu-id="88e90-104">Это изменение реализовано в рамках исправления [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span><span class="sxs-lookup"><span data-stu-id="88e90-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="88e90-105">Обсуждение этого вопроса см. на странице [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="88e90-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="88e90-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="88e90-106">Version introduced</span></span>

<span data-ttu-id="88e90-107">3.0</span><span class="sxs-lookup"><span data-stu-id="88e90-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="88e90-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="88e90-108">Old behavior</span></span>

<span data-ttu-id="88e90-109">Свойство `MemoryCacheOptions.CompactOnMemoryPressure` было доступно.</span><span class="sxs-lookup"><span data-stu-id="88e90-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="88e90-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="88e90-110">New behavior</span></span>

<span data-ttu-id="88e90-111">Свойство `MemoryCacheOptions.CompactOnMemoryPressure` было удалено.</span><span class="sxs-lookup"><span data-stu-id="88e90-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="88e90-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="88e90-112">Reason for change</span></span>

<span data-ttu-id="88e90-113">Автоматическое сжатие кэша приводило к возникновению проблем.</span><span class="sxs-lookup"><span data-stu-id="88e90-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="88e90-114">Чтобы не допустить непредвиденное поведение, сжимайте кэш только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="88e90-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="88e90-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="88e90-115">Recommended action</span></span>

<span data-ttu-id="88e90-116">Чтобы сжать кэш, выполните приведение с понижением к `MemoryCache` и вызовите `Compact` при необходимости.</span><span class="sxs-lookup"><span data-stu-id="88e90-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="88e90-117">Категория</span><span class="sxs-lookup"><span data-stu-id="88e90-117">Category</span></span>

<span data-ttu-id="88e90-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="88e90-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="88e90-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="88e90-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
