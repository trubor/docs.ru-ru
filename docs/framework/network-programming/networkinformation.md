---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 550555be7cc95cafebabfd3ac230ced024a9202c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261622"
---
# <a name="networkinformation"></a><span data-ttu-id="b06c6-102">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="b06c6-102">NetworkInformation</span></span>

<span data-ttu-id="b06c6-103">Пространство имен <xref:System.Net.NetworkInformation> содержит классы для программного сбора информации о событиях, изменениях, статистике и свойствах сети.</span><span class="sxs-lookup"><span data-stu-id="b06c6-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="b06c6-104">Можно также определить доступность удаленного узла с помощью класса <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b06c6-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="b06c6-105">Доступность сети и события</span><span class="sxs-lookup"><span data-stu-id="b06c6-105">Network Availability and Events</span></span>  

 <span data-ttu-id="b06c6-106">Класс <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> позволяет определить, изменились ли адрес или состояние доступности сети.</span><span class="sxs-lookup"><span data-stu-id="b06c6-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="b06c6-107">Чтобы использовать этот класс, создайте обработчик событий для обработки этого изменения и свяжите его с <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> или <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="b06c6-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="b06c6-108">Дополнительные сведения см. в разделе [Практическое руководство. Определение доступности сети и изменений адреса](how-to-detect-network-availability-and-address-changes.md).</span><span class="sxs-lookup"><span data-stu-id="b06c6-108">For more information, see [How to: Detect Network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="b06c6-109">Статистика сети и свойства</span><span class="sxs-lookup"><span data-stu-id="b06c6-109">Network Statistics and Properties</span></span>  

 <span data-ttu-id="b06c6-110">Вы можете собирать статистику сетевой активности и сведения о свойствах на основе интерфейса или протокола.</span><span class="sxs-lookup"><span data-stu-id="b06c6-110">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="b06c6-111">Классы <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType> и <xref:System.Net.NetworkInformation.PhysicalAddress> предоставляют информацию о конкретном сетевом интерфейсе, а классы <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics> и <xref:System.Net.NetworkInformation.UdpStatistics> — информацию о пакетах уровня 3 и 4.</span><span class="sxs-lookup"><span data-stu-id="b06c6-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="b06c6-112">Дополнительные сведения см. в разделе [Практическое руководство. Получение информации об интерфейсах и протоколах](how-to-get-interface-and-protocol-information.md).</span><span class="sxs-lookup"><span data-stu-id="b06c6-112">For more information, see [How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="b06c6-113">Определение доступности удаленного узла</span><span class="sxs-lookup"><span data-stu-id="b06c6-113">Determine if a Remote Host is Reachable</span></span>  

 <span data-ttu-id="b06c6-114">С помощью класса <xref:System.Net.NetworkInformation.Ping> можно определить, работает ли удаленный узел, находится ли он в сети и возможен ли доступ к нему.</span><span class="sxs-lookup"><span data-stu-id="b06c6-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="b06c6-115">Дополнительные сведения см. в статье [Практическое руководство. Проверка связи с узлом](how-to-ping-a-host.md).</span><span class="sxs-lookup"><span data-stu-id="b06c6-115">For more information, see [How to: Ping a Host](how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06c6-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b06c6-116">See also</span></span>

- [<span data-ttu-id="b06c6-117">Примеры сетевого программирования</span><span class="sxs-lookup"><span data-stu-id="b06c6-117">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
