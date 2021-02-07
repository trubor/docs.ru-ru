---
description: 'Дополнительные сведения: возврат пересечения наборов двух последовательностей'
title: Возврат пересечения наборов двух последовательностей.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 163e138761caadb73b6dc5d672c02353a88a2c22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662989"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="1a27f-103">Возврат пересечения наборов двух последовательностей.</span><span class="sxs-lookup"><span data-stu-id="1a27f-103">Return the Set Intersection of Two Sequences</span></span>

<span data-ttu-id="1a27f-104">Для возвращения пересечения наборов двух последовательностей используется оператор <xref:System.Linq.Queryable.Intersect%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a27f-104">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a27f-105">Пример</span><span class="sxs-lookup"><span data-stu-id="1a27f-105">Example</span></span>  

 <span data-ttu-id="1a27f-106">В этом примере используется <xref:System.Linq.Queryable.Intersect%2A> для возврата последовательности всех стран или регионов, в которых `Customers` и, и в `Employees` реальном времени.</span><span class="sxs-lookup"><span data-stu-id="1a27f-106">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="1a27f-107">В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] оператор <xref:System.Linq.Queryable.Intersect%2A> правильно определен только в наборах.</span><span class="sxs-lookup"><span data-stu-id="1a27f-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="1a27f-108">Семантика для мультинаборов не определена.</span><span class="sxs-lookup"><span data-stu-id="1a27f-108">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a27f-109">См. также</span><span class="sxs-lookup"><span data-stu-id="1a27f-109">See also</span></span>

- [<span data-ttu-id="1a27f-110">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="1a27f-110">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="1a27f-111">Трансляция стандартных операторов запросов</span><span class="sxs-lookup"><span data-stu-id="1a27f-111">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
