---
description: 'Дополнительные сведения: Установка подключения'
title: Установка подключения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: e7f8c837476a678f003eb0477934bb8bd08fd896
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724340"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="4b49e-103">Установка подключения</span><span class="sxs-lookup"><span data-stu-id="4b49e-103">Establishing the Connection</span></span>

<span data-ttu-id="4b49e-104">Для создания соединения с Microsoft SQL Server используется объект <xref:System.Data.SqlClient.SqlConnection> поставщика данных .NET Framework для SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4b49e-104">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="4b49e-105">Для соединения с источником данных OLE DB используется объект <xref:System.Data.OleDb.OleDbConnection> поставщика данных .NET Framework для OLE DB.</span><span class="sxs-lookup"><span data-stu-id="4b49e-105">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="4b49e-106">Для соединения с источником данных используется объект <xref:System.Data.Odbc.OdbcConnection> поставщика данных .NET Framework для ODBC.</span><span class="sxs-lookup"><span data-stu-id="4b49e-106">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="4b49e-107">Для соединения с источником данных Oracle используется объект <xref:System.Data.OracleClient.OracleConnection> поставщика данных .NET Framework для Oracle.</span><span class="sxs-lookup"><span data-stu-id="4b49e-107">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="4b49e-108">Сведения о безопасном хранении и извлечении строк подключения см. в статье [Защита сведений о подключении](protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="4b49e-108">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="4b49e-109">Закрытие соединений</span><span class="sxs-lookup"><span data-stu-id="4b49e-109">Closing Connections</span></span>  

 <span data-ttu-id="4b49e-110">Рекомендуется всегда закрывать соединение после использования, чтобы обеспечить его возврат в пул.</span><span class="sxs-lookup"><span data-stu-id="4b49e-110">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="4b49e-111">Блок `Using` в Visual Basic или C# автоматически удаляет соединение при выходе в коде из блока даже при наличии необработанного исключения.</span><span class="sxs-lookup"><span data-stu-id="4b49e-111">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="4b49e-112">Дополнительные сведения об операторе using см. [здесь](../../../csharp/language-reference/keywords/using-statement.md) и [здесь](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4b49e-112">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="4b49e-113">Также можно использовать методы `Close` или `Dispose` объекта соединения для используемого поставщика.</span><span class="sxs-lookup"><span data-stu-id="4b49e-113">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="4b49e-114">Соединения, которые явно не закрыты, нельзя добавить или вернуть в пул.</span><span class="sxs-lookup"><span data-stu-id="4b49e-114">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="4b49e-115">Например, соединение, которое вышло за пределы области, но явно закрыто не было, будет возвращено в пул соединений только в том случае, если был достигнут максимальный размер этого пула, а соединение еще действует.</span><span class="sxs-lookup"><span data-stu-id="4b49e-115">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="4b49e-116">Дополнительные сведения см. в статье [Пулы соединений OLE DB, ODBC и Oracle](ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="4b49e-116">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b49e-117">В методе `Finalize` вашего класса нельзя вызывать методы `Close` или `Dispose` объектов **Connection**, **DataReader** или любого другого управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="4b49e-117">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="4b49e-118">В методе завершения следует только освобождать неуправляемые ресурсы, которыми ваш класс непосредственно владеет.</span><span class="sxs-lookup"><span data-stu-id="4b49e-118">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="4b49e-119">Если класс не владеет какими-либо неуправляемыми ресурсами, не включайте в его определение метод `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="4b49e-119">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="4b49e-120">Дополнительные сведения см. в статье [Сборка мусора](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b49e-120">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b49e-121">События входа в систему и выхода из системы не вызываются на сервере при выборке подключения из пула подключений и при возврате его в пул подключений, поскольку при возврате в пул подключений подключение фактически не закрывается.</span><span class="sxs-lookup"><span data-stu-id="4b49e-121">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="4b49e-122">Дополнительные сведения см. в разделе [Пулы подключений SQL Server (ADO.NET)](sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="4b49e-122">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="4b49e-123">Подключение к SQL Server</span><span class="sxs-lookup"><span data-stu-id="4b49e-123">Connecting to SQL Server</span></span>  

 <span data-ttu-id="4b49e-124">Поставщик данных .NET Framework для SQL Server поддерживает формат строки соединения, аналогичный формату строки соединения OLE DB (ADO).</span><span class="sxs-lookup"><span data-stu-id="4b49e-124">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="4b49e-125">Сведения о допустимых именах и значениях формата строки см. в свойстве <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> объекта <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="4b49e-125">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="4b49e-126">Можно также использовать класс <xref:System.Data.SqlClient.SqlConnectionStringBuilder> для создания синтаксически правильных строк соединения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4b49e-126">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="4b49e-127">Дополнительные сведения см. в статье [Connection String Builders](connection-string-builders.md) (Построители строк подключения).</span><span class="sxs-lookup"><span data-stu-id="4b49e-127">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="4b49e-128">В следующем примере кода демонстрируется способ создания и открытия соединения с базой данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4b49e-128">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="4b49e-129">Встроенная безопасность и ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b49e-129">Integrated Security and ASP.NET</span></span>  

 <span data-ttu-id="4b49e-130">Встроенная безопасность SQL Server (именуемая также доверительными соединениями) обеспечивает защиту при соединении с SQL Server, так как не отображает идентификатор пользователя и пароль в строке соединения, поэтому является рекомендуемым методом проверки подлинности соединения.</span><span class="sxs-lookup"><span data-stu-id="4b49e-130">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="4b49e-131">Встроенная безопасность основана на использовании текущего идентификатора безопасности, или маркера выполняемого процесса.</span><span class="sxs-lookup"><span data-stu-id="4b49e-131">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="4b49e-132">В приложениях рабочего стола, как правило, используется идентификатор текущего, вошедшего в систему пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b49e-132">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="4b49e-133">Идентификатор безопасности приложений ASP.NET может быть настроен на получение одного из нескольких различных параметров.</span><span class="sxs-lookup"><span data-stu-id="4b49e-133">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="4b49e-134">Дополнительные сведения об идентификаторе безопасности, который используется в приложении ASP.NET при соединении с SQL Server, см. в статьях [Олицетворение ASP.NET](/previous-versions/aspnet/xh507fc5(v=vs.100)), [Проверка подлинности ASP.NET ](/previous-versions/aspnet/eeyk640h(v=vs.100)) и практическом руководстве [ Доступ к SQL Server с помощью встроенных функций безопасности Windows](/previous-versions/aspnet/bsz5788z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4b49e-134">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="4b49e-135">Соединение с источником данных OLE DB</span><span class="sxs-lookup"><span data-stu-id="4b49e-135">Connecting to an OLE DB Data Source</span></span>  

 <span data-ttu-id="4b49e-136">Поставщик данных платформа .NET Framework для OLE DB предоставляет возможность подключения к источникам данных, предоставляемым с помощью OLE DB (через SQLOLEDB, поставщик OLE DB для SQL Server) с помощью объекта **OleDbConnection** .</span><span class="sxs-lookup"><span data-stu-id="4b49e-136">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="4b49e-137">Формат строки соединения поставщика данных .NET Framework для OLE DB идентичен формату строки соединения, используемому в ADO, за исключением следующего.</span><span class="sxs-lookup"><span data-stu-id="4b49e-137">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="4b49e-138">Требуется ключевое слово **provider** .</span><span class="sxs-lookup"><span data-stu-id="4b49e-138">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="4b49e-139">Ключевые слова **URL-адреса**, **удаленного поставщика** и **удаленного сервера** не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="4b49e-139">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="4b49e-140">Дополнительные сведения о строках соединения OLE DB см. в разделе <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b49e-140">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="4b49e-141">Построитель <xref:System.Data.OleDb.OleDbConnectionStringBuilder> также используется для создания строк соединения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4b49e-141">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b49e-142">Объект **OleDbConnection** не поддерживает настройку или получение динамических свойств, относящихся к поставщику OLE DB.</span><span class="sxs-lookup"><span data-stu-id="4b49e-142">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="4b49e-143">Поддерживаются только те свойства, которые можно передать в строке соединения поставщику OLE DB.</span><span class="sxs-lookup"><span data-stu-id="4b49e-143">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="4b49e-144">В следующем примере кода демонстрируется способ создания и открытия соединения с источником данных OLE DB.</span><span class="sxs-lookup"><span data-stu-id="4b49e-144">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="4b49e-145">Отказ от использования файлов в формате UDL</span><span class="sxs-lookup"><span data-stu-id="4b49e-145">Do Not Use Universal Data Link Files</span></span>  

 <span data-ttu-id="4b49e-146">Сведения о соединении для объекта **OleDbConnection** можно указать в файле UDL. Однако это следует избегать.</span><span class="sxs-lookup"><span data-stu-id="4b49e-146">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="4b49e-147">UDL-файлы не подвергаются шифрованию, и строки соединения хранятся в них в виде простого текста.</span><span class="sxs-lookup"><span data-stu-id="4b49e-147">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="4b49e-148">Так как UDL-файл представляет собой внешний файловый ресурс для приложения, его нельзя защитить средствами .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b49e-148">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="4b49e-149">Соединение с источником данных ODBC</span><span class="sxs-lookup"><span data-stu-id="4b49e-149">Connecting to an ODBC Data Source</span></span>  

 <span data-ttu-id="4b49e-150">Поставщик данных платформа .NET Framework для ODBC обеспечивает подключение к источникам данных, предоставляемым с помощью ODBC, с помощью объекта **OdbcConnection** .</span><span class="sxs-lookup"><span data-stu-id="4b49e-150">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="4b49e-151">Формат строки соединения поставщика данных .NET Framework для ODBC создан с учетом настолько полного согласования с форматом строки соединения ODBC, насколько это возможно.</span><span class="sxs-lookup"><span data-stu-id="4b49e-151">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="4b49e-152">Также можно указать имя источника данных ODBC (DSN).</span><span class="sxs-lookup"><span data-stu-id="4b49e-152">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="4b49e-153">Дополнительные сведения о **OdbcConnection** см. в разделе <xref:System.Data.Odbc.OdbcConnection> .</span><span class="sxs-lookup"><span data-stu-id="4b49e-153">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="4b49e-154">В следующем примере кода демонстрируется способ создания и открытия соединения с источником данных ODBC.</span><span class="sxs-lookup"><span data-stu-id="4b49e-154">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="4b49e-155">Соединение с источником данных Oracle</span><span class="sxs-lookup"><span data-stu-id="4b49e-155">Connecting to an Oracle Data Source</span></span>  

 <span data-ttu-id="4b49e-156">Поставщик данных платформа .NET Framework для Oracle обеспечивает подключение к источникам данных Oracle с помощью объекта **OracleConnection** .</span><span class="sxs-lookup"><span data-stu-id="4b49e-156">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="4b49e-157">Формат строки соединения поставщика данных .NET Framework для Oracle создан с учетом настолько полного согласования с форматом строки соединения поставщика OLE DB для Oracle (MSDAORA), насколько это возможно.</span><span class="sxs-lookup"><span data-stu-id="4b49e-157">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="4b49e-158">Дополнительные сведения о **OracleConnection** см. в разделе <xref:System.Data.OracleClient.OracleConnection> .</span><span class="sxs-lookup"><span data-stu-id="4b49e-158">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="4b49e-159">В следующем примере кода демонстрируется способ создания и открытия соединения с источником данных Oracle.</span><span class="sxs-lookup"><span data-stu-id="4b49e-159">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b49e-160">См. также</span><span class="sxs-lookup"><span data-stu-id="4b49e-160">See also</span></span>

- [<span data-ttu-id="4b49e-161">Подключение к источнику данных</span><span class="sxs-lookup"><span data-stu-id="4b49e-161">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="4b49e-162">Строки подключения</span><span class="sxs-lookup"><span data-stu-id="4b49e-162">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="4b49e-163">OLE DB, ODBC и объединение подключений в пул в Oracle</span><span class="sxs-lookup"><span data-stu-id="4b49e-163">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="4b49e-164">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4b49e-164">ADO.NET Overview</span></span>](ado-net-overview.md)
