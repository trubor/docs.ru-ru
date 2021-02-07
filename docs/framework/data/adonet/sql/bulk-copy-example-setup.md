---
description: 'Дополнительные сведения: пример установки с массовым копированием'
title: Установка примера массового копирования
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: ae05dfa5f1ab19a3021b2b79ecd2bbee6a3ecae1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718555"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="627d7-103">Установка примера массового копирования</span><span class="sxs-lookup"><span data-stu-id="627d7-103">Bulk Copy Example Setup</span></span>

<span data-ttu-id="627d7-104">Класс <xref:System.Data.SqlClient.SqlBulkCopy> можно использовать для записи данных только в таблицы SQL Server.</span><span class="sxs-lookup"><span data-stu-id="627d7-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="627d7-105">В примерах кода в этом разделе используется образец базы данных SQL Server **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="627d7-105">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="627d7-106">Чтобы не допустить изменения существующих таблиц, примеры кода записывают данные в таблицы, которые сначала необходимо создать.</span><span class="sxs-lookup"><span data-stu-id="627d7-106">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="627d7-107">Таблицы **BulkCopyDemoMatchingColumns** и **BulkCopyDemoDifferentColumns** основаны на таблице **AdventureWorks** **Production.Products**.</span><span class="sxs-lookup"><span data-stu-id="627d7-107">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="627d7-108">В примерах кода, использующих эти таблицы, данные из таблицы **Production.Products** добавляются к одной из этих таблиц-образцов.</span><span class="sxs-lookup"><span data-stu-id="627d7-108">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="627d7-109">Таблица **BulkCopyDemoDifferentColumns** используется для демонстрации сопоставления столбцов из источника данных с целевой таблицей. Таблица **BulkCopyDemoMatchingColumns** используется в большинстве других примеров.</span><span class="sxs-lookup"><span data-stu-id="627d7-109">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="627d7-110">Некоторые примеры кода демонстрируют использование одного класса <xref:System.Data.SqlClient.SqlBulkCopy> для записи в несколько таблиц.</span><span class="sxs-lookup"><span data-stu-id="627d7-110">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="627d7-111">В этих примерах в качестве целевых таблиц применяются **BulkCopyDemoOrderHeader** и **BulkCopyDemoOrderDetail**.</span><span class="sxs-lookup"><span data-stu-id="627d7-111">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="627d7-112">Эти таблицы основаны на таблицах **Sales.SalesOrderHeader** и **Sales.SalesOrderDetail** из базы данных **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="627d7-112">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="627d7-113">Образцы кода **SqlBulkCopy** предоставляются только для демонстрации синтаксиса применения **SqlBulkCopy**.</span><span class="sxs-lookup"><span data-stu-id="627d7-113">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="627d7-114">Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL `INSERT … SELECT` для копирования данных.</span><span class="sxs-lookup"><span data-stu-id="627d7-114">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="627d7-115">Подготовка таблиц</span><span class="sxs-lookup"><span data-stu-id="627d7-115">Table Setup</span></span>  

 <span data-ttu-id="627d7-116">Чтобы создать таблицы, необходимые для правильной работы примеров кода, выполните следующие инструкции Transact-SQL в базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="627d7-116">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="627d7-117">См. также</span><span class="sxs-lookup"><span data-stu-id="627d7-117">See also</span></span>

- [<span data-ttu-id="627d7-118">Операции с массовым копированием в SQL Server</span><span class="sxs-lookup"><span data-stu-id="627d7-118">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="627d7-119">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="627d7-119">ADO.NET Overview</span></span>](../ado-net-overview.md)
