---
description: 'Подробнее: сводка процесса вывода схемы набора данных'
title: Общие сведения о процессе определения схемы набора данных
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 637e4325558708c15d6d4eb17de9c0cf13b3b256
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651565"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="9cd96-103">Общие сведения о процессе определения схемы набора данных</span><span class="sxs-lookup"><span data-stu-id="9cd96-103">Summary of the DataSet Schema Inference Process</span></span>

<span data-ttu-id="9cd96-104">Процесс вывода схемы из XML-документа вначале определяет, какие элементы будут выведены как таблицы.</span><span class="sxs-lookup"><span data-stu-id="9cd96-104">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="9cd96-105">Из оставшегося XML процесс вывода схемы определяет столбцы этих таблиц.</span><span class="sxs-lookup"><span data-stu-id="9cd96-105">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="9cd96-106">Для вложенных таблиц процесс вывода формирует вложенные объекты <xref:System.Data.DataRelation> и <xref:System.Data.ForeignKeyConstraint>.</span><span class="sxs-lookup"><span data-stu-id="9cd96-106">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="9cd96-107">Ниже приведен краткий обзор правил вывода.</span><span class="sxs-lookup"><span data-stu-id="9cd96-107">The following is a brief summary of inference rules:</span></span>  
  
- <span data-ttu-id="9cd96-108">Элементы с атрибутами выводятся как таблицы.</span><span class="sxs-lookup"><span data-stu-id="9cd96-108">Elements that have attributes are inferred as tables.</span></span>  
  
- <span data-ttu-id="9cd96-109">Элементы, имеющие дочерние элементы, выводятся как таблицы.</span><span class="sxs-lookup"><span data-stu-id="9cd96-109">Elements that have child elements are inferred as tables.</span></span>  
  
- <span data-ttu-id="9cd96-110">Повторяющиеся элементы выводятся как одна таблица.</span><span class="sxs-lookup"><span data-stu-id="9cd96-110">Elements that repeat are inferred as a single table.</span></span>  
  
- <span data-ttu-id="9cd96-111">Если элемент документа (корневой элемент) не имеет ни атрибутов, ни дочерних элементов, которые выводились бы как столбцы, он выводится как <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9cd96-111">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9cd96-112">В противном случае элемент документа выводится как таблица.</span><span class="sxs-lookup"><span data-stu-id="9cd96-112">Otherwise, the document element is inferred as a table.</span></span>  
  
- <span data-ttu-id="9cd96-113">Атрибуты выводятся как столбцы.</span><span class="sxs-lookup"><span data-stu-id="9cd96-113">Attributes are inferred as columns.</span></span>  
  
- <span data-ttu-id="9cd96-114">Элементы, которые не повторяются и не имеют ни атрибутов, ни дочерних элементов, выводятся как столбцы.</span><span class="sxs-lookup"><span data-stu-id="9cd96-114">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
- <span data-ttu-id="9cd96-115">Для элементов, которые выводятся в виде вложенных таблиц в других элементах, которые также выводятся в виде таблиц, между двумя таблицами создается вложенная **связь DataRelation** .</span><span class="sxs-lookup"><span data-stu-id="9cd96-115">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="9cd96-116">Новый первичный ключевой столбец с именем **TableName_Id** добавляется в обе таблицы и используется **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="9cd96-116">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="9cd96-117">Объект **ForeignKeyConstraint** создается между двумя таблицами, использующими столбец **TableName_Id** .</span><span class="sxs-lookup"><span data-stu-id="9cd96-117">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
- <span data-ttu-id="9cd96-118">Для элементов, которые выводятся в виде таблиц и содержат текст, но не имеют дочерних элементов, для текста каждого элемента создается новый столбец с именем **TableName_Text** .</span><span class="sxs-lookup"><span data-stu-id="9cd96-118">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="9cd96-119">Если элемент выводится как таблица и имеет текст, но при этом имеет дочерние элементы, текст пропускается.</span><span class="sxs-lookup"><span data-stu-id="9cd96-119">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cd96-120">См. также</span><span class="sxs-lookup"><span data-stu-id="9cd96-120">See also</span></span>

- [<span data-ttu-id="9cd96-121">Определение реляционной структуры набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="9cd96-121">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="9cd96-122">Загрузка набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="9cd96-122">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="9cd96-123">Загрузка сведений о схеме набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="9cd96-123">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="9cd96-124">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="9cd96-124">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="9cd96-125">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="9cd96-125">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="9cd96-126">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9cd96-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
