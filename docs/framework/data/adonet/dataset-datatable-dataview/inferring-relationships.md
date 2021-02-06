---
description: Дополнительные сведения о выведение связей
title: Определение отношений
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: a117581d512c1427c638ea862169ab3c7623d783
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652150"
---
# <a name="inferring-relationships"></a><span data-ttu-id="41d74-103">Определение отношений</span><span class="sxs-lookup"><span data-stu-id="41d74-103">Inferring Relationships</span></span>

<span data-ttu-id="41d74-104">Если элемент, выводимый в виде таблицы, имеет дочерний элемент, который также выводится в виде таблицы, между двумя этими таблицами будет создана связь <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="41d74-104">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="41d74-105">Новый столбец с именем **ParentTableName_Id** будет добавлен как в таблицу, созданную для родительского элемента, так и на таблицу, созданную для дочернего элемента.</span><span class="sxs-lookup"><span data-stu-id="41d74-105">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="41d74-106">Свойству **ColumnMapping** этого столбца идентификаторов будет присвоено значение **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="41d74-106">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="41d74-107">Столбец будет автоматически инкрементным первичным ключом для родительской таблицы и будет использоваться для **связи DataRelation** между двумя таблицами.</span><span class="sxs-lookup"><span data-stu-id="41d74-107">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="41d74-108">Тип данных добавленного столбца идентификаторов будет **System. Int32**, в отличие от типа данных всех других выводимых столбцов, которые имеют тип **System. String**.</span><span class="sxs-lookup"><span data-stu-id="41d74-108">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="41d74-109">Объект <xref:System.Data.ForeignKeyConstraint> с **DeleteRule**  =  **CASCADE** также будет создан с помощью нового столбца как в родительской, так и в дочерней таблице.</span><span class="sxs-lookup"><span data-stu-id="41d74-109">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="41d74-110">Например, рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="41d74-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="41d74-111">Процесс вывода приведет к созданию двух таблиц: **Element1** и **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="41d74-111">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="41d74-112">Таблица **Element1** будет содержать два столбца: **Element1_Id** и **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="41d74-112">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="41d74-113">Свойству **ColumnMapping** столбца **Element1_Id** будет присвоено значение **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="41d74-113">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="41d74-114">Свойству **ColumnMapping** столбца **ChildElement2** будет присвоено значение **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="41d74-114">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="41d74-115">Столбец **Element1_Id** будет установлен в качестве первичного ключа таблицы **Element1** .</span><span class="sxs-lookup"><span data-stu-id="41d74-115">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="41d74-116">Таблица **ChildElement1** будет содержать три столбца: **attr1**, **attr2** и **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="41d74-116">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="41d74-117">Свойству **ColumnMapping** для столбцов **attr1** и **attr2** будет присвоено значение **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="41d74-117">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="41d74-118">Свойству **ColumnMapping** столбца **Element1_Id** будет присвоено значение **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="41d74-118">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="41d74-119">**DataRelation** и **ForeignKeyConstraint** будут созданы с использованием **Element1_Id** столбцов из обеих таблиц.</span><span class="sxs-lookup"><span data-stu-id="41d74-119">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="41d74-120">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="41d74-120">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="41d74-121">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="41d74-121">**Table:** Element1</span></span>  
  
|<span data-ttu-id="41d74-122">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="41d74-122">Element1_Id</span></span>|<span data-ttu-id="41d74-123">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="41d74-123">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="41d74-124">0</span><span class="sxs-lookup"><span data-stu-id="41d74-124">0</span></span>|<span data-ttu-id="41d74-125">Text2</span><span class="sxs-lookup"><span data-stu-id="41d74-125">Text2</span></span>|  
  
 <span data-ttu-id="41d74-126">**Таблица:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="41d74-126">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="41d74-127">attr1</span><span class="sxs-lookup"><span data-stu-id="41d74-127">attr1</span></span>|<span data-ttu-id="41d74-128">attr2</span><span class="sxs-lookup"><span data-stu-id="41d74-128">attr2</span></span>|<span data-ttu-id="41d74-129">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="41d74-129">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="41d74-130">value1</span><span class="sxs-lookup"><span data-stu-id="41d74-130">value1</span></span>|<span data-ttu-id="41d74-131">value2</span><span class="sxs-lookup"><span data-stu-id="41d74-131">value2</span></span>|<span data-ttu-id="41d74-132">0</span><span class="sxs-lookup"><span data-stu-id="41d74-132">0</span></span>|  
  
 <span data-ttu-id="41d74-133">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="41d74-133">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="41d74-134">**Паренттабле:** Element1</span><span class="sxs-lookup"><span data-stu-id="41d74-134">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="41d74-135">**Парентколумн:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="41d74-135">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="41d74-136">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="41d74-136">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="41d74-137">**Чилдколумн:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="41d74-137">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="41d74-138">**Вложенные:** Условия</span><span class="sxs-lookup"><span data-stu-id="41d74-138">**Nested:** True</span></span>  
  
 <span data-ttu-id="41d74-139">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="41d74-139">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="41d74-140">**Столбец:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="41d74-140">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="41d74-141">**Паренттабле:** Element1</span><span class="sxs-lookup"><span data-stu-id="41d74-141">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="41d74-142">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="41d74-142">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="41d74-143">**DeleteRule:** Аргумент</span><span class="sxs-lookup"><span data-stu-id="41d74-143">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="41d74-144">**Акцептрежектруле:** None</span><span class="sxs-lookup"><span data-stu-id="41d74-144">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d74-145">См. также</span><span class="sxs-lookup"><span data-stu-id="41d74-145">See also</span></span>

- [<span data-ttu-id="41d74-146">Определение реляционной структуры набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="41d74-146">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="41d74-147">Загрузка набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="41d74-147">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="41d74-148">Загрузка сведений о схеме набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="41d74-148">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="41d74-149">Вложение отношений DataRelation</span><span class="sxs-lookup"><span data-stu-id="41d74-149">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="41d74-150">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="41d74-150">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="41d74-151">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="41d74-151">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="41d74-152">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="41d74-152">ADO.NET Overview</span></span>](../ado-net-overview.md)
