---
description: Дополнительные сведения о том, как выполнить фильтрацию на уровне DataContext.
title: Практическое руководство. Как фильтровать данные на уровне DataContext
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: ffb287ac1ef8cc19044ec3d519e745f905fe213d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785982"
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="2df0c-103">Практическое руководство. Как фильтровать данные на уровне DataContext</span><span class="sxs-lookup"><span data-stu-id="2df0c-103">How to: Filter at the DataContext Level</span></span>

<span data-ttu-id="2df0c-104">Фильтрацию `EntitySets` можно выполнить на уровне `DataContext`.</span><span class="sxs-lookup"><span data-stu-id="2df0c-104">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="2df0c-105">Подобные фильтры применяются ко всем запросам, осуществленным с помощью экземпляра <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="2df0c-105">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2df0c-106">Пример</span><span class="sxs-lookup"><span data-stu-id="2df0c-106">Example</span></span>  

 <span data-ttu-id="2df0c-107">В следующем примере <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> используется для фильтрации предварительно загруженных заказов для клиентов по `ShippedDate`.</span><span class="sxs-lookup"><span data-stu-id="2df0c-107">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="2df0c-108">См. также</span><span class="sxs-lookup"><span data-stu-id="2df0c-108">See also</span></span>

- [<span data-ttu-id="2df0c-109">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="2df0c-109">Query Concepts</span></span>](query-concepts.md)
