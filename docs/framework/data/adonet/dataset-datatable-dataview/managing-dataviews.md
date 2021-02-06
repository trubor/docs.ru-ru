---
description: 'Дополнительные сведения: Управление представлениями'
title: Управление объектами DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: cdd9da9c4f67321dba36d22610704fc2e2561930
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652098"
---
# <a name="managing-dataviews"></a><span data-ttu-id="635fb-103">Управление объектами DataView</span><span class="sxs-lookup"><span data-stu-id="635fb-103">Managing DataViews</span></span>

<span data-ttu-id="635fb-104">С помощью класса <xref:System.Data.DataViewManager> можно управлять параметрами представлений во всех таблицах <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="635fb-104">You can use a <xref:System.Data.DataViewManager> to manage view settings for all the tables in a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="635fb-105">Если у вас есть элемент управления, который необходимо привязать к нескольким таблицам, например сетку, которая переходит между связями, то **DataViewManager** является идеальным.</span><span class="sxs-lookup"><span data-stu-id="635fb-105">If you have a control that you want to bind to multiple tables, such as a grid that navigates relationships, a **DataViewManager** is ideal.</span></span>  
  
 <span data-ttu-id="635fb-106">**DataViewManager** содержит коллекцию <xref:System.Data.DataViewSetting> объектов, которые используются для задания параметра представления таблиц в <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="635fb-106">The **DataViewManager** contains a collection of <xref:System.Data.DataViewSetting> objects that are used to set the view setting of the tables in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="635fb-107"><xref:System.Data.DataViewSettingCollection>Содержит один <xref:System.Data.DataViewSetting> объект для каждой таблицы в **наборе данных**.</span><span class="sxs-lookup"><span data-stu-id="635fb-107">The <xref:System.Data.DataViewSettingCollection> contains one <xref:System.Data.DataViewSetting> object for each table in a **DataSet**.</span></span> <span data-ttu-id="635fb-108">Можно задать свойства **апплидефаултсорт**, **Sort**, **RowFilter** и **RowStateFilter** по умолчанию для упоминаемой таблицы, используя его **датавиевсеттинг**.</span><span class="sxs-lookup"><span data-stu-id="635fb-108">You can set the default **ApplyDefaultSort**, **Sort**, **RowFilter**, and **RowStateFilter** properties of the referenced table by using its **DataViewSetting**.</span></span> <span data-ttu-id="635fb-109">Вы можете ссылаться на **датавиевсеттинг** для конкретной таблицы по имени или по порядковому номеру или путем передачи ссылки на этот объект таблицы.</span><span class="sxs-lookup"><span data-stu-id="635fb-109">You can reference the **DataViewSetting** for a particular table by name or ordinal reference, or by passing a reference to that specific table object.</span></span> <span data-ttu-id="635fb-110">Доступ к коллекции объектов **датавиевсеттинг** в **DataViewManager** можно получить с помощью свойства **датавиевсеттингс** .</span><span class="sxs-lookup"><span data-stu-id="635fb-110">You can access the collection of **DataViewSetting** objects in a **DataViewManager** by using the **DataViewSettings** property.</span></span>  
  
 <span data-ttu-id="635fb-111">В следующем примере кода **набор данных** заполняется таблицами базы данных SQL Server **Northwind** , **клиентами**, **заказами** и **заказами**, создаются связи между таблицами, используется **DataViewManager** для задания параметров **DataView** по умолчанию и привязка **DataGrid** к **DataViewManager**.</span><span class="sxs-lookup"><span data-stu-id="635fb-111">The following code example fills a **DataSet** with the SQL Server **Northwind** database tables **Customers**, **Orders**, and **Order Details**, creates the relationships between the tables, uses a **DataViewManager** to set default **DataView** settings, and binds a **DataGrid** to the **DataViewManager**.</span></span> <span data-ttu-id="635fb-112">В примере задаются параметры **DataView** по умолчанию для всех таблиц в **наборе данных** для сортировки по первичному ключу таблицы (**апплидефаултсорт**  =  **true**), а затем изменяется порядок сортировки таблицы **Customers** для сортировки по **CompanyName**.</span><span class="sxs-lookup"><span data-stu-id="635fb-112">The example sets the default **DataView** settings for all tables in the **DataSet** to sort by the primary key of the table (**ApplyDefaultSort** = **true**), and then modifies the sort order of the **Customers** table to sort by **CompanyName**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection to Northwind.  
