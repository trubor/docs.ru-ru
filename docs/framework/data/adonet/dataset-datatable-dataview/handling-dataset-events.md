---
description: 'Дополнительные сведения: обработка событий набора данных'
title: Обработка событий наборов данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: a0000396c7c1e2762a5a2937f7979d917257facc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652371"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="049ea-103">Обработка событий наборов данных</span><span class="sxs-lookup"><span data-stu-id="049ea-103">Handling DataSet Events</span></span>

<span data-ttu-id="049ea-104">Объект <xref:System.Data.DataSet> предоставляет три события: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>и <xref:System.Data.DataSet.MergeFailed>.</span><span class="sxs-lookup"><span data-stu-id="049ea-104">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="049ea-105">Событие MergeFailed</span><span class="sxs-lookup"><span data-stu-id="049ea-105">The MergeFailed Event</span></span>  

 <span data-ttu-id="049ea-106">Наиболее часто используемым событием объекта `DataSet` является `MergeFailed`, которое вызывается, когда возникает конфликт в схеме объектов `DataSet` , подвергнутых слиянию.</span><span class="sxs-lookup"><span data-stu-id="049ea-106">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="049ea-107">Это происходит, когда целевой и исходный объекты <xref:System.Data.DataRow> имеют одинаковое значение первичного ключа, и свойству <xref:System.Data.DataSet.EnforceConstraints%2A> присваивается значение `true`.</span><span class="sxs-lookup"><span data-stu-id="049ea-107">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="049ea-108">Например, если столбцы первичного ключа таблицы, подвергнутые слиянию, совпадают в таблицах двух объектов `DataSet` , то возникает исключение и вызывается событие `MergeFailed` .</span><span class="sxs-lookup"><span data-stu-id="049ea-108">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="049ea-109">Объект <xref:System.Data.MergeFailedEventArgs> , переданный событию `MergeFailed` , имеет свойство <xref:System.Data.MergeFailedEventArgs.Conflict%2A> , определяющее конфликт в схеме между двумя объектами `DataSet` , и свойство <xref:System.Data.MergeFailedEventArgs.Table%2A> , определяющее имя таблицы, участвующей в конфликте.</span><span class="sxs-lookup"><span data-stu-id="049ea-109">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="049ea-110">В следующем фрагменте кода показан способ добавления обработчика события `MergeFailed` .</span><span class="sxs-lookup"><span data-stu-id="049ea-110">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a><span data-ttu-id="049ea-111">Инициализированное событие</span><span class="sxs-lookup"><span data-stu-id="049ea-111">The Initialized Event</span></span>  

 <span data-ttu-id="049ea-112">Событие <xref:System.Data.DataSet.Initialized> происходит после инициализации нового экземпляра `DataSet` конструктором `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="049ea-112">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="049ea-113">Свойство <xref:System.Data.DataSet.IsInitialized%2A> возвращает значение `true` , если `DataSet` выполнил инициализацию. В противном случае оно возвращает значение `false`.</span><span class="sxs-lookup"><span data-stu-id="049ea-113">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="049ea-114">Метод <xref:System.Data.DataSet.BeginInit%2A> , который начинает инициализацию `DataSet`, присваивает свойству <xref:System.Data.DataSet.IsInitialized%2A> значение `false`.</span><span class="sxs-lookup"><span data-stu-id="049ea-114">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="049ea-115">Метод <xref:System.Data.DataSet.EndInit%2A> , который заканчивает инициализацию `DataSet`, присваивает свойству значение `true`.</span><span class="sxs-lookup"><span data-stu-id="049ea-115">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="049ea-116">Эти методы используются средой разработки Visual Studio для инициализации `DataSet` , которая используется другим компонентом.</span><span class="sxs-lookup"><span data-stu-id="049ea-116">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="049ea-117">Они редко используются в коде.</span><span class="sxs-lookup"><span data-stu-id="049ea-117">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="049ea-118">Удаленное событие</span><span class="sxs-lookup"><span data-stu-id="049ea-118">The Disposed Event</span></span>  

 <span data-ttu-id="049ea-119">`DataSet` является производным от класса <xref:System.ComponentModel.MarshalByValueComponent> , который предоставляет и метод <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> , и событие <xref:System.ComponentModel.MarshalByValueComponent.Disposed> .</span><span class="sxs-lookup"><span data-stu-id="049ea-119">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="049ea-120"><xref:System.ComponentModel.MarshalByValueComponent.Disposed>Событие добавляет обработчик событий для прослушивания ликвидированного события в компоненте.</span><span class="sxs-lookup"><span data-stu-id="049ea-120">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="049ea-121"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> `DataSet` Если требуется выполнить код при вызове метода, можно использовать событие <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> .</span><span class="sxs-lookup"><span data-stu-id="049ea-121">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="049ea-122"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> Освобождает ресурсы, используемые <xref:System.ComponentModel.MarshalByValueComponent> .</span><span class="sxs-lookup"><span data-stu-id="049ea-122"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="049ea-123">`DataSet`Объекты и `DataTable` наследуются от <xref:System.ComponentModel.MarshalByValueComponent> и поддерживают <xref:System.Runtime.Serialization.ISerializable> интерфейс для удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="049ea-123">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="049ea-124">Это единственные объекты ADO.NET, которые разрешают удаленное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="049ea-124">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="049ea-125">Дополнительные сведения см. в разделе [удаленное взаимодействие .NET](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="049ea-125">For more information, see [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="049ea-126">Сведения о других событиях, доступных при работе с `DataSet` , см. в разделе [Обработка событий DataTable](handling-datatable-events.md) и [Обработка событий DataAdapter](../handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="049ea-126">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](handling-datatable-events.md) and [Handling DataAdapter Events](../handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="049ea-127">См. также</span><span class="sxs-lookup"><span data-stu-id="049ea-127">See also</span></span>

- [<span data-ttu-id="049ea-128">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="049ea-128">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="049ea-129">[Проверка данных](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="049ea-129">[Validating Data](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="049ea-130">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="049ea-130">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="049ea-131">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="049ea-131">ADO.NET Overview</span></span>](../ado-net-overview.md)
