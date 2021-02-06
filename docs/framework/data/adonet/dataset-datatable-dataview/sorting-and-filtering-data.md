---
description: 'Дополнительные сведения: Сортировка и фильтрация данных'
title: Сортировка и фильтрация данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: a8b74dc13e88f8d5e70bb27291e0e6e34817f0ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651617"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="b2d46-103">Сортировка и фильтрация данных</span><span class="sxs-lookup"><span data-stu-id="b2d46-103">Sorting and Filtering Data</span></span>

<span data-ttu-id="b2d46-104"><xref:System.Data.DataView> предоставляет несколько способов сортировки и фильтрации данных в <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="b2d46-104">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
- <span data-ttu-id="b2d46-105">Можно использовать свойство <xref:System.Data.DataView.Sort%2A> для задания одного или нескольких порядков сортировки столбцов и включить параметры ASC (по возрастанию) и DESC (по убыванию).</span><span class="sxs-lookup"><span data-stu-id="b2d46-105">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
- <span data-ttu-id="b2d46-106">Свойство <xref:System.Data.DataView.ApplyDefaultSort%2A> служит для автоматического создания порядка сортировки по возрастанию на основании столбца или столбцов первичного ключа таблицы.</span><span class="sxs-lookup"><span data-stu-id="b2d46-106">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="b2d46-107"><xref:System.Data.DataView.ApplyDefaultSort%2A> применяется только в том случае, если свойство **Sort** является нулевой ссылкой или пустой строкой и если в таблице определен первичный ключ.</span><span class="sxs-lookup"><span data-stu-id="b2d46-107"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
- <span data-ttu-id="b2d46-108">Свойство <xref:System.Data.DataView.RowFilter%2A> можно использовать для задания подмножеств строк на основании значений их столбцов.</span><span class="sxs-lookup"><span data-stu-id="b2d46-108">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="b2d46-109">Дополнительные сведения о допустимых выражениях для свойства **RowFilter** см. в справочных сведениях по <xref:System.Data.DataColumn.Expression%2A> свойству <xref:System.Data.DataColumn> класса.</span><span class="sxs-lookup"><span data-stu-id="b2d46-109">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="b2d46-110">Если требуется возвратить результаты определенного запроса к данным, в отличие от предоставления динамического представления подмножества данных, используйте <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> методы или объекта **DataView** для достижения лучшей производительности, а не для установки свойства **RowFilter** .</span><span class="sxs-lookup"><span data-stu-id="b2d46-110">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="b2d46-111">При установке свойства **RowFilter** перестраивается индекс данных, добавляются дополнительные затраты на приложение и снижается производительность.</span><span class="sxs-lookup"><span data-stu-id="b2d46-111">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="b2d46-112">Свойство **RowFilter** лучше использовать в приложении с привязкой к данным, в котором привязанный элемент управления отображает отфильтрованные результаты.</span><span class="sxs-lookup"><span data-stu-id="b2d46-112">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="b2d46-113">Методы **Find** и **FindRows** используют текущий индекс без необходимости перестроения индекса.</span><span class="sxs-lookup"><span data-stu-id="b2d46-113">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="b2d46-114">Дополнительные сведения о методах **Find** и **FindRows** см. в разделе [Поиск строк](finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="b2d46-114">For more information about the **Find** and **FindRows** methods, see [Finding Rows](finding-rows.md).</span></span>  
  
- <span data-ttu-id="b2d46-115">Свойство <xref:System.Data.DataView.RowStateFilter%2A> можно использовать для определения, какие версии строк следует просматривать.</span><span class="sxs-lookup"><span data-stu-id="b2d46-115">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="b2d46-116">Объект **DataView** неявно определяет, какая версия строки должна быть предоставлена в зависимости от **RowState** базовой строки.</span><span class="sxs-lookup"><span data-stu-id="b2d46-116">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="b2d46-117">Например, если для **RowStateFilter** задано значение **DataViewRowState. Deleted**, **DataView** отображает **исходную** версию строк всех **удаленных** строк, так как **Текущая** версия строки отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b2d46-117">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="b2d46-118">Вы можете определить, какая версия строки предоставляется с помощью свойства **rowversion** **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="b2d46-118">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="b2d46-119">В следующей таблице показаны параметры для **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="b2d46-119">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="b2d46-120">Параметры DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="b2d46-120">DataViewRowState options</span></span>|<span data-ttu-id="b2d46-121">Описание</span><span class="sxs-lookup"><span data-stu-id="b2d46-121">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="b2d46-122">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="b2d46-122">**CurrentRows**</span></span>|<span data-ttu-id="b2d46-123">**Текущая** версия строки всех **неизмененных**, **добавленных** и **измененных** строк.</span><span class="sxs-lookup"><span data-stu-id="b2d46-123">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="b2d46-124">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b2d46-124">This is the default.</span></span>|  
    |<span data-ttu-id="b2d46-125">**Добавлено**</span><span class="sxs-lookup"><span data-stu-id="b2d46-125">**Added**</span></span>|<span data-ttu-id="b2d46-126">Версия **текущей** строки всех **добавленных** строк.</span><span class="sxs-lookup"><span data-stu-id="b2d46-126">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="b2d46-127">**Удалено**</span><span class="sxs-lookup"><span data-stu-id="b2d46-127">**Deleted**</span></span>|<span data-ttu-id="b2d46-128">Версия **исходной** строки всех **удаленных** строк.</span><span class="sxs-lookup"><span data-stu-id="b2d46-128">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="b2d46-129">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="b2d46-129">**ModifiedCurrent**</span></span>|<span data-ttu-id="b2d46-130">Версия **текущей** строки для всех **измененных** строк.</span><span class="sxs-lookup"><span data-stu-id="b2d46-130">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="b2d46-131">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="b2d46-131">**ModifiedOriginal**</span></span>|<span data-ttu-id="b2d46-132">Версия **исходной** строки всех **измененных** строк.</span><span class="sxs-lookup"><span data-stu-id="b2d46-132">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="b2d46-133">**Нет**</span><span class="sxs-lookup"><span data-stu-id="b2d46-133">**None**</span></span>|<span data-ttu-id="b2d46-134">Нет строк.</span><span class="sxs-lookup"><span data-stu-id="b2d46-134">No rows.</span></span>|  
    |<span data-ttu-id="b2d46-135">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="b2d46-135">**OriginalRows**</span></span>|<span data-ttu-id="b2d46-136">Версия **исходной** строки всех **неизмененных**, **измененных** и **удаленных** строк.</span><span class="sxs-lookup"><span data-stu-id="b2d46-136">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="b2d46-137">**Без изменений**</span><span class="sxs-lookup"><span data-stu-id="b2d46-137">**Unchanged**</span></span>|<span data-ttu-id="b2d46-138">Версия **текущей** строки всех **неизмененных** строк.</span><span class="sxs-lookup"><span data-stu-id="b2d46-138">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="b2d46-139">Дополнительные сведения о состояниях строк и версиях строк см. в разделе [состояния строк и версии](row-states-and-row-versions.md)строк.</span><span class="sxs-lookup"><span data-stu-id="b2d46-139">For more information about row states and row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="b2d46-140">В следующем примере кода создается представление, которое показывает все продукты, где число элементов на складе меньше или равно уровню переупорядочения, отсортированного вначале по идентификаторам поставщиков, а затем по названиям продуктов.</span><span class="sxs-lookup"><span data-stu-id="b2d46-140">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2d46-141">См. также</span><span class="sxs-lookup"><span data-stu-id="b2d46-141">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="b2d46-142">Объекты DataView</span><span class="sxs-lookup"><span data-stu-id="b2d46-142">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="b2d46-143">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b2d46-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
