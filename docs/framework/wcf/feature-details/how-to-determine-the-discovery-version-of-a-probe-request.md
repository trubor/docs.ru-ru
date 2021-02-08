---
description: Дополнительные сведения см. в статье как определить версию обнаружения запроса на пробу.
title: Как определить версию обнаружения зондирующего запроса
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: c41283cb84d75dd2dbf7e86da0dec075ab8b6635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793796"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="4a89a-103">Как определить версию обнаружения зондирующего запроса</span><span class="sxs-lookup"><span data-stu-id="4a89a-103">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="4a89a-104">Прокси-сервер обнаружения может выдать несколько конечных точек обнаружения с помощью разных версий обнаружения.</span><span class="sxs-lookup"><span data-stu-id="4a89a-104">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="4a89a-105">Когда запрос проверки многоадресной рассылки UDP поступает на прокси-сервер, прокси-сервер должен ответить с сообщением о подавлении многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="4a89a-105">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="4a89a-106">Для этого ему пришлось бы узнать версию обнаружения запроса.</span><span class="sxs-lookup"><span data-stu-id="4a89a-106">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="4a89a-107">Определение версии обнаружения зондирующего запроса</span><span class="sxs-lookup"><span data-stu-id="4a89a-107">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="4a89a-108">В методе, отвечающем на запрос пробы (например <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> ,), используйте свойство static для поиска <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="4a89a-108">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="4a89a-109">См. также</span><span class="sxs-lookup"><span data-stu-id="4a89a-109">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="4a89a-110">Реализация прокси-сервера обнаружения</span><span class="sxs-lookup"><span data-stu-id="4a89a-110">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)
