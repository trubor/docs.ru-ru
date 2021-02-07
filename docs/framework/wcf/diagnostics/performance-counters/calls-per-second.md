---
description: 'Дополнительные сведения: число вызовов в секунду'
title: Количество вызовов в секунду
ms.date: 03/30/2017
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
ms.openlocfilehash: 1d204e4c88d9f9ab113e59c76f1eaecc280e552e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759657"
---
# <a name="calls-per-second"></a><span data-ttu-id="0cc89-103">Количество вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="0cc89-103">Calls Per Second</span></span>

<span data-ttu-id="0cc89-104">Имя счетчика: Calls Per Second</span><span class="sxs-lookup"><span data-stu-id="0cc89-104">Counter Name: Calls Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="0cc89-105">Описание</span><span class="sxs-lookup"><span data-stu-id="0cc89-105">Description</span></span>  

 <span data-ttu-id="0cc89-106">Число вызовов данной операции в секунду.</span><span class="sxs-lookup"><span data-stu-id="0cc89-106">Number of calls to this operation in a second.</span></span>  
  
 <span data-ttu-id="0cc89-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="0cc89-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0cc89-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="0cc89-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
