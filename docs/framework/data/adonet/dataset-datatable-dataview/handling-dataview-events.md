---
description: Дополнительные сведения см. в статье обработка событий DataView.
title: Обработка событий DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: d3e72adefa6b320d48b90d481a20644b62009cdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652319"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="23b8b-103">Обработка событий DataView</span><span class="sxs-lookup"><span data-stu-id="23b8b-103">Handling DataView Events</span></span>

<span data-ttu-id="23b8b-104">Событие <xref:System.Data.DataView.ListChanged> объекта <xref:System.Data.DataView> используется для определения того, было ли обновлено представление.</span><span class="sxs-lookup"><span data-stu-id="23b8b-104">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="23b8b-105">К обновлениям, которые вызывают это событие, относятся добавление, удаление или изменение строки в базовой таблице, добавление или удаление столбца из схемы базовой таблицы, изменение в родительской или дочерней связи.</span><span class="sxs-lookup"><span data-stu-id="23b8b-105">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="23b8b-106">Событие **ListChanged** также уведомляет вас, если список просматриваемых строк существенно изменился из-за применения нового порядка сортировки или фильтра.</span><span class="sxs-lookup"><span data-stu-id="23b8b-106">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="23b8b-107">Событие **ListChanged** реализует делегат **листчанжедевенсандлер** <xref:System.ComponentModel> пространства имен и принимает в качестве входных данных <xref:System.ComponentModel.ListChangedEventArgs> объект.</span><span class="sxs-lookup"><span data-stu-id="23b8b-107">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="23b8b-108">Вы можете определить, какой тип изменения произошло с помощью <xref:System.ComponentModel.ListChangedType> значения перечисления в свойстве **ListChangedType** объекта **ListChangedEventArgs** .</span><span class="sxs-lookup"><span data-stu-id="23b8b-108">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="23b8b-109">Для изменений, затрагивающих Добавление, удаление или перемещение строк, можно получить доступ к новому индексу добавленной или перемещенной строки и предыдущему индексу удаленной строки с помощью свойства **невиндекс** объекта **ListChangedEventArgs** .</span><span class="sxs-lookup"><span data-stu-id="23b8b-109">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="23b8b-110">В случае перемещенной строки доступ к предыдущему индексу перемещенной строки можно получить с помощью свойства **олдиндекс** объекта **ListChangedEventArgs** .</span><span class="sxs-lookup"><span data-stu-id="23b8b-110">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="23b8b-111">**DataViewManager** также предоставляет событие **ListChanged** для уведомления о том, что таблица была добавлена или удалена, или если в коллекцию **связей** базового **набора данных** было внесено изменение.</span><span class="sxs-lookup"><span data-stu-id="23b8b-111">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="23b8b-112">В следующем примере кода показано, как добавить обработчик событий **ListChanged** .</span><span class="sxs-lookup"><span data-stu-id="23b8b-112">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="23b8b-113">См. также</span><span class="sxs-lookup"><span data-stu-id="23b8b-113">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="23b8b-114">Объекты DataView</span><span class="sxs-lookup"><span data-stu-id="23b8b-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="23b8b-115">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="23b8b-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
