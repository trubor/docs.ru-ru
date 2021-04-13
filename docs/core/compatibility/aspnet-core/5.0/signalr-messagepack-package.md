---
title: Критическое изменение. SignalR. Протокол MessagePack для концентратора перемещен в пакет MessagePack 2.x
description: Сведения о критическом изменении в ASP.NET Core 5.0 — SignalR. Протокол MessagePack для концентратора перемещен в пакет MessagePack 2.x
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 6851c4fdbaab61e7655dd71ba3c21b8835b2b855
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497116"
---
# <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="a169b-103">SignalR. Протокол MessagePack для концентратора перемещен в пакет MessagePack 2.x</span><span class="sxs-lookup"><span data-stu-id="a169b-103">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="a169b-104">[Протокол концентратора MessagePack](/aspnet/core/signalr/messagepackhubprotocol) для ASP.NET Core SignalR использует [пакет NuGet MessagePack](https://www.nuget.org/packages/MessagePack) для сериализации MessagePack.</span><span class="sxs-lookup"><span data-stu-id="a169b-104">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="a169b-105">ASP.NET Core 5.0 обновляет пакет с 1.x до последней версии пакета 2.x.</span><span class="sxs-lookup"><span data-stu-id="a169b-105">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="a169b-106">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span><span class="sxs-lookup"><span data-stu-id="a169b-106">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a169b-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a169b-107">Version introduced</span></span>

<span data-ttu-id="a169b-108">5.0 Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="a169b-108">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a169b-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="a169b-109">Old behavior</span></span>

<span data-ttu-id="a169b-110">Чтобы сериализовать и десериализировать сообщения MessagePack, ASP.NET Core SignalR использовал пакет MessagePack 1.x.</span><span class="sxs-lookup"><span data-stu-id="a169b-110">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="a169b-111">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="a169b-111">New behavior</span></span>

<span data-ttu-id="a169b-112">ASP.NET Core SignalR использует для сериализации и десериализации сообщений MessagePack пакет MessagePack версии 2.x.</span><span class="sxs-lookup"><span data-stu-id="a169b-112">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a169b-113">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="a169b-113">Reason for change</span></span>

<span data-ttu-id="a169b-114">Последние улучшения в пакете MessagePack версии 2.x принесли полезные функции.</span><span class="sxs-lookup"><span data-stu-id="a169b-114">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a169b-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a169b-115">Recommended action</span></span>

<span data-ttu-id="a169b-116">Это критическое изменение применяется в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="a169b-116">This breaking change applies when:</span></span>

* <span data-ttu-id="a169b-117">При установке или настройке значений на <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span><span class="sxs-lookup"><span data-stu-id="a169b-117">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="a169b-118">При использовании API MessagePack напрямую и протокола концентратора ASP.NET Core MessagePack SignalR в одном проекте.</span><span class="sxs-lookup"><span data-stu-id="a169b-118">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="a169b-119">Вместо предыдущей версии будет загружена новая версия.</span><span class="sxs-lookup"><span data-stu-id="a169b-119">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="a169b-120">Руководство по миграции от авторов пакетов см. в статье [Переход с MessagePack версии 1.x на MessagePack версии 2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span><span class="sxs-lookup"><span data-stu-id="a169b-120">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="a169b-121">Затрагиваются некоторые аспекты сериализации и десериализации сообщений.</span><span class="sxs-lookup"><span data-stu-id="a169b-121">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="a169b-122">В частности, имеются [изменения поведения, определяющие порядок сериализации значений DateTime](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span><span class="sxs-lookup"><span data-stu-id="a169b-122">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a169b-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a169b-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
