---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. ДураблепартиЦипантреплайвхилепрепаринг'
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fcaa50dd4faa548cad8ff085f1c66f94c63bd010
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635666"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="29f3b-103">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="29f3b-103">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>

<span data-ttu-id="29f3b-104">Служба протокола WS-AT получила ответное сообщение от постоянного участника, который не ответил на подготовительное сообщение.</span><span class="sxs-lookup"><span data-stu-id="29f3b-104">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="29f3b-105">Поэтому транзакция была прервана.</span><span class="sxs-lookup"><span data-stu-id="29f3b-105">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="29f3b-106">Описание</span><span class="sxs-lookup"><span data-stu-id="29f3b-106">Description</span></span>  

 <span data-ttu-id="29f3b-107">Трассируется, если ответное сообщение получается, пока постоянный участник находится в состоянии подготовки.</span><span class="sxs-lookup"><span data-stu-id="29f3b-107">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="29f3b-108">Это недопустимое сообщение для данного состояния, поэтому транзакция прерывается.</span><span class="sxs-lookup"><span data-stu-id="29f3b-108">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="29f3b-109">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="29f3b-109">Troubleshooting</span></span>

<span data-ttu-id="29f3b-110">Получение этой ошибки может означать, что устойчивый участник (включая подчиненный Трансактионманажерс) был восстановлен после сбоя; Тем не менее, результат транзакции не известен и запрашивает свое состояние.</span><span class="sxs-lookup"><span data-stu-id="29f3b-110">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f3b-111">См. также</span><span class="sxs-lookup"><span data-stu-id="29f3b-111">See also</span></span>

- [<span data-ttu-id="29f3b-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="29f3b-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="29f3b-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="29f3b-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="29f3b-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="29f3b-114">Administration and Diagnostics</span></span>](../index.md)
