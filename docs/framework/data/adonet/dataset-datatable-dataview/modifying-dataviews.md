---
description: 'Дополнительные сведения: изменение представлений с представлениями'
title: Изменение объектов DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: e0f62c0b8553cd4b83c28da99b8bdec316c8a91d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651838"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="ff22c-103">Изменение объектов DataView</span><span class="sxs-lookup"><span data-stu-id="ff22c-103">Modifying DataViews</span></span>

<span data-ttu-id="ff22c-104">Объект <xref:System.Data.DataView> можно использовать, чтобы добавлять, удалять или изменять строки данных в базовой таблице.</span><span class="sxs-lookup"><span data-stu-id="ff22c-104">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="ff22c-105">Возможность использования **DataView** для изменения данных в базовой таблице контролируется путем установки одного из трех логических свойств **DataView**.</span><span class="sxs-lookup"><span data-stu-id="ff22c-105">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="ff22c-106">А именно: <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A> и <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff22c-106">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="ff22c-107">По умолчанию для них задано **значение true** .</span><span class="sxs-lookup"><span data-stu-id="ff22c-107">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="ff22c-108">Если **AllowNew** имеет **значение true**, можно использовать <xref:System.Data.DataView.AddNew%2A> метод объекта **DataView** для создания нового объекта <xref:System.Data.DataRowView> .</span><span class="sxs-lookup"><span data-stu-id="ff22c-108">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="ff22c-109">Обратите внимание, что новая строка фактически не добавляется в базовую строку <xref:System.Data.DataTable> до тех пор, пока <xref:System.Data.DataRowView.EndEdit%2A> не будет вызван метод **DataRowView** .</span><span class="sxs-lookup"><span data-stu-id="ff22c-109">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="ff22c-110">При <xref:System.Data.DataRowView.CancelEdit%2A> вызове метода **DataRowView** новая строка отбрасывается.</span><span class="sxs-lookup"><span data-stu-id="ff22c-110">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="ff22c-111">Обратите внимание, что в каждый момент времени можно изменять только один **DataRowView** .</span><span class="sxs-lookup"><span data-stu-id="ff22c-111">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="ff22c-112">При вызове метода **AddNew** или **BeginEdit** для **DataRowView** в случае существования ожидающей строки **EndEdit** вызывается неявно для ожидающей строки.</span><span class="sxs-lookup"><span data-stu-id="ff22c-112">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="ff22c-113">При вызове **EndEdit** изменения применяются к базовой **таблице** данных и затем могут быть зафиксированы или отклонены с помощью методов **AcceptChanges** или **RejectChanges** объекта **DataTable**, **DataSet** или **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="ff22c-113">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="ff22c-114">Если **AllowNew** имеет **значение false**, то при вызове метода **AddNew** объекта **DataRowView** выдается исключение.</span><span class="sxs-lookup"><span data-stu-id="ff22c-114">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="ff22c-115">Если **AllowEdit** имеет **значение true**, можно изменить содержимое **DataRow** через **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="ff22c-115">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="ff22c-116">Вы можете подтвердить изменения в базовой строке с помощью **DataRowView. EndEdit** или отклонить изменения с помощью **DataRowView. CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="ff22c-116">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="ff22c-117">Отметим, что одновременно можно изменять только одну строку.</span><span class="sxs-lookup"><span data-stu-id="ff22c-117">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="ff22c-118">При вызове методов **AddNew** или **BeginEdit** для **DataRowView** при наличии ожидающей строки **EndEdit** вызывается неявно для ожидающей строки.</span><span class="sxs-lookup"><span data-stu-id="ff22c-118">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="ff22c-119">При вызове **EndEdit** предлагаемые изменения помещаются в **текущую** версию строки базового объекта **DataRow** и затем могут быть зафиксированы или отклонены с помощью методов **AcceptChanges** или **RejectChanges** объекта **DataTable**, **DataSet** или **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="ff22c-119">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="ff22c-120">Если **AllowEdit** имеет **значение false**, при попытке изменить значение в **объекте DataView** возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="ff22c-120">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="ff22c-121">При редактировании существующего **DataRowView** события базовой **таблицы DataTable** по-прежнему будут создаваться с предложенными изменениями.</span><span class="sxs-lookup"><span data-stu-id="ff22c-121">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="ff22c-122">Обратите внимание, что при вызове **EndEdit** или **CancelEdit** в базовой **DataRow** ожидающие изменения будут применены или отменены независимо от того, вызывается ли **EndEdit** или **CancelEdit** в **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="ff22c-122">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="ff22c-123">Если **алловделете** имеет **значение true**, строки из **DataView** можно удалить с помощью метода **Delete** объекта **DataView** или **DataRowView** , а строки будут удалены из базовой **таблицы** данных.</span><span class="sxs-lookup"><span data-stu-id="ff22c-123">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="ff22c-124">Позже можно зафиксировать или отклонить удаления с помощью **AcceptChanges** или **RejectChanges** соответственно.</span><span class="sxs-lookup"><span data-stu-id="ff22c-124">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="ff22c-125">Если **алловделете** имеет **значение false**, то при вызове метода **Delete** объекта **DataView** или **DataRowView** возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="ff22c-125">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="ff22c-126">Следующий пример кода отключает использование **DataView** для удаления строк и добавляет новую строку в базовую таблицу с помощью **DataView**.</span><span class="sxs-lookup"><span data-stu-id="ff22c-126">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff22c-127">См. также</span><span class="sxs-lookup"><span data-stu-id="ff22c-127">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="ff22c-128">Объекты DataView</span><span class="sxs-lookup"><span data-stu-id="ff22c-128">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="ff22c-129">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ff22c-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
