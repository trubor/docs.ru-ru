---
title: Критическое изменение. Kestrel. Транспорт Libuv помечен как устаревший
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Kestrel. Транспорт Libuv помечен как устаревший
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f66b9b646671e07957e6d30a95333d392eb29617
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759775"
---
# <a name="kestrel-libuv-transport-marked-as-obsolete"></a><span data-ttu-id="7cc7b-103">Kestrel. Транспорт Libuv помечен как устаревший</span><span class="sxs-lookup"><span data-stu-id="7cc7b-103">Kestrel: Libuv transport marked as obsolete</span></span>

<span data-ttu-id="7cc7b-104">В более ранних версиях ASP.NET Core в качестве сведений о реализации асинхронного ввода и вывода использовались Libuv.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-104">Earlier versions of ASP.NET Core used Libuv as an implementation detail of how asynchronous input and output was performed.</span></span> <span data-ttu-id="7cc7b-105">В ASP.NET Core 2.0 был разработан альтернативный транспорт на основе <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-105">In ASP.NET Core 2.0, an alternative, <xref:System.Net.Sockets.Socket>-based transport was developed.</span></span> <span data-ttu-id="7cc7b-106">В ASP.NET Core 2.1 Kestrel переключается на использование транспорта на основе `Socket` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-106">In ASP.NET Core 2.1, Kestrel switched to using the `Socket`-based transport by default.</span></span> <span data-ttu-id="7cc7b-107">Поддержка Libuv сохранялась по соображениям совместимости.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-107">Libuv support was maintained for compatibility reasons.</span></span>

<span data-ttu-id="7cc7b-108">На этом этапе использование транспорта на основе `Socket`гораздо более распространено, чем транспорт Libuv.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-108">At this point, use of the `Socket`-based transport is far more common than the Libuv transport.</span></span> <span data-ttu-id="7cc7b-109">Следовательно, поддержка Libuv помечена как устаревшая в .NET 5.0 и будет полностью удалена в .NET 6.0.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-109">Consequently, Libuv support is marked as obsolete in .NET 5.0 and will be removed entirely in .NET 6.0.</span></span>

<span data-ttu-id="7cc7b-110">В рамках этого изменения поддержка Libuv для новых платформ операционной системы (например, Windows ARM64) не будет добавлена в .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-110">As part of this change, Libuv support for new operating system platforms (like Windows ARM64) won't be added in the .NET 5.0 timeframe.</span></span>

<span data-ttu-id="7cc7b-111">Сведения о критических проблемах, требующих использования транспорта Libuv, см. в GitHub в разделе [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span><span class="sxs-lookup"><span data-stu-id="7cc7b-111">For discussion on blocking issues that require the use of the Libuv transport, see the GitHub issue at [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7cc7b-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="7cc7b-112">Version introduced</span></span>

<span data-ttu-id="7cc7b-113">5.0, предварительная версия 8</span><span class="sxs-lookup"><span data-stu-id="7cc7b-113">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="7cc7b-114">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="7cc7b-114">Old behavior</span></span>

<span data-ttu-id="7cc7b-115">API-интерфейсы Libuv не помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-115">The Libuv APIs aren't marked as obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="7cc7b-116">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="7cc7b-116">New behavior</span></span>

<span data-ttu-id="7cc7b-117">API-интерфейсы Libuv помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-117">The Libuv APIs are marked as obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7cc7b-118">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="7cc7b-118">Reason for change</span></span>

<span data-ttu-id="7cc7b-119">По умолчанию используется транспорт на основе `Socket`.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-119">The `Socket`-based transport is the default.</span></span> <span data-ttu-id="7cc7b-120">Нет никаких причин для продолжения использования транспорта Libuv.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-120">There aren't any compelling reasons to continue using the Libuv transport.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7cc7b-121">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="7cc7b-121">Recommended action</span></span>

<span data-ttu-id="7cc7b-122">Прекращение использования [пакета Libuv](https://www.nuget.org/packages/Libuv) и методов расширения.</span><span class="sxs-lookup"><span data-stu-id="7cc7b-122">Discontinue use of the [Libuv package](https://www.nuget.org/packages/Libuv) and extension methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7cc7b-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7cc7b-123">Affected APIs</span></span>

- [<span data-ttu-id="7cc7b-124">WebHostBuilderLibuvExtensions</span><span class="sxs-lookup"><span data-stu-id="7cc7b-124">WebHostBuilderLibuvExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [<span data-ttu-id="7cc7b-125">WebHostBuilderLibuvExtensions.UseLibuv</span><span class="sxs-lookup"><span data-stu-id="7cc7b-125">WebHostBuilderLibuvExtensions.UseLibuv</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [<span data-ttu-id="7cc7b-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span><span class="sxs-lookup"><span data-stu-id="7cc7b-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [<span data-ttu-id="7cc7b-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span><span class="sxs-lookup"><span data-stu-id="7cc7b-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [<span data-ttu-id="7cc7b-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span><span class="sxs-lookup"><span data-stu-id="7cc7b-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [<span data-ttu-id="7cc7b-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span><span class="sxs-lookup"><span data-stu-id="7cc7b-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [<span data-ttu-id="7cc7b-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span><span class="sxs-lookup"><span data-stu-id="7cc7b-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
