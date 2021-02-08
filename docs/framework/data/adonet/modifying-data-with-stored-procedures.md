---
description: 'Дополнительные сведения: изменение данных с помощью хранимых процедур'
title: Изменение данных с помощью хранимых процедур
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 66a4aa9577c71605bde0152a142a65dfa81a31d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786229"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="49803-103">Изменение данных с помощью хранимых процедур</span><span class="sxs-lookup"><span data-stu-id="49803-103">Modifying Data with Stored Procedures</span></span>

<span data-ttu-id="49803-104">Хранимые процедуры могут принимать данные в виде входных параметров и возвращать их в виде выходных параметров, результирующих наборов или возвращаемых значений.</span><span class="sxs-lookup"><span data-stu-id="49803-104">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="49803-105">Образец, приведенный ниже, показывает, как ADO.NET отправляет и получает входные и выходные параметры, а также возвращаемые значения.</span><span class="sxs-lookup"><span data-stu-id="49803-105">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="49803-106">Пример добавляет в таблицу новую запись, где столбец первичного ключа является столбцом идентификаторов в базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="49803-106">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49803-107">При использовании хранимых процедур SQL Server для изменения или удаления данных с помощью <xref:System.Data.SqlClient.SqlDataAdapter> убедитесь, что в определении хранимой процедуры не указана инструкция SET NOCOUNT ON.</span><span class="sxs-lookup"><span data-stu-id="49803-107">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="49803-108">В таком случае возвращается число затронутых строк, равное нулю, что `DataAdapter` интерпретирует как конфликт параллелизма.</span><span class="sxs-lookup"><span data-stu-id="49803-108">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="49803-109">Это событие вызовет исключение <xref:System.Data.DBConcurrencyException>.</span><span class="sxs-lookup"><span data-stu-id="49803-109">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49803-110">Пример</span><span class="sxs-lookup"><span data-stu-id="49803-110">Example</span></span>  

 <span data-ttu-id="49803-111">Пример использует следующую хранимую процедуру для вставки новой категории в таблицу **Northwind** **Categories**.</span><span class="sxs-lookup"><span data-stu-id="49803-111">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="49803-112">Хранимая процедура принимает значение столбца **CategoryName** в качестве входного параметра и с помощью функции SCOPE_IDENTITY() получает новое значения поля идентификатора **CategoryID** и возвращает его в выходном параметре.</span><span class="sxs-lookup"><span data-stu-id="49803-112">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="49803-113">Оператор RETURN использует @ROWCOUNT функцию @ для возврата количества вставленных строк.</span><span class="sxs-lookup"><span data-stu-id="49803-113">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="49803-114">Следующий пример кода использует хранимую процедуру `InsertCategory`, показанную выше, в качестве источника для свойства <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> класса <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="49803-114">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="49803-115">Выходной параметр `@Identity` будет отражен в наборе данных <xref:System.Data.DataSet> после вставки записи в базу данных при вызове метода `Update` объекта <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="49803-115">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="49803-116">Код также получает возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="49803-116">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49803-117">При использовании параметра <xref:System.Data.OleDb.OleDbDataAdapter> необходимо указать параметры с параметром с параметром <xref:System.Data.ParameterDirection> **ReturnValue** перед другими параметрами.</span><span class="sxs-lookup"><span data-stu-id="49803-117">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="49803-118">См. также</span><span class="sxs-lookup"><span data-stu-id="49803-118">See also</span></span>

- [<span data-ttu-id="49803-119">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49803-119">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="49803-120">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="49803-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="49803-121">Выполнение команды</span><span class="sxs-lookup"><span data-stu-id="49803-121">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="49803-122">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49803-122">ADO.NET Overview</span></span>](ado-net-overview.md)
