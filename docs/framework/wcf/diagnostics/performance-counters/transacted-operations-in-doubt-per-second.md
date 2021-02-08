---
description: 'Дополнительные сведения: сомнительных транзакционных операций в секунду'
title: Количество операций с поддержкой транзакций с сомнительным результатом в секунду
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: e4f8b8c9db1c92ea4348763cdc4a633f058dbaf2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771097"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="c8fa7-103">Количество операций с поддержкой транзакций с сомнительным результатом в секунду</span><span class="sxs-lookup"><span data-stu-id="c8fa7-103">Transacted Operations In Doubt Per Second</span></span>

<span data-ttu-id="c8fa7-104">Имя счетчика: Количество операций с поддержкой транзакций с сомнительным результатом в секунду.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-104">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8fa7-105">Описание</span><span class="sxs-lookup"><span data-stu-id="c8fa7-105">Description</span></span>  

 <span data-ttu-id="c8fa7-106">Количество операций с поддержкой транзакций, имеющих сомнительный результат, возникающих в данной службе за секунду.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-106">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="c8fa7-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c8fa7-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c8fa7-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
