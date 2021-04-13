---
title: Критическое изменение. Kestrel. Транспорт Libuv помечен как устаревший
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Kestrel. Транспорт Libuv помечен как устаревший
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7edec666df729edbffe60b6017a2b8ee5f46ae67
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497636"
---
# <a name="kestrel-libuv-transport-marked-as-obsolete"></a><span data-ttu-id="8a511-103">Kestrel. Транспорт Libuv помечен как устаревший</span><span class="sxs-lookup"><span data-stu-id="8a511-103">Kestrel: Libuv transport marked as obsolete</span></span>

<span data-ttu-id="8a511-104">В более ранних версиях ASP.NET Core в качестве сведений о реализации асинхронного ввода и вывода использовались Libuv.</span><span class="sxs-lookup"><span data-stu-id="8a511-104">Earlier versions of ASP.NET Core used Libuv as an implementation detail of how asynchronous input and output was performed.</span></span> <span data-ttu-id="8a511-105">В ASP.NET Core 2.0 был разработан альтернативный транспорт на основе <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="8a511-105">In ASP.NET Core 2.0, an alternative, <xref:System.Net.Sockets.Socket>-based transport was developed.</span></span> <span data-ttu-id="8a511-106">В ASP.NET Core 2.1 Kestrel переключается на использование транспорта на основе `Socket` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8a511-106">In ASP.NET Core 2.1, Kestrel switched to using the `Socket`-based transport by default.</span></span> <span data-ttu-id="8a511-107">Поддержка Libuv сохранялась по соображениям совместимости.</span><span class="sxs-lookup"><span data-stu-id="8a511-107">Libuv support was maintained for compatibility reasons.</span></span>

<span data-ttu-id="8a511-108">На этом этапе использование транспорта на основе `Socket`гораздо более распространено, чем транспорт Libuv.</span><span class="sxs-lookup"><span data-stu-id="8a511-108">At this point, use of the `Socket`-based transport is far more common than the Libuv transport.</span></span> <span data-ttu-id="8a511-109">Следовательно, поддержка Libuv помечена как устаревшая в .NET 5.0 и будет полностью удалена в .NET 6.0.</span><span class="sxs-lookup"><span data-stu-id="8a511-109">Consequently, Libuv support is marked as obsolete in .NET 5.0 and will be removed entirely in .NET 6.0.</span></span>

<span data-ttu-id="8a511-110">В рамках этого изменения поддержка Libuv для новых платформ операционной системы (например, Windows ARM64) не будет добавлена в .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="8a511-110">As part of this change, Libuv support for new operating system platforms (like Windows ARM64) won't be added in the .NET 5.0 timeframe.</span></span>

<span data-ttu-id="8a511-111">Сведения о критических проблемах, требующих использования транспорта Libuv, см. в GitHub в разделе [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span><span class="sxs-lookup"><span data-stu-id="8a511-111">For discussion on blocking issues that require the use of the Libuv transport, see the GitHub issue at [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8a511-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="8a511-112">Version introduced</span></span>

<span data-ttu-id="8a511-113">5.0, предварительная версия 8</span><span class="sxs-lookup"><span data-stu-id="8a511-113">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="8a511-114">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="8a511-114">Old behavior</span></span>

<span data-ttu-id="8a511-115">API-интерфейсы Libuv не помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="8a511-115">The Libuv APIs aren't marked as obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="8a511-116">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="8a511-116">New behavior</span></span>

<span data-ttu-id="8a511-117">API-интерфейсы Libuv помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="8a511-117">The Libuv APIs are marked as obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="8a511-118">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="8a511-118">Reason for change</span></span>

<span data-ttu-id="8a511-119">По умолчанию используется транспорт на основе `Socket`.</span><span class="sxs-lookup"><span data-stu-id="8a511-119">The `Socket`-based transport is the default.</span></span> <span data-ttu-id="8a511-120">Нет никаких причин для продолжения использования транспорта Libuv.</span><span class="sxs-lookup"><span data-stu-id="8a511-120">There aren't any compelling reasons to continue using the Libuv transport.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8a511-121">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="8a511-121">Recommended action</span></span>

<span data-ttu-id="8a511-122">Прекращение использования [пакета Libuv](https://www.nuget.org/packages/Libuv) и методов расширения.</span><span class="sxs-lookup"><span data-stu-id="8a511-122">Discontinue use of the [Libuv package](https://www.nuget.org/packages/Libuv) and extension methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8a511-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="8a511-123">Affected APIs</span></span>

- [<span data-ttu-id="8a511-124">WebHostBuilderLibuvExtensions</span><span class="sxs-lookup"><span data-stu-id="8a511-124">WebHostBuilderLibuvExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [<span data-ttu-id="8a511-125">WebHostBuilderLibuvExtensions.UseLibuv</span><span class="sxs-lookup"><span data-stu-id="8a511-125">WebHostBuilderLibuvExtensions.UseLibuv</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [<span data-ttu-id="8a511-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span><span class="sxs-lookup"><span data-stu-id="8a511-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [<span data-ttu-id="8a511-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span><span class="sxs-lookup"><span data-stu-id="8a511-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [<span data-ttu-id="8a511-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span><span class="sxs-lookup"><span data-stu-id="8a511-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [<span data-ttu-id="8a511-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span><span class="sxs-lookup"><span data-stu-id="8a511-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [<span data-ttu-id="8a511-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span><span class="sxs-lookup"><span data-stu-id="8a511-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
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
