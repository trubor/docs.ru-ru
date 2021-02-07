---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: упорядочение (LINQ to DataSet)'
title: Примеры синтаксиса запросов на основе методов. Упорядочение (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: d655ff52fe30a9af15245a4c9989062107bb6842
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672664"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="8bb6c-103">Примеры синтаксиса запросов на основе методов. Упорядочение (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8bb6c-103">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>

<span data-ttu-id="8bb6c-104">В примерах данного раздела показано, как применять методы <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Reverse%2A> и <xref:System.Linq.Enumerable.ThenBy%2A> для запроса к объекту <xref:System.Data.DataSet> и упорядочения результатов с использованием синтаксиса запросов на основе методов.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="8bb6c-105">`FillDataSet`Метод, используемый в этих примерах, задается при [загрузке данных в набор данных](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="8bb6c-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="8bb6c-106">В примерах данного раздела используются таблицы Contact, Address, Product, SalesOrderHeader и SalesOrderDetail из образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8bb6c-107">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="8bb6c-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="8bb6c-108">Дополнительные сведения см. в разделе [инструкции. Создание проекта LINQ to DataSet в Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8bb6c-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="8bb6c-109">OrderBy</span><span class="sxs-lookup"><span data-stu-id="8bb6c-109">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="8bb6c-110">Пример</span><span class="sxs-lookup"><span data-stu-id="8bb6c-110">Example</span></span>  

 <span data-ttu-id="8bb6c-111">В этом примере метод <xref:System.Linq.Enumerable.OrderBy%2A> используется с пользовательским сравнивающим классом для сортировки фамилий с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-111">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="8bb6c-112">Reverse</span><span class="sxs-lookup"><span data-stu-id="8bb6c-112">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="8bb6c-113">Пример</span><span class="sxs-lookup"><span data-stu-id="8bb6c-113">Example</span></span>  

 <span data-ttu-id="8bb6c-114">В этом примере метод <xref:System.Linq.Enumerable.Reverse%2A> используется для создания списка заказов, в которых `OrderDate` предшествует 20 февраля 2002 г.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-114">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="8bb6c-115">ThenBy</span><span class="sxs-lookup"><span data-stu-id="8bb6c-115">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="8bb6c-116">Пример</span><span class="sxs-lookup"><span data-stu-id="8bb6c-116">Example</span></span>  

 <span data-ttu-id="8bb6c-117">В этом примере методы <xref:System.Linq.Enumerable.OrderBy%2A> и <xref:System.Linq.Enumerable.ThenBy%2A> используются с пользовательским сравнивающим классом сначала для сортировки по цене по прейскуранту, а затем по названию продукта в убывающем порядке с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-117">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="8bb6c-118">См. также</span><span class="sxs-lookup"><span data-stu-id="8bb6c-118">See also</span></span>

- [<span data-ttu-id="8bb6c-119">Загрузка данных в набор данных</span><span class="sxs-lookup"><span data-stu-id="8bb6c-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="8bb6c-120">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8bb6c-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="8bb6c-121">Общие сведения о стандартных операторах запроса (C#)</span><span class="sxs-lookup"><span data-stu-id="8bb6c-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8bb6c-122">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bb6c-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
