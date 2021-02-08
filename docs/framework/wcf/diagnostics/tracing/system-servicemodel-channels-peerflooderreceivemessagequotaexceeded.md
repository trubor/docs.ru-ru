---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Пирфлудеррецеивемессажекуотаексцеедед'
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 8ad164b253491f3a533c4828cd76f915eb5aed68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780874"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="686be-103">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="686be-103">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>

<span data-ttu-id="686be-104">Скорость получения входящих сообщений слишком высока.</span><span class="sxs-lookup"><span data-stu-id="686be-104">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="686be-105">Описание</span><span class="sxs-lookup"><span data-stu-id="686be-105">Description</span></span>  

 <span data-ttu-id="686be-106">Эта трассировка возникает при попытке обработки входящих сообщений.</span><span class="sxs-lookup"><span data-stu-id="686be-106">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="686be-107">Не удалось перенаправить сообщение конкретному соседнему узлу, так как была превышена квота, заданная для этого узла.</span><span class="sxs-lookup"><span data-stu-id="686be-107">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="686be-108">Это происходит, если соседнему узлу, который не отвечает, не удается очистить журнал ожидания сообщений для этого узла.</span><span class="sxs-lookup"><span data-stu-id="686be-108">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="686be-109">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="686be-109">Troubleshooting</span></span>  

 <span data-ttu-id="686be-110">Необходимо снизить частоту отправки сообщений в этой сетке.</span><span class="sxs-lookup"><span data-stu-id="686be-110">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686be-111">См. также</span><span class="sxs-lookup"><span data-stu-id="686be-111">See also</span></span>

- [<span data-ttu-id="686be-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="686be-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="686be-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="686be-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="686be-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="686be-114">Administration and Diagnostics</span></span>](../index.md)
