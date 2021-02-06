---
description: 'Дополнительные сведения о: экземпляры'
title: Экземпляры
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 9cd602164816a419b481ff600a7537593d4f500e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655270"
---
# <a name="instances"></a><span data-ttu-id="17d2e-103">Экземпляры</span><span class="sxs-lookup"><span data-stu-id="17d2e-103">Instances</span></span>

<span data-ttu-id="17d2e-104">Имя счетчика: Instances.</span><span class="sxs-lookup"><span data-stu-id="17d2e-104">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="17d2e-105">Описание</span><span class="sxs-lookup"><span data-stu-id="17d2e-105">Description</span></span>  

 <span data-ttu-id="17d2e-106">Число контекстов экземпляра, которое в настоящий момент содержит служба.</span><span class="sxs-lookup"><span data-stu-id="17d2e-106">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="17d2e-107">В большинстве случаев число контекстов экземпляра идентично числу экземпляров.</span><span class="sxs-lookup"><span data-stu-id="17d2e-107">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="17d2e-108">Однако приведенные ниже сценарии являются исключением из этого правила.</span><span class="sxs-lookup"><span data-stu-id="17d2e-108">However, the following scenarios are exception to this rule.</span></span>  
  
- <span data-ttu-id="17d2e-109">Метод службы явным образом вызывает метод <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>.</span><span class="sxs-lookup"><span data-stu-id="17d2e-109">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
- <span data-ttu-id="17d2e-110"><xref:System.ServiceModel.ReleaseInstanceMode> применяется к экземпляру <xref:System.ServiceModel.OperationBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="17d2e-110">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d2e-111">См. также</span><span class="sxs-lookup"><span data-stu-id="17d2e-111">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
