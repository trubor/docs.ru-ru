---
description: 'Дополнительные сведения: Добавление существующих ограничений в набор данных'
title: Добавление существующих ограничений к набору данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: cad0dd1bd16747a5e76e10784d00c14cd9aa8c2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729576"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="292e0-103">Добавление существующих ограничений к набору данных</span><span class="sxs-lookup"><span data-stu-id="292e0-103">Adding Existing Constraints to a DataSet</span></span>

<span data-ttu-id="292e0-104">Метод **Fill** объекта **DataAdapter** заполняет <xref:System.Data.DataSet> только столбцами таблицы и строками из источника данных. Хотя ограничения обычно задаются источником данных, метод **Fill** по умолчанию не добавляет эти сведения о схеме в **набор данных** .</span><span class="sxs-lookup"><span data-stu-id="292e0-104">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="292e0-105">Чтобы заполнить **набор** данных существующими сведениями об ограничениях первичного ключа из источника данных, можно либо вызвать метод **FillSchema** объекта **DataAdapter**, либо установить свойство **миссингсчемаактион** объекта **DataAdapter** в **аддвискэй** перед вызовом **Fill**.</span><span class="sxs-lookup"><span data-stu-id="292e0-105">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="292e0-106">Тем самым ограничения первичного ключа в наборе данных **DataSet** будут соответствовать ограничениям первичного ключа в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="292e0-106">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="292e0-107">Сведения об ограничениях внешнего ключа не включаются и должны создаваться явным образом, как показано в разделе [ограничения DataTable](./dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="292e0-107">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](./dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
<span data-ttu-id="292e0-108">Добавление данных схемы в **DataSet** перед его заполнением обеспечивает включение ограничений первичного ключа в объекты <xref:System.Data.DataTable> набора данных **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="292e0-108">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="292e0-109">В результате при дополнительных вызовах для заполнения **DataSet** данные столбца первичного ключа используются для проверки соответствия новых строк из источника данных текущим строкам в каждой таблице **DataTable** и текущие данные таблиц перезаписываются данными из источника.</span><span class="sxs-lookup"><span data-stu-id="292e0-109">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="292e0-110">При отсутствии данных схемы новые строки добавляются из источника данных к набору данных **DataSet**, что приводит к появлению повторяющихся строк.</span><span class="sxs-lookup"><span data-stu-id="292e0-110">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="292e0-111">Если столбец в источнике данных определен как автоматически увеличивающийся, метод **FillSchema** или метод **Fill** с **миссингсчемаактион** **аддвискэй**, создает **столбец** данных с свойством **AutoIncrement** , имеющим значение `true` .</span><span class="sxs-lookup"><span data-stu-id="292e0-111">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="292e0-112">Но выполнение задачи присваивания значений свойств **AutoIncrementStep** и **AutoIncrementSeed** необходимо взять на себя.</span><span class="sxs-lookup"><span data-stu-id="292e0-112">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="292e0-113">Дополнительные сведения о столбцах с автоматическим приращением см. в разделе [Создание столбцов с автоувеличением](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="292e0-113">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
<span data-ttu-id="292e0-114">Использование метода **FillSchema** или присвоение свойству **MissingSchemaAction** значения **AddWithKey** требует дополнительной обработки в источнике данных, чтобы определить сведения о столбцах первичного ключа.</span><span class="sxs-lookup"><span data-stu-id="292e0-114">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="292e0-115">Такая дополнительная обработка может снизить производительность.</span><span class="sxs-lookup"><span data-stu-id="292e0-115">This additional processing can hinder performance.</span></span> <span data-ttu-id="292e0-116">Если сведения о столбцах первичного ключа известны во время разработки, рекомендуется явно задавать столбец или столбцы первичного ключа, чтобы добиться оптимальной производительности.</span><span class="sxs-lookup"><span data-stu-id="292e0-116">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="292e0-117">Сведения о явном задании сведений о первичном ключе для таблицы см. в разделе [Определение первичных ключей](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="292e0-117">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>
  
<span data-ttu-id="292e0-118">В следующем примере кода показано, как добавить сведения о схеме в **набор данных** с помощью **FillSchema**:</span><span class="sxs-lookup"><span data-stu-id="292e0-118">The following code example shows how to add schema information to a **DataSet** using **FillSchema**:</span></span>
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
<span data-ttu-id="292e0-119">В следующем примере кода показано, как добавить сведения о схеме в **набор данных** с помощью свойства **миссингсчемаактион. аддвискэй** метода **Fill** :</span><span class="sxs-lookup"><span data-stu-id="292e0-119">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method:</span></span>
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="292e0-120">Обработка нескольких результирующих наборов</span><span class="sxs-lookup"><span data-stu-id="292e0-120">Handling multiple result sets</span></span>  

<span data-ttu-id="292e0-121">Если объект **DataAdapter** обнаруживает несколько результирующих наборов, возвращенных из **SelectCommand**, он создает несколько таблиц в **наборе данных**.</span><span class="sxs-lookup"><span data-stu-id="292e0-121">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="292e0-122">Эти таблицы по умолчанию получают имя **Table** *N* с последовательно увеличивающимся суффиксом, но начиная с **Table**, а не с "Table0".</span><span class="sxs-lookup"><span data-stu-id="292e0-122">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="292e0-123">Если имя таблицы передается в качестве аргумента в метод **FillSchema** , то таблицам будет присвоено отсчитываемое от нуля имя **TableName** *N*, начинающееся с **TableName** вместо "TableName0".</span><span class="sxs-lookup"><span data-stu-id="292e0-123">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="292e0-124">Если метод **FillSchema** объекта **OleDbDataAdapter** вызывается для команды, возвращающей несколько результирующих наборов, возвращается только информация о схеме из первого результирующего набора.</span><span class="sxs-lookup"><span data-stu-id="292e0-124">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="292e0-125">При возврате сведений о схеме для нескольких результирующих наборов с помощью **OleDbDataAdapter** рекомендуется указать **миссингсчемаактион** **аддвискэй** и получить сведения о схеме при вызове метода **Fill** .</span><span class="sxs-lookup"><span data-stu-id="292e0-125">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292e0-126">См. также</span><span class="sxs-lookup"><span data-stu-id="292e0-126">See also</span></span>

- [<span data-ttu-id="292e0-127">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="292e0-127">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="292e0-128">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="292e0-128">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="292e0-129">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="292e0-129">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="292e0-130">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="292e0-130">ADO.NET Overview</span></span>](ado-net-overview.md)
