---
description: 'Дополнительные сведения о: Курдинаторрековериложентрикоррупт'
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 3a848c634a226b34023a24898f9827162b4dafc7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771344"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="14dfb-103">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="14dfb-103">CoordinatorRecoveryLogEntryCorrupt</span></span>

<span data-ttu-id="14dfb-104">Идентификатор: 139</span><span class="sxs-lookup"><span data-stu-id="14dfb-104">Id: 139</span></span>  
  
 <span data-ttu-id="14dfb-105">Важность: ошибка</span><span class="sxs-lookup"><span data-stu-id="14dfb-105">Severity: Error</span></span>  
  
 <span data-ttu-id="14dfb-106">Категория: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="14dfb-106">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="14dfb-107">Описание</span><span class="sxs-lookup"><span data-stu-id="14dfb-107">Description</span></span>  

 <span data-ttu-id="14dfb-108">Это событие показывает, что запись в журнале восстановления координатора была повреждена и ее не удалось десериализовать.</span><span class="sxs-lookup"><span data-stu-id="14dfb-108">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="14dfb-109">Эта ошибка может привести к потере данных.</span><span class="sxs-lookup"><span data-stu-id="14dfb-109">Data loss may result from this error.</span></span> <span data-ttu-id="14dfb-110">В событии указаны идентификатор транзакции, данные о восстановлении (в кодировке Base64), исключение, имя и ИД процесса.</span><span class="sxs-lookup"><span data-stu-id="14dfb-110">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14dfb-111">См. также</span><span class="sxs-lookup"><span data-stu-id="14dfb-111">See also</span></span>

- [<span data-ttu-id="14dfb-112">Ведение журналов событий</span><span class="sxs-lookup"><span data-stu-id="14dfb-112">Event Logging</span></span>](index.md)
- [<span data-ttu-id="14dfb-113">Общие справочные сведения о событиях</span><span class="sxs-lookup"><span data-stu-id="14dfb-113">Events General Reference</span></span>](events-general-reference.md)
