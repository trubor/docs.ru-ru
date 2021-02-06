---
description: 'Дополнительные сведения: вывод текста элемента'
title: Определение текста элемента
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 5d0d9b1b3bb6164cd3cf26b429a4c7d658ee4128
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652215"
---
# <a name="inferring-element-text"></a><span data-ttu-id="42f38-103">Определение текста элемента</span><span class="sxs-lookup"><span data-stu-id="42f38-103">Inferring Element Text</span></span>

<span data-ttu-id="42f38-104">Если элемент содержит текст и не имеет дочерних элементов, которые должны выводиться как таблицы (например, элементы с атрибутами или повторяющиеся элементы), в таблицу, выводимую для элемента, будет добавлен новый столбец с именем **TableName_Text** .</span><span class="sxs-lookup"><span data-stu-id="42f38-104">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="42f38-105">Текст, содержащийся в элементе, будет добавлен в строку таблицы и сохранен в новом столбце.</span><span class="sxs-lookup"><span data-stu-id="42f38-105">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="42f38-106">Свойству **ColumnMapping** нового столбца будет присвоено значение **MappingType. SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="42f38-106">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="42f38-107">Например, рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="42f38-107">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="42f38-108">В процессе вывода создается таблица с именем **Element1** с двумя столбцами: **attr1** и **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="42f38-108">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="42f38-109">Свойству **ColumnMapping** столбца **attr1** будет присвоено значение **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="42f38-109">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="42f38-110">Свойству **ColumnMapping** столбца **Element1_Text** будет присвоено значение **MappingType. SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="42f38-110">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="42f38-111">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="42f38-111">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="42f38-112">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="42f38-112">**Table:** Element1</span></span>  
  
|<span data-ttu-id="42f38-113">attr1</span><span class="sxs-lookup"><span data-stu-id="42f38-113">attr1</span></span>|<span data-ttu-id="42f38-114">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="42f38-114">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="42f38-115">value1</span><span class="sxs-lookup"><span data-stu-id="42f38-115">value1</span></span>|<span data-ttu-id="42f38-116">Text1</span><span class="sxs-lookup"><span data-stu-id="42f38-116">Text1</span></span>|  
  
 <span data-ttu-id="42f38-117">Если элемент содержит текст, а также имеет дочерние элементы, содержащие текст, столбец не будет добавлен в таблицу для хранения текста, содержащегося в элементе.</span><span class="sxs-lookup"><span data-stu-id="42f38-117">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="42f38-118">Текст, содержащийся в элементе, пропускается, а текст в дочерних элементах включается в строку таблицы.</span><span class="sxs-lookup"><span data-stu-id="42f38-118">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="42f38-119">Например, рассмотрим следующий XML-код:</span><span class="sxs-lookup"><span data-stu-id="42f38-119">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="42f38-120">В процессе вывода создается таблица с именем **Element1** с одним столбцом с именем **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="42f38-120">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="42f38-121">Текст элемента **ChildElement1** будет включаться в строку таблицы.</span><span class="sxs-lookup"><span data-stu-id="42f38-121">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="42f38-122">Весь прочий текст будет пропущен.</span><span class="sxs-lookup"><span data-stu-id="42f38-122">The other text will be ignored.</span></span> <span data-ttu-id="42f38-123">Свойству **ColumnMapping** столбца **ChildElement1** будет присвоено значение **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="42f38-123">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="42f38-124">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="42f38-124">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="42f38-125">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="42f38-125">**Table:** Element1</span></span>  
  
|<span data-ttu-id="42f38-126">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="42f38-126">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="42f38-127">Text2</span><span class="sxs-lookup"><span data-stu-id="42f38-127">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42f38-128">См. также</span><span class="sxs-lookup"><span data-stu-id="42f38-128">See also</span></span>

- [<span data-ttu-id="42f38-129">Определение реляционной структуры набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="42f38-129">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="42f38-130">Загрузка набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="42f38-130">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="42f38-131">Загрузка сведений о схеме набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="42f38-131">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="42f38-132">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="42f38-132">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="42f38-133">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="42f38-133">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="42f38-134">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="42f38-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
