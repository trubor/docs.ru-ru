---
description: 'Дополнительные сведения: выведение столбцов'
title: Определение столбцов
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 528d4ea20260b5f1fbf30536eafcaec8c5f9215a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652254"
---
# <a name="inferring-columns"></a><span data-ttu-id="c6889-103">Определение столбцов</span><span class="sxs-lookup"><span data-stu-id="c6889-103">Inferring Columns</span></span>

<span data-ttu-id="c6889-104">ADO.NET определяет по XML-документу, какие элементы выводятся как таблицы для <xref:System.Data.DataSet>, а затем выводятся столбцы для этих таблиц.</span><span class="sxs-lookup"><span data-stu-id="c6889-104">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="c6889-105">В ADO.NET 2,0 появился новый механизм вывода схемы, который выводит строго типизированный тип данных для каждого элемента **simpleType** .</span><span class="sxs-lookup"><span data-stu-id="c6889-105">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="c6889-106">В предыдущих версиях тип данных выводимого элемента **simpleType** всегда имеет значение **xsd: String**.</span><span class="sxs-lookup"><span data-stu-id="c6889-106">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="c6889-107">Миграция и обратная совместимость</span><span class="sxs-lookup"><span data-stu-id="c6889-107">Migration and Backward Compatibility</span></span>  

 <span data-ttu-id="c6889-108">Метод **ReadXml** принимает аргумент типа **инферсчема**.</span><span class="sxs-lookup"><span data-stu-id="c6889-108">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="c6889-109">Этот аргумент позволяет задать поведение, совместимое с предыдущими версиями.</span><span class="sxs-lookup"><span data-stu-id="c6889-109">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="c6889-110">Доступные значения перечисления **инферсчема** показаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="c6889-110">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="c6889-111">Обеспечивает обратную совместимость, выводя в качестве простого типа всегда тип <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c6889-111">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="c6889-112">Выводит строго типизированный тип данных.</span><span class="sxs-lookup"><span data-stu-id="c6889-112">Infers a strongly typed data type.</span></span> <span data-ttu-id="c6889-113">Вызывает исключение при использовании с <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="c6889-113">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="c6889-114">Пропускает любую встроенную схему и считывает данные в существующую схему <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c6889-114">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="c6889-115">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c6889-115">Attributes</span></span>  

 <span data-ttu-id="c6889-116">Как определено в [выведение таблиц](inferring-tables.md), элемент с атрибутами будет выведен как таблица.</span><span class="sxs-lookup"><span data-stu-id="c6889-116">As defined in [Inferring Tables](inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="c6889-117">Атрибуты этого элемента будут выведены как столбцы для таблицы.</span><span class="sxs-lookup"><span data-stu-id="c6889-117">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="c6889-118">Свойству **ColumnMapping** столбцов будет присвоено значение **MappingType. Attribute**, чтобы гарантировать, что имена столбцов будут записаны как атрибуты, если схема записывается обратно в XML.</span><span class="sxs-lookup"><span data-stu-id="c6889-118">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="c6889-119">Значения атрибутов хранятся в строке в таблице.</span><span class="sxs-lookup"><span data-stu-id="c6889-119">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="c6889-120">Например, рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="c6889-120">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="c6889-121">В процессе вывода создается таблица с именем **Element1** с двумя столбцами, **attr1** и **attr2**.</span><span class="sxs-lookup"><span data-stu-id="c6889-121">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="c6889-122">Свойство **ColumnMapping** обоих столбцов будет иметь значение **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="c6889-122">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="c6889-123">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="c6889-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="c6889-124">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="c6889-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="c6889-125">attr1</span><span class="sxs-lookup"><span data-stu-id="c6889-125">attr1</span></span>|<span data-ttu-id="c6889-126">attr2</span><span class="sxs-lookup"><span data-stu-id="c6889-126">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="c6889-127">value1</span><span class="sxs-lookup"><span data-stu-id="c6889-127">value1</span></span>|<span data-ttu-id="c6889-128">value2</span><span class="sxs-lookup"><span data-stu-id="c6889-128">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="c6889-129">Элементы без атрибутов или дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c6889-129">Elements Without Attributes or Child Elements</span></span>  

 <span data-ttu-id="c6889-130">Если элемент не имеет дочерних элементов или атрибутов, то он будет выведен как столбец.</span><span class="sxs-lookup"><span data-stu-id="c6889-130">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="c6889-131">Свойству **ColumnMapping** столбца будет присвоено значение **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="c6889-131">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="c6889-132">Текст для дочерних элементов хранится в строке в таблице.</span><span class="sxs-lookup"><span data-stu-id="c6889-132">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="c6889-133">Например, рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="c6889-133">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="c6889-134">В процессе вывода создается таблица с именем **Element1** с двумя столбцами, **ChildElement1** и **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="c6889-134">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="c6889-135">Свойство **ColumnMapping** обоих столбцов будет иметь значение **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="c6889-135">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="c6889-136">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="c6889-136">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="c6889-137">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="c6889-137">**Table:** Element1</span></span>  
  
|<span data-ttu-id="c6889-138">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="c6889-138">ChildElement1</span></span>|<span data-ttu-id="c6889-139">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="c6889-139">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="c6889-140">Text1</span><span class="sxs-lookup"><span data-stu-id="c6889-140">Text1</span></span>|<span data-ttu-id="c6889-141">Text2</span><span class="sxs-lookup"><span data-stu-id="c6889-141">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6889-142">См. также</span><span class="sxs-lookup"><span data-stu-id="c6889-142">See also</span></span>

- [<span data-ttu-id="c6889-143">Определение реляционной структуры набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="c6889-143">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="c6889-144">Загрузка набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="c6889-144">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="c6889-145">Загрузка сведений о схеме набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="c6889-145">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="c6889-146">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="c6889-146">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="c6889-147">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="c6889-147">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="c6889-148">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c6889-148">ADO.NET Overview</span></span>](../ado-net-overview.md)
