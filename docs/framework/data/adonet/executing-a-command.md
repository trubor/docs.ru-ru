---
description: Дополнительные сведения о выполнении команды
title: Выполнение команды
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: 7b5fe46bf4d82fcd4f24cc0eb19e85a2ee9aca7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724327"
---
# <a name="executing-a-command"></a><span data-ttu-id="195c6-103">Выполнение команды</span><span class="sxs-lookup"><span data-stu-id="195c6-103">Executing a Command</span></span>

<span data-ttu-id="195c6-104">Каждый поставщик данных .NET Framework, включенный в состав .NET Framework, имеет собственный объект команды, наследуемый от <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="195c6-104">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="195c6-105">Поставщик данных .NET Framework для OLE DB содержит объект <xref:System.Data.OleDb.OleDbCommand>, поставщик данных .NET Framework для SQL Server - объект <xref:System.Data.SqlClient.SqlCommand>, поставщик данных .NET Framework для ODBC - объект <xref:System.Data.Odbc.OdbcCommand>, а поставщик данных .NET Framework для Oracle - объект <xref:System.Data.OracleClient.OracleCommand>.</span><span class="sxs-lookup"><span data-stu-id="195c6-105">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="195c6-106">Каждый из этих объектов предоставляет методы выполнения команд с учетом типа команды и требуемого возвращаемого значения, как описано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="195c6-106">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="195c6-107">Команда</span><span class="sxs-lookup"><span data-stu-id="195c6-107">Command</span></span>|<span data-ttu-id="195c6-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="195c6-108">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="195c6-109">Возвращает объект `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="195c6-109">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="195c6-110">Возвращает одно скалярное значение.</span><span class="sxs-lookup"><span data-stu-id="195c6-110">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="195c6-111">Выполняет команду, которая не возвращает строк.</span><span class="sxs-lookup"><span data-stu-id="195c6-111">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="195c6-112">Возвращает значение типа <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="195c6-112">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="195c6-113">Этот метод предусмотрен только для объекта `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="195c6-113">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="195c6-114">Каждый строго типизированный объект команды поддерживает также перечисление <xref:System.Data.CommandType>, которое указывает способ интерпретации строки команды, как описано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="195c6-114">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="195c6-115">CommandType</span><span class="sxs-lookup"><span data-stu-id="195c6-115">CommandType</span></span>|<span data-ttu-id="195c6-116">Описание</span><span class="sxs-lookup"><span data-stu-id="195c6-116">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="195c6-117">Команда SQL, определяющая инструкции, которые выполняются применительно к источнику данных.</span><span class="sxs-lookup"><span data-stu-id="195c6-117">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="195c6-118">Имя хранимой процедуры.</span><span class="sxs-lookup"><span data-stu-id="195c6-118">The name of the stored procedure.</span></span> <span data-ttu-id="195c6-119">Свойство команды `Parameters` может использоваться для доступа к входным и выходным параметрам и возвращаемым значениям независимо от вызываемого метода `Execute`.</span><span class="sxs-lookup"><span data-stu-id="195c6-119">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="195c6-120">При использовании `ExecuteReader` возвращаемые значения и выходные параметры будут недоступными, пока не будет закрыт `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="195c6-120">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="195c6-121">Имя таблицы.</span><span class="sxs-lookup"><span data-stu-id="195c6-121">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="195c6-122">Пример</span><span class="sxs-lookup"><span data-stu-id="195c6-122">Example</span></span>  

 <span data-ttu-id="195c6-123">Следующий пример кода демонстрирует способ создания объекта <xref:System.Data.SqlClient.SqlCommand> для выполнения хранимой процедуры путем установки его свойств.</span><span class="sxs-lookup"><span data-stu-id="195c6-123">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="195c6-124">Объект <xref:System.Data.SqlClient.SqlParameter> используется для задания входных параметров хранимой процедуры.</span><span class="sxs-lookup"><span data-stu-id="195c6-124">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="195c6-125">Команда выполняется с помощью метода <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>, и выходное значение из <xref:System.Data.SqlClient.SqlDataReader> отображается в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="195c6-125">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="195c6-126">Команды устранения неполадок</span><span class="sxs-lookup"><span data-stu-id="195c6-126">Troubleshooting Commands</span></span>  

 <span data-ttu-id="195c6-127">Поставщик данных .NET Framework для SQL Server добавляет счетчики производительности, позволяя обнаруживать периодически возникающие проблемы, связанные со сбоями команд.</span><span class="sxs-lookup"><span data-stu-id="195c6-127">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="195c6-128">Дополнительные сведения см. в разделе [счетчики производительности](performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="195c6-128">For more information see [Performance Counters](performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195c6-129">См. также</span><span class="sxs-lookup"><span data-stu-id="195c6-129">See also</span></span>

- [<span data-ttu-id="195c6-130">Команды и параметры</span><span class="sxs-lookup"><span data-stu-id="195c6-130">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="195c6-131">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="195c6-131">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="195c6-132">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="195c6-132">ADO.NET Overview</span></span>](ado-net-overview.md)
