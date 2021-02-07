---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: операторы SET (LINQ to DataSet)'
title: Примеры синтаксиса запросов на основе методов. Операторы набора (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 3a50c9793e3af6fdab08227b4789c4042dd64931
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723755"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="93eab-103">Примеры синтаксиса запросов на основе методов. Операторы набора (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="93eab-103">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="93eab-104">В примерах этого раздела показано, как использовать <xref:System.Linq.Enumerable.Distinct%2A> операторы, <xref:System.Linq.Enumerable.Except%2A> , <xref:System.Linq.Enumerable.Intersect%2A> и <xref:System.Linq.Enumerable.Union%2A> для выполнения операций сравнения на основе наборов строк данных.[ Загрузка данных в набор данных](loading-data-into-a-dataset.md) см. в разделе [Сравнение строк DataRow](comparing-datarows-linq-to-dataset.md) для получения дополнительных сведений о <xref:System.Data.DataRowComparer> .</span><span class="sxs-lookup"><span data-stu-id="93eab-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](loading-data-into-a-dataset.md) See [Comparing DataRows](comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="93eab-105">`FillDataSet`Метод, используемый в этих примерах, задается при [загрузке данных в набор данных](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="93eab-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="93eab-106">В примерах данного раздела используются таблицы Contact, Address, Product, SalesOrderHeader и SalesOrderDetail из образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="93eab-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="93eab-107">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="93eab-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="93eab-108">Дополнительные сведения см. в разделе [инструкции. Создание проекта LINQ to DataSet в Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="93eab-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="93eab-109">Distinct</span><span class="sxs-lookup"><span data-stu-id="93eab-109">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="93eab-110">Пример</span><span class="sxs-lookup"><span data-stu-id="93eab-110">Example</span></span>  

 <span data-ttu-id="93eab-111">В этом примере метод <xref:System.Linq.Enumerable.Distinct%2A> используется для удаления повторяющихся элементов в последовательности.</span><span class="sxs-lookup"><span data-stu-id="93eab-111">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="93eab-112">Исключения</span><span class="sxs-lookup"><span data-stu-id="93eab-112">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="93eab-113">Пример</span><span class="sxs-lookup"><span data-stu-id="93eab-113">Example</span></span>  

 <span data-ttu-id="93eab-114">В этом примере метод <xref:System.Linq.Enumerable.Except%2A> используется, чтобы вернуть контакты, которые есть в первой таблице, но отсутствуют во второй.</span><span class="sxs-lookup"><span data-stu-id="93eab-114">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="93eab-115">Пересечение</span><span class="sxs-lookup"><span data-stu-id="93eab-115">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="93eab-116">Пример</span><span class="sxs-lookup"><span data-stu-id="93eab-116">Example</span></span>  

 <span data-ttu-id="93eab-117">В этом примере используется метод <xref:System.Linq.Enumerable.Intersect%2A>, чтобы вернуть контакты, которые есть в обеих таблицах.</span><span class="sxs-lookup"><span data-stu-id="93eab-117">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="93eab-118">Union</span><span class="sxs-lookup"><span data-stu-id="93eab-118">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="93eab-119">Пример</span><span class="sxs-lookup"><span data-stu-id="93eab-119">Example</span></span>  

 <span data-ttu-id="93eab-120">В этом примере используется метод <xref:System.Linq.Enumerable.Union%2A> для возврата уникальных контактов из двух таблиц.</span><span class="sxs-lookup"><span data-stu-id="93eab-120">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="93eab-121">См. также</span><span class="sxs-lookup"><span data-stu-id="93eab-121">See also</span></span>

- [<span data-ttu-id="93eab-122">Загрузка данных в набор данных</span><span class="sxs-lookup"><span data-stu-id="93eab-122">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="93eab-123">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="93eab-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="93eab-124">Общие сведения о стандартных операторах запроса (C#)</span><span class="sxs-lookup"><span data-stu-id="93eab-124">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="93eab-125">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93eab-125">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
