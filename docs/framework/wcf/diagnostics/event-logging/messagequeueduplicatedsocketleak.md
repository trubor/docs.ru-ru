---
description: 'Дополнительные сведения о: Мессажекуеуедупликатедсоккетлеак'
title: MessageQueueDuplicatedSocketLeak
ms.date: 03/30/2017
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
ms.openlocfilehash: d439485a00c7d9c155cad78d741d16a40c37a438
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99656011"
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="e28ab-103">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="e28ab-103">MessageQueueDuplicatedSocketLeak</span></span>

<span data-ttu-id="e28ab-104">Идентификатор: 165</span><span class="sxs-lookup"><span data-stu-id="e28ab-104">Id: 165</span></span>  
  
 <span data-ttu-id="e28ab-105">Важность: ошибка</span><span class="sxs-lookup"><span data-stu-id="e28ab-105">Severity: Error</span></span>  
  
 <span data-ttu-id="e28ab-106">Категория: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="e28ab-106">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="e28ab-107">Описание</span><span class="sxs-lookup"><span data-stu-id="e28ab-107">Description</span></span>  

 <span data-ttu-id="e28ab-108">Это событие показывает, что произошла ошибка при диспетчеризации дублированного сокета.</span><span class="sxs-lookup"><span data-stu-id="e28ab-108">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="e28ab-109">В данном процессе происходит утечка этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="e28ab-109">This handle is now leaked in the process.</span></span> <span data-ttu-id="e28ab-110">В событии указаны источник, исключение, имя процесса и ИД процесса.</span><span class="sxs-lookup"><span data-stu-id="e28ab-110">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e28ab-111">См. также</span><span class="sxs-lookup"><span data-stu-id="e28ab-111">See also</span></span>

- [<span data-ttu-id="e28ab-112">Ведение журналов событий</span><span class="sxs-lookup"><span data-stu-id="e28ab-112">Event Logging</span></span>](index.md)
- [<span data-ttu-id="e28ab-113">Общие справочные сведения о событиях</span><span class="sxs-lookup"><span data-stu-id="e28ab-113">Events General Reference</span></span>](events-general-reference.md)
