---
description: 'Дополнительные сведения о: DbConnection, DbCommand и DbException'
title: DbConnection, DbCommand и DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: b5cb748a8dd5fb06f2f5dc5ab0479a679b2cc07d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651279"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="6eb00-103">DbConnection, DbCommand и DbException</span><span class="sxs-lookup"><span data-stu-id="6eb00-103">DbConnection, DbCommand and DbException</span></span>

<span data-ttu-id="6eb00-104">После создания <xref:System.Data.Common.DbProviderFactory> и <xref:System.Data.Common.DbConnection> можно будет пользоваться командами и модулями чтения данных, чтобы получать данные из источника данных.</span><span class="sxs-lookup"><span data-stu-id="6eb00-104">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="6eb00-105">Пример извлечения данных</span><span class="sxs-lookup"><span data-stu-id="6eb00-105">Retrieving Data Example</span></span>  

 <span data-ttu-id="6eb00-106">В этом примере в качестве аргумента указывается объект `DbConnection`.</span><span class="sxs-lookup"><span data-stu-id="6eb00-106">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="6eb00-107">Объект <xref:System.Data.Common.DbCommand> создается для выбора данных из таблицы Categories путем задания <xref:System.Data.Common.DbCommand.CommandText%2A> инструкции SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="6eb00-107">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="6eb00-108">Предполагается, что в источнике данных существует таблица Categories.</span><span class="sxs-lookup"><span data-stu-id="6eb00-108">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="6eb00-109">Открывается соединение, и данные получаются при помощи объекта <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="6eb00-109">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="6eb00-110">Пример выполнения команды</span><span class="sxs-lookup"><span data-stu-id="6eb00-110">Executing a Command Example</span></span>  

 <span data-ttu-id="6eb00-111">В этом примере в качестве аргумента указывается объект `DbConnection`.</span><span class="sxs-lookup"><span data-stu-id="6eb00-111">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="6eb00-112">Если объект `DbConnection` является допустимым, то открывается соединение, создается и выполняется команда <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="6eb00-112">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="6eb00-113"><xref:System.Data.Common.DbCommand.CommandText%2A> задается инструкции SQL INSERT, которая выполняет вставку в таблицу Categories в базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="6eb00-113">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="6eb00-114">Предполагается, что база данных Northwind существует в источнике данных, а также что используемый в инструкции INSERT синтаксис SQL является допустимым для указанного поставщика.</span><span class="sxs-lookup"><span data-stu-id="6eb00-114">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="6eb00-115">Ошибки в источнике данных обрабатываются блоком кода <xref:System.Data.Common.DbException>, а все остальные исключения - в блоке <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="6eb00-115">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="6eb00-116">Обработка ошибок данных при помощи DbException</span><span class="sxs-lookup"><span data-stu-id="6eb00-116">Handling Data Errors with DbException</span></span>  

 <span data-ttu-id="6eb00-117">Класс <xref:System.Data.Common.DbException> является базовым классом для всех исключений, формируемых от имени источника данных.</span><span class="sxs-lookup"><span data-stu-id="6eb00-117">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="6eb00-118">В коде обработки исключений его можно использовать для обработки исключений, формируемых разными поставщиками, при этом нет необходимости ссылаться на определенный класс исключений.</span><span class="sxs-lookup"><span data-stu-id="6eb00-118">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="6eb00-119">Следующий фрагмент кода демонстрирует, как использовать класс <xref:System.Data.Common.DbException> для отображения сведений об ошибке, возвращаемых источником данных, при помощи свойств <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A> и <xref:System.Exception.Message%2A>.</span><span class="sxs-lookup"><span data-stu-id="6eb00-119">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="6eb00-120">В выходных сведениях приводится тип ошибки, источник, указывающий имя поставщика, код ошибки и связанное с ошибкой сообщение.</span><span class="sxs-lookup"><span data-stu-id="6eb00-120">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6eb00-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6eb00-121">See also</span></span>

- [<span data-ttu-id="6eb00-122">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="6eb00-122">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="6eb00-123">Получение класса DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="6eb00-123">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="6eb00-124">Изменение данных с помощью DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="6eb00-124">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="6eb00-125">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6eb00-125">ADO.NET Overview</span></span>](ado-net-overview.md)