' Create a Connection, DataAdapters, and a DataSet.  
Dim custDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID FROM Orders", connection)  
Dim ordDetDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection)  
  
Dim custDS As DataSet = New DataSet()  
  
' Open the Connection.  
connection.Open()  
  
    ' Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
  
    custDA.Fill(custDS, "Customers")  
    orderDA.Fill(custDS, "Orders")  
    ordDetDA.Fill(custDS, "OrderDetails")  
  
    ' Close the Connection.  
    connection.Close()  
  
    ' Create relationships.  
    custDS.Relations.Add("CustomerOrders", _  
          custDS.Tables("Customers").Columns("CustomerID"), _  
          custDS.Tables("Orders").Columns("CustomerID"))  
  
    custDS.Relations.Add("OrderDetails", _  
          custDS.Tables("Orders").Columns("OrderID"), _  
          custDS.Tables("OrderDetails").Columns("OrderID"))  
  
' Create default DataView settings.  
Dim viewManager As DataViewManager = New DataViewManager(custDS)  
  
Dim viewSetting As DataViewSetting  
For Each viewSetting In viewManager.DataViewSettings  
  viewSetting.ApplyDefaultSort = True  
Next  
  
viewManager.DataViewSettings("Customers").Sort = "CompanyName"  
  
' Bind to a DataGrid.  
Dim grid As System.Windows.Forms.DataGrid = New System.Windows.Forms.DataGrid()  
grid.SetDataBinding(viewManager, "Customers")  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection to Northwind.  
// Create a Connection, DataAdapters, and a DataSet.  
SqlDataAdapter custDA = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderDA = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID FROM Orders", connection);  
SqlDataAdapter ordDetDA = new SqlDataAdapter(  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection);  
  
DataSet custDS = new DataSet();  
  
// Open the Connection.  
connection.Open();  
  
    // Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
  
    custDA.Fill(custDS, "Customers");  
    orderDA.Fill(custDS, "Orders");  
    ordDetDA.Fill(custDS, "OrderDetails");  
  
    // Close the Connection.  
    connection.Close();  
  
    // Create relationships.  
    custDS.Relations.Add("CustomerOrders",  
          custDS.Tables["Customers"].Columns["CustomerID"],  
          custDS.Tables["Orders"].Columns["CustomerID"]);  
  
    custDS.Relations.Add("OrderDetails",  
          custDS.Tables["Orders"].Columns["OrderID"],  
          custDS.Tables["OrderDetails"].Columns["OrderID"]);  
  
// Create default DataView settings.  
DataViewManager viewManager = new DataViewManager(custDS);  
  
foreach (DataViewSetting viewSetting in viewManager.DataViewSettings)  
  viewSetting.ApplyDefaultSort = true;  
  
viewManager.DataViewSettings["Customers"].Sort = "CompanyName";  
  
// Bind to a DataGrid.  
System.Windows.Forms.DataGrid grid = new System.Windows.Forms.DataGrid();  
grid.SetDataBinding(viewManager, "Customers");  
```  
  
## <a name="see-also"></a><span data-ttu-id="635fb-113">См. также</span><span class="sxs-lookup"><span data-stu-id="635fb-113">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [<span data-ttu-id="635fb-114">Объекты DataView</span><span class="sxs-lookup"><span data-stu-id="635fb-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="635fb-115">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="635fb-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
