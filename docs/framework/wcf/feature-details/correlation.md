---
description: 'Дополнительные сведения: корреляция'
title: Корреляция
ms.date: 03/30/2017
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
ms.openlocfilehash: c4142a4e7c9472eaf52fc5339221bb59c1883f9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780366"
---
# <a name="correlation"></a><span data-ttu-id="99a6d-103">Корреляция</span><span class="sxs-lookup"><span data-stu-id="99a6d-103">Correlation</span></span>

<span data-ttu-id="99a6d-104">При взаимодействии приложения службы рабочего процесса с другими службами важно обеспечить передачу сообщений соответствующему экземпляру рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="99a6d-104">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="99a6d-105">Механизм для этого предоставляет корреляция.</span><span class="sxs-lookup"><span data-stu-id="99a6d-105">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="99a6d-106">В подразделах этого раздела приведены общие сведения о корреляции, порядке ее использования в различных сценариях служб рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="99a6d-106">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99a6d-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="99a6d-107">In This Section</span></span>  

 [<span data-ttu-id="99a6d-108">Общие сведения о корреляции</span><span class="sxs-lookup"><span data-stu-id="99a6d-108">Correlation Overview</span></span>](correlation-overview.md)  
 <span data-ttu-id="99a6d-109">Содержит общие сведения о типах корреляции, доступных в [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99a6d-109">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="99a6d-110">Сохраняемый дуплекс</span><span class="sxs-lookup"><span data-stu-id="99a6d-110">Durable Duplex</span></span>](durable-duplex-correlation.md)  
 <span data-ttu-id="99a6d-111">Описывает сохраняемую дуплексную корреляцию.</span><span class="sxs-lookup"><span data-stu-id="99a6d-111">Describes durable duplex correlation.</span></span>
  
 [<span data-ttu-id="99a6d-112">Запрос-ответ</span><span class="sxs-lookup"><span data-stu-id="99a6d-112">Request-Reply</span></span>](request-reply-correlation.md)  
 <span data-ttu-id="99a6d-113">Описывает корреляцию запросов и ответов.</span><span class="sxs-lookup"><span data-stu-id="99a6d-113">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="99a6d-114">Устранение неполадок корреляции</span><span class="sxs-lookup"><span data-stu-id="99a6d-114">Troubleshooting Correlation</span></span>](troubleshooting-correlation.md)  
 <span data-ttu-id="99a6d-115">Предоставляет методы для устранения неполадок корреляции.</span><span class="sxs-lookup"><span data-stu-id="99a6d-115">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a6d-116">См. также</span><span class="sxs-lookup"><span data-stu-id="99a6d-116">See also</span></span>

- <xref:System.ServiceModel.Activities.CorrelationHandle>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.Receive>
- <xref:System.ServiceModel.CorrelationQuery>
