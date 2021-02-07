---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. Препаредмессажеретри'
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: 99106493f0eec900875a713b439111fadb150c62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677279"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="dc158-103">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="dc158-103">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>

<span data-ttu-id="dc158-104">Координатору, который не отвечает, было повторно отправлено сообщение готовности.</span><span class="sxs-lookup"><span data-stu-id="dc158-104">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dc158-105">Описание</span><span class="sxs-lookup"><span data-stu-id="dc158-105">Description</span></span>  

 <span data-ttu-id="dc158-106">Трассируется, если локальному диспетчеру транзакций потребовалось повторно отправить сообщение готовности ("Prepared") вышестоящему координатору, так как за заданное время не был получен отклик.</span><span class="sxs-lookup"><span data-stu-id="dc158-106">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="dc158-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="dc158-107">Troubleshooting</span></span>  

 <span data-ttu-id="dc158-108">Рассмотрите потенциальные проблемы с сетью или продуктом, которые могут препятствовать своевременной доставке отклика.</span><span class="sxs-lookup"><span data-stu-id="dc158-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="dc158-109">Если таких сообщений много, это может указывать на проблемы инфраструктуры или чрезмерно большое время отклика.</span><span class="sxs-lookup"><span data-stu-id="dc158-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="dc158-110">Обе проблемы значительно снижают пропускную способность транзакций в системе.</span><span class="sxs-lookup"><span data-stu-id="dc158-110">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc158-111">См. также</span><span class="sxs-lookup"><span data-stu-id="dc158-111">See also</span></span>

- [<span data-ttu-id="dc158-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="dc158-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="dc158-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="dc158-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dc158-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="dc158-114">Administration and Diagnostics</span></span>](../index.md)
