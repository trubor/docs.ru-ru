---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Фаиледпипеконнект'
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: dbbb3ba2848eaefe70a6d6308daecf84e0a8c7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644480"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="560b9-103">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="560b9-103">System.ServiceModel.Channels.FailedPipeConnect</span></span>

<span data-ttu-id="560b9-104">Сбой попытки соединения с конечной точкой именованного канала.</span><span class="sxs-lookup"><span data-stu-id="560b9-104">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="560b9-105">По истечении заданного промежутка времени выполнена еще одна попытка.</span><span class="sxs-lookup"><span data-stu-id="560b9-105">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="560b9-106">Описание</span><span class="sxs-lookup"><span data-stu-id="560b9-106">Description</span></span>  

 <span data-ttu-id="560b9-107">Данная информационная трассировка показывает сбой соединения с конечной точкой именованного канала.</span><span class="sxs-lookup"><span data-stu-id="560b9-107">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="560b9-108">Возможная причина: не найдена или занята конечная точка именованного канала.</span><span class="sxs-lookup"><span data-stu-id="560b9-108">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="560b9-109">Через короткие промежутки времени производится несколько дополнительных попыток, пока одна из них не будет успешной, или до истечения времени, заданного свойством OpenTimeout.</span><span class="sxs-lookup"><span data-stu-id="560b9-109">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="560b9-110">См. также</span><span class="sxs-lookup"><span data-stu-id="560b9-110">See also</span></span>

- [<span data-ttu-id="560b9-111">Трассировка</span><span class="sxs-lookup"><span data-stu-id="560b9-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="560b9-112">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="560b9-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="560b9-113">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="560b9-113">Administration and Diagnostics</span></span>](../index.md)
