---
description: 'Дополнительные сведения: возврат объединения наборов двух последовательностей'
title: Возврат объединения наборов двух последовательностей.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 5541316560c05712e22c54f706b02d868fadb381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662966"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="ef68d-103">Возврат объединения наборов двух последовательностей.</span><span class="sxs-lookup"><span data-stu-id="ef68d-103">Return the Set Union of Two Sequences</span></span>

<span data-ttu-id="ef68d-104">Оператор <xref:System.Linq.Queryable.Union%2A> используется для возвращения объединения наборов двух последовательностей.</span><span class="sxs-lookup"><span data-stu-id="ef68d-104">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef68d-105">Пример</span><span class="sxs-lookup"><span data-stu-id="ef68d-105">Example</span></span>  

 <span data-ttu-id="ef68d-106">В этом примере используется <xref:System.Linq.Queryable.Union%2A> для возврата последовательности всех стран или регионов, в которых есть `Customers` или `Employees` .</span><span class="sxs-lookup"><span data-stu-id="ef68d-106">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="ef68d-107">В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Queryable.Union%2A> оператор определяется для множества наборов как неупорядоченное объединение множества наборов (фактически результат [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) предложения в SQL).</span><span class="sxs-lookup"><span data-stu-id="ef68d-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="ef68d-108">Дополнительные сведения и примеры см. в разделе <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ef68d-108">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ef68d-109">См. также</span><span class="sxs-lookup"><span data-stu-id="ef68d-109">See also</span></span>

- [<span data-ttu-id="ef68d-110">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="ef68d-110">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="ef68d-111">Трансляция стандартных операторов запросов</span><span class="sxs-lookup"><span data-stu-id="ef68d-111">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
