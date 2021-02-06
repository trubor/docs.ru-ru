---
description: 'Дополнительные сведения: счетчики производительности операций'
title: Счетчики производительности операций
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: e0a503d4d8b178d5d3f4ef240bf84c4b02a581ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655205"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="21dfd-103">Счетчики производительности операций</span><span class="sxs-lookup"><span data-stu-id="21dfd-103">Operation Performance Counters</span></span>

<span data-ttu-id="21dfd-104">При просмотре с помощью системного монитора (Perfmon.exe) счетчики производительности операций находятся под объектом производительности `ServiceModelOperation 4.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="21dfd-104">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="21dfd-105">Каждая операция содержит отдельный экземпляр.</span><span class="sxs-lookup"><span data-stu-id="21dfd-105">Each operation has an individual instance.</span></span> <span data-ttu-id="21dfd-106">Следовательно, если указанный контракт имеет 10 операций, 10 экземпляров счетчика операций связаны с этим контрактом.</span><span class="sxs-lookup"><span data-stu-id="21dfd-106">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="21dfd-107">Экземпляры объекта именуются по следующей схеме:</span><span class="sxs-lookup"><span data-stu-id="21dfd-107">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="21dfd-108">Этот счетчик позволяет измерить, как используется вызов и насколько успешно выполняется операция.</span><span class="sxs-lookup"><span data-stu-id="21dfd-108">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="21dfd-109">Длина имени экземпляра счетчика производительности ограничена.</span><span class="sxs-lookup"><span data-stu-id="21dfd-109">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="21dfd-110">Если имя экземпляра счетчика Windows Communication Foundation (WCF) превышает максимальную длину, WCF заменяет часть имени экземпляра на хэш-значение.</span><span class="sxs-lookup"><span data-stu-id="21dfd-110">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21dfd-111">См. также</span><span class="sxs-lookup"><span data-stu-id="21dfd-111">See also</span></span>

- [<span data-ttu-id="21dfd-112">Счетчики производительности</span><span class="sxs-lookup"><span data-stu-id="21dfd-112">Performance Counters</span></span>](index.md)
