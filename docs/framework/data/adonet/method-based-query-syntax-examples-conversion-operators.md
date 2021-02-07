---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: операторы преобразования (LINQ to DataSet)'
title: Примеры синтаксиса запросов на основе методов. Операторы преобразования (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 958e5c0ac1d1d8a98e6099ffcad055e78f07b23e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672742"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="fe68f-103">Примеры синтаксиса запросов на основе методов. Операторы преобразования (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="fe68f-103">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="fe68f-104">Примеры в данном разделе демонстрируют, как использовать методы <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> и <xref:System.Linq.Enumerable.ToList%2A> для немедленного выполнения выражения запроса.</span><span class="sxs-lookup"><span data-stu-id="fe68f-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="fe68f-105">`FillDataSet`Метод, используемый в этих примерах, задается при [загрузке данных в набор данных](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="fe68f-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="fe68f-106">В примерах данного раздела используются таблицы Contact, Address, Product, SalesOrderHeader и SalesOrderDetail из образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fe68f-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="fe68f-107">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="fe68f-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="fe68f-108">Дополнительные сведения см. в разделе [инструкции. Создание проекта LINQ to DataSet в Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="fe68f-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="fe68f-109">ToArray</span><span class="sxs-lookup"><span data-stu-id="fe68f-109">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="fe68f-110">Пример</span><span class="sxs-lookup"><span data-stu-id="fe68f-110">Example</span></span>  

 <span data-ttu-id="fe68f-111">В этом примере метод <xref:System.Linq.Enumerable.ToArray%2A> используется для немедленного преобразования последовательности в массив.</span><span class="sxs-lookup"><span data-stu-id="fe68f-111">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="fe68f-112">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="fe68f-112">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="fe68f-113">Пример</span><span class="sxs-lookup"><span data-stu-id="fe68f-113">Example</span></span>  

 <span data-ttu-id="fe68f-114">В этом примере метод <xref:System.Linq.Enumerable.ToDictionary%2A> используется для немедленного преобразования последовательности и связанного выражения ключа в словарь.</span><span class="sxs-lookup"><span data-stu-id="fe68f-114">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="fe68f-115">ToList</span><span class="sxs-lookup"><span data-stu-id="fe68f-115">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="fe68f-116">Пример</span><span class="sxs-lookup"><span data-stu-id="fe68f-116">Example</span></span>  

 <span data-ttu-id="fe68f-117">В этом примере метод <xref:System.Linq.Enumerable.ToList%2A> используется для немедленного преобразования последовательности в объект <xref:System.Collections.Generic.List%601>, где `T` - тип объекта <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="fe68f-117">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="fe68f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="fe68f-118">See also</span></span>

- [<span data-ttu-id="fe68f-119">Загрузка данных в набор данных</span><span class="sxs-lookup"><span data-stu-id="fe68f-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="fe68f-120">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="fe68f-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="fe68f-121">Общие сведения о стандартных операторах запроса (C#)</span><span class="sxs-lookup"><span data-stu-id="fe68f-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="fe68f-122">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe68f-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
