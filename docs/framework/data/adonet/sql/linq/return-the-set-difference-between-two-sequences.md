---
description: 'Дополнительные сведения: возврат разности множества двух последовательностей'
title: Возврат разности наборов между двумя последовательностями
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 6836195ac4e1ee678fd3e8089e7c341f7dd247e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662990"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="c9977-103">Возврат разности наборов между двумя последовательностями</span><span class="sxs-lookup"><span data-stu-id="c9977-103">Return the Set Difference Between Two Sequences</span></span>

<span data-ttu-id="c9977-104">Оператор <xref:System.Linq.Queryable.Except%2A> используется для возвращения разности наборов между двумя последовательностями.</span><span class="sxs-lookup"><span data-stu-id="c9977-104">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9977-105">Пример</span><span class="sxs-lookup"><span data-stu-id="c9977-105">Example</span></span>  

 <span data-ttu-id="c9977-106">В этом примере используется <xref:System.Linq.Queryable.Except%2A> для возврата последовательности всех стран или регионов, в которых `Customers` динамический, но не в `Employees` режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="c9977-106">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="c9977-107">В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] оператор <xref:System.Linq.Queryable.Except%2A> правильно определен только в наборах.</span><span class="sxs-lookup"><span data-stu-id="c9977-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="c9977-108">Семантика для мультинаборов не определена.</span><span class="sxs-lookup"><span data-stu-id="c9977-108">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9977-109">См. также</span><span class="sxs-lookup"><span data-stu-id="c9977-109">See also</span></span>

- [<span data-ttu-id="c9977-110">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="c9977-110">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="c9977-111">Трансляция стандартных операторов запросов</span><span class="sxs-lookup"><span data-stu-id="c9977-111">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
