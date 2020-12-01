---
title: Облака PNRP
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: 60b6fb44116fe2d8af50fb0b310615b3b962977b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263208"
---
# <a name="pnrp-clouds"></a><span data-ttu-id="fbfc5-102">Облака PNRP</span><span class="sxs-lookup"><span data-stu-id="fbfc5-102">PNRP Clouds</span></span>

<span data-ttu-id="fbfc5-103">"Облако" PNRP представляет собой набор узлов, которые могут взаимодействовать друг с другом по сети.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-103">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="fbfc5-104">Синонимами термина "облако" являются "одноранговая сеть" и "одноранговый граф".</span><span class="sxs-lookup"><span data-stu-id="fbfc5-104">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="fbfc5-105">Взаимодействие между узлами в разных облаках невозможно.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-105">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="fbfc5-106">Экземпляр <xref:System.Net.PeerToPeer.Cloud> уникальным образом идентифицируется по имени, в котором учитывается регистр символов.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-106">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="fbfc5-107">Один одноранговый узел может быть подключен к нескольким облакам.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-107">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="fbfc5-108">Облака тесно связаны с сетевыми интерфейсами.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-108">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="fbfc5-109">На многосетевом компьютере с двумя сетевыми адаптерами, подключенными к разным сетям, будет возвращено три облака: по одному для каждого локального адреса канала для интерфейса, а также общее глобальное облако.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-109">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="fbfc5-110">Протокол PNRP использует три "области" облака, под которыми понимаются группы компьютеров, доступные друг другу для поиска:</span><span class="sxs-lookup"><span data-stu-id="fbfc5-110">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
- <span data-ttu-id="fbfc5-111">Глобальное облако соответствует пространству глобальных IPv6-адресов, которые представляют все компьютеры с IPv6-адресами в Интернете.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-111">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="fbfc5-112">Существует только одно глобальное облако.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-112">There is only a single global cloud.</span></span>  
  
- <span data-ttu-id="fbfc5-113">Локальное облако канала соответствует пространству локальных IPv6-адресов канала и локальных адресов канала.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-113">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="fbfc5-114">Локальное облако привязано к конкретному каналу, который обычно совпадает с локально подключенной сетью.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-114">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="fbfc5-115">Локальных облаков может быть несколько.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-115">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="fbfc5-116">Локальное облако сайта соответствует пространству IPv6-адресов сайта и локальных адресов сайта.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-116">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="fbfc5-117">Это облако по-прежнему поддерживается протоколом PNRP, однако считается устаревшим.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-117">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="fbfc5-118">Облака</span><span class="sxs-lookup"><span data-stu-id="fbfc5-118">Clouds</span></span>  

 <span data-ttu-id="fbfc5-119">Облака PNRP представлены экземплярами класса <xref:System.Net.PeerToPeer.Cloud>.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-119">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="fbfc5-120">Группы облаков, используемых одноранговыми узлами, представлены экземплярами класса <xref:System.Net.PeerToPeer.CloudCollection>.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-120">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="fbfc5-121">Коллекции облаков PNRP, известных текущему одноранговому узлу, можно получить с помощью статического метода <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-121">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="fbfc5-122">Отдельные облака имеют уникальные имена, представленные в виде строки в формате Юникод длиной 256 символов.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-122">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="fbfc5-123">Эти имена вместе с описываемыми выше областями используются для построения уникальных экземпляров класса Cloud.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-123">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="fbfc5-124">Эти экземпляры могут быть сериализованы и воссозданы для постоянного использования.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-124">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="fbfc5-125">После создания или получения экземпляра класса Cloud с его помощью можно регистрировать имена известных одноранговых узлов, которые будут образовывать одноранговую сеть.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-125">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbfc5-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fbfc5-126">See also</span></span>

- <xref:System.Net.PeerToPeer.Cloud>
- [<span data-ttu-id="fbfc5-127">Протокол PNRP</span><span class="sxs-lookup"><span data-stu-id="fbfc5-127">Peer Name Resolution Protocol</span></span>](peer-name-resolution-protocol.md)
