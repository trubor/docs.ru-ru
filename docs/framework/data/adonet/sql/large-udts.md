---
description: 'Подробнее: крупные определяемые пользователем типы'
title: Большие, определяемые пользователем типы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: e1a40330bb48d6320dc96533e764f1b856e0f410
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663187"
---
# <a name="large-udts"></a><span data-ttu-id="0f984-103">Большие UDT</span><span class="sxs-lookup"><span data-stu-id="0f984-103">Large UDTs</span></span>

<span data-ttu-id="0f984-104">Определяемые пользователем типы призваны дать разработчику возможность расширить серверную систему скалярных типов путем хранения объектов среды CLR в базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0f984-104">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="0f984-105">Определяемые пользователем типы могут содержать несколько элементов, и их поведение может отличаться от традиционных псевдонимов типов данных, которые состоят из одного системного типа данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0f984-105">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f984-106">Чтобы воспользоваться расширенной поддержкой SqlClient определяемых пользователем типов данных большого размера, необходимо установить .NET Framework 3.5 с пакетом обновления 1 (SP1) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="0f984-106">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="0f984-107">Ранее размер определяемых пользователем типов был ограничен 8 килобайтами.</span><span class="sxs-lookup"><span data-stu-id="0f984-107">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="0f984-108">Это ограничение было снято в SQL Server 2008 для определяемых пользователем типов, имеющих формат <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="0f984-108">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="0f984-109">Полную документацию по определяемым пользователем типам данных см. в электронной документации по SQL Server для используемой версии SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0f984-109">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="0f984-110">**Документация по SQL Server**</span><span class="sxs-lookup"><span data-stu-id="0f984-110">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="0f984-111">Пользовательские типы CLR</span><span class="sxs-lookup"><span data-stu-id="0f984-111">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="0f984-112">Загрузка схем определяемых пользователем типов данных с помощью метода GetSchema</span><span class="sxs-lookup"><span data-stu-id="0f984-112">Retrieving UDT Schemas Using GetSchema</span></span>  

 <span data-ttu-id="0f984-113">Метод <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A><xref:System.Data.SqlClient.SqlConnection> возвращает сведения о схеме базы данных в <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="0f984-113">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="0f984-114">Дополнительные сведения см. в разделе [SQL Server коллекции схем](../sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="0f984-114">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="0f984-115">Значения столбца GetSchemaTable для определяемых пользователем типов данных</span><span class="sxs-lookup"><span data-stu-id="0f984-115">GetSchemaTable Column Values for UDTs</span></span>  

 <span data-ttu-id="0f984-116">Метод <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A><xref:System.Data.SqlClient.SqlDataReader> возвращает <xref:System.Data.DataTable>, описывающее метаданные столбца.</span><span class="sxs-lookup"><span data-stu-id="0f984-116">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="0f984-117">В следующей таблице описаны различия в метаданных столбцов для больших пользовательских типов данных между SQL Server 2005 и SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="0f984-117">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="0f984-118">Столбец SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="0f984-118">SqlDataReader column</span></span>|<span data-ttu-id="0f984-119">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="0f984-119">SQL Server 2005</span></span>|<span data-ttu-id="0f984-120">SQL Server 2008 и более поздние версии</span><span class="sxs-lookup"><span data-stu-id="0f984-120">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="0f984-121">Различается</span><span class="sxs-lookup"><span data-stu-id="0f984-121">Varies</span></span>|<span data-ttu-id="0f984-122">Различается</span><span class="sxs-lookup"><span data-stu-id="0f984-122">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="0f984-123">255</span><span class="sxs-lookup"><span data-stu-id="0f984-123">255</span></span>|<span data-ttu-id="0f984-124">255</span><span class="sxs-lookup"><span data-stu-id="0f984-124">255</span></span>|  
|`NumericScale`|<span data-ttu-id="0f984-125">255</span><span class="sxs-lookup"><span data-stu-id="0f984-125">255</span></span>|<span data-ttu-id="0f984-126">255</span><span class="sxs-lookup"><span data-stu-id="0f984-126">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="0f984-127">Экземпляр UDT</span><span class="sxs-lookup"><span data-stu-id="0f984-127">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="0f984-128">Экземпляр UDT</span><span class="sxs-lookup"><span data-stu-id="0f984-128">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="0f984-129">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="0f984-129">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="0f984-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="0f984-130">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="0f984-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="0f984-131">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="0f984-132">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="0f984-132">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="0f984-133">Имя из трех частей, указанное как *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="0f984-133">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="0f984-134">Различается</span><span class="sxs-lookup"><span data-stu-id="0f984-134">Varies</span></span>|<span data-ttu-id="0f984-135">Различается</span><span class="sxs-lookup"><span data-stu-id="0f984-135">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="0f984-136">Вопросы, связанные с SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="0f984-136">SqlDataReader Considerations</span></span>  

 <span data-ttu-id="0f984-137">Объект <xref:System.Data.SqlClient.SqlDataReader> в SQL Server 2008 был расширен для поддержки загрузки значений определяемых пользователем типов данных большого размера.</span><span class="sxs-lookup"><span data-stu-id="0f984-137">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="0f984-138">Как большие значения пользовательского типа обрабатываются <xref:System.Data.SqlClient.SqlDataReader>, зависит от используемой версии SQL Server, а также от `Type System Version`, указанного в строке подключения.</span><span class="sxs-lookup"><span data-stu-id="0f984-138">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="0f984-139">Для получения дополнительной информации см. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f984-139">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="0f984-140">Следующие методы <xref:System.Data.SqlClient.SqlDataReader> будут возвращать <xref:System.Data.SqlTypes.SqlBinary> вместо пользовательского типа, если для `Type System Version` установлено значение SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="0f984-140">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="0f984-141">Следующие методы будут возвращать массив `Byte[]` вместо пользовательского типа, если для `Type System Version` установлено значение SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="0f984-141">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="0f984-142">Обратите внимание, что для текущей версии ADO.NET никакие преобразования не выполняются.</span><span class="sxs-lookup"><span data-stu-id="0f984-142">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="0f984-143">Указание SqlParameters</span><span class="sxs-lookup"><span data-stu-id="0f984-143">Specifying SqlParameters</span></span>  

 <span data-ttu-id="0f984-144">Следующие свойства <xref:System.Data.SqlClient.SqlParameter> были расширены для работы с большими пользовательскими типами.</span><span class="sxs-lookup"><span data-stu-id="0f984-144">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="0f984-145">Свойство SqlParameter</span><span class="sxs-lookup"><span data-stu-id="0f984-145">SqlParameter Property</span></span>|<span data-ttu-id="0f984-146">Описание</span><span class="sxs-lookup"><span data-stu-id="0f984-146">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="0f984-147">Возвращает или задает объект, представляющий значение параметра.</span><span class="sxs-lookup"><span data-stu-id="0f984-147">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="0f984-148">Значение по умолчанию — NULL.</span><span class="sxs-lookup"><span data-stu-id="0f984-148">The default is null.</span></span> <span data-ttu-id="0f984-149">Свойством может быть `SqlBinary`, `Byte[]` или управляемый объект.</span><span class="sxs-lookup"><span data-stu-id="0f984-149">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="0f984-150">Возвращает или задает объект, представляющий значение параметра.</span><span class="sxs-lookup"><span data-stu-id="0f984-150">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="0f984-151">Значение по умолчанию — NULL.</span><span class="sxs-lookup"><span data-stu-id="0f984-151">The default is null.</span></span> <span data-ttu-id="0f984-152">Свойством может быть `SqlBinary`, `Byte[]` или управляемый объект.</span><span class="sxs-lookup"><span data-stu-id="0f984-152">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="0f984-153">Возвращает или задает размер значения параметра для разрешения.</span><span class="sxs-lookup"><span data-stu-id="0f984-153">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="0f984-154">Значение по умолчанию — 0.</span><span class="sxs-lookup"><span data-stu-id="0f984-154">The default value is 0.</span></span> <span data-ttu-id="0f984-155">Свойство может быть целым числом, представляющим размер значения параметра.</span><span class="sxs-lookup"><span data-stu-id="0f984-155">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="0f984-156">Для больших определяемых пользователем типов оно может равняться действительному размеру определяемого пользователем типа или иметь значение –1 — для неизвестных.</span><span class="sxs-lookup"><span data-stu-id="0f984-156">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="0f984-157">Пример извлечения данных</span><span class="sxs-lookup"><span data-stu-id="0f984-157">Retrieving Data Example</span></span>  

 <span data-ttu-id="0f984-158">В следующем фрагменте кода показано, как получить большие данные пользовательского типа.</span><span class="sxs-lookup"><span data-stu-id="0f984-158">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="0f984-159">Переменная `connectionString` предполагает допустимое соединение с базой данных SQL Server, а переменная `commandString` предполагает, что допустимая инструкция SELECT со столбцом первичного ключа указана первой.</span><span class="sxs-lookup"><span data-stu-id="0f984-159">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
```csharp  
using (SqlConnection connection = new SqlConnection(
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f984-160">См. также</span><span class="sxs-lookup"><span data-stu-id="0f984-160">See also</span></span>

- [<span data-ttu-id="0f984-161">Настройка параметров и типы данных параметров</span><span class="sxs-lookup"><span data-stu-id="0f984-161">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="0f984-162">Извлечение сведений о схеме базы данных</span><span class="sxs-lookup"><span data-stu-id="0f984-162">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="0f984-163">Сопоставления типов данных SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f984-163">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="0f984-164">Двоичные данные и данные больших значений SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f984-164">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="0f984-165">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0f984-165">ADO.NET Overview</span></span>](../ado-net-overview.md)
