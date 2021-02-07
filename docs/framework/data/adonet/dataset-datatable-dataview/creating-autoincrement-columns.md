---
description: 'Дополнительные сведения: создание столбцов с автоувеличением'
title: Создание столбцов AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 7568b1013b7af5aef7a6fc1f28dc163a082743a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739642"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="93e0e-103">Создание столбцов AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="93e0e-103">Creating AutoIncrement Columns</span></span>

<span data-ttu-id="93e0e-104">Чтобы обеспечить наличие в столбце уникальных значений, можно указать, что значения в столбце должны увеличиваться автоматически при добавлении новых строк к таблице.</span><span class="sxs-lookup"><span data-stu-id="93e0e-104">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="93e0e-105">Чтобы создать автоматическое приращение <xref:System.Data.DataColumn> , присвойте <xref:System.Data.DataColumn.AutoIncrement%2A> свойству столбца значение **true**.</span><span class="sxs-lookup"><span data-stu-id="93e0e-105">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="93e0e-106"><xref:System.Data.DataColumn>Затем начинается со значения, определенного в <xref:System.Data.DataColumn.AutoIncrementSeed%2A> свойстве, и при добавлении каждой строки значение столбца **AutoIncrement** увеличивается на значение, определенное в <xref:System.Data.DataColumn.AutoIncrementStep%2A> свойстве столбца.</span><span class="sxs-lookup"><span data-stu-id="93e0e-106">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="93e0e-107">Для столбцов с **автоувеличением** рекомендуется, <xref:System.Data.DataColumn.ReadOnly%2A> чтобы свойство **DataColumn** было установлено в **значение true**.</span><span class="sxs-lookup"><span data-stu-id="93e0e-107">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="93e0e-108">В следующем примере показано, как создать столбец, значения в котором начинаются с 200 и каждый раз увеличиваются с шагом 3.</span><span class="sxs-lookup"><span data-stu-id="93e0e-108">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="93e0e-109">См. также</span><span class="sxs-lookup"><span data-stu-id="93e0e-109">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="93e0e-110">Определение схемы таблицы данных</span><span class="sxs-lookup"><span data-stu-id="93e0e-110">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="93e0e-111">DataTables</span><span class="sxs-lookup"><span data-stu-id="93e0e-111">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="93e0e-112">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="93e0e-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
