---
title: Сравните ASP.NET SignalR и SignalR ASP.NET Core
description: Как ASP.NET Core SignalR отличается от его предшественника, ASP.NET SignalR?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 89236bd0272c8f20cf9838dddefeb9afee1f3d93
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401696"
---
# <a name="compare-aspnet-signalr-and-aspnet-core-signalr"></a><span data-ttu-id="37947-103">Сравните ASP.NET SignalR и SignalR ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="37947-103">Compare ASP.NET SignalR and ASP.NET Core SignalR</span></span>

<span data-ttu-id="37947-104">ASP.NET Core SignalR несовместим с клиентами или серверами, использующими SignalR ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="37947-104">ASP.NET Core SignalR is incompatible with clients or servers using ASP.NET SignalR.</span></span> <span data-ttu-id="37947-105">Необходимо обновить клиенты и сервер, чтобы они использовали ASP.NET Core SignalR.</span><span class="sxs-lookup"><span data-stu-id="37947-105">You'll need to update both clients and server to use ASP.NET Core SignalR.</span></span> <span data-ttu-id="37947-106">Некоторые различия описаны в этом разделе, а полный список доступен в [документах](/aspnet/core/signalr/version-differences). Для ASP.NET Core SignalR требуется .NET Core 2,1 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="37947-106">Some differences are described in this section, while the full list is available in the [docs](/aspnet/core/signalr/version-differences). ASP.NET Core SignalR requires .NET Core 2.1 or greater.</span></span>

## <a name="feature-differences"></a><span data-ttu-id="37947-107">Различия в функциях</span><span class="sxs-lookup"><span data-stu-id="37947-107">Feature differences</span></span>

- <span data-ttu-id="37947-108">ASP.NET SignalR автоматически пытается повторно подключиться к удаленным подключениям; Это поведение является явным согласием для клиентов ASP.NET Core SignalR</span><span class="sxs-lookup"><span data-stu-id="37947-108">ASP.NET SignalR automatically attempts to reconnect dropped connections; this behavior is opt-in for ASP.NET Core SignalR clients</span></span>
- <span data-ttu-id="37947-109">Обе платформы поддерживают JSON; ASP.NET Core SignalR также поддерживает двоичный протокол на основе MessagePack, а также могут быть созданы пользовательские протоколы.</span><span class="sxs-lookup"><span data-stu-id="37947-109">Both frameworks support JSON; ASP.NET Core SignalR also supports a binary protocol based on MessagePack, and custom protocols can be created.</span></span>
- <span data-ttu-id="37947-110">Непостоянное движение кадров, поддерживаемое ASP.NET SignalR, не поддерживается в ASP.NET Core SignalR.</span><span class="sxs-lookup"><span data-stu-id="37947-110">The Forever Frame transport, supported by ASP.NET SignalR, isn't supported in ASP.NET Core SignalR.</span></span>
- <span data-ttu-id="37947-111">ASP.NET Core SignalR необходимо настроить, добавив `services.AddSignalR()` `app.UseEndpoints` в `Startup.ConfigureServices` и `Startup.Configure` соответственно.</span><span class="sxs-lookup"><span data-stu-id="37947-111">ASP.NET Core SignalR must be configured by adding `services.AddSignalR()` and `app.UseEndpoints` in `Startup.ConfigureServices` and `Startup.Configure`, respectively.</span></span>
- <span data-ttu-id="37947-112">Для ASP.NET Core SignalR требуются прикрепленные сеансы; ASP.NET SignalR нет.</span><span class="sxs-lookup"><span data-stu-id="37947-112">ASP.NET Core SignalR requires sticky sessions; ASP.NET SignalR doesn't.</span></span>
- <span data-ttu-id="37947-113">ASP.NET Core упрощает модель подключения; подключения выполняются только в одном концентраторе.</span><span class="sxs-lookup"><span data-stu-id="37947-113">ASP.NET Core simplifies the connection model; connections are only made to a single hub.</span></span>
- <span data-ttu-id="37947-114">ASP.NET Core SignalR поддерживает потоковую передачу данных от концентратора клиенту.</span><span class="sxs-lookup"><span data-stu-id="37947-114">ASP.NET Core SignalR supports streaming data from the hub to the client.</span></span>
- <span data-ttu-id="37947-115">ASP.NET Core SignalR не поддерживает передачу состояния между клиентами и концентратором.</span><span class="sxs-lookup"><span data-stu-id="37947-115">ASP.NET Core SignalR doesn't support passing state between clients and the hub.</span></span>
- <span data-ttu-id="37947-116">`PersistentConnection`Класс не существует в ASP.NET Core SignalR.</span><span class="sxs-lookup"><span data-stu-id="37947-116">The `PersistentConnection` class doesn't exist in ASP.NET Core SignalR.</span></span>
- <span data-ttu-id="37947-117">ASP.NET SignalR поддерживает SQL Server и Redis.</span><span class="sxs-lookup"><span data-stu-id="37947-117">ASP.NET SignalR supports SQL Server and Redis.</span></span> <span data-ttu-id="37947-118">ASP.NET Core SignalR поддерживает [Azure SignalR](/azure/azure-signalr/) и Redis.</span><span class="sxs-lookup"><span data-stu-id="37947-118">ASP.NET Core SignalR supports [Azure SignalR](/azure/azure-signalr/) and Redis.</span></span>

## <a name="references"></a><span data-ttu-id="37947-119">Ссылки</span><span class="sxs-lookup"><span data-stu-id="37947-119">References</span></span>

- [<span data-ttu-id="37947-120">Различия между ASP.NET SignalR и SignalR ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="37947-120">Differences between ASP.NET SignalR and ASP.NET Core SignalR</span></span>](/aspnet/core/signalr/version-differences)
- [<span data-ttu-id="37947-121">Служба SignalR Azure</span><span class="sxs-lookup"><span data-stu-id="37947-121">Azure SignalR Service</span></span>](/azure/azure-signalr/)

>[!div class="step-by-step"]
><span data-ttu-id="37947-122">[Назад](razor-differences.md)
>[Вперед](testing-differences.md)</span><span class="sxs-lookup"><span data-stu-id="37947-122">[Previous](razor-differences.md)
[Next](testing-differences.md)</span></span>
