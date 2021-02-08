---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. РегистерпартиЦипантфаилуре'
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e930ee66720a9f397999d729e8d680fce9a37e29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770629"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="6f980-103">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="6f980-103">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>

<span data-ttu-id="6f980-104">Службе протокола WS-AT не удалось зарегистрировать участника для протокола управления.</span><span class="sxs-lookup"><span data-stu-id="6f980-104">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6f980-105">Описание</span><span class="sxs-lookup"><span data-stu-id="6f980-105">Description</span></span>  

 <span data-ttu-id="6f980-106">Отслеживается, обнаруживает ли MSDTC недопустимый запрос на регистрацию.</span><span class="sxs-lookup"><span data-stu-id="6f980-106">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="6f980-107">Это может происходить из-за множественных запросов на регистрацию завершения и внутренних ошибок.</span><span class="sxs-lookup"><span data-stu-id="6f980-107">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6f980-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="6f980-108">Troubleshooting</span></span>  

 <span data-ttu-id="6f980-109">Не пытайтесь зарегистрировать завершение несколько раз.</span><span class="sxs-lookup"><span data-stu-id="6f980-109">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="6f980-110">Проверьте строку состояния в сообщении трассировки, чтобы определить, имеются ли элементы, с которыми можно произвести какие-либо действия.</span><span class="sxs-lookup"><span data-stu-id="6f980-110">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f980-111">См. также</span><span class="sxs-lookup"><span data-stu-id="6f980-111">See also</span></span>

- [<span data-ttu-id="6f980-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="6f980-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="6f980-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="6f980-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6f980-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="6f980-114">Administration and Diagnostics</span></span>](../index.md)
