---
title: PNRP в разработке приложений
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 7c59b2be8384c8f8cc6bbdc4546a678cfe1c538d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263195"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="eb6a6-102">PNRP в разработке приложений</span><span class="sxs-lookup"><span data-stu-id="eb6a6-102">PNRP in Application Development</span></span>

<span data-ttu-id="eb6a6-103">В ОС Windows Vista сетевые приложения могут получать доступ к функциям публикации и разрешения имен через упрощенный программный интерфейс (API) PNRP.</span><span class="sxs-lookup"><span data-stu-id="eb6a6-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="eb6a6-104">Реализация протокола PNRP</span><span class="sxs-lookup"><span data-stu-id="eb6a6-104">Implementing the Peer Name Resolution Protocol</span></span>  

 <span data-ttu-id="eb6a6-105">С помощью упрощенного API PNRP не задаются явно облака для регистрации имен и адресов. Компонент PNRP автоматически определяет соответствующие облака, к которым требуется присоединиться, и адреса для публикации в них.</span><span class="sxs-lookup"><span data-stu-id="eb6a6-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="eb6a6-106">В оптимально упрощенном разрешении имен PNRP в системе Windows Vista PNRP-имена теперь интегрированы в функцию Windows Sockets getaddrinfo().</span><span class="sxs-lookup"><span data-stu-id="eb6a6-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="eb6a6-107">При использовании PNRP для преобразования имени в IPv6-адрес приложения могут пользоваться функцией getaddrinfo() для преобразования полного доменного имени (FQDN) name.prnp.net, в котором name — это имя однорангового узла, которое преобразуется.</span><span class="sxs-lookup"><span data-stu-id="eb6a6-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="eb6a6-108">Домен pnrp.net — это зарезервированный домен в Windows Vista для разрешения имен PNRP.</span><span class="sxs-lookup"><span data-stu-id="eb6a6-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="eb6a6-109">Передача сообщений между одноранговыми приложениями по-прежнему осуществляется с применением базовых архитектур, таких как PeerChannel и [Большие наборы данных и потоковая передача](../wcf/feature-details/large-data-and-streaming.md) WCF.</span><span class="sxs-lookup"><span data-stu-id="eb6a6-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6a6-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="eb6a6-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
