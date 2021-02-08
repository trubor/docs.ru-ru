---
description: 'Дополнительные сведения: отдельные операции по операциям копирования'
title: Отдельные операции массового копирования
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: f6b046fbd73ad798f3f9f117eea0b72f46e43b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767483"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="80767-103">Отдельные операции массового копирования</span><span class="sxs-lookup"><span data-stu-id="80767-103">Single Bulk Copy Operations</span></span>

<span data-ttu-id="80767-104">Самый простой способ массового копирования SQL Server — выполнение одной операции в базе данных.</span><span class="sxs-lookup"><span data-stu-id="80767-104">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="80767-105">По умолчанию операция массового копирования выполняется как изолированная, т. е. не как транзакция и без возможности отката.</span><span class="sxs-lookup"><span data-stu-id="80767-105">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>

> [!NOTE]
> <span data-ttu-id="80767-106">Если при возникновении ошибки необходимо частично или полностью отменить массовое копирование, можно использовать управляемую <xref:System.Data.SqlClient.SqlBulkCopy> транзакцию или выполнить операцию массового копирования в существующей транзакции.</span><span class="sxs-lookup"><span data-stu-id="80767-106">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="80767-107">**SqlBulkCopy** также будет работать с <xref:System.Transactions>, если это соединение прикреплено (явно или неявно) к транзакции **System.Transactions**.</span><span class="sxs-lookup"><span data-stu-id="80767-107">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>
>
> <span data-ttu-id="80767-108">Дополнительные сведения см. в разделе [операции с транзакциями и операциями с массовым копированием](transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="80767-108">For more information, see [Transaction and Bulk Copy Operations](transaction-and-bulk-copy-operations.md).</span></span>

<span data-ttu-id="80767-109">Для массового копирования выполните описанную ниже процедуру.</span><span class="sxs-lookup"><span data-stu-id="80767-109">The general steps for performing a bulk copy operation are as follows:</span></span>

1. <span data-ttu-id="80767-110">Подключитесь к исходному серверу и получите данные для копирования.</span><span class="sxs-lookup"><span data-stu-id="80767-110">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="80767-111">Данные также могут поступать из других источников, если их можно извлечь из объекта <xref:System.Data.IDataReader> или <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="80767-111">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>

2. <span data-ttu-id="80767-112">Подключитесь к целевому серверу (если только не требуется, чтобы объект **SqlBulkCopy** сам установил соединение).</span><span class="sxs-lookup"><span data-stu-id="80767-112">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>

3. <span data-ttu-id="80767-113">Создайте объект <xref:System.Data.SqlClient.SqlBulkCopy>, задав все необходимые свойства.</span><span class="sxs-lookup"><span data-stu-id="80767-113">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>

4. <span data-ttu-id="80767-114">Задайте свойство **DestinationTableName**, чтобы указать целевую таблицу для операции массовой вставки.</span><span class="sxs-lookup"><span data-stu-id="80767-114">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>

5. <span data-ttu-id="80767-115">Вызовите один из методов **WriteToServer**.</span><span class="sxs-lookup"><span data-stu-id="80767-115">Call one of the **WriteToServer** methods.</span></span>

6. <span data-ttu-id="80767-116">Кроме того, если это необходимо, можно обновить свойства и вызвать метод **WriteToServer**.</span><span class="sxs-lookup"><span data-stu-id="80767-116">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>

7. <span data-ttu-id="80767-117">Вызовите <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A> или заключите код операций массового копирования в инструкцию `Using`.</span><span class="sxs-lookup"><span data-stu-id="80767-117">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>

> [!CAUTION]
> <span data-ttu-id="80767-118">Мы рекомендуем, чтобы исходные и целевые типы данных столбцов совпадали.</span><span class="sxs-lookup"><span data-stu-id="80767-118">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="80767-119">Если типы данных разные, объект **SqlBulkCopy** попытается преобразовать каждое исходное значение в целевой тип данных с использованием правил, применяемых методом <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="80767-119">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="80767-120">Преобразование может повлиять на производительность и может привести к непредвиденным ошибкам.</span><span class="sxs-lookup"><span data-stu-id="80767-120">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="80767-121">Например, в большинстве случаев тип данных `Double` может преобразовываться в тип данных `Decimal`, но это происходит не всегда.</span><span class="sxs-lookup"><span data-stu-id="80767-121">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>

## <a name="example"></a><span data-ttu-id="80767-122">Пример</span><span class="sxs-lookup"><span data-stu-id="80767-122">Example</span></span>

<span data-ttu-id="80767-123">Следующее консольное приложение показывает, как загрузить данные с помощью класса <xref:System.Data.SqlClient.SqlBulkCopy>.</span><span class="sxs-lookup"><span data-stu-id="80767-123">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="80767-124">В этом примере объект <xref:System.Data.SqlClient.SqlDataReader> используется, чтобы скопировать данные из таблицы **Production.Product** в базе данных SQL Server **AdventureWorks** в такую же таблицу в этой же базе данных.</span><span class="sxs-lookup"><span data-stu-id="80767-124">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80767-125">Этот пример не будет выполняться, если вы не создали рабочие таблицы, как описано в статье [Пример установки с помощью инструкций копирования](bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="80767-125">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="80767-126">Этот код предназначен только для демонстрации синтаксиса использования **SqlBulkCopy**.</span><span class="sxs-lookup"><span data-stu-id="80767-126">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="80767-127">Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL `INSERT … SELECT` для копирования данных.</span><span class="sxs-lookup"><span data-stu-id="80767-127">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="80767-128">Выполнение операции массового копирования при помощи Transact-SQL и класса команды</span><span class="sxs-lookup"><span data-stu-id="80767-128">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>

<span data-ttu-id="80767-129">Следующий пример демонстрирует использование метода <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> для выполнения инструкции BULK INSERT.</span><span class="sxs-lookup"><span data-stu-id="80767-129">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>

> [!NOTE]
> <span data-ttu-id="80767-130">Путь к источнику данных указан относительно сервера.</span><span class="sxs-lookup"><span data-stu-id="80767-130">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="80767-131">Для успешного выполнения массового копирования у процесса сервера должен быть доступ к этому пути.</span><span class="sxs-lookup"><span data-stu-id="80767-131">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>

```vb
Using connection As SqlConnection = New SqlConnection(connectionString)
Dim queryString As String = _
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"
connection.Open()
SqlCommand command = New SqlCommand(queryString, connection);

command.ExecuteNonQuery()
End Using
```

```csharp
using (SqlConnection connection = New SqlConnection(connectionString))
{
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +
    "FROM 'f:\mydata\data.tbl' " +
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";
connection.Open();
SqlCommand command = new SqlCommand(queryString, connection);

command.ExecuteNonQuery();
}
```

## <a name="see-also"></a><span data-ttu-id="80767-132">См. также</span><span class="sxs-lookup"><span data-stu-id="80767-132">See also</span></span>

- [<span data-ttu-id="80767-133">Операции с массовым копированием в SQL Server</span><span class="sxs-lookup"><span data-stu-id="80767-133">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="80767-134">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="80767-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
