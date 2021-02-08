---
description: 'Дополнительные сведения: объединение двух последовательностей'
title: Сцепление двух последовательностей
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 5e48f3e2900bf53d042eb9c2aad6535bad9ec7e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773177"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="3a5d0-103">Сцепление двух последовательностей</span><span class="sxs-lookup"><span data-stu-id="3a5d0-103">Concatenate Two Sequences</span></span>

<span data-ttu-id="3a5d0-104">Для объединения двух последовательностей используется оператор <xref:System.Linq.Queryable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="3a5d0-104">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="3a5d0-105">Оператор <xref:System.Linq.Queryable.Concat%2A> определен для упорядоченных множественных наборов, в которых порядок получателя и аргумента совпадают.</span><span class="sxs-lookup"><span data-stu-id="3a5d0-105">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="3a5d0-106">В SQL упорядочивание является последним шагом перед получением результатов.</span><span class="sxs-lookup"><span data-stu-id="3a5d0-106">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="3a5d0-107">Поэтому оператор <xref:System.Linq.Queryable.Concat%2A> реализован с помощью `UNION ALL` и не сохраняет порядок своих аргументов.</span><span class="sxs-lookup"><span data-stu-id="3a5d0-107">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="3a5d0-108">Для обеспечения правильного порядка в результатах требуется их явное упорядочение.</span><span class="sxs-lookup"><span data-stu-id="3a5d0-108">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a5d0-109">Пример</span><span class="sxs-lookup"><span data-stu-id="3a5d0-109">Example</span></span>  

 <span data-ttu-id="3a5d0-110">В данном примере для возвращения последовательности всех номеров телефонов и факсов <xref:System.Linq.Queryable.Concat%2A> и `Customer` используется `Employee`.</span><span class="sxs-lookup"><span data-stu-id="3a5d0-110">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="3a5d0-111">Пример</span><span class="sxs-lookup"><span data-stu-id="3a5d0-111">Example</span></span>  

 <span data-ttu-id="3a5d0-112">В данном примере для возвращения последовательности всех сопоставлений имен и номеров телефонов <xref:System.Linq.Queryable.Concat%2A> и `Customer` используется `Employee`.</span><span class="sxs-lookup"><span data-stu-id="3a5d0-112">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="3a5d0-113">См. также</span><span class="sxs-lookup"><span data-stu-id="3a5d0-113">See also</span></span>

- [<span data-ttu-id="3a5d0-114">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="3a5d0-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="3a5d0-115">Трансляция стандартных операторов запросов</span><span class="sxs-lookup"><span data-stu-id="3a5d0-115">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
