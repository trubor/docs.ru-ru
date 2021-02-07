---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: статистические операторы'
title: Примеры синтаксиса запросов на основе методов. Статистические операторы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 26398af95398905f2e28c603ef90a04a4a2c56bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673619"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="aa2e1-103">Примеры синтаксиса запросов на основе методов. Статистические операторы</span><span class="sxs-lookup"><span data-stu-id="aa2e1-103">Method-Based Query Syntax Examples: Aggregate Operators</span></span>

<span data-ttu-id="aa2e1-104">В примерах этого раздела показано, как использовать <xref:System.Linq.Enumerable.Aggregate%2A> методы, <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Count%2A> ,,, <xref:System.Linq.Enumerable.LongCount%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> и <xref:System.Linq.Enumerable.Sum%2A> для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса запросов на основе методов.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="aa2e1-105">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="aa2e1-106">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="aa2e1-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="aa2e1-107">Среднее значение</span><span class="sxs-lookup"><span data-stu-id="aa2e1-107">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa2e1-108">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-108">Example</span></span>  

 <span data-ttu-id="aa2e1-109">В следующем примере применяется метод <xref:System.Linq.Enumerable.Average%2A> для нахождения средней цены по прейскуранту продуктов.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-109">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-110">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-110">Example</span></span>  

 <span data-ttu-id="aa2e1-111">В следующем примере используется метод <xref:System.Linq.Enumerable.Average%2A> для нахождения средней цены по прейскуранту для продуктов каждого типа.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-111">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-112">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-112">Example</span></span>  

 <span data-ttu-id="aa2e1-113">В следующем примере применяется метод <xref:System.Linq.Enumerable.Average%2A> для нахождения средней суммы заказа.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-113">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-114">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-114">Example</span></span>  

 <span data-ttu-id="aa2e1-115">В следующем примере используется метод <xref:System.Linq.Enumerable.Average%2A> для получения средней суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-115">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-116">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-116">Example</span></span>  

 <span data-ttu-id="aa2e1-117">В следующем примере используется метод <xref:System.Linq.Enumerable.Average%2A> для возврата заказов со средней суммой заказа для каждого контактного лица.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-117">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="aa2e1-118">Count</span><span class="sxs-lookup"><span data-stu-id="aa2e1-118">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa2e1-119">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-119">Example</span></span>  

 <span data-ttu-id="aa2e1-120">В следующем примере применяется метод <xref:System.Linq.Enumerable.Count%2A> для возврата количества продуктов в таблице Product.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-120">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-121">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-121">Example</span></span>  

 <span data-ttu-id="aa2e1-122">В следующем примере используется метод <xref:System.Linq.Enumerable.Count%2A> для возврата списка идентификаторов контактных лиц и определения того, сколько заказов имеет каждый из них.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-122">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-123">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-123">Example</span></span>  

 <span data-ttu-id="aa2e1-124">В следующем примере продукты группируются по цвету и используется метод <xref:System.Linq.Enumerable.Count%2A> для возврата количества продуктов в каждой цветовой группе.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-124">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="aa2e1-125">LongCount</span><span class="sxs-lookup"><span data-stu-id="aa2e1-125">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa2e1-126">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-126">Example</span></span>  

 <span data-ttu-id="aa2e1-127">В следующем примере происходит возврат количества контактов с применением типа данных Long Integer.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-127">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="aa2e1-128">Max</span><span class="sxs-lookup"><span data-stu-id="aa2e1-128">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa2e1-129">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-129">Example</span></span>  

 <span data-ttu-id="aa2e1-130">В следующем примере используется метод <xref:System.Linq.Enumerable.Max%2A> для возврата наибольшей суммы заказа.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-130">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-131">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-131">Example</span></span>  

 <span data-ttu-id="aa2e1-132">В следующем примере используется метод <xref:System.Linq.Enumerable.Max%2A> для получения наибольшей суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-132">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-133">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-133">Example</span></span>  

 <span data-ttu-id="aa2e1-134">В следующем примере используется метод <xref:System.Linq.Enumerable.Max%2A> для получения наибольшей суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-134">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="aa2e1-135">Min</span><span class="sxs-lookup"><span data-stu-id="aa2e1-135">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa2e1-136">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-136">Example</span></span>  

 <span data-ttu-id="aa2e1-137">В следующем примере используется метод <xref:System.Linq.Enumerable.Min%2A> для возврата наименьшей суммы заказа.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-137">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-138">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-138">Example</span></span>  

 <span data-ttu-id="aa2e1-139">В следующем примере используется метод <xref:System.Linq.Enumerable.Min%2A> для получения заказов с наименьшей суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-139">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-140">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-140">Example</span></span>  

 <span data-ttu-id="aa2e1-141">В следующем примере используется метод <xref:System.Linq.Enumerable.Min%2A> для получения заказов с наименьшей суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-141">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="aa2e1-142">SUM</span><span class="sxs-lookup"><span data-stu-id="aa2e1-142">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa2e1-143">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-143">Example</span></span>  

 <span data-ttu-id="aa2e1-144">В следующем примере используется метод <xref:System.Linq.Enumerable.Sum%2A>, который возвращает общую сумму количества продуктов в заказах из таблицы SalesOrderDetail.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-144">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="aa2e1-145">Пример</span><span class="sxs-lookup"><span data-stu-id="aa2e1-145">Example</span></span>  

 <span data-ttu-id="aa2e1-146">В следующем примере используется метод <xref:System.Linq.Enumerable.Sum%2A> для получения суммы заказа для каждого идентификатора контактного лица.</span><span class="sxs-lookup"><span data-stu-id="aa2e1-146">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="aa2e1-147">См. также</span><span class="sxs-lookup"><span data-stu-id="aa2e1-147">See also</span></span>

- [<span data-ttu-id="aa2e1-148">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="aa2e1-148">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
