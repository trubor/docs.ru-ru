---
description: 'Дополнительные сведения: выполнение операций с каталогами'
title: Выполнение операций каталога
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: c484e3a56d846de66c6e13b374efe58430ab86b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754346"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="afc9a-103">Выполнение операций каталога</span><span class="sxs-lookup"><span data-stu-id="afc9a-103">Performing Catalog Operations</span></span>

<span data-ttu-id="afc9a-104">Чтобы выполнить команду изменения базы данных или каталога, такую как инструкция CREATE TABLE или CREATE PROCEDURE, создайте объект **Command** с помощью соответствующих инструкций SQL и объекта **Connection**.</span><span class="sxs-lookup"><span data-stu-id="afc9a-104">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="afc9a-105">Выполните команду с помощью метода **ExecuteNonQuery** объекта **Command** .</span><span class="sxs-lookup"><span data-stu-id="afc9a-105">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="afc9a-106">В следующем примере кода создается хранимая процедура в базе данных Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="afc9a-106">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a><span data-ttu-id="afc9a-107">См. также</span><span class="sxs-lookup"><span data-stu-id="afc9a-107">See also</span></span>

- [<span data-ttu-id="afc9a-108">Использование команд для изменения данных</span><span class="sxs-lookup"><span data-stu-id="afc9a-108">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="afc9a-109">Команды и параметры</span><span class="sxs-lookup"><span data-stu-id="afc9a-109">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="afc9a-110">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="afc9a-110">ADO.NET Overview</span></span>](ado-net-overview.md)
