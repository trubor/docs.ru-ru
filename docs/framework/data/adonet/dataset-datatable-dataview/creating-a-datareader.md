---
description: 'Дополнительные сведения: создание DataReader'
title: Создание объекта DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 3a9f47ce90beaa3da4c2835f8b75e770a6179a9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725107"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="845b1-103">Создание объекта DataReader</span><span class="sxs-lookup"><span data-stu-id="845b1-103">Creating a DataReader</span></span>

<span data-ttu-id="845b1-104">Классы <xref:System.Data.DataTable> и <xref:System.Data.DataSet> имеют метод <xref:System.Data.DataTable.CreateDataReader%2A>, возвращающий содержимое объекта <xref:System.Data.DataTable> или содержимое объекта <xref:System.Data.DataSet> коллекции <xref:System.Data.DataSet.Tables%2A> в виде одного или нескольких доступных для чтения результирующих наборов с последовательным доступом.</span><span class="sxs-lookup"><span data-stu-id="845b1-104">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="845b1-105">Пример</span><span class="sxs-lookup"><span data-stu-id="845b1-105">Example</span></span>  

 <span data-ttu-id="845b1-106">Следующее приложение командной строки создает экземпляр <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="845b1-106">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="845b1-107">Затем в примере передается заполненная <xref:System.Data.DataTable> процедура, которая вызывает <xref:System.Data.DataTable.CreateDataReader%2A> метод, который выполняет итерацию по результатам, содержащимся в <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="845b1-107">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="845b1-108">В этом примере в окне консоли отображаются следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="845b1-108">The example displays the following output in the console window:</span></span>  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="845b1-109">См. также</span><span class="sxs-lookup"><span data-stu-id="845b1-109">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="845b1-110">Объекты DataTableReader</span><span class="sxs-lookup"><span data-stu-id="845b1-110">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="845b1-111">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="845b1-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
