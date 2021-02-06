---
description: 'Дополнительные сведения: состояния строк и версии строк'
title: Состояния и версии строк
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 7d436ffcfcf59f5daa4fc6eaa9f9018b92e5c608
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651682"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="18a4c-103">Состояния и версии строк</span><span class="sxs-lookup"><span data-stu-id="18a4c-103">Row States and Row Versions</span></span>

<span data-ttu-id="18a4c-104">ADO.NET управляет строками таблиц с помощью состояний и версий строк.</span><span class="sxs-lookup"><span data-stu-id="18a4c-104">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="18a4c-105">Состояние строки указывает на статус строки, а версии строк хранят значения изменения строки, включая текущее, исходное и применяемое по умолчанию значения.</span><span class="sxs-lookup"><span data-stu-id="18a4c-105">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="18a4c-106">Например, после внесения изменения в столбец строки эта строка будет иметь состояние `Modified` и две версии: `Current`, содержащую текущие значения, и `Original`, содержащую значения этой строки до изменения столбца.</span><span class="sxs-lookup"><span data-stu-id="18a4c-106">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="18a4c-107">Каждый объект <xref:System.Data.DataRow> имеет свойство <xref:System.Data.DataRow.RowState%2A>, которое отображает текущее состояние строки.</span><span class="sxs-lookup"><span data-stu-id="18a4c-107">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="18a4c-108">В следующей таблице кратко описано каждое из значений перечисления `RowState`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-108">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="18a4c-109">Значение перечисления RowState</span><span class="sxs-lookup"><span data-stu-id="18a4c-109">RowState value</span></span>|<span data-ttu-id="18a4c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="18a4c-110">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="18a4c-111">Не было выполнено никаких изменений с момента последнего вызова метода `AcceptChanges` или с момента создания строки методом `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-111">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="18a4c-112">Строка добавлена к таблице, но метод `AcceptChanges` не вызывался.</span><span class="sxs-lookup"><span data-stu-id="18a4c-112">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="18a4c-113">Изменены некоторые элементы строки.</span><span class="sxs-lookup"><span data-stu-id="18a4c-113">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="18a4c-114">Строка удалена из таблицы, но метод `AcceptChanges` не вызывался.</span><span class="sxs-lookup"><span data-stu-id="18a4c-114">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="18a4c-115">Строка не принадлежит ни к одной коллекции `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-115">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="18a4c-116">Свойство `RowState` только что созданной строки имеет значение `Detached`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-116">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="18a4c-117">После добавления новой строки `DataRow` к коллекции `DataRowCollection` с помощью вызова метода `Add` свойству `RowState` присваивается значение `Added`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-117">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="18a4c-118">Значение `Detached` также присваивается строке, удаленной из `DataRowCollection` с помощью метода `Remove` или путем последовательного вызова методов `Delete` и `AcceptChanges`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-118">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="18a4c-119">Если метод `AcceptChanges` вызывается для <xref:System.Data.DataSet>, <xref:System.Data.DataTable> или <xref:System.Data.DataRow>, удаляются все строки со значением состояния `Deleted`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-119">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="18a4c-120">Оставшимся строкам присваивается состояние `Unchanged`, а значения в версии строки `Original` перезаписываются значениями версии строки `Current`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-120">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="18a4c-121">Если вызывается метод `RejectChanges`, удаляются все строки со значением состояния `Added`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-121">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="18a4c-122">Оставшимся строкам присваивается состояние `Unchanged`, а значения в версии строки `Current` перезаписываются значениями версии строки `Original`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-122">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="18a4c-123">Можно просматривать разные версии строки, передавая параметр <xref:System.Data.DataRowVersion> со ссылкой на столбец, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="18a4c-123">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="18a4c-124">В следующей таблице кратко описано каждое из значений перечисления `DataRowVersion`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-124">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="18a4c-125">Значение DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="18a4c-125">DataRowVersion value</span></span>|<span data-ttu-id="18a4c-126">Описание</span><span class="sxs-lookup"><span data-stu-id="18a4c-126">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="18a4c-127">Текущие значения строки.</span><span class="sxs-lookup"><span data-stu-id="18a4c-127">The current values for the row.</span></span> <span data-ttu-id="18a4c-128">Эта версия не существует для строк, у которых `RowState` равно `Deleted`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-128">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="18a4c-129">Версия по умолчанию для конкретной строки.</span><span class="sxs-lookup"><span data-stu-id="18a4c-129">The default row version for a particular row.</span></span> <span data-ttu-id="18a4c-130">Версия по умолчанию для строки `Added`, `Modified` и `Deleted` представляет собой `Current`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-130">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="18a4c-131">Версия по умолчанию для строки `Detached` - `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-131">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="18a4c-132">Исходные значения строки.</span><span class="sxs-lookup"><span data-stu-id="18a4c-132">The original values for the row.</span></span> <span data-ttu-id="18a4c-133">Эта версия не существует для строк, у которых `RowState` равно `Added`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-133">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="18a4c-134">Предложенные значения строки.</span><span class="sxs-lookup"><span data-stu-id="18a4c-134">The proposed values for the row.</span></span> <span data-ttu-id="18a4c-135">Эта версия строки существует в течение операции изменения строки или для строки, не содержащейся в коллекции `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-135">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="18a4c-136">Можно проверить, имеет ли `DataRow` конкретную версию строки, вызвав метод <xref:System.Data.DataRow.HasVersion%2A> и передав ему `DataRowVersion` в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="18a4c-136">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="18a4c-137">Например, `DataRow.HasVersion(DataRowVersion.Original)` возвратит значение `false` для только что добавленных строк перед тем, как был вызван метод `AcceptChanges`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-137">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="18a4c-138">В следующем примере кода показаны значения во всех удаленных строках таблицы.</span><span class="sxs-lookup"><span data-stu-id="18a4c-138">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="18a4c-139">Строки `Deleted` не имеют версии строки `Current`, поэтому для доступа к значениям столбцов необходимо передать аргумент `DataRowVersion.Original`.</span><span class="sxs-lookup"><span data-stu-id="18a4c-139">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="18a4c-140">См. также</span><span class="sxs-lookup"><span data-stu-id="18a4c-140">See also</span></span>

- [<span data-ttu-id="18a4c-141">Управление данными в таблице данных</span><span class="sxs-lookup"><span data-stu-id="18a4c-141">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="18a4c-142">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="18a4c-142">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="18a4c-143">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="18a4c-143">DataAdapters and DataReaders</span></span>](../dataadapters-and-datareaders.md)
- [<span data-ttu-id="18a4c-144">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="18a4c-144">ADO.NET Overview</span></span>](../ado-net-overview.md)
