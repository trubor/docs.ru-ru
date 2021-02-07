---
description: Дополнительные сведения см. в статье как получить сведения в виде Read-Only
title: Практическое руководство. Как получать информацию в режиме только для чтения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 7743e555bcc3f6371ca601d02313e30895e57961
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723456"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="18a06-103">Практическое руководство. Как получать информацию в режиме только для чтения</span><span class="sxs-lookup"><span data-stu-id="18a06-103">How to: Retrieve Information As Read-Only</span></span>

<span data-ttu-id="18a06-104">Если не планируется изменять данные, можно повысить производительность запросов за счет поиска результатов, предназначенных только для чтения.</span><span class="sxs-lookup"><span data-stu-id="18a06-104">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="18a06-105">Чтобы реализовать обработку запросов только для чтения, установите для свойства <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> значение `false`.</span><span class="sxs-lookup"><span data-stu-id="18a06-105">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18a06-106">Если для свойства <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> установлено значение `false`, то для свойства <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> неявно устанавливается значение `false`.</span><span class="sxs-lookup"><span data-stu-id="18a06-106">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18a06-107">Пример</span><span class="sxs-lookup"><span data-stu-id="18a06-107">Example</span></span>  

 <span data-ttu-id="18a06-108">В следующем примере кода извлекается коллекция дат приема на работу сотрудников, предназначенная только для чтения.</span><span class="sxs-lookup"><span data-stu-id="18a06-108">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="18a06-109">См. также</span><span class="sxs-lookup"><span data-stu-id="18a06-109">See also</span></span>

- [<span data-ttu-id="18a06-110">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="18a06-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="18a06-111">Запрос к базе данных</span><span class="sxs-lookup"><span data-stu-id="18a06-111">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="18a06-112">Отложенная и немедленная загрузка</span><span class="sxs-lookup"><span data-stu-id="18a06-112">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)
