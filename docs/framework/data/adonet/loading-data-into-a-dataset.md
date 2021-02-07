---
description: 'Дополнительные сведения: Загрузка данных в набор данных'
title: Загрузка данных в набор данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 167a399d17257008e884fbcccc96de17398b8f88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681686"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="e95ab-103">Загрузка данных в набор данных</span><span class="sxs-lookup"><span data-stu-id="e95ab-103">Loading Data Into a DataSet</span></span>

<span data-ttu-id="e95ab-104"><xref:System.Data.DataSet>Прежде чем можно будет выполнить запрос к нему с помощью LINQ to DataSet, сначала необходимо заполнить объект.</span><span class="sxs-lookup"><span data-stu-id="e95ab-104">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="e95ab-105">Существует несколько способов заполнения объекта <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e95ab-105">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e95ab-106">Например, можно использовать [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] для запроса базы данных и загрузки результатов в <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="e95ab-106">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e95ab-107">Дополнительные сведения см. в разделе [LINQ to SQL](./sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="e95ab-107">For more information, see [LINQ to SQL](./sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="e95ab-108">Другой распространенный способ загрузки данных в объект <xref:System.Data.DataSet> - использование класса <xref:System.Data.Common.DataAdapter> для получения данных из базы данных.</span><span class="sxs-lookup"><span data-stu-id="e95ab-108">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="e95ab-109">Это продемонстрировано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e95ab-109">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e95ab-110">Пример</span><span class="sxs-lookup"><span data-stu-id="e95ab-110">Example</span></span>  

 <span data-ttu-id="e95ab-111">В этом примере объект <xref:System.Data.Common.DataAdapter> используется для запроса к базе данных AdventureWorks, получения сведений о продажах начиная с 2002 года и загрузки результатов в объект <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e95ab-111">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e95ab-112">После <xref:System.Data.DataSet> заполнения можно создавать запросы к нему с помощью LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="e95ab-112">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="e95ab-113">`FillDataSet`Метод в этом примере используется в примерах запросов в [LINQ to DataSet примерах](linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="e95ab-113">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](linq-to-dataset-examples.md).</span></span> <span data-ttu-id="e95ab-114">Дополнительные сведения см. в разделе [запросы к наборам данных](querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="e95ab-114">For more information, see [Querying DataSets](querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="e95ab-115">См. также</span><span class="sxs-lookup"><span data-stu-id="e95ab-115">See also</span></span>

- [<span data-ttu-id="e95ab-116">Общие сведения о LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e95ab-116">LINQ to DataSet Overview</span></span>](linq-to-dataset-overview.md)
- [<span data-ttu-id="e95ab-117">Запросы к DataSet</span><span class="sxs-lookup"><span data-stu-id="e95ab-117">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="e95ab-118">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e95ab-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
