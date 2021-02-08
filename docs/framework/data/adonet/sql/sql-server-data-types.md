---
description: 'Дополнительные сведения: SQL Server типов данных и ADO.NET'
title: Типы данных SQL Server и ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 841fa5864bf54b5e4fc4dc24dab64e6ac1435c7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767301"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="c80ab-103">Типы данных SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c80ab-103">SQL Server Data Types and ADO.NET</span></span>

<span data-ttu-id="c80ab-104">В SQL Server и .NET Framework используются различные системы типов, что может привести к потенциальной потере данных.</span><span class="sxs-lookup"><span data-stu-id="c80ab-104">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="c80ab-105">Чтобы сохранить целостность данных, поставщик данных .NET Framework для SQL Server (<xref:System.Data.SqlClient>) предоставляет типизированные методы доступа для работы с данными SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c80ab-105">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="c80ab-106">Перечисления в классах <xref:System.Data.SqlDbType> можно использовать для указания типов данных <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="c80ab-106">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="c80ab-107">Дополнительные сведения и таблица с описанием сопоставлений типов данных между типами данных SQL Server и платформа .NET Framework см. в разделе [SQL Server сопоставления типов данных](../sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="c80ab-107">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="c80ab-108">В SQL Server 2008 появились новые типы данных, разработанные для удовлетворения бизнес-потребностей при работе с датами и временем, структурированными, частично структурированными и неструктурированными данными.</span><span class="sxs-lookup"><span data-stu-id="c80ab-108">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="c80ab-109">Они описаны в электронной документации на SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="c80ab-109">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="c80ab-110">Типы данных SQL Server, доступные для использования в приложении, зависят от используемой версии SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c80ab-110">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="c80ab-111">Дополнительные сведения см. в электронной документации для соответствующей версии SQL Server в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="c80ab-111">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="c80ab-112">**Документация по SQL Server**</span><span class="sxs-lookup"><span data-stu-id="c80ab-112">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="c80ab-113">Типы данных (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c80ab-113">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a><span data-ttu-id="c80ab-114">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="c80ab-114">In This Section</span></span>  

 [<span data-ttu-id="c80ab-115">Типы SqlType и набор данных</span><span class="sxs-lookup"><span data-stu-id="c80ab-115">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="c80ab-116">Описывает тип поддержки пространства имен `SqlTypes` в `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="c80ab-116">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="c80ab-117">Обработка значений NULL</span><span class="sxs-lookup"><span data-stu-id="c80ab-117">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="c80ab-118">Демонстрирует работу со значениями NULL и логикой трех значений.</span><span class="sxs-lookup"><span data-stu-id="c80ab-118">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="c80ab-119">Сравнение значений GUID и uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="c80ab-119">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="c80ab-120">Демонстрируется работа со значениями GUID и uniqueidentifier в SQL Server и .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c80ab-120">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="c80ab-121">Данные даты и времени</span><span class="sxs-lookup"><span data-stu-id="c80ab-121">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="c80ab-122">В этой статье описывается использование новых типов данных даты и времени, появившихся в SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="c80ab-122">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="c80ab-123">Большие, определяемые пользователем типы</span><span class="sxs-lookup"><span data-stu-id="c80ab-123">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="c80ab-124">Здесь демонстрируется получение данных из UDT с большими значениями, представленных в SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="c80ab-124">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="c80ab-125">XML-данные в SQL Server</span><span class="sxs-lookup"><span data-stu-id="c80ab-125">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="c80ab-126">Сведения о том, как работать с XML-данными, полученными из SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c80ab-126">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c80ab-127">Справочник</span><span class="sxs-lookup"><span data-stu-id="c80ab-127">Reference</span></span>  

 <xref:System.Data.DataSet>  
 <span data-ttu-id="c80ab-128">Описание класса `DataSet` и всех его членов.</span><span class="sxs-lookup"><span data-stu-id="c80ab-128">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="c80ab-129">Описание пространства имен `SqlTypes` и всех его членов.</span><span class="sxs-lookup"><span data-stu-id="c80ab-129">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="c80ab-130">Описание перечисления `SqlDbType` и всех его членов.</span><span class="sxs-lookup"><span data-stu-id="c80ab-130">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="c80ab-131">Описание перечисления `DbType` и всех его членов.</span><span class="sxs-lookup"><span data-stu-id="c80ab-131">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c80ab-132">См. также</span><span class="sxs-lookup"><span data-stu-id="c80ab-132">See also</span></span>

- [<span data-ttu-id="c80ab-133">Сопоставления типов данных SQL Server</span><span class="sxs-lookup"><span data-stu-id="c80ab-133">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="c80ab-134">Настройка параметров и типы данных параметров</span><span class="sxs-lookup"><span data-stu-id="c80ab-134">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="c80ab-135">Параметры, возвращающие табличные значения</span><span class="sxs-lookup"><span data-stu-id="c80ab-135">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="c80ab-136">Двоичные данные и данные больших значений SQL Server</span><span class="sxs-lookup"><span data-stu-id="c80ab-136">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="c80ab-137">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c80ab-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
