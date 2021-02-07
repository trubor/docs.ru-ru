---
description: Дополнительные сведения о строках и DataRowView
title: Объекты DataRow и DataRowView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: d7700922a9ae76fb9898412b6a08394059e6e494
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724951"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="53068-103">Объекты DataRow и DataRowView</span><span class="sxs-lookup"><span data-stu-id="53068-103">DataRows and DataRowViews</span></span>

<span data-ttu-id="53068-104">Представление <xref:System.Data.DataView> предоставляет перечисляемую коллекцию объектов <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="53068-104">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="53068-105">Объекты **DataRowView** предоставляют значения в виде массивов объектов, индексируемых либо по имени, либо по порядковому номеру столбца в базовой таблице.</span><span class="sxs-lookup"><span data-stu-id="53068-105">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="53068-106">Доступ к представлению <xref:System.Data.DataRow> , предоставляемому **DataRowView** , можно получить с помощью <xref:System.Data.DataRowView.Row%2A> свойства **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="53068-106">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="53068-107">При просмотре значений с помощью **DataRowView** <xref:System.Data.DataView.RowStateFilter%2A> свойство **DataView** определяет, какая версия строки базового объекта **DataRow** предоставляется.</span><span class="sxs-lookup"><span data-stu-id="53068-107">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="53068-108">Сведения о доступе к разным версиям строк с помощью **DataRow** см. в разделе [состояния строк и версии строк](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="53068-108">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="53068-109">В следующем примере кода показаны все текущие и исходные значения в таблице.</span><span class="sxs-lookup"><span data-stu-id="53068-109">The following code example displays all the current and original values in a table.</span></span>  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="53068-110">См. также</span><span class="sxs-lookup"><span data-stu-id="53068-110">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="53068-111">Объекты DataView</span><span class="sxs-lookup"><span data-stu-id="53068-111">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="53068-112">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="53068-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
