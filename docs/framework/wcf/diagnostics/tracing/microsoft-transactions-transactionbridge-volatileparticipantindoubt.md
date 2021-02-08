---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. ВолатилепартиЦипантиндаубт'
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: c9d95285e09d017aa82c86e7c5c6f9fd758b9f80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803247"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="22180-103">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="22180-103">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>

<span data-ttu-id="22180-104">Служба протокола WS-AT получила сообщение "Готово" или "Повторная отправка" от неопознанного неустойчивого участника.</span><span class="sxs-lookup"><span data-stu-id="22180-104">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="22180-105">Ошибка, возвращенная участнику, оповещает о том, что результат транзакции не известен.</span><span class="sxs-lookup"><span data-stu-id="22180-105">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="22180-106">Описание</span><span class="sxs-lookup"><span data-stu-id="22180-106">Description</span></span>  

 <span data-ttu-id="22180-107">Трассируется, когда локальный диспетчер транзакций получает сообщение "Готово" или "Повторная отправка" от уже забытого неустойчивого перечисления.</span><span class="sxs-lookup"><span data-stu-id="22180-107">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="22180-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="22180-108">Troubleshooting</span></span>  

 <span data-ttu-id="22180-109">Выявите возможные причины поздних сообщений, поступающих от неустойчивого участника.</span><span class="sxs-lookup"><span data-stu-id="22180-109">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22180-110">См. также</span><span class="sxs-lookup"><span data-stu-id="22180-110">See also</span></span>

- [<span data-ttu-id="22180-111">Трассировка</span><span class="sxs-lookup"><span data-stu-id="22180-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="22180-112">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="22180-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="22180-113">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="22180-113">Administration and Diagnostics</span></span>](../index.md)
