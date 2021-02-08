---
description: 'Дополнительные сведения: обновление данных в источнике данных'
title: Обновление данных в источнике данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: a55d6a53f4607908fa279474419803eac3963909
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766573"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="5fa1b-103">Обновление данных в источнике данных</span><span class="sxs-lookup"><span data-stu-id="5fa1b-103">Updating Data in a Data Source</span></span>

<span data-ttu-id="5fa1b-104">Инструкции SQL, изменяющие данные (например, INSERT, UPDATE, или DELETE), не возвращают строки.</span><span class="sxs-lookup"><span data-stu-id="5fa1b-104">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="5fa1b-105">Аналогичным образом, многие хранимые процедуры выполняют некоторое действие, но не возвращают строки.</span><span class="sxs-lookup"><span data-stu-id="5fa1b-105">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="5fa1b-106">Для выполнения команд, которые не возвращают строки, создайте объект **Command** с соответствующей командой SQL и объект **Connection**, включающий требуемую коллекцию **Parameters**.</span><span class="sxs-lookup"><span data-stu-id="5fa1b-106">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="5fa1b-107">Выполните команду с помощью метода **ExecuteNonQuery** объекта **Command** .</span><span class="sxs-lookup"><span data-stu-id="5fa1b-107">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="5fa1b-108">Метод **ExecuteNonQuery** возвращает значение типа integer, представляющее число строк, затрагиваемых выполненной инструкцией или хранимой процедурой.</span><span class="sxs-lookup"><span data-stu-id="5fa1b-108">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="5fa1b-109">Если выполняется несколько инструкций, возвращенное значение является суммой количеств записей, затронутых всеми выполненными инструкциями.</span><span class="sxs-lookup"><span data-stu-id="5fa1b-109">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fa1b-110">Пример</span><span class="sxs-lookup"><span data-stu-id="5fa1b-110">Example</span></span>  

 <span data-ttu-id="5fa1b-111">В следующем примере кода выполняется инструкция INSERT для вставки записи в базу данных с помощью **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="5fa1b-111">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 <span data-ttu-id="5fa1b-112">В следующем примере кода выполняется хранимая процедура, созданная с помощью примера кода из статьи [Выполнение операций c каталогами](performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5fa1b-112">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="5fa1b-113">Ни одна строка не возвращается хранимой процедурой, так что при использовании метода **ExecuteNonQuery** хранимая процедура получает входной параметр и возвращает выходной параметр и значение.</span><span class="sxs-lookup"><span data-stu-id="5fa1b-113">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="5fa1b-114">Для <xref:System.Data.OleDb.OleDbCommand> объекта необходимо сначала добавить параметр **ReturnValue** в коллекцию **Parameters** .</span><span class="sxs-lookup"><span data-stu-id="5fa1b-114">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fa1b-115">См. также</span><span class="sxs-lookup"><span data-stu-id="5fa1b-115">See also</span></span>

- [<span data-ttu-id="5fa1b-116">Использование команд для изменения данных</span><span class="sxs-lookup"><span data-stu-id="5fa1b-116">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="5fa1b-117">Обновление источников данных с объектами DataAdapter</span><span class="sxs-lookup"><span data-stu-id="5fa1b-117">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="5fa1b-118">Команды и параметры</span><span class="sxs-lookup"><span data-stu-id="5fa1b-118">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="5fa1b-119">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5fa1b-119">ADO.NET Overview</span></span>](ado-net-overview.md)
