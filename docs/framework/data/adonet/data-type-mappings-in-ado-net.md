---
description: Дополнительные сведения о сопоставлении типов данных в ADO.NET
title: Сопоставления типов данных
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: c1829fdc2ebc053d1fd3a76e827a81e582572233
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786450"
---
# <a name="data-type-mappings-in-adonet"></a><span data-ttu-id="cbcb2-103">Сопоставления типов данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cbcb2-103">Data Type Mappings in ADO.NET</span></span>

<span data-ttu-id="cbcb2-104">Платформа .NET Framework основана на общей системе типов, в которой определяются способы объявления, использования типов и управления ими во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-104">The .NET Framework is based on the common type system, which defines how types are declared, used, and managed in the runtime.</span></span> <span data-ttu-id="cbcb2-105">Система типов состоит из типов-значений и типов-ссылок, производных от базового типа <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-105">It consists of both value types and reference types, which all derive from the <xref:System.Object> base type.</span></span> <span data-ttu-id="cbcb2-106">При работе с источником данных не указанный явным образом тип данных выводится из поставщика данных.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-106">When working with a data source, the data type is inferred from the data provider if it is not explicitly specified.</span></span> <span data-ttu-id="cbcb2-107">Например, объект <xref:System.Data.DataSet> не зависит ни от одного конкретного источника данных.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-107">For example, a <xref:System.Data.DataSet> object is independent of any specific data source.</span></span> <span data-ttu-id="cbcb2-108">Получение данных в `DataSet` осуществляется из источника данных, а изменения передаются для сохранения в источнике данных с использованием `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-108">Data in a `DataSet` is retrieved from a data source, and changes are persisted back to the data source by using a `DataAdapter`.</span></span> <span data-ttu-id="cbcb2-109">Это означает, что при `DataAdapter` заполнении <xref:System.Data.DataTable> в `DataSet` со значениями из источника данных результирующие типы данных столбцов в `DataTable` являются платформа .NET Framework типами, а не типами, характерными для платформа .NET Frameworkного поставщика данных, используемого для подключения к источнику данных.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-109">This means that when a `DataAdapter` fills a <xref:System.Data.DataTable> in a `DataSet` with values from a data source, the resulting data types of the columns in the `DataTable` are .NET Framework types, instead of types specific to the .NET Framework data provider that is used to connect to the data source.</span></span>  
  
 <span data-ttu-id="cbcb2-110">Аналогично, когда `DataReader` возвращает значение из источника данных, результирующее значение сохраняется в локальной переменной с типом .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-110">Likewise, when a `DataReader` returns a value from a data source, the resulting value is stored in a local variable that has a .NET Framework type.</span></span> <span data-ttu-id="cbcb2-111">Как для операций, так `Fill` `DataAdapter` и для `Get` методов `DataReader` , тип платформа .NET Framework выводится из значения, возвращаемого поставщиком данных платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-111">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the value returned from the .NET Framework data provider.</span></span>  
  
 <span data-ttu-id="cbcb2-112">Если известен тип возвращаемого значения, то вместо выводимого типа данных можно воспользоваться типизированными методами доступа объекта `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-112">Instead of relying on the inferred data type, you can use the typed accessor methods of the `DataReader` when you know the specific type of the value being returned.</span></span> <span data-ttu-id="cbcb2-113">Типизированные методы доступа обеспечивают оптимальную производительность, возвращая значение с конкретным типом .NET Framework, что устраняет необходимость в дополнительном преобразовании типов.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-113">Typed accessor methods give you better performance by returning a value as a specific .NET Framework type, which eliminates the need for additional type conversion.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbcb2-114">Значения NULL для типов данных поставщика данных платформа .NET Framework представлены в `DBNull.Value` .</span><span class="sxs-lookup"><span data-stu-id="cbcb2-114">Null values for .NET Framework data provider data types are represented by `DBNull.Value`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cbcb2-115">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="cbcb2-115">In This Section</span></span>  

 [<span data-ttu-id="cbcb2-116">Сопоставления типов данных SQL Server</span><span class="sxs-lookup"><span data-stu-id="cbcb2-116">SQL Server Data Type Mappings</span></span>](sql-server-data-type-mappings.md)  
 <span data-ttu-id="cbcb2-117">Выводит список сопоставлений выводимых типов данных и методов доступа к данным для объекта <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-117">Lists inferred data type mappings and data accessor methods for <xref:System.Data.SqlClient>.</span></span>  
  
 [<span data-ttu-id="cbcb2-118">Сопоставления типов данных OLE DB</span><span class="sxs-lookup"><span data-stu-id="cbcb2-118">OLE DB Data Type Mappings</span></span>](ole-db-data-type-mappings.md)  
 <span data-ttu-id="cbcb2-119">Выводит список сопоставлений выводимых типов данных и методов доступа к данным для объекта <xref:System.Data.OleDb>.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-119">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OleDb>.</span></span>  
  
 [<span data-ttu-id="cbcb2-120">Сопоставления типов данных ODBC</span><span class="sxs-lookup"><span data-stu-id="cbcb2-120">ODBC Data Type Mappings</span></span>](odbc-data-type-mappings.md)  
 <span data-ttu-id="cbcb2-121">Выводит список сопоставлений выводимых типов данных и методов доступа к данным для объекта <xref:System.Data.Odbc>.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-121">Lists inferred data type mappings and data accessor methods for <xref:System.Data.Odbc>.</span></span>  
  
 [<span data-ttu-id="cbcb2-122">Сопоставления типов данных Oracle</span><span class="sxs-lookup"><span data-stu-id="cbcb2-122">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="cbcb2-123">Выводит список сопоставлений выводимых типов данных и методов доступа к данным для объекта <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-123">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OracleClient>.</span></span>  
  
 [<span data-ttu-id="cbcb2-124">Числа с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="cbcb2-124">Floating-Point Numbers</span></span>](floating-point-numbers.md)  
 <span data-ttu-id="cbcb2-125">Описывает проблемы, с которыми разработчики часто сталкиваются при работе с числами с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="cbcb2-125">Describes issues that developers frequently encounter when working with floating-point numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbcb2-126">См. также</span><span class="sxs-lookup"><span data-stu-id="cbcb2-126">See also</span></span>

- [<span data-ttu-id="cbcb2-127">Типы данных SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cbcb2-127">SQL Server Data Types and ADO.NET</span></span>](./sql/sql-server-data-types.md)
- [<span data-ttu-id="cbcb2-128">Настройка параметров и типы данных параметров</span><span class="sxs-lookup"><span data-stu-id="cbcb2-128">Configuring Parameters and Parameter Data Types</span></span>](configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="cbcb2-129">Извлечение сведений о схеме базы данных</span><span class="sxs-lookup"><span data-stu-id="cbcb2-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="cbcb2-130">Система общих типов CTS</span><span class="sxs-lookup"><span data-stu-id="cbcb2-130">Common Type System</span></span>](../../../standard/base-types/common-type-system.md)
- <span data-ttu-id="cbcb2-131">[Преобразование типов](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="cbcb2-131">[Converting Types](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span></span>
- [<span data-ttu-id="cbcb2-132">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cbcb2-132">ADO.NET Overview</span></span>](ado-net-overview.md)
