---
description: 'Дополнительные сведения: выполнение пакетных операций с использованием адаптеров обработки'
title: Выполнение пакетных операций с использованием объектов DataAdapters
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: d0472761a0a3893872f073cfe25921066a0f96bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672339"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="fc915-103">Выполнение пакетных операций с использованием объектов DataAdapters</span><span class="sxs-lookup"><span data-stu-id="fc915-103">Performing Batch Operations Using DataAdapters</span></span>

<span data-ttu-id="fc915-104">Поддержка пакетных операций в ADO.NET позволяет объекту <xref:System.Data.Common.DataAdapter> группировать операции INSERT, UPDATE и DELETE из <xref:System.Data.DataSet> или <xref:System.Data.DataTable> к серверу вместо отправки за один раз одной операции.</span><span class="sxs-lookup"><span data-stu-id="fc915-104">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="fc915-105">Уменьшение числа двусторонних передач сигнала на сервер обычно приводит к значительному повышению производительности.</span><span class="sxs-lookup"><span data-stu-id="fc915-105">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="fc915-106">Пакетные обновления поддерживаются для поставщиков .NET-данных для SQL Server (<xref:System.Data.SqlClient>) и Oracle (<xref:System.Data.OracleClient>).</span><span class="sxs-lookup"><span data-stu-id="fc915-106">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="fc915-107">При обновлении базы данных изменениями из объекта <xref:System.Data.DataSet> в более ранних версиях ADO.NET метод `Update` для `DataAdapter` выполняет обновления в базе данных по одной строке.</span><span class="sxs-lookup"><span data-stu-id="fc915-107">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="fc915-108">Когда он просматривает строки в указанной таблице <xref:System.Data.DataTable>, он проверяет каждую строку <xref:System.Data.DataRow>, чтобы выявить, не была ли она изменена.</span><span class="sxs-lookup"><span data-stu-id="fc915-108">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="fc915-109">Если строка изменена, он вызывает соответствующую команду `UpdateCommand`, `InsertCommand` или `DeleteCommand` в зависимости от значения свойства <xref:System.Data.DataRow.RowState%2A> для этой строки.</span><span class="sxs-lookup"><span data-stu-id="fc915-109">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="fc915-110">Каждое обновление строки подразумевает сетевую двустороннюю передачу сигнала в базу данных.</span><span class="sxs-lookup"><span data-stu-id="fc915-110">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="fc915-111">Начиная с ADO.NET 2.0, объект <xref:System.Data.Common.DbDataAdapter> предоставляет свойство <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc915-111">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="fc915-112">При установке для свойства `UpdateBatchSize` положительного целого значения обновления базы данных посылаются как пакеты указанного размера.</span><span class="sxs-lookup"><span data-stu-id="fc915-112">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="fc915-113">Например, при установке `UpdateBatchSize` в 10 производится группирование 10 отдельных инструкций и передача их как один пакет.</span><span class="sxs-lookup"><span data-stu-id="fc915-113">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="fc915-114">При установке `UpdateBatchSize` в 0 <xref:System.Data.Common.DataAdapter> использует самой большой размер пакета, который может обработать сервер.</span><span class="sxs-lookup"><span data-stu-id="fc915-114">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="fc915-115">При его установке в 1 отключаются пакетные обновления, т. к. строки посылаются по одной.</span><span class="sxs-lookup"><span data-stu-id="fc915-115">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="fc915-116">Выполнение очень больших пакетов может снизить производительность.</span><span class="sxs-lookup"><span data-stu-id="fc915-116">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="fc915-117">Поэтому необходимо экспериментальным путем найти параметр оптимального размера пакета перед реализацией приложения.</span><span class="sxs-lookup"><span data-stu-id="fc915-117">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="fc915-118">Использование свойства UpdateBatchSize</span><span class="sxs-lookup"><span data-stu-id="fc915-118">Using the UpdateBatchSize Property</span></span>  

 <span data-ttu-id="fc915-119">Если пакетные обновления включены, значение свойства <xref:System.Data.IDbCommand.UpdatedRowSource%2A> для `UpdateCommand`, `InsertCommand` и `DeleteCommand` объекта DataAdapter должно быть установлено в <xref:System.Data.UpdateRowSource.None> или <xref:System.Data.UpdateRowSource.OutputParameters>.</span><span class="sxs-lookup"><span data-stu-id="fc915-119">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="fc915-120">При выполнении пакетного обновления значение свойства <xref:System.Data.IDbCommand.UpdatedRowSource%2A> команды для <xref:System.Data.UpdateRowSource.FirstReturnedRecord> или <xref:System.Data.UpdateRowSource.Both> недействительно.</span><span class="sxs-lookup"><span data-stu-id="fc915-120">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="fc915-121">Следующая процедура демонстрирует использование свойства `UpdateBatchSize`.</span><span class="sxs-lookup"><span data-stu-id="fc915-121">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="fc915-122">Процедура принимает два аргумента, объект <xref:System.Data.DataSet>, который имеет столбцы, представляющие поля **ProductCategoryID** и **Name** в таблице **Production.ProductCategory**, и целое число, представляющее размер пакета (число строк в пакете).</span><span class="sxs-lookup"><span data-stu-id="fc915-122">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="fc915-123">Код создает новый объект <xref:System.Data.SqlClient.SqlDataAdapter>, устанавливая его свойства <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> и <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc915-123">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="fc915-124">В коде предполагается, что объект <xref:System.Data.DataSet> имеет измененные строки.</span><span class="sxs-lookup"><span data-stu-id="fc915-124">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="fc915-125">В нем устанавливается свойство `UpdateBatchSize` и выполняется обновление.</span><span class="sxs-lookup"><span data-stu-id="fc915-125">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="fc915-126">Обработка событий и ошибок, связанных с обновлением пакета</span><span class="sxs-lookup"><span data-stu-id="fc915-126">Handling Batch Update-Related Events and Errors</span></span>  

 <span data-ttu-id="fc915-127">Объект **DataAdapter** имеет два события, связанных с обновлением: **RowUpdating** и **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="fc915-127">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="fc915-128">В более ранних версиях ADO.NET, если пакетная обработка отключена, каждое из этих событий формируется для каждой обрабатываемой строки.</span><span class="sxs-lookup"><span data-stu-id="fc915-128">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="fc915-129">**Событие RowUpdating** создается до выполнения обновления, а **событие RowUpdated** создается после завершения обновления базы данных.</span><span class="sxs-lookup"><span data-stu-id="fc915-129">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="fc915-130">Изменение поведения событий при пакетных обновлениях</span><span class="sxs-lookup"><span data-stu-id="fc915-130">Event Behavior Changes with Batch Updates</span></span>  

 <span data-ttu-id="fc915-131">Если пакетное обновление включено, несколько строк обновляются одной операцией базы данных.</span><span class="sxs-lookup"><span data-stu-id="fc915-131">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="fc915-132">Поэтому для каждого пакета происходит только одно событие `RowUpdated`, в то время как событие `RowUpdating` происходит для каждой обрабатываемой строки.</span><span class="sxs-lookup"><span data-stu-id="fc915-132">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="fc915-133">Если пакетное обновление отключено, два события инициируются с чередованием один к одному, где одно событие `RowUpdating` и одно событие `RowUpdated` инициируется для строки, а затем одно событие `RowUpdating` и одно событие `RowUpdated` инициируются для следующей строки, до тех пор пока не будут обработаны все строки.</span><span class="sxs-lookup"><span data-stu-id="fc915-133">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="fc915-134">Доступ к обновленным строкам</span><span class="sxs-lookup"><span data-stu-id="fc915-134">Accessing Updated Rows</span></span>  

 <span data-ttu-id="fc915-135">Если пакетная обработка отключена, доступ к обновляемой строке может быть выполнен при помощи свойства <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> класса <xref:System.Data.Common.RowUpdatedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="fc915-135">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="fc915-136">Если пакетная обработка включена для нескольких строк, формируется одно событие `RowUpdated`.</span><span class="sxs-lookup"><span data-stu-id="fc915-136">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="fc915-137">Поэтому значение свойства `Row` для каждой из строк равно NULL.</span><span class="sxs-lookup"><span data-stu-id="fc915-137">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="fc915-138">События `RowUpdating` по-прежнему вызываются для каждой строки.</span><span class="sxs-lookup"><span data-stu-id="fc915-138">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="fc915-139">Метод <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> класса <xref:System.Data.Common.RowUpdatedEventArgs> позволяет обращаться к обработанным строкам, копируя ссылки на строки в массив.</span><span class="sxs-lookup"><span data-stu-id="fc915-139">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="fc915-140">Если строки не обрабатываются, метод `CopyToRows` инициирует исключение <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="fc915-140">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="fc915-141">Свойство <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> используется для возврата числа строк, обработанных перед вызовом метода <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc915-141">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="fc915-142">Обработка ошибок данных</span><span class="sxs-lookup"><span data-stu-id="fc915-142">Handling Data Errors</span></span>  

 <span data-ttu-id="fc915-143">Пакетное выполнение оказывает то же влияние, что и выполнение каждой отдельной инструкции.</span><span class="sxs-lookup"><span data-stu-id="fc915-143">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="fc915-144">Инструкции выполняются в порядке, который инструкции добавили в пакет.</span><span class="sxs-lookup"><span data-stu-id="fc915-144">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="fc915-145">Ошибки обрабатываются в пакетном режиме, как если было бы при отключении пакетного режима.</span><span class="sxs-lookup"><span data-stu-id="fc915-145">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="fc915-146">Каждая строка обрабатывается отдельно.</span><span class="sxs-lookup"><span data-stu-id="fc915-146">Each row is processed separately.</span></span> <span data-ttu-id="fc915-147">Только успешно обработанные в базе данных строки будут обновлены в соответствующей строке <xref:System.Data.DataRow> таблицы <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="fc915-147">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="fc915-148">Поставщик данных и сервер базы данных определяют, какие конструкции SQL поддерживаются для пакетного обновления.</span><span class="sxs-lookup"><span data-stu-id="fc915-148">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="fc915-149">Если неподдерживаемая инструкция подается на выполнение, создается исключение.</span><span class="sxs-lookup"><span data-stu-id="fc915-149">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc915-150">См. также</span><span class="sxs-lookup"><span data-stu-id="fc915-150">See also</span></span>

- [<span data-ttu-id="fc915-151">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="fc915-151">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="fc915-152">Обновление источников данных с объектами DataAdapter</span><span class="sxs-lookup"><span data-stu-id="fc915-152">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="fc915-153">Обработка событий DataAdapter</span><span class="sxs-lookup"><span data-stu-id="fc915-153">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)
- [<span data-ttu-id="fc915-154">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fc915-154">ADO.NET Overview</span></span>](ado-net-overview.md)
