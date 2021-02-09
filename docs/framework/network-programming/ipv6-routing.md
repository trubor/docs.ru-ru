---
description: 'Узнайте подробнее о: Маршрутизация IPv6'
title: Маршрутизация IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 75499a7380ab0ea7c38c83a6407a0c2a269b5fce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672040"
---
# <a name="ipv6-routing"></a><span data-ttu-id="68f5f-103">Маршрутизация IPv6</span><span class="sxs-lookup"><span data-stu-id="68f5f-103">IPv6 Routing</span></span>

<span data-ttu-id="68f5f-104">Гибкий механизм маршрутизации является преимуществом IPv6.</span><span class="sxs-lookup"><span data-stu-id="68f5f-104">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="68f5f-105">Способ выделения идентификаторов сетей IPv4 требует от маршрутизаторов, находящихся в магистральных каналах в Интернете, поддержки больших таблиц маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="68f5f-105">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="68f5f-106">Эти маршрутизаторы должны знать все маршруты, чтобы пересылать пакеты, которые могут быть направлены на любой узел в Интернете.</span><span class="sxs-lookup"><span data-stu-id="68f5f-106">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="68f5f-107">Благодаря возможности объединения адресов IPv6 обеспечивает гибкую адресацию и существенно сокращает размер таблиц маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="68f5f-107">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="68f5f-108">В этой новой архитектуре адресации промежуточные маршрутизаторы должны отслеживать локальную часть своей сети для правильной пересылки сообщений.</span><span class="sxs-lookup"><span data-stu-id="68f5f-108">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="68f5f-109">Обнаружение окружения</span><span class="sxs-lookup"><span data-stu-id="68f5f-109">Neighbor Discovery</span></span>  

 <span data-ttu-id="68f5f-110">Ниже приведены некоторые функции, предоставляемые обнаружением окружения.</span><span class="sxs-lookup"><span data-stu-id="68f5f-110">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="68f5f-111">Обнаружение маршрутизаторов.</span><span class="sxs-lookup"><span data-stu-id="68f5f-111">Router discovery.</span></span> <span data-ttu-id="68f5f-112">Это позволяет узлам определять локальные маршрутизаторы.</span><span class="sxs-lookup"><span data-stu-id="68f5f-112">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="68f5f-113">Разрешение адресов.</span><span class="sxs-lookup"><span data-stu-id="68f5f-113">Address resolution.</span></span> <span data-ttu-id="68f5f-114">Это позволяет узлам разрешать для адрес канального уровня для соответствующего адреса следующего прыжка (замена протокола ARP).</span><span class="sxs-lookup"><span data-stu-id="68f5f-114">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="68f5f-115">Автоматическая настройка адресов.</span><span class="sxs-lookup"><span data-stu-id="68f5f-115">Address auto-configuration.</span></span> <span data-ttu-id="68f5f-116">Это позволяет узлам выполнять автоматическую настройку адресов локальных узлов и глобальных адресов.</span><span class="sxs-lookup"><span data-stu-id="68f5f-116">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="68f5f-117">Обнаружение окружения использует ICMPv6-сообщения, которые включают:</span><span class="sxs-lookup"><span data-stu-id="68f5f-117">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="68f5f-118">Объявление маршрутизаторов.</span><span class="sxs-lookup"><span data-stu-id="68f5f-118">Router advertisement.</span></span> <span data-ttu-id="68f5f-119">Отправляется маршрутизатором на псевдопериодической основе или в ответ на запрос маршрутизаторов.</span><span class="sxs-lookup"><span data-stu-id="68f5f-119">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="68f5f-120">Маршрутизаторы IPv6 используют объявления маршрутизаторов для сообщения о своей доступности, для указания префиксов адресов и других параметров.</span><span class="sxs-lookup"><span data-stu-id="68f5f-120">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="68f5f-121">Запрос маршрутизаторов.</span><span class="sxs-lookup"><span data-stu-id="68f5f-121">Router solicitation.</span></span> <span data-ttu-id="68f5f-122">Отправляется узлом для запроса того, чтобы маршрутизаторы в канале немедленно отправили объявление маршрутизаторов.</span><span class="sxs-lookup"><span data-stu-id="68f5f-122">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="68f5f-123">Запрос поиска соседей.</span><span class="sxs-lookup"><span data-stu-id="68f5f-123">Neighbor solicitation.</span></span> <span data-ttu-id="68f5f-124">Отправляется узлами для разрешения адресов, обнаружения повторяющихся адресов или для проверки доступности соседей.</span><span class="sxs-lookup"><span data-stu-id="68f5f-124">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="68f5f-125">Объявление соседей.</span><span class="sxs-lookup"><span data-stu-id="68f5f-125">Neighbor advertisement.</span></span> <span data-ttu-id="68f5f-126">Рассылается узлами в ответ на запрос поиска соседей или для предупреждения соседей об изменении адреса канального уровня.</span><span class="sxs-lookup"><span data-stu-id="68f5f-126">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="68f5f-127">Перенаправление.</span><span class="sxs-lookup"><span data-stu-id="68f5f-127">Redirect.</span></span> <span data-ttu-id="68f5f-128">Отправляется маршрутизаторами, чтобы указать лучший адрес следующего прыжка для конкретного назначения для отправляющего узла.</span><span class="sxs-lookup"><span data-stu-id="68f5f-128">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f5f-129">См. также</span><span class="sxs-lookup"><span data-stu-id="68f5f-129">See also</span></span>

- [<span data-ttu-id="68f5f-130">Протокол IP версии 6</span><span class="sxs-lookup"><span data-stu-id="68f5f-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="68f5f-131">Сокеты</span><span class="sxs-lookup"><span data-stu-id="68f5f-131">Sockets</span></span>](sockets.md)
