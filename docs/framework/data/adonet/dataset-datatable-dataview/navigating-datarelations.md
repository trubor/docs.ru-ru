---
description: 'Дополнительные сведения: Навигация по связям DataRelation'
title: Навигация по отношениям DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 72d5bbb282b3b43434e528390769e1203519e8e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651812"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="afa34-103">Навигация по отношениям DataRelation</span><span class="sxs-lookup"><span data-stu-id="afa34-103">Navigating DataRelations</span></span>

<span data-ttu-id="afa34-104">Одно из основных назначений объекта <xref:System.Data.DataRelation> состоит в обеспечении переходов от одного объекта <xref:System.Data.DataTable> к другому в пределах <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="afa34-104">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="afa34-105">Это позволяет извлекать все связанные <xref:System.Data.DataRow> объекты в одной **таблице DataTable** при наличии одного объекта **DataRow** из связанного объекта **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="afa34-105">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="afa34-106">Например, после установления **отношения DataRelation** между таблицей Customers и таблицей заказов можно получить все строки заказа для конкретной строки клиента с помощью **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="afa34-106">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="afa34-107">В следующем примере кода создается **отношение DataRelation** между таблицей **Customers** и таблицей **Orders** **набора данных** и возвращаются все заказы для каждого клиента.</span><span class="sxs-lookup"><span data-stu-id="afa34-107">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="afa34-108">Следующий пример основан на предыдущем примере; в нем четыре таблицы связываются друг с другом и происходит переход по этим связям.</span><span class="sxs-lookup"><span data-stu-id="afa34-108">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="afa34-109">Как и в предыдущем примере, **CustomerID** связывает таблицу **Customers** с таблицей **Orders** .</span><span class="sxs-lookup"><span data-stu-id="afa34-109">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="afa34-110">Для каждого клиента в таблице **Customers** все дочерние строки в таблице **Orders** определяются, чтобы получить количество заказов конкретного клиента и их значения **OrderID** .</span><span class="sxs-lookup"><span data-stu-id="afa34-110">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="afa34-111">Развернутый пример также возвращает значения из таблиц **OrderDetails** и **Products** .</span><span class="sxs-lookup"><span data-stu-id="afa34-111">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="afa34-112">Таблица **Orders** связана с таблицей **OrderDetails** с помощью **OrderID** , чтобы определить, какие товары и количества были заказаны для каждого заказа клиента.</span><span class="sxs-lookup"><span data-stu-id="afa34-112">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="afa34-113">Так как таблица **OrderDetails** содержит только **ProductID** заказанного товара, **OrderDetails** связан с **продуктами** , использующими **ProductID** для возврата значения **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="afa34-113">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="afa34-114">В этом отношении таблица **Products** является родительской, а таблица **Order Details** является дочерней.</span><span class="sxs-lookup"><span data-stu-id="afa34-114">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="afa34-115">В результате при итерации по таблице **OrderDetails** вызывается **жетпарентров** для получения связанного значения **ProductName** .</span><span class="sxs-lookup"><span data-stu-id="afa34-115">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="afa34-116">Обратите внимание, что при создании **DataRelation** для таблиц **Customers** и **Orders** значение не указывается для флага **креатеконстраинтс** (значение по умолчанию — **true**).</span><span class="sxs-lookup"><span data-stu-id="afa34-116">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="afa34-117">Предполагается, что все строки в таблице **Orders** имеют значение **CustomerID** , которое существует в родительской таблице **Customers** .</span><span class="sxs-lookup"><span data-stu-id="afa34-117">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="afa34-118">Если **идентификатор клиента** существует в таблице **Orders** , которая не существует в таблице **Customers** , то <xref:System.Data.ForeignKeyConstraint> вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="afa34-118">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="afa34-119">Если дочерний столбец может содержать значения, которые не содержит родительский столбец, установите для флага **креатеконстраинтс** **значение false** при добавлении **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="afa34-119">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="afa34-120">В этом примере флаг **креатеконстраинтс** имеет значение **false** для **DataRelation** между таблицей **Orders** и **OrderDetails** .</span><span class="sxs-lookup"><span data-stu-id="afa34-120">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="afa34-121">Это позволяет приложению возвращать все записи из таблицы **OrderDetails** и только подмножество записей из таблицы **Orders** без создания исключения времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="afa34-121">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="afa34-122">В этом расширенном образце вывод формируется в следующем формате.</span><span class="sxs-lookup"><span data-stu-id="afa34-122">The expanded sample generates output in the following format.</span></span>  
  
```output  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 <span data-ttu-id="afa34-123">Следующий пример кода является расширенным примером, в котором возвращаются значения из таблиц **OrderDetails** и **Products** , при этом возвращается только подмножество записей в таблице **Orders** .</span><span class="sxs-lookup"><span data-stu-id="afa34-123">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="afa34-124">См. также</span><span class="sxs-lookup"><span data-stu-id="afa34-124">See also</span></span>

- [<span data-ttu-id="afa34-125">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="afa34-125">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="afa34-126">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="afa34-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
