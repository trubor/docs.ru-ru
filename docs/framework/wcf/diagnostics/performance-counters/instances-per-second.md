---
description: 'Дополнительные сведения: экземпляров в секунду'
title: Количество экземпляров в секунду
ms.date: 03/30/2017
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
ms.openlocfilehash: cfcdd85bef8b1873101c1bbb63ce40bd161a97f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655309"
---
# <a name="instances-per-second"></a><span data-ttu-id="86450-103">Количество экземпляров в секунду</span><span class="sxs-lookup"><span data-stu-id="86450-103">Instances Per Second</span></span>

<span data-ttu-id="86450-104">Имя счетчика: Instances Created Per Second.</span><span class="sxs-lookup"><span data-stu-id="86450-104">Counter Name: Instances Created Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="86450-105">Описание</span><span class="sxs-lookup"><span data-stu-id="86450-105">Description</span></span>  

 <span data-ttu-id="86450-106">Общее количество экземпляров службы, создаваемых за секунду.</span><span class="sxs-lookup"><span data-stu-id="86450-106">Total number of service instances created in a second.</span></span>  
  
 <span data-ttu-id="86450-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="86450-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="86450-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="86450-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
