---
description: 'Дополнительные сведения: количество транзакций в секунду'
title: Количество поступивших транзакций в секунду
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: f37c79e89efb8a013719f44350772919b7222a61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771006"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="2d2fa-103">Количество поступивших транзакций в секунду</span><span class="sxs-lookup"><span data-stu-id="2d2fa-103">Transactions Flowed Per Second</span></span>

<span data-ttu-id="2d2fa-104">Имя счетчика: Количество поступивших транзакций в секунду</span><span class="sxs-lookup"><span data-stu-id="2d2fa-104">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="2d2fa-105">Описание</span><span class="sxs-lookup"><span data-stu-id="2d2fa-105">Description</span></span>  

 <span data-ttu-id="2d2fa-106">Количество транзакций в операции в секунду.</span><span class="sxs-lookup"><span data-stu-id="2d2fa-106">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="2d2fa-107">Значение этого счетчика увеличивается каждый раз, когда в сообщении, отправляемом в операцию, содержится идентификатор транзакции.</span><span class="sxs-lookup"><span data-stu-id="2d2fa-107">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="2d2fa-108">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="2d2fa-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2d2fa-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2d2fa-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
