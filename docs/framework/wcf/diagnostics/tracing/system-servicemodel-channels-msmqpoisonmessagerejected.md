---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Мсмкпоисонмессажережектед'
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 856c28dd313867de0661d4950dd67e6740e2b338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759306"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="f9eb2-103">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="f9eb2-103">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>

<span data-ttu-id="f9eb2-104">Подозрительное сообщение отклонено.</span><span class="sxs-lookup"><span data-stu-id="f9eb2-104">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f9eb2-105">Описание</span><span class="sxs-lookup"><span data-stu-id="f9eb2-105">Description</span></span>  

 <span data-ttu-id="f9eb2-106">Указывает, что было обнаружено и отклонено подозрительное сообщение.</span><span class="sxs-lookup"><span data-stu-id="f9eb2-106">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="f9eb2-107">Возникает, если свойство `ReceiveErrorHandling` объекта NetMsmqBinding или MsmqIntegrationBinding имеет значение `Reject`.</span><span class="sxs-lookup"><span data-stu-id="f9eb2-107">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="f9eb2-108">Отклоненное сообщение отправляется обратно в [очередь недоставленных](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)сообщений отправителя.</span><span class="sxs-lookup"><span data-stu-id="f9eb2-108">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="f9eb2-109">Дополнительные сведения о том, когда сообщения становятся подозрительными и как настроить службу для их правильной обработки, см. в разделе [Обработка подозрительных сообщений](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="f9eb2-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="f9eb2-110">Дополнительные сведения о том, что означает отклоненное сообщение в MSMQ, см. в разделе [мкмаркмессажережектед](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f9eb2-110">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9eb2-111">См. также</span><span class="sxs-lookup"><span data-stu-id="f9eb2-111">See also</span></span>

- [<span data-ttu-id="f9eb2-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="f9eb2-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="f9eb2-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="f9eb2-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f9eb2-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="f9eb2-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="f9eb2-115">Обработка подозрительных сообщений</span><span class="sxs-lookup"><span data-stu-id="f9eb2-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="f9eb2-116">[мкмаркмессажережектед](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f9eb2-116">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
