---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. Волатилеауткометимеаут'
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 5dd6ecce995d315581e1335e4dc83c425a6381b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677240"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="643f8-103">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="643f8-103">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>

<span data-ttu-id="643f8-104">Истекло время ожидания службой протокола WS-AT ответа на результативное сообщение от неустойчивого участника.</span><span class="sxs-lookup"><span data-stu-id="643f8-104">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="643f8-105">При возвращении участника результат транзакции будет поставлен под сомнение.</span><span class="sxs-lookup"><span data-stu-id="643f8-105">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="643f8-106">Описание</span><span class="sxs-lookup"><span data-stu-id="643f8-106">Description</span></span>  

 <span data-ttu-id="643f8-107">Трассируется, когда неустойчивый участник принял решение зафиксировать или прервать транзакцию, однако не ответил на сообщение Commit или Rollback в течение заданного времени.</span><span class="sxs-lookup"><span data-stu-id="643f8-107">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="643f8-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="643f8-108">Troubleshooting</span></span>  

 <span data-ttu-id="643f8-109">Убедитесь, что все неустойчивые участники имеют возможность ответить в течение заданного времени.</span><span class="sxs-lookup"><span data-stu-id="643f8-109">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="643f8-110">Период времени по умолчанию - 180 секунд.</span><span class="sxs-lookup"><span data-stu-id="643f8-110">The default time period is 180 seconds.</span></span>  <span data-ttu-id="643f8-111">Если этого недостаточно, увеличьте значение политики таймера `VolatileOutcomeDelay` для протокола WS-AT.</span><span class="sxs-lookup"><span data-stu-id="643f8-111">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643f8-112">См. также</span><span class="sxs-lookup"><span data-stu-id="643f8-112">See also</span></span>

- [<span data-ttu-id="643f8-113">Трассировка</span><span class="sxs-lookup"><span data-stu-id="643f8-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="643f8-114">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="643f8-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="643f8-115">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="643f8-115">Administration and Diagnostics</span></span>](../index.md)
