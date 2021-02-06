---
description: 'Дополнительные сведения: примеры операторов DataSet-Specific (LINQ to DataSet)'
title: Связанные с определенными наборами данных примеры операторов (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 2fd54453621ce180901aaf6fbb5b975067ad9831
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651331"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="b31e0-103">Связанные с определенными наборами данных примеры операторов (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="b31e0-103">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="b31e0-104">В примерах этого раздела показано, как использовать методы <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> и класс <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="b31e0-104">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="b31e0-105">`FillDataSet`Метод, используемый в этих примерах, задается при [загрузке данных в набор данных](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="b31e0-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="b31e0-106">В примерах данного раздела используются таблицы Contact, Address, Product, SalesOrderHeader и SalesOrderDetail из образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b31e0-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b31e0-107">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="b31e0-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="b31e0-108">Дополнительные сведения см. в разделе [инструкции. Создание проекта LINQ to DataSet в Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b31e0-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="b31e0-109">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="b31e0-109">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="b31e0-110">Пример</span><span class="sxs-lookup"><span data-stu-id="b31e0-110">Example</span></span>  

 <span data-ttu-id="b31e0-111">В данном примере в объект <xref:System.Data.DataTable> загружаются результаты запроса с помощью метода <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="b31e0-111">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="b31e0-112">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="b31e0-112">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="b31e0-113">Пример</span><span class="sxs-lookup"><span data-stu-id="b31e0-113">Example</span></span>  

 <span data-ttu-id="b31e0-114">В данном примере две строки данных сравниваются с помощью класса <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="b31e0-114">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="b31e0-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b31e0-115">See also</span></span>

- [<span data-ttu-id="b31e0-116">Загрузка данных в набор данных</span><span class="sxs-lookup"><span data-stu-id="b31e0-116">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="b31e0-117">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="b31e0-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
