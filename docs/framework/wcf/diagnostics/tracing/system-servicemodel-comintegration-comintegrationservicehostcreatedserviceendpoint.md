---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Мсмкмовеорделетеаттемптфаилед'
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 7b3c8dad9e3a3e88dff72706917f3729d55b3799
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769745"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="66b12-103">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="66b12-103">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>

<span data-ttu-id="66b12-104">Не удается переместить или удалить сообщение.</span><span class="sxs-lookup"><span data-stu-id="66b12-104">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="66b12-105">Описание</span><span class="sxs-lookup"><span data-stu-id="66b12-105">Description</span></span>  

 <span data-ttu-id="66b12-106">Эта трассировка показывает, что при попытке переместить, удалить или отклонить сообщение MSMQ произошел сбой.</span><span class="sxs-lookup"><span data-stu-id="66b12-106">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="66b12-107">Сообщения MSMQ используются Windows Communication Foundation (WCF) (при использовании с NetMsmqBinding или MsmqIntegrationBinding). Эта трассировка связана с выбранным значением свойства в `ReceiveErrorHandling` NetMsmqBinding или MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="66b12-107">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="66b12-108">Эта трассировка не указывает на общий сбой системы.</span><span class="sxs-lookup"><span data-stu-id="66b12-108">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="66b12-109">Однако она показывает, что выбранное средство удаления подозрительного сообщения не подходит для сообщения.</span><span class="sxs-lookup"><span data-stu-id="66b12-109">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="66b12-110">Дополнительные сведения о том, когда сообщения становятся подозрительными и как настроить службу для их правильной обработки, см. в разделе [Обработка подозрительных сообщений](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="66b12-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b12-111">См. также</span><span class="sxs-lookup"><span data-stu-id="66b12-111">See also</span></span>

- [<span data-ttu-id="66b12-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="66b12-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="66b12-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="66b12-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="66b12-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="66b12-114">Administration and Diagnostics</span></span>](../index.md)
