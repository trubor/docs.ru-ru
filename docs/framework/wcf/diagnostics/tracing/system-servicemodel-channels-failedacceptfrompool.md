---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Фаиледакцептфромпул'
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 1b3c15594611726fd4872197b97ad4ed56c085c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635263"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="20fa7-103">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="20fa7-103">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>

<span data-ttu-id="20fa7-104">При попытке повторного использования подключения в пуле произошел сбой.</span><span class="sxs-lookup"><span data-stu-id="20fa7-104">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="20fa7-105">По истечении заданного промежутка времени выполнена еще одна попытка.</span><span class="sxs-lookup"><span data-stu-id="20fa7-105">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="20fa7-106">Описание</span><span class="sxs-lookup"><span data-stu-id="20fa7-106">Description</span></span>  

 <span data-ttu-id="20fa7-107">Данная информационная трассировка показывает, что при попытке повторного использования подключения в пуле произошла ошибка.</span><span class="sxs-lookup"><span data-stu-id="20fa7-107">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="20fa7-108">Ошибка могла произойти из-за несовместимости или неготовности подключения в пуле, либо того, что оно до сих пор активно.</span><span class="sxs-lookup"><span data-stu-id="20fa7-108">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="20fa7-109">Дополнительные попытки повторного использования другого подключения в пуле предпринимаются по истечении заданного промежутка времени, и если не найдено ни одного используемого подключения, создается новое подключение.</span><span class="sxs-lookup"><span data-stu-id="20fa7-109">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20fa7-110">См. также</span><span class="sxs-lookup"><span data-stu-id="20fa7-110">See also</span></span>

- [<span data-ttu-id="20fa7-111">Трассировка</span><span class="sxs-lookup"><span data-stu-id="20fa7-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="20fa7-112">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="20fa7-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="20fa7-113">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="20fa7-113">Administration and Diagnostics</span></span>](../index.md)
