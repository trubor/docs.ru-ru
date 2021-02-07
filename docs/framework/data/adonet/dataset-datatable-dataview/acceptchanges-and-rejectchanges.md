---
description: 'Дополнительные сведения о: AcceptChanges и RejectChanges'
title: AcceptChanges и RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: e21952063bf27f4f969669eb76b964fc7537b59a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725263"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="2bd06-103">AcceptChanges и RejectChanges</span><span class="sxs-lookup"><span data-stu-id="2bd06-103">AcceptChanges and RejectChanges</span></span>

<span data-ttu-id="2bd06-104">После проверки точности изменений, внесенных в данные в <xref:System.Data.DataTable> , можно принять изменения с помощью <xref:System.Data.DataRow.AcceptChanges%2A> метода <xref:System.Data.DataRow> , <xref:System.Data.DataTable> или <xref:System.Data.DataSet> , который установит **текущие** значения строк в качестве **исходных** значений, и установит для свойства **RowState** значение **без изменений**.</span><span class="sxs-lookup"><span data-stu-id="2bd06-104">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="2bd06-105">При принятии или отклонении изменений удаляется любая **роверрор** информация, а свойству **HasErrors** присваивается **значение false**.</span><span class="sxs-lookup"><span data-stu-id="2bd06-105">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="2bd06-106">Принятие или отклонение изменений также может затрагивать обновление данных в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="2bd06-106">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="2bd06-107">Дополнительные сведения см. в разделе [Обновление источников данных с помощью DataAdapter](../updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="2bd06-107">For more information, see [Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="2bd06-108">Если в **DataTable** существуют ограничения внешнего ключа, изменения, принятые или Отклоненные с помощью **AcceptChanges** и **RejectChanges** , распространяются на дочерние строки **DataRow** в соответствии с объектом **ForeignKeyConstraint. акцептрежектруле**.</span><span class="sxs-lookup"><span data-stu-id="2bd06-108">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="2bd06-109">Дополнительные сведения см. в разделе [ограничения DataTable](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="2bd06-109">For more information, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="2bd06-110">В следующем примере происходит проверка на наличие строк с ошибками, по возможности устраняются ошибки и отклоняются строки, в которых ошибка не может быть устранена.</span><span class="sxs-lookup"><span data-stu-id="2bd06-110">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="2bd06-111">Обратите внимание, что для разрешенных ошибок значение **роверрор** сбрасывается в пустую строку, в результате чего свойство **HasErrors** устанавливается в значение **false**.</span><span class="sxs-lookup"><span data-stu-id="2bd06-111">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="2bd06-112">Если все строки с ошибками были разрешены или отклонены, вызывается метод **AcceptChanges** , чтобы принять все изменения для всей **таблицы DataTable**.</span><span class="sxs-lookup"><span data-stu-id="2bd06-112">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bd06-113">См. также</span><span class="sxs-lookup"><span data-stu-id="2bd06-113">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="2bd06-114">Управление данными в таблице данных</span><span class="sxs-lookup"><span data-stu-id="2bd06-114">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="2bd06-115">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2bd06-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
