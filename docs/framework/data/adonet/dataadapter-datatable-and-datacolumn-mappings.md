---
description: Дополнительные сведения о сопоставлении DataAdapter DataTable и DataColumn
title: Сопоставления DataAdapter DataTable и DataColumn
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 25007925afa57dd0cb6e75f808444f1bfaeea9b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739740"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="9276b-103">Сопоставления DataAdapter DataTable и DataColumn</span><span class="sxs-lookup"><span data-stu-id="9276b-103">DataAdapter DataTable and DataColumn Mappings</span></span>

<span data-ttu-id="9276b-104">Объект **DataAdapter** содержит коллекцию из нуля или более <xref:System.Data.Common.DataTableMapping> объектов в своем свойстве **TableMappings** .</span><span class="sxs-lookup"><span data-stu-id="9276b-104">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="9276b-105">**Экземпляр DataTableMapping** предоставляет основное сопоставление данных, возвращенных запросом к источнику данных, и <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="9276b-105">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="9276b-106">Имя **экземпляр DataTableMapping** может быть передано вместо имени **DataTable** в метод **Fill** объекта **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="9276b-106">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="9276b-107">В следующем примере создается экземпляр класса **DataTableMapping** с именем **AuthorsMapping** для таблицы **Authors**.</span><span class="sxs-lookup"><span data-stu-id="9276b-107">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="9276b-108">Класс **DataTableMapping** позволяет использовать имена столбцов в объекте **DataTable**, отличные от таковых в базе данных.</span><span class="sxs-lookup"><span data-stu-id="9276b-108">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="9276b-109">В сопоставлении **DataAdapter** это сопоставление используется для согласования столбцов при обновлении таблицы.</span><span class="sxs-lookup"><span data-stu-id="9276b-109">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="9276b-110">Если не указан объект **TableName** или имя **DataTableMapping** при вызове метода **Fill** или **Update** объекта **DataAdapter**, то в объекте **DataAdapter** выполняется поиск экземпляра **DataTableMapping** с именем "Table".</span><span class="sxs-lookup"><span data-stu-id="9276b-110">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="9276b-111">Если этот **экземпляр DataTableMapping** не существует, то **TableName** объекта **DataTable** имеет значение Table.</span><span class="sxs-lookup"><span data-stu-id="9276b-111">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="9276b-112">Можно указать применяемый по умолчанию класс **DataTableMapping** при создании объекта **DataTableMapping** с именем "Table".</span><span class="sxs-lookup"><span data-stu-id="9276b-112">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="9276b-113">В следующем примере кода создается экземпляр **DataTableMapping** (из пространства имен <xref:System.Data.Common>) и задается в качестве применяемого по умолчанию отображения для указанного объекта **DataAdapter** путем присваивания ему имени "Table".</span><span class="sxs-lookup"><span data-stu-id="9276b-113">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="9276b-114">Затем в этом примере столбцы из первой таблицы в результатах запроса (таблицы **Customers** базы данных **Northwind**) сопоставляются с набором понятных для пользователя имен в таблице **Northwind Customers** в <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9276b-114">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9276b-115">Для столбцов, к которым не применяется сопоставление, используются имена столбцов из источника данных.</span><span class="sxs-lookup"><span data-stu-id="9276b-115">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="9276b-116">В более сложных ситуациях может быть принято решение, что один и тот же экземпляр **DataAdapter** должен поддерживать загрузку разных таблиц с различными сопоставлениями.</span><span class="sxs-lookup"><span data-stu-id="9276b-116">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="9276b-117">Для этого просто добавьте дополнительные объекты **экземпляр DataTableMapping** .</span><span class="sxs-lookup"><span data-stu-id="9276b-117">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="9276b-118">Если методу **Fill** передается экземпляр **DataSet** и имя **DataTableMapping**, то при наличии сопоставления с этим именем используется это сопоставление; в противном случае используется объект **DataTable** с этим именем.</span><span class="sxs-lookup"><span data-stu-id="9276b-118">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="9276b-119">В следующих примерах создается экземпляр **DataTableMapping** с именем **Customers** и именем объекта **DataTable**, равным **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="9276b-119">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="9276b-120">Затем в этом примере строки, возвращаемые инструкцией SELECT, сопоставляются с объектом **DataTable**, имеющим имя **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="9276b-120">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="9276b-121">Если имя исходного столбца не задано для сопоставления столбцов, или имя исходной таблицы не задано для сопоставления таблиц, то автоматически создаются имена, применяемые по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9276b-121">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="9276b-122">Если для сопоставления столбцов не указан исходный столбец, сопоставлению столбцов присваивается добавочное имя по умолчанию **SourceColumn** *N,* начиная с **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="9276b-122">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="9276b-123">Если для сопоставления таблицы не указано имя исходной таблицы, сопоставлению таблицы присваивается добавочное имя по умолчанию **SourceTable** *N*, начиная с **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="9276b-123">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9276b-124">Рекомендуется избегать использования соглашения об именах **SourceColumn** *N* для сопоставления столбцов или **SourceTable** *N* для сопоставления таблиц, поскольку заданное имя может конфликтовать с существующим именем заданного по умолчанию сопоставления столбцов в коллекции **ColumnMappingCollection** или с именем сопоставления таблиц в коллекции **DataTableMappingCollection**.</span><span class="sxs-lookup"><span data-stu-id="9276b-124">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="9276b-125">Если указанное имя уже существует, возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="9276b-125">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="9276b-126">Обработка нескольких результирующих наборов</span><span class="sxs-lookup"><span data-stu-id="9276b-126">Handling Multiple Result Sets</span></span>  

 <span data-ttu-id="9276b-127">Если команда **SelectCommand** возвращает несколько таблиц, то в методе **Fill** для таблиц в объекте **DataSet** автоматически формируются имена, которые в качестве суффиксов имеют автоматически увеличивающиеся значения. Значения начинаются с указанного имени таблицы и увеличиваются в форме **TableName** *N*, первым значением является **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="9276b-127">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="9276b-128">Можно использовать сопоставления таблиц для сопоставления автоматически создаваемого имени таблицы с тем именем, которое требуется задать для таблицы в объекте **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9276b-128">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="9276b-129">Например, для к команды **SelectCommand**, которая возвращает две таблицы, **Customers** и **Orders**, можно выполнить следующий вызов метода **Fill**.</span><span class="sxs-lookup"><span data-stu-id="9276b-129">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="9276b-130">В объекте **DataSet** будут созданы две таблицы: **Customers** и **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="9276b-130">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="9276b-131">Можно использовать сопоставления таблиц для обеспечения того, чтобы вторая таблица получила имя **Orders** вместо **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="9276b-131">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="9276b-132">Для этого необходимо сопоставить исходную таблицу **Customers1** с таблицей **Orders** из **DataSet**, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="9276b-132">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="9276b-133">См. также</span><span class="sxs-lookup"><span data-stu-id="9276b-133">See also</span></span>

- [<span data-ttu-id="9276b-134">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="9276b-134">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="9276b-135">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9276b-135">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="9276b-136">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9276b-136">ADO.NET Overview</span></span>](ado-net-overview.md)
