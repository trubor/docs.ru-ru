---
description: Дополнительные сведения о Выведение таблиц
title: Определение таблиц
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 00a24cbfc44aea4279b0a115214ec26d3eac59ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652163"
---
# <a name="inferring-tables"></a><span data-ttu-id="1bb26-103">Определение таблиц</span><span class="sxs-lookup"><span data-stu-id="1bb26-103">Inferring Tables</span></span>

<span data-ttu-id="1bb26-104">При выведении схемы для <xref:System.Data.DataSet> из XML-документа ADO.NET сначала определяет, какой из XML-элементов представляет таблицы.</span><span class="sxs-lookup"><span data-stu-id="1bb26-104">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="1bb26-105">Следующие XML-структуры приводят к созданию таблицы для схемы **набора данных** :</span><span class="sxs-lookup"><span data-stu-id="1bb26-105">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="1bb26-106">Элементы с атрибутами.</span><span class="sxs-lookup"><span data-stu-id="1bb26-106">Elements with attributes</span></span>  
  
- <span data-ttu-id="1bb26-107">Элементы с дочерними элементами.</span><span class="sxs-lookup"><span data-stu-id="1bb26-107">Elements with child elements</span></span>  
  
- <span data-ttu-id="1bb26-108">Повторяющиеся элементы.</span><span class="sxs-lookup"><span data-stu-id="1bb26-108">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="1bb26-109">Элементы с атрибутами</span><span class="sxs-lookup"><span data-stu-id="1bb26-109">Elements with Attributes</span></span>  

 <span data-ttu-id="1bb26-110">Элементы с заданными атрибутами приводятся в выведенных таблицах.</span><span class="sxs-lookup"><span data-stu-id="1bb26-110">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="1bb26-111">Например, рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="1bb26-111">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1bb26-112">В процессе вывода создается таблица с именем Element1.</span><span class="sxs-lookup"><span data-stu-id="1bb26-112">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="1bb26-113">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1bb26-113">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1bb26-114">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="1bb26-114">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1bb26-115">attr1</span><span class="sxs-lookup"><span data-stu-id="1bb26-115">attr1</span></span>|<span data-ttu-id="1bb26-116">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="1bb26-116">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="1bb26-117">value1</span><span class="sxs-lookup"><span data-stu-id="1bb26-117">value1</span></span>||  
|<span data-ttu-id="1bb26-118">value2</span><span class="sxs-lookup"><span data-stu-id="1bb26-118">value2</span></span>|<span data-ttu-id="1bb26-119">Text1</span><span class="sxs-lookup"><span data-stu-id="1bb26-119">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="1bb26-120">Элементы с дочерними элементами</span><span class="sxs-lookup"><span data-stu-id="1bb26-120">Elements with Child Elements</span></span>  

 <span data-ttu-id="1bb26-121">Элементы, имеющие дочерние элементы, приводятся в выведенных таблицах.</span><span class="sxs-lookup"><span data-stu-id="1bb26-121">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="1bb26-122">Например, рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="1bb26-122">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1bb26-123">В процессе вывода создается таблица с именем Element1.</span><span class="sxs-lookup"><span data-stu-id="1bb26-123">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="1bb26-124">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1bb26-124">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1bb26-125">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="1bb26-125">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1bb26-126">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="1bb26-126">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="1bb26-127">Text1</span><span class="sxs-lookup"><span data-stu-id="1bb26-127">Text1</span></span>|  
  
 <span data-ttu-id="1bb26-128">Элемент документа или корневой элемент приводится в выведенной таблице, если он имеет атрибуты или дочерние элементы, которые выводятся в виде столбцов.</span><span class="sxs-lookup"><span data-stu-id="1bb26-128">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="1bb26-129">Если элемент документа не имеет атрибутов и не содержит дочерних элементов, которые будут выводиться как столбцы, то элемент выводится как **набор данных**.</span><span class="sxs-lookup"><span data-stu-id="1bb26-129">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="1bb26-130">Например, рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="1bb26-130">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1bb26-131">В процессе вывода создается таблица с именем DocumentElement.</span><span class="sxs-lookup"><span data-stu-id="1bb26-131">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="1bb26-132">**Набор данных:** невдатасет</span><span class="sxs-lookup"><span data-stu-id="1bb26-132">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="1bb26-133">**Таблица:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1bb26-133">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="1bb26-134">Element1</span><span class="sxs-lookup"><span data-stu-id="1bb26-134">Element1</span></span>|<span data-ttu-id="1bb26-135">Element2</span><span class="sxs-lookup"><span data-stu-id="1bb26-135">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="1bb26-136">Text1</span><span class="sxs-lookup"><span data-stu-id="1bb26-136">Text1</span></span>|<span data-ttu-id="1bb26-137">Text2</span><span class="sxs-lookup"><span data-stu-id="1bb26-137">Text2</span></span>|  
  
 <span data-ttu-id="1bb26-138">В качестве альтернативы рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="1bb26-138">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1bb26-139">Процесс вывода создает **набор данных** с именем «documentElement», содержащий таблицу с именем «Element1».</span><span class="sxs-lookup"><span data-stu-id="1bb26-139">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="1bb26-140">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1bb26-140">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1bb26-141">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="1bb26-141">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1bb26-142">attr1</span><span class="sxs-lookup"><span data-stu-id="1bb26-142">attr1</span></span>|<span data-ttu-id="1bb26-143">attr2</span><span class="sxs-lookup"><span data-stu-id="1bb26-143">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="1bb26-144">value1</span><span class="sxs-lookup"><span data-stu-id="1bb26-144">value1</span></span>|<span data-ttu-id="1bb26-145">value2</span><span class="sxs-lookup"><span data-stu-id="1bb26-145">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="1bb26-146">Повторяющиеся элементы</span><span class="sxs-lookup"><span data-stu-id="1bb26-146">Repeating Elements</span></span>  

 <span data-ttu-id="1bb26-147">Повторяющиеся элементы приводятся в выведенной таблице.</span><span class="sxs-lookup"><span data-stu-id="1bb26-147">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="1bb26-148">Например, рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="1bb26-148">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1bb26-149">В процессе вывода создается таблица с именем Element1.</span><span class="sxs-lookup"><span data-stu-id="1bb26-149">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="1bb26-150">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1bb26-150">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1bb26-151">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="1bb26-151">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1bb26-152">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="1bb26-152">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="1bb26-153">Text1</span><span class="sxs-lookup"><span data-stu-id="1bb26-153">Text1</span></span>|  
|<span data-ttu-id="1bb26-154">Text2</span><span class="sxs-lookup"><span data-stu-id="1bb26-154">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bb26-155">См. также</span><span class="sxs-lookup"><span data-stu-id="1bb26-155">See also</span></span>

- [<span data-ttu-id="1bb26-156">Определение реляционной структуры набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="1bb26-156">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="1bb26-157">Загрузка набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="1bb26-157">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="1bb26-158">Загрузка сведений о схеме набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="1bb26-158">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="1bb26-159">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="1bb26-159">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="1bb26-160">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="1bb26-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1bb26-161">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1bb26-161">ADO.NET Overview</span></span>](../ado-net-overview.md)
