---
description: 'Дополнительные сведения: как отключить отложенную загрузку'
title: Практическое руководство. Как отключить отложенную загрузку
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 739c9b0b65eda73d6c504409395eb805b0c02873
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785839"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="b7821-103">Практическое руководство. Как отключить отложенную загрузку</span><span class="sxs-lookup"><span data-stu-id="b7821-103">How to: Turn Off Deferred Loading</span></span>

<span data-ttu-id="b7821-104">Чтобы отключить отложенную загрузку, свойству <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> следует задать значение `false`.</span><span class="sxs-lookup"><span data-stu-id="b7821-104">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="b7821-105">Дополнительные сведения см. в разделе [Отложенная и немедленная загрузка](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="b7821-105">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7821-106">Отложенная загрузка отключается при отключении отслеживания объекта.</span><span class="sxs-lookup"><span data-stu-id="b7821-106">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="b7821-107">Дополнительные сведения см. [в разделе как получить данные только для чтения](how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="b7821-107">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7821-108">Пример</span><span class="sxs-lookup"><span data-stu-id="b7821-108">Example</span></span>  

 <span data-ttu-id="b7821-109">В следующем примере показано отключение отложенной загрузки путем установки свойству <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> значения `false`.</span><span class="sxs-lookup"><span data-stu-id="b7821-109">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b7821-110">См. также</span><span class="sxs-lookup"><span data-stu-id="b7821-110">See also</span></span>

- [<span data-ttu-id="b7821-111">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="b7821-111">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="b7821-112">Запрос к базе данных</span><span class="sxs-lookup"><span data-stu-id="b7821-112">Querying the Database</span></span>](querying-the-database.md)
