---
description: 'Дополнительные сведения см. в статье примеры синтаксиса выражений запросов: упорядочение'
title: Примеры синтаксиса выражений запросов. Упорядочение
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: 931225344311e8dde6318564ddeba6eae0e2411d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696104"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="b34a4-103">Примеры синтаксиса выражений запросов. Упорядочение</span><span class="sxs-lookup"><span data-stu-id="b34a4-103">Query Expression Syntax Examples: Ordering</span></span>

<span data-ttu-id="b34a4-104">В примерах этого раздела показано, как использовать `OrderBy` методы и `OrderByDescending` для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса выражения запроса.</span><span class="sxs-lookup"><span data-stu-id="b34a4-104">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="b34a4-105">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b34a4-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b34a4-106">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="b34a4-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="b34a4-107">OrderBy</span><span class="sxs-lookup"><span data-stu-id="b34a4-107">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="b34a4-108">Пример</span><span class="sxs-lookup"><span data-stu-id="b34a4-108">Example</span></span>  

 <span data-ttu-id="b34a4-109">В следующем примере выражение <xref:System.Linq.Enumerable.OrderBy%2A> используется для возвращения списка контактов, упорядоченного по фамилии.</span><span class="sxs-lookup"><span data-stu-id="b34a4-109">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="b34a4-110">Пример</span><span class="sxs-lookup"><span data-stu-id="b34a4-110">Example</span></span>  

 <span data-ttu-id="b34a4-111">В следующем примере выражение <xref:System.Linq.Enumerable.OrderBy%2A> используется для сортировки контактов по длине фамилии.</span><span class="sxs-lookup"><span data-stu-id="b34a4-111">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="b34a4-112">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="b34a4-112">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="b34a4-113">Пример</span><span class="sxs-lookup"><span data-stu-id="b34a4-113">Example</span></span>  

 <span data-ttu-id="b34a4-114">В следующем примере выражение `orderby… descending` (`Order By … Descending` на Visual Basic), эквивалентное методу <xref:System.Linq.Enumerable.OrderByDescending%2A>, используется для сортировки прейскуранта по убыванию.</span><span class="sxs-lookup"><span data-stu-id="b34a4-114">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="b34a4-115">ThenBy</span><span class="sxs-lookup"><span data-stu-id="b34a4-115">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="b34a4-116">Пример</span><span class="sxs-lookup"><span data-stu-id="b34a4-116">Example</span></span>  

 <span data-ttu-id="b34a4-117">В следующем примере выражения <xref:System.Linq.Queryable.OrderBy%2A> и <xref:System.Linq.Queryable.ThenBy%2A> используются для возвращения списка контактов, упорядоченных вначале по фамилии, затем по имени.</span><span class="sxs-lookup"><span data-stu-id="b34a4-117">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="b34a4-118">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="b34a4-118">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="b34a4-119">Пример</span><span class="sxs-lookup"><span data-stu-id="b34a4-119">Example</span></span>  

 <span data-ttu-id="b34a4-120">В следующем примере выражение `OrderBy… Descending`, эквивалентное методу <xref:System.Linq.Enumerable.ThenByDescending%2A>, используется для сортировки списка продуктов: вначале по названию, затем по прейскурантной цене - по убыванию.</span><span class="sxs-lookup"><span data-stu-id="b34a4-120">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="b34a4-121">См. также</span><span class="sxs-lookup"><span data-stu-id="b34a4-121">See also</span></span>

- [<span data-ttu-id="b34a4-122">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b34a4-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
