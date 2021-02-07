---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: Join (LINQ to DataSet)'
title: Примеры синтаксиса запросов на основе методов. Соединение (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: f19921ceb874d120a3b50896f3ec82159ef03aac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672703"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="ab434-103">Примеры синтаксиса запросов на основе методов. Соединение (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="ab434-103">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>

<span data-ttu-id="ab434-104">Соединение - важная операция в запросах, которые обращаются к источникам данных без доступных для навигации взаимосвязей, например к таблицам реляционной базы данных.</span><span class="sxs-lookup"><span data-stu-id="ab434-104">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="ab434-105">Соединение двух источников данных представляет собой взаимосвязь объектов одного источника данных с объектами, использующими общий атрибут в другом источнике данных.</span><span class="sxs-lookup"><span data-stu-id="ab434-105">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="ab434-106">Дополнительные сведения см. в разделе Общие сведения [о стандартных операторах запросов (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) или [Общие сведения о стандартных операторах запросов (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ab434-106">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="ab434-107">В примерах данного раздела показано, как использовать метод <xref:System.Linq.Enumerable.Join%2A> для запросов к объекту <xref:System.Data.DataSet> с использованием синтаксиса запросов на основе методов.</span><span class="sxs-lookup"><span data-stu-id="ab434-107">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="ab434-108">`FillDataSet`Метод, используемый в этих примерах, задается при [загрузке данных в набор данных](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ab434-108">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="ab434-109">В примерах данного раздела используются таблицы Contact, Address, Product, SalesOrderHeader и SalesOrderDetail из образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ab434-109">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ab434-110">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="ab434-110">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="ab434-111">Дополнительные сведения см. в разделе [инструкции. Создание проекта LINQ to DataSet в Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ab434-111">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="ab434-112">Join</span><span class="sxs-lookup"><span data-stu-id="ab434-112">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="ab434-113">Пример</span><span class="sxs-lookup"><span data-stu-id="ab434-113">Example</span></span>  

 <span data-ttu-id="ab434-114">В этом примере выполняется соединение таблиц `Contact` и `SalesOrderHeader`.</span><span class="sxs-lookup"><span data-stu-id="ab434-114">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="ab434-115">Пример</span><span class="sxs-lookup"><span data-stu-id="ab434-115">Example</span></span>  

 <span data-ttu-id="ab434-116">В этом примере выполняется соединение таблиц `Contact` и `SalesOrderHeader`, а результаты группируются по идентификатору контактного лица.</span><span class="sxs-lookup"><span data-stu-id="ab434-116">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="ab434-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ab434-117">See also</span></span>

- [<span data-ttu-id="ab434-118">Загрузка данных в набор данных</span><span class="sxs-lookup"><span data-stu-id="ab434-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="ab434-119">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="ab434-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="ab434-120">Общие сведения о стандартных операторах запроса (C#)</span><span class="sxs-lookup"><span data-stu-id="ab434-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ab434-121">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab434-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
