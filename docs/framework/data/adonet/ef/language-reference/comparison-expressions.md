---
description: 'Дополнительные сведения: выражения сравнения'
title: Выражения сравнения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: 95d93597048b36e48227387e2135afab1486e1ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697001"
---
# <a name="comparison-expressions"></a><span data-ttu-id="1a446-103">Выражения сравнения</span><span class="sxs-lookup"><span data-stu-id="1a446-103">Comparison Expressions</span></span>

<span data-ttu-id="1a446-104">Выражение сравнения проверяет, является ли значение константы, свойства или результата метода равным другому значению, не равным ему, большим или меньшим его.</span><span class="sxs-lookup"><span data-stu-id="1a446-104">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="1a446-105">Если определенное сравнение недопустимо для LINQ to Entities, будет создано исключение.</span><span class="sxs-lookup"><span data-stu-id="1a446-105">If a particular comparison is not valid for LINQ to Entities, an exception will be thrown.</span></span> <span data-ttu-id="1a446-106">Все сравнения, как явные, так и неявные, требуют сравнимости всех компонентов в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="1a446-106">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="1a446-107">Выражения сравнения часто используются в предложениях `Where` для ограничения результатов запроса.</span><span class="sxs-lookup"><span data-stu-id="1a446-107">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="1a446-108">Следующий пример с синтаксисом выражений запроса представляет собой запрос, возвращающий данные заказа, номер которого равен SO43663.</span><span class="sxs-lookup"><span data-stu-id="1a446-108">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="1a446-109">Следующий пример с синтаксисом запроса на основе методов представляет собой запрос, возвращающий данные заказа с номером SO43663.</span><span class="sxs-lookup"><span data-stu-id="1a446-109">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="1a446-110">Следующий пример с синтаксисом выражений запроса представляет собой запрос, возвращающий данные заказов, отправленных 8 июля 2001 года.</span><span class="sxs-lookup"><span data-stu-id="1a446-110">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="1a446-111">Следующий пример с синтаксисом запроса на основе методов представляет собой запрос, возвращающий данные заказов, отправленных 8 июля 2001 года.</span><span class="sxs-lookup"><span data-stu-id="1a446-111">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="1a446-112">Выражения, результатом которых является константа, преобразуются на сервере. Попытка вычислить их локально не производится.</span><span class="sxs-lookup"><span data-stu-id="1a446-112">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="1a446-113">В следующем примере в предложении `Where` используется выражение, возвращающее константу.</span><span class="sxs-lookup"><span data-stu-id="1a446-113">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="1a446-114">LINQ to Entities не поддерживает использование класса пользователя в качестве константы.</span><span class="sxs-lookup"><span data-stu-id="1a446-114">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="1a446-115">Однако ссылка на свойство пользовательского класса считается константой; она будет преобразована в константное выражение дерева команд и выполнена в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="1a446-115">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="1a446-116">Методы, возвращающие постоянное выражение, не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="1a446-116">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="1a446-117">В следующем примере в предложении `Where` используется метод, возвращающий константу.</span><span class="sxs-lookup"><span data-stu-id="1a446-117">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="1a446-118">Во время выполнения этого примера будет выдано исключение.</span><span class="sxs-lookup"><span data-stu-id="1a446-118">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="1a446-119">См. также</span><span class="sxs-lookup"><span data-stu-id="1a446-119">See also</span></span>

- [<span data-ttu-id="1a446-120">Выражения в запросах LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1a446-120">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
