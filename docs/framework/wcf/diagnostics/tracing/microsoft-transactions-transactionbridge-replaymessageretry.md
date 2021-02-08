---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. Реплаймессажеретри'
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: e4de1416fab2cf7098d0276b6130999c01ea6e3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803260"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="544d6-103">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="544d6-103">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>

<span data-ttu-id="544d6-104">Координатору, который не отвечает, было повторно отправлено сообщение Replay.</span><span class="sxs-lookup"><span data-stu-id="544d6-104">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="544d6-105">Описание</span><span class="sxs-lookup"><span data-stu-id="544d6-105">Description</span></span>  

 <span data-ttu-id="544d6-106">Трассируется, если локальному диспетчеру транзакций потребовалось повторно отправить сообщение Replay вышестоящему координатору, так как за заданное время не был получен отклик.</span><span class="sxs-lookup"><span data-stu-id="544d6-106">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="544d6-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="544d6-107">Troubleshooting</span></span>  

 <span data-ttu-id="544d6-108">Рассмотрите потенциальные проблемы с сетью или продуктом, которые могут препятствовать своевременной доставке отклика.</span><span class="sxs-lookup"><span data-stu-id="544d6-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="544d6-109">Если таких сообщений много, это может указывать на проблемы инфраструктуры или чрезмерно большое время отклика.</span><span class="sxs-lookup"><span data-stu-id="544d6-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="544d6-110">Обе проблемы значительно снижают пропускную способность транзакций в системе.</span><span class="sxs-lookup"><span data-stu-id="544d6-110">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544d6-111">См. также</span><span class="sxs-lookup"><span data-stu-id="544d6-111">See also</span></span>

- [<span data-ttu-id="544d6-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="544d6-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="544d6-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="544d6-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="544d6-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="544d6-114">Administration and Diagnostics</span></span>](../index.md)
