---
description: 'Дополнительные сведения: System. ServiceModel. Мануалфловсроттлелимитреачед'
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 90c911131259ea02023eb05a97793f00f3eb43fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99633339"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="5cc03-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="5cc03-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>

<span data-ttu-id="5cc03-104">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="5cc03-104">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="5cc03-105">Описание</span><span class="sxs-lookup"><span data-stu-id="5cc03-105">Description</span></span>  

 <span data-ttu-id="5cc03-106">Система достигла предела, заданного ограничителем ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="5cc03-106">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="5cc03-107">Значение регулировки, в зависимости от конкретного случая, может быть изменено с помощью изменения свойства ManualFlowControlLimit либо в классе ServiceHost, либо в классе InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="5cc03-107">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="5cc03-108">Такая трассировка выдается, если ручной предел управления потоками первоначально снижается до 0.</span><span class="sxs-lookup"><span data-stu-id="5cc03-108">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="5cc03-109">Последующие изменения до 0 не трассируются.</span><span class="sxs-lookup"><span data-stu-id="5cc03-109">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="5cc03-110">Предел управления потоками в контексте экземпляра трассируется один раз для каждого контекста.</span><span class="sxs-lookup"><span data-stu-id="5cc03-110">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc03-111">См. также</span><span class="sxs-lookup"><span data-stu-id="5cc03-111">See also</span></span>

- [<span data-ttu-id="5cc03-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="5cc03-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="5cc03-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="5cc03-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5cc03-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="5cc03-114">Administration and Diagnostics</span></span>](../index.md)
