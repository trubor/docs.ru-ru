---
description: 'Дополнительные сведения: счетчики производительности службы'
title: Счетчики производительности службы
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 16f6f2548cf7f92b64264ac606423c69e62cd110
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686041"
---
# <a name="service-performance-counters"></a><span data-ttu-id="93158-103">Счетчики производительности службы</span><span class="sxs-lookup"><span data-stu-id="93158-103">Service Performance Counters</span></span>

<span data-ttu-id="93158-104">Счетчики производительности службы измеряют поведение службы в целом, их можно использовать для диагностики производительности всей службы.</span><span class="sxs-lookup"><span data-stu-id="93158-104">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="93158-105">При просмотре с помощью системного монитора (Perfmon.exe) счетчики находятся под объектом производительности `ServiceModelService 4.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="93158-105">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="93158-106">Экземпляры именуются по следующей схеме:</span><span class="sxs-lookup"><span data-stu-id="93158-106">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="93158-107">Длина имени экземпляра счетчика производительности ограничена.</span><span class="sxs-lookup"><span data-stu-id="93158-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="93158-108">Если имя экземпляра счетчика Windows Communication Foundation (WCF) превышает максимальную длину, WCF заменяет часть имени экземпляра на хэш-значение.</span><span class="sxs-lookup"><span data-stu-id="93158-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93158-109">См. также</span><span class="sxs-lookup"><span data-stu-id="93158-109">See also</span></span>

- [<span data-ttu-id="93158-110">Счетчики производительности</span><span class="sxs-lookup"><span data-stu-id="93158-110">Performance Counters</span></span>](index.md)
