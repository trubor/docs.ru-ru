---
description: 'Дополнительные сведения: получение сведений о схеме базы данных'
title: Извлечение сведений о схеме базы данных
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 84ac94a72b23d0b1d6924600f2fd33b2a285eab8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663408"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="b7257-103">Извлечение сведений о схеме базы данных</span><span class="sxs-lookup"><span data-stu-id="b7257-103">Retrieving Database Schema Information</span></span>

<span data-ttu-id="b7257-104">Получение сведений о схеме из базы данных выполняется с помощью процесса обнаружения схемы.</span><span class="sxs-lookup"><span data-stu-id="b7257-104">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="b7257-105">Обнаружение схемы позволяет приложениям запрашивать управляемые поставщики для поиска и возвращения сведений о схеме базы данных, также называемых *метаданными*, для данной базы данных.</span><span class="sxs-lookup"><span data-stu-id="b7257-105">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="b7257-106">Различные элементы схемы базы данных, например таблицы, столбцы и хранимые процедуры, предоставляются через коллекции схем.</span><span class="sxs-lookup"><span data-stu-id="b7257-106">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="b7257-107">Каждая коллекция схемы в зависимости от используемого поставщика содержит различные сведения о схеме.</span><span class="sxs-lookup"><span data-stu-id="b7257-107">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="b7257-108">Каждый из платформа .NET Framework управляемых поставщиков реализует метод **GetSchema** в классе **Connection** , а сведения о схеме, возвращаемые методом **GetSchema** , поступают в виде <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="b7257-108">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="b7257-109">**GetSchema** — перегружаемый метод, содержащий необязательные параметры для указания возвращаемой коллекции схем и ограничения объема возвращаемых сведений.</span><span class="sxs-lookup"><span data-stu-id="b7257-109">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="b7257-110">Поставщики данных платформа .NET Framework для OLE DB, ODBC, Oracle и SqlClient предоставляют метод **GetSchemaTable** , возвращающий объект DataTable, описывающий метаданные столбца для **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="b7257-110">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="b7257-111">Поставщик данных .NET Framework для OLE DB также предоставляет данные схемы с помощью метода <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> объекта <xref:System.Data.OleDb.OleDbConnection>.</span><span class="sxs-lookup"><span data-stu-id="b7257-111">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="b7257-112">В качестве аргументов **жетоледбсчематабле** принимает <xref:System.Data.OleDb.OleDbSchemaGuid> , определяющий возвращаемую информацию о схеме, и массив ограничений на возвращаемые столбцы.</span><span class="sxs-lookup"><span data-stu-id="b7257-112">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="b7257-113">**Жетоледбсчематабле** возвращает <xref:System.Data.DataTable> заполненную информацию о запрашиваемой схеме.</span><span class="sxs-lookup"><span data-stu-id="b7257-113">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7257-114">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="b7257-114">In This Section</span></span>  

 [<span data-ttu-id="b7257-115">Метод GetSchema и коллекции схем</span><span class="sxs-lookup"><span data-stu-id="b7257-115">GetSchema and Schema Collections</span></span>](getschema-and-schema-collections.md)  
 <span data-ttu-id="b7257-116">Описание метода **GetSchema** и его использования для получения и ограничения сведений о схеме из базы данных.</span><span class="sxs-lookup"><span data-stu-id="b7257-116">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="b7257-117">Ограничения схемы</span><span class="sxs-lookup"><span data-stu-id="b7257-117">Schema Restrictions</span></span>  
 <span data-ttu-id="b7257-118">Описание ограничений схемы, которые можно использовать с методом **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="b7257-118">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="b7257-119">Общие коллекции схем</span><span class="sxs-lookup"><span data-stu-id="b7257-119">Common Schema Collections</span></span>](common-schema-collections.md)  
 <span data-ttu-id="b7257-120">Описывает стандартные коллекции схем, поддерживаемые всеми управляемыми поставщиками .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7257-120">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="b7257-121">SQL Server коллекции схем</span><span class="sxs-lookup"><span data-stu-id="b7257-121">SQL Server Schema Collections</span></span>](sql-server-schema-collections.md)  
 <span data-ttu-id="b7257-122">Описывается коллекция схем, поддерживаемая поставщиком .NET Framework для SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b7257-122">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="b7257-123">Коллекции схемы в Oracle</span><span class="sxs-lookup"><span data-stu-id="b7257-123">Oracle Schema Collections</span></span>](oracle-schema-collections.md)  
 <span data-ttu-id="b7257-124">Описывается коллекция схем, поддерживаемая поставщиком .NET Framework для Oracle.</span><span class="sxs-lookup"><span data-stu-id="b7257-124">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="b7257-125">Коллекции схемы ODBC</span><span class="sxs-lookup"><span data-stu-id="b7257-125">ODBC Schema Collections</span></span>](odbc-schema-collections.md)  
 <span data-ttu-id="b7257-126">Описываются коллекции схем для драйверов ODBC.</span><span class="sxs-lookup"><span data-stu-id="b7257-126">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="b7257-127">Коллекции схемы OLE DB</span><span class="sxs-lookup"><span data-stu-id="b7257-127">OLE DB Schema Collections</span></span>](ole-db-schema-collections.md)  
 <span data-ttu-id="b7257-128">Описываются коллекции схем для поставщиков OLE DB.</span><span class="sxs-lookup"><span data-stu-id="b7257-128">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b7257-129">Справочник</span><span class="sxs-lookup"><span data-stu-id="b7257-129">Reference</span></span>  

 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="b7257-130">Описание метода **GetSchema** класса <xref:System.Data.Common.DbConnection>.</span><span class="sxs-lookup"><span data-stu-id="b7257-130">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="b7257-131">Описание метода **GetSchema** класса <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="b7257-131">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="b7257-132">Описание метода **GetSchema** класса <xref:System.Data.OleDb.OleDbConnection>.</span><span class="sxs-lookup"><span data-stu-id="b7257-132">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="b7257-133">Описание метода **GetSchema** класса <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="b7257-133">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="b7257-134">Описание метода **GetSchema** класса <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="b7257-134">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="b7257-135">Описание метода **GetSchemaTable** класса <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b7257-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="b7257-136">Описание метода **GetSchemaTable** класса <xref:System.Data.Odbc.OdbcDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b7257-136">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="b7257-137">Описание метода **GetSchemaTable** класса <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b7257-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="b7257-138">Описание метода **GetSchemaTable** класса <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b7257-138">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="b7257-139">Описание метода **GetSchemaTable** класса <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b7257-139">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7257-140">См. также</span><span class="sxs-lookup"><span data-stu-id="b7257-140">See also</span></span>

- [<span data-ttu-id="b7257-141">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7257-141">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="b7257-142">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7257-142">ADO.NET Overview</span></span>](ado-net-overview.md)
