---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Пирмаинтаинерактивити'
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: da4e4cf87da808cb6779445b6507b51d098132b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780885"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="91a72-103">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="91a72-103">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>

<span data-ttu-id="91a72-104">Модуль PeerMaintainer выполняет определенную операцию (подробности содержатся в теле сообщения трассировки).</span><span class="sxs-lookup"><span data-stu-id="91a72-104">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="91a72-105">Описание</span><span class="sxs-lookup"><span data-stu-id="91a72-105">Description</span></span>  

 <span data-ttu-id="91a72-106">Эта трассировка возникает в ходе различных операций модуля обслуживания PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="91a72-106">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="91a72-107">PeerMaintainer - это внутренний компонент узла PeerNode.</span><span class="sxs-lookup"><span data-stu-id="91a72-107">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="91a72-108">Каждую минуту или каждые 32 полученных сообщения он отправляет соседним узлам сообщение LinkUtility со статистическими данными о том, сколько сообщений было принято/отправлено и сколько из них полезны (не дубликаты, не подделаны).</span><span class="sxs-lookup"><span data-stu-id="91a72-108">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="91a72-109">Это позволяет определить значение LinkUtility определенного соседнего узла.</span><span class="sxs-lookup"><span data-stu-id="91a72-109">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="91a72-110">Приблизительно каждые пять минут модуль обслуживания проверяет состояние соединений с соседними узлами.</span><span class="sxs-lookup"><span data-stu-id="91a72-110">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="91a72-111">Если количество соединений с соседними узлами превышает идеальное число, модуль обслуживания урезает наименее полезные соединения.</span><span class="sxs-lookup"><span data-stu-id="91a72-111">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="91a72-112">Если соединений недостаточно, модуль обслуживания приобретает новые соединения.</span><span class="sxs-lookup"><span data-stu-id="91a72-112">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a72-113">См. также</span><span class="sxs-lookup"><span data-stu-id="91a72-113">See also</span></span>

- [<span data-ttu-id="91a72-114">Трассировка</span><span class="sxs-lookup"><span data-stu-id="91a72-114">Tracing</span></span>](index.md)
- [<span data-ttu-id="91a72-115">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="91a72-115">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="91a72-116">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="91a72-116">Administration and Diagnostics</span></span>](../index.md)
