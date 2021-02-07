---
description: 'Дополнительные сведения: размещение'
title: Hosting2
ms.date: 03/30/2017
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
ms.openlocfilehash: 4371cbb3b65242235ad0bb26c2b99b8e35d729c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742970"
---
# <a name="hosting"></a><span data-ttu-id="d52b0-103">Hosting</span><span class="sxs-lookup"><span data-stu-id="d52b0-103">Hosting</span></span>

<span data-ttu-id="d52b0-104">В подразделах этого раздела описано размещение служб.</span><span class="sxs-lookup"><span data-stu-id="d52b0-104">The topics in the section describe service hosting.</span></span> <span data-ttu-id="d52b0-105">Служба может размещаться в службы IIS (IIS), службе активации Windows (WAS), Windows Server AppFabric, службе Windows или управляемом приложении — этот вариант часто называется *размещением в собственном расположении*.</span><span class="sxs-lookup"><span data-stu-id="d52b0-105">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="d52b0-106">Важно отметить, что при запуске службы или любого расширения от недоверенного узла нарушается безопасность.</span><span class="sxs-lookup"><span data-stu-id="d52b0-106">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d52b0-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d52b0-107">In This Section</span></span>  

 [<span data-ttu-id="d52b0-108">Размещение в службах IIS</span><span class="sxs-lookup"><span data-stu-id="d52b0-108">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)  
 <span data-ttu-id="d52b0-109">Описывает, как служба Windows Communication Foundation (WCF) размещается в службы IIS или [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="d52b0-109">Describes how a Windows Communication Foundation (WCF) service is hosted in Internet Information Services or [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)).</span></span>  
  
 [<span data-ttu-id="d52b0-110">Размещение в службе активации процессов Windows</span><span class="sxs-lookup"><span data-stu-id="d52b0-110">Hosting in Windows Process Activation Service</span></span>](hosting-in-windows-process-activation-service.md)  
 <span data-ttu-id="d52b0-111">Описывает, как служба WCF размещается службой активации процессов Windows.</span><span class="sxs-lookup"><span data-stu-id="d52b0-111">Describes how a WCF service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="d52b0-112">Размещение в приложении службы Windows</span><span class="sxs-lookup"><span data-stu-id="d52b0-112">Hosting in a Windows Service Application</span></span>](hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="d52b0-113">Описывает, как служба WCF размещается в службе Windows.</span><span class="sxs-lookup"><span data-stu-id="d52b0-113">Describes how a WCF service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="d52b0-114">Размещение в управляемом приложении</span><span class="sxs-lookup"><span data-stu-id="d52b0-114">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)  
 <span data-ttu-id="d52b0-115">Описывает, как служба WCF размещается в управляемом приложении.</span><span class="sxs-lookup"><span data-stu-id="d52b0-115">Describes how a WCF service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="d52b0-116">Активация на основе конфигурации в IIS и WAS</span><span class="sxs-lookup"><span data-stu-id="d52b0-116">Configuration-Based Activation in IIS and WAS</span></span>](configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="d52b0-117">Описывает размещение службы WCF в IIS или WAS без использования SVC-файла.</span><span class="sxs-lookup"><span data-stu-id="d52b0-117">Describes how a WCF service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="d52b0-118">Поддержка нескольких привязок узла IIS</span><span class="sxs-lookup"><span data-stu-id="d52b0-118">Supporting Multiple IIS Site Bindings</span></span>](supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="d52b0-119">Описывает, как задать несколько базовых адресов службы с помощью одной схемы URI для одного веб-узла.</span><span class="sxs-lookup"><span data-stu-id="d52b0-119">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d52b0-120">См. также</span><span class="sxs-lookup"><span data-stu-id="d52b0-120">See also</span></span>

- [<span data-ttu-id="d52b0-121">Размещение служб</span><span class="sxs-lookup"><span data-stu-id="d52b0-121">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="d52b0-122">[Функции размещения Windows Server App Fabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d52b0-122">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
