---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: секционирование (LINQ'
title: 'Примеры синтаксиса запросов на основе методов: секционирование (LINQ)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: 1e045fb4f0b627bdb5a926de2272bbaa59abdcee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723781"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="cc7e2-103">Примеры синтаксиса запросов на основе методов: секционирование (LINQ)</span><span class="sxs-lookup"><span data-stu-id="cc7e2-103">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>

<span data-ttu-id="cc7e2-104">В примерах данного раздела показано, как использовать методы <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A> и <xref:System.Linq.Enumerable.TakeWhile%2A> для запросов к объекту <xref:System.Data.DataSet> с использованием синтаксиса выражений запросов.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="cc7e2-105">`FillDataSet`Метод, используемый в этих примерах, задается при [загрузке данных в набор данных](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="cc7e2-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="cc7e2-106">В примерах данного раздела используются таблицы Contact, Address, Product, SalesOrderHeader и SalesOrderDetail из образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="cc7e2-107">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="cc7e2-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="cc7e2-108">Дополнительные сведения см. в разделе [инструкции. Создание проекта LINQ to DataSet в Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="cc7e2-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="cc7e2-109">Пропустить</span><span class="sxs-lookup"><span data-stu-id="cc7e2-109">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="cc7e2-110">Пример</span><span class="sxs-lookup"><span data-stu-id="cc7e2-110">Example</span></span>  

 <span data-ttu-id="cc7e2-111">В данном примере метод <xref:System.Linq.Enumerable.Skip%2A> используется для получения всех контактов из таблицы `Contact`, за исключением первых пяти.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-111">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="cc7e2-112">Пример</span><span class="sxs-lookup"><span data-stu-id="cc7e2-112">Example</span></span>  

 <span data-ttu-id="cc7e2-113">В данном примере используется метод <xref:System.Linq.Enumerable.Skip%2A> для получения всех адресов в Сиэтле (Seattle), кроме первых двух.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-113">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="cc7e2-114">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="cc7e2-114">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="cc7e2-115">Пример</span><span class="sxs-lookup"><span data-stu-id="cc7e2-115">Example</span></span>  

 <span data-ttu-id="cc7e2-116">В этом примере методы <xref:System.Linq.Enumerable.OrderBy%2A> и <xref:System.Linq.Enumerable.SkipWhile%2A> используются для получения из таблицы `Product` продуктов, цена которых по прейскуранту составляет более 300,00.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-116">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="cc7e2-117">Take</span><span class="sxs-lookup"><span data-stu-id="cc7e2-117">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="cc7e2-118">Пример</span><span class="sxs-lookup"><span data-stu-id="cc7e2-118">Example</span></span>  

 <span data-ttu-id="cc7e2-119">В данном примере метод <xref:System.Linq.Enumerable.Take%2A> используется для получения только первых пяти контактов из таблицы `Contact`.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-119">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="cc7e2-120">Пример</span><span class="sxs-lookup"><span data-stu-id="cc7e2-120">Example</span></span>  

 <span data-ttu-id="cc7e2-121">В данном примере используется метод <xref:System.Linq.Enumerable.Take%2A> для получения первых трех адресов в Сиэтле (Seattle).</span><span class="sxs-lookup"><span data-stu-id="cc7e2-121">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="cc7e2-122">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="cc7e2-122">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="cc7e2-123">Пример</span><span class="sxs-lookup"><span data-stu-id="cc7e2-123">Example</span></span>  

 <span data-ttu-id="cc7e2-124">В этом примере методы <xref:System.Linq.Enumerable.OrderBy%2A> и <xref:System.Linq.Enumerable.TakeWhile%2A> используются для получения из таблицы `Product` продуктов, цена которых по прейскуранту составляет менее 300,00.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-124">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="cc7e2-125">См. также</span><span class="sxs-lookup"><span data-stu-id="cc7e2-125">See also</span></span>

- [<span data-ttu-id="cc7e2-126">Загрузка данных в набор данных</span><span class="sxs-lookup"><span data-stu-id="cc7e2-126">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="cc7e2-127">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="cc7e2-127">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="cc7e2-128">Общие сведения о стандартных операторах запроса (C#)</span><span class="sxs-lookup"><span data-stu-id="cc7e2-128">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="cc7e2-129">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc7e2-129">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
