---
title: Балансировка нагрузки gRPC-gRPC для разработчиков WCF
description: Выбор подсистемы балансировки нагрузки для работы со службами gRPC Services.
ms.date: 12/15/2020
ms.openlocfilehash: 55f61608dce1f159b11d7265a47938ba49e9e188
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938589"
---
# <a name="load-balancing-grpc"></a><span data-ttu-id="4bdc3-103">GRPC балансировки нагрузки</span><span class="sxs-lookup"><span data-stu-id="4bdc3-103">Load balancing gRPC</span></span>

<span data-ttu-id="4bdc3-104">Типичное развертывание приложения gRPC включает ряд идентичных экземпляров службы, обеспечивая устойчивость и горизонтальную масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="4bdc3-105">Балансировка нагрузки распределяет входящие запросы между этими экземплярами, чтобы обеспечить полное использование всех доступных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-105">Load balancing distributes incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="4bdc3-106">Чтобы обеспечить невидимость этой балансировки нагрузки для клиента, обычно используется сервер балансировщика нагрузки прокси-сервера для обработки запросов от клиентов и их маршрутизации к экземплярам серверной части.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="4bdc3-107">Подсистемы балансировки нагрузки классифицируются в соответствии с *уровнем* , с которым они работают.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="4bdc3-108">Подсистемы балансировки нагрузки уровня 4 работают на *транспортном* уровне, например с сокетами TCP, соединениями и пакетами.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections, and packets.</span></span> <span data-ttu-id="4bdc3-109">Подсистемы балансировки нагрузки уровня 7 работают на уровне *приложения* , специально обрабатывая запросы HTTP/2 для приложений gRPC.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="4bdc3-110">Подсистемы балансировки нагрузки на уровне 4</span><span class="sxs-lookup"><span data-stu-id="4bdc3-110">L4 load balancers</span></span>

<span data-ttu-id="4bdc3-111">Балансировщик нагрузки уровня 4 принимает запрос TCP-соединения от клиента, открывает другое соединение с одним из внутренних экземпляров и копирует данные между двумя соединениями без реальной обработки.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="4bdc3-112">Параметр уровня "уровень 4" обеспечивает высокую производительность и низкую задержку, но с небольшим управлением или аналитикой.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-112">L4 offers excellent performance and low latency, but with little control or intelligence.</span></span> <span data-ttu-id="4bdc3-113">Пока клиент остается открытым, все запросы будут направлены на один и тот же экземпляр серверной части.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

 <span data-ttu-id="4bdc3-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) является примером балансировщика нагрузки на уровне 4.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) is an example of an L4 load balancer.</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="4bdc3-115">Подсистемы балансировки нагрузки уровня 7</span><span class="sxs-lookup"><span data-stu-id="4bdc3-115">L7 load balancers</span></span>

<span data-ttu-id="4bdc3-116">Балансировщик нагрузки уровня "на уровне 7" анализирует входящие запросы HTTP/2 и передает их на экземпляры серверной части по запросу, независимо от того, как долго соединение удерживает клиент.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="4bdc3-117">Примеры подсистем балансировки нагрузки уровня 7:</span><span class="sxs-lookup"><span data-stu-id="4bdc3-117">Examples of L7 load balancers:</span></span>

- [<span data-ttu-id="4bdc3-118">NGINX</span><span class="sxs-lookup"><span data-stu-id="4bdc3-118">NGINX</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="4bdc3-119">HAProxy</span><span class="sxs-lookup"><span data-stu-id="4bdc3-119">HAProxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="4bdc3-120">траефик</span><span class="sxs-lookup"><span data-stu-id="4bdc3-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="4bdc3-121">Как правило, подсистемы балансировки нагрузки уровня "на уровне 7" являются лучшим выбором для gRPC и других приложений HTTP/2 (и для приложений HTTP, как правило, на самом деле).</span><span class="sxs-lookup"><span data-stu-id="4bdc3-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="4bdc3-122">Подсистемы балансировки нагрузки уровня 4 будут *работать* с gRPC приложениями, но они в первую очередь полезны, когда важны низкая задержка и низкая нагрузка.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-122">L4 load balancers will *work* with gRPC applications, but they're primarily useful when low latency and low overhead are important.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4bdc3-123">На момент написания этой статьи некоторые подсистемы балансировки нагрузки уровня 7 не поддерживают все части спецификации HTTP/2, необходимые службам gRPC Services, например конечные заголовки.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-123">At the time of this writing, some L7 load balancers don't support all the parts of the HTTP/2 specification that are required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="4bdc3-124">Если вы используете TLS-шифрование, подсистемы балансировки нагрузки могут завершить TLS-подключение и передать незашифрованные запросы серверному приложению или передать зашифрованный запрос вместе.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-124">If you're using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or they can pass the encrypted request along.</span></span> <span data-ttu-id="4bdc3-125">В любом случае балансировщик нагрузки должен быть настроен с помощью открытого и закрытого ключей сервера, чтобы можно было расшифровывать запросы на обработку.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-125">Either way, the load balancer will need to be configured with the server's public and private key so it can decrypt requests for processing.</span></span>

<span data-ttu-id="4bdc3-126">См. документацию по предпочтительной подсистеме балансировки нагрузки, чтобы узнать, как настроить его для обработки запросов HTTP/2 к серверным службам.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-126">See to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="4bdc3-127">Балансировка нагрузки в Kubernetes</span><span class="sxs-lookup"><span data-stu-id="4bdc3-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="4bdc3-128">Описание балансировки нагрузки между внутренними службами в Kubernetes см. в [разделе о](service-mesh.md) связях между службами.</span><span class="sxs-lookup"><span data-stu-id="4bdc3-128">See [the section on service meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4bdc3-129">[Назад](service-mesh.md)
>[Вперед](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="4bdc3-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>
