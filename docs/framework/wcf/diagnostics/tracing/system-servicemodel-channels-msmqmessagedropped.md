---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Мсмкмессажедроппед'
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 41b9c6d5399f0f6b458404ee4b64624e5863c777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780964"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="88aa1-103">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="88aa1-103">System.ServiceModel.Channels.MsmqMessageDropped</span></span>

<span data-ttu-id="88aa1-104">Сообщение удалено из очереди MSMQ.</span><span class="sxs-lookup"><span data-stu-id="88aa1-104">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="88aa1-105">Описание</span><span class="sxs-lookup"><span data-stu-id="88aa1-105">Description</span></span>  

 <span data-ttu-id="88aa1-106">Данная трассировка указывает, что сообщение MSMQ было удалено.</span><span class="sxs-lookup"><span data-stu-id="88aa1-106">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="88aa1-107">Сообщения MSMQ могут быть удалены, когда Windows Communication Foundation (WCF) (используется с NetMsmqBinding или MsmqIntegrationBinding) не может их обработать.</span><span class="sxs-lookup"><span data-stu-id="88aa1-107">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="88aa1-108">Такие сообщения считаются подозрительными.</span><span class="sxs-lookup"><span data-stu-id="88aa1-108">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="88aa1-109">Подозрительное сообщение отбрасывается, если свойству `ReceiveErrorHandling` класса NetMsmqBinding или класса MsmqIntegrationBinding присвоено значение `Drop`.</span><span class="sxs-lookup"><span data-stu-id="88aa1-109">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="88aa1-110">Такое сообщение удаляется из очереди, и восстановить его после этого невозможно.</span><span class="sxs-lookup"><span data-stu-id="88aa1-110">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="88aa1-111">Дополнительные сведения о том, когда сообщения становятся подозрительными и как настроить службу для их правильной обработки, см. в разделе [Обработка подозрительных сообщений](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="88aa1-111">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88aa1-112">См. также</span><span class="sxs-lookup"><span data-stu-id="88aa1-112">See also</span></span>

- [<span data-ttu-id="88aa1-113">Трассировка</span><span class="sxs-lookup"><span data-stu-id="88aa1-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="88aa1-114">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="88aa1-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="88aa1-115">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="88aa1-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="88aa1-116">Обработка подозрительных сообщений</span><span class="sxs-lookup"><span data-stu-id="88aa1-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
