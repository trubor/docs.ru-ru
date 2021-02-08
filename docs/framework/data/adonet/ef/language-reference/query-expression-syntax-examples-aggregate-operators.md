---
description: 'Дополнительные сведения: примеры синтаксиса выражений запросов: статистические операторы'
title: Примеры синтаксиса выражений запросов. Операторы статистических выражений
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
ms.openlocfilehash: c0fd9c3faf770a00a54341cf3718c2dda91a4d7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767938"
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="9ade4-103">Примеры синтаксиса выражений запросов. Операторы статистических выражений</span><span class="sxs-lookup"><span data-stu-id="9ade4-103">Query Expression Syntax Examples: Aggregate Operators</span></span>

<span data-ttu-id="9ade4-104">В примерах этого раздела показано, как использовать <xref:System.Linq.Enumerable.Average%2A> методы, <xref:System.Linq.Enumerable.Count%2A> , <xref:System.Linq.Enumerable.Max%2A> , <xref:System.Linq.Enumerable.Min%2A> и <xref:System.Linq.Enumerable.Sum%2A> для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса выражений запросов.</span><span class="sxs-lookup"><span data-stu-id="9ade4-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="9ade4-105">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9ade4-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9ade4-106">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="9ade4-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="9ade4-107">Среднее значение</span><span class="sxs-lookup"><span data-stu-id="9ade4-107">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ade4-108">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-108">Example</span></span>  

 <span data-ttu-id="9ade4-109">В следующем примере используется метод <xref:System.Linq.Enumerable.Average%2A> для нахождения средней цены по прейскуранту для продуктов каждого типа.</span><span class="sxs-lookup"><span data-stu-id="9ade4-109">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="9ade4-110">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-110">Example</span></span>  

 <span data-ttu-id="9ade4-111">В следующем примере для получения средней суммы заказа для каждого идентификатора контактного лица используется метод <xref:System.Linq.Enumerable.Average%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ade4-111">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="9ade4-112">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-112">Example</span></span>  

 <span data-ttu-id="9ade4-113">В следующем примере для получения заказов со средней суммой заказа для каждого идентификатора контактного лица используется метод <xref:System.Linq.Enumerable.Average%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ade4-113">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="9ade4-114">Count</span><span class="sxs-lookup"><span data-stu-id="9ade4-114">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ade4-115">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-115">Example</span></span>  

 <span data-ttu-id="9ade4-116">В следующем примере метод <xref:System.Linq.Enumerable.Count%2A> используется, чтобы возвратить список идентификаторов контактных лиц, а также информацию о том, сколько заказов у каждого из них.</span><span class="sxs-lookup"><span data-stu-id="9ade4-116">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="9ade4-117">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-117">Example</span></span>  

 <span data-ttu-id="9ade4-118">В следующем примере продукты группируются по цвету, а метод <xref:System.Linq.Enumerable.Count%2A> используется в нем для возврата числа продуктов в каждой цветовой группе.</span><span class="sxs-lookup"><span data-stu-id="9ade4-118">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="9ade4-119">Max</span><span class="sxs-lookup"><span data-stu-id="9ade4-119">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ade4-120">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-120">Example</span></span>  

 <span data-ttu-id="9ade4-121">В следующем примере используется метод <xref:System.Linq.Enumerable.Max%2A> для получения наибольшей суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="9ade4-121">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="9ade4-122">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-122">Example</span></span>  

 <span data-ttu-id="9ade4-123">В следующем примере используется метод <xref:System.Linq.Enumerable.Max%2A> для получения наибольшей суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="9ade4-123">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="9ade4-124">Min</span><span class="sxs-lookup"><span data-stu-id="9ade4-124">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ade4-125">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-125">Example</span></span>  

 <span data-ttu-id="9ade4-126">В следующем примере используется метод <xref:System.Linq.Enumerable.Min%2A> для получения заказов с наименьшей суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="9ade4-126">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="9ade4-127">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-127">Example</span></span>  

 <span data-ttu-id="9ade4-128">В следующем примере используется метод <xref:System.Linq.Enumerable.Min%2A> для получения заказов с наименьшей суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="9ade4-128">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="9ade4-129">SUM</span><span class="sxs-lookup"><span data-stu-id="9ade4-129">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ade4-130">Пример</span><span class="sxs-lookup"><span data-stu-id="9ade4-130">Example</span></span>  

 <span data-ttu-id="9ade4-131">В следующем примере используется метод <xref:System.Linq.Enumerable.Sum%2A> для получения суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="9ade4-131">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="9ade4-132">См. также</span><span class="sxs-lookup"><span data-stu-id="9ade4-132">See also</span></span>

- [<span data-ttu-id="9ade4-133">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9ade4-133">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
