---
description: 'Дополнительные сведения: удаление DataRow'
title: Удаление DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: fff3117256629c2fa0262e2aa163da09174390dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739577"
---
# <a name="datarow-deletion"></a><span data-ttu-id="949b2-103">Удаление DataRow</span><span class="sxs-lookup"><span data-stu-id="949b2-103">DataRow Deletion</span></span>

<span data-ttu-id="949b2-104">Существует два метода, которые можно использовать для удаления <xref:System.Data.DataRow> объекта из <xref:System.Data.DataTable> объекта: метод **Remove** <xref:System.Data.DataRowCollection> объекта и <xref:System.Data.DataRow.Delete%2A> метод объекта **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="949b2-104">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="949b2-105">В то время как <xref:System.Data.DataRowCollection.Remove%2A> метод удаляет **DataRow** из **датаровколлектион**, <xref:System.Data.DataRow.Delete%2A> метод помечает только строку для удаления.</span><span class="sxs-lookup"><span data-stu-id="949b2-105">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="949b2-106">Фактическое удаление происходит, когда приложение вызывает метод **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="949b2-106">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="949b2-107">Использование метода <xref:System.Data.DataRow.Delete%2A> позволяет программно проверять, какие строки помечены для удаления, перед их фактическим удалением.</span><span class="sxs-lookup"><span data-stu-id="949b2-107">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="949b2-108">Когда строка отмечена для удаления, ее свойство <xref:System.Data.DataRow.RowState%2A> имеет значение <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="949b2-108">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="949b2-109">Ни <xref:System.Data.DataRow.Delete%2A>, ни <xref:System.Data.DataRowCollection.Remove%2A> не должны вызываться в цикле foreach во время итерации по объекту <xref:System.Data.DataRowCollection>.</span><span class="sxs-lookup"><span data-stu-id="949b2-109">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="949b2-110">Ни <xref:System.Data.DataRow.Delete%2A>, ни <xref:System.Data.DataRowCollection.Remove%2A> не изменяет состояние коллекции.</span><span class="sxs-lookup"><span data-stu-id="949b2-110"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="949b2-111">При использовании <xref:System.Data.DataSet> **таблицы** данных или в сочетании с **DataAdapter** и реляционным источником данных используйте метод **Delete** объекта **DataRow** для удаления строки.</span><span class="sxs-lookup"><span data-stu-id="949b2-111">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="949b2-112">Метод **Delete** помечает строку как **удаленную** в **наборе данных** или **DataTable** , но не удаляет ее.</span><span class="sxs-lookup"><span data-stu-id="949b2-112">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="949b2-113">Вместо этого, когда **DataAdapter** обнаруживает строку, помеченную как **Удаленная**, она выполняет метод **DeleteCommand** для удаления строки в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="949b2-113">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="949b2-114">Затем строку можно удалить без возможности восстановления с помощью метода **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="949b2-114">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="949b2-115">При использовании метода **Remove** для удаления строки строка удаляется полностью из таблицы, но **DataAdapter** не удаляет строку в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="949b2-115">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="949b2-116">Метод **Remove** объекта **датаровколлектион** принимает **DataRow** в качестве аргумента и удаляет его из коллекции, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="949b2-116">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="949b2-117">В следующем примере показано, как вызвать метод **Delete** для **DataRow** , чтобы изменить его свойство **RowState** на **deleted**.</span><span class="sxs-lookup"><span data-stu-id="949b2-117">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="949b2-118">Если строка помечена для удаления и вызывается метод **AcceptChanges** объекта **DataTable** , то строка удаляется из **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="949b2-118">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="949b2-119">В отличие от этого, при вызове RejectChanges **RowState** строки восстанавливается до того, как она была помечена как **Удаленная**.</span><span class="sxs-lookup"><span data-stu-id="949b2-119">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="949b2-120">Если **добавляется** **RowState** объекта **DataRow** , то есть он был только что добавлен в таблицу, а затем помечается как **Удаленный**, он удаляется из таблицы.</span><span class="sxs-lookup"><span data-stu-id="949b2-120">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="949b2-121">См. также</span><span class="sxs-lookup"><span data-stu-id="949b2-121">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="949b2-122">Управление данными в таблице данных</span><span class="sxs-lookup"><span data-stu-id="949b2-122">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="949b2-123">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="949b2-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
