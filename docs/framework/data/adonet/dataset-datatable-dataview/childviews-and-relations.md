---
description: 'Дополнительные сведения о: ChildView и связи'
title: ChildView и отношения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d475d356-6abb-4701-8fd1-2906fb93dfba
ms.openlocfilehash: f27526ef0ad5bee70b0c67542e2611ff85b156f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739720"
---
# <a name="childviews-and-relations"></a><span data-ttu-id="9cbb5-103">ChildView и отношения</span><span class="sxs-lookup"><span data-stu-id="9cbb5-103">ChildViews and Relations</span></span>

<span data-ttu-id="9cbb5-104">Если какая-то связь существует между таблицами в <xref:System.Data.DataSet>, то можно создать объект <xref:System.Data.DataView>, содержащий строки из связанной дочерней таблицы, с применением метода <xref:System.Data.DataRowView.CreateChildView%2A> объекта <xref:System.Data.DataRowView> по отношению к строкам в родительской таблице.</span><span class="sxs-lookup"><span data-stu-id="9cbb5-104">If a relationship exists between tables in a <xref:System.Data.DataSet>, you can create a <xref:System.Data.DataView> containing rows from the related child table by using the <xref:System.Data.DataRowView.CreateChildView%2A> method of the <xref:System.Data.DataRowView> for the rows in the parent table.</span></span> <span data-ttu-id="9cbb5-105">Например, следующий код отображает **категории** и связанные с ними **продукты** в алфавитном порядке, отсортированном по **CategoryName** и **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="9cbb5-105">For example, the following code displays **Categories** and their related **Products** in alphabetical order sorted by **CategoryName** and **ProductName**.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
Dim prodTable As DataTable = catDS.Tables("Products")  
  
' Create a relation between the Categories and Products tables.  
Dim relation As DataRelation = catDS.Relations.Add("CatProdRel", _  
  catTable.Columns("CategoryID"), _  
  prodTable.Columns("CategoryID"))  
  
' Create DataViews for the Categories and Products tables.  
Dim catView As DataView = New DataView(catTable, "", _  
  "CategoryName", DataViewRowState.CurrentRows)  
Dim prodView As DataView  
  
' Iterate through the Categories table.  
Dim catDRV, prodDRV As DataRowView  
  
For Each catDRV In catView  
  Console.WriteLine(catDRV("CategoryName"))  
  
  ' Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation)  
  prodView.Sort = "ProductName"  
  
  For Each prodDRV In prodView  
    Console.WriteLine(vbTab & prodDRV("ProductName"))  
  Next  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
DataTable prodTable = catDS.Tables["Products"];  
  
// Create a relation between the Categories and Products tables.  
DataRelation relation = catDS.Relations.Add("CatProdRel",
  catTable.Columns["CategoryID"],  
                                                            prodTable.Columns["CategoryID"]);  
  
// Create DataViews for the Categories and Products tables.  
DataView catView = new DataView(catTable, "", "CategoryName",
  DataViewRowState.CurrentRows);  
DataView prodView;  
  
// Iterate through the Categories table.  
foreach (DataRowView catDRV in catView)  
{  
  Console.WriteLine(catDRV["CategoryName"]);  
  
  // Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation);  
  prodView.Sort = "ProductName";  
  
  foreach (DataRowView prodDRV in prodView)  
    Console.WriteLine("\t" + prodDRV["ProductName"]);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cbb5-106">См. также</span><span class="sxs-lookup"><span data-stu-id="9cbb5-106">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="9cbb5-107">Объекты DataView</span><span class="sxs-lookup"><span data-stu-id="9cbb5-107">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="9cbb5-108">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9cbb5-108">ADO.NET Overview</span></span>](../ado-net-overview.md)
