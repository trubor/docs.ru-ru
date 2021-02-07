---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. Коммитмессажеретри'
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 8f45463ac31c210acd8534df2c4e1ef2922f1c8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720609"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="13346-103">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="13346-103">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>

<span data-ttu-id="13346-104">Повторная попытка сообщения фиксации была отправлена участнику, который не отвечает.</span><span class="sxs-lookup"><span data-stu-id="13346-104">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="13346-105">Описание</span><span class="sxs-lookup"><span data-stu-id="13346-105">Description</span></span>  

 <span data-ttu-id="13346-106">Трассируется, если локальному диспетчеру транзакций потребовалось заново отправить сообщение фиксации подчиненному участнику, так как за заданное время не был получен отклик.</span><span class="sxs-lookup"><span data-stu-id="13346-106">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="13346-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="13346-107">Troubleshooting</span></span>  

 <span data-ttu-id="13346-108">Рассмотрите потенциальные проблемы с сетью или продуктом, которые могут препятствовать своевременной доставке отклика.</span><span class="sxs-lookup"><span data-stu-id="13346-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="13346-109">Если таких сообщений много, это может указывать на проблемы инфраструктуры или чрезмерно большое время отклика.</span><span class="sxs-lookup"><span data-stu-id="13346-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="13346-110">Обе проблемы значительно снижают пропускную способность транзакций в системе.</span><span class="sxs-lookup"><span data-stu-id="13346-110">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13346-111">См. также</span><span class="sxs-lookup"><span data-stu-id="13346-111">See also</span></span>

- [<span data-ttu-id="13346-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="13346-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="13346-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="13346-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="13346-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="13346-114">Administration and Diagnostics</span></span>](../index.md)
