---
description: 'Дополнительные сведения: ограничения на вывод'
title: Ограничения определения
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 926e456acfc5eac2598be40490b72523facfd058
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652267"
---
# <a name="inference-limitations"></a><span data-ttu-id="af98c-103">Ограничения определения</span><span class="sxs-lookup"><span data-stu-id="af98c-103">Inference Limitations</span></span>

<span data-ttu-id="af98c-104">Процесс вывода схемы <xref:System.Data.DataSet> из XML-кода может приводиться в различных схемах в зависимости от XML-элементов в каждом документе.</span><span class="sxs-lookup"><span data-stu-id="af98c-104">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="af98c-105">Например, рассмотрим следующие XML-документы.</span><span class="sxs-lookup"><span data-stu-id="af98c-105">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="af98c-106">Document1:</span><span class="sxs-lookup"><span data-stu-id="af98c-106">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="af98c-107">Document2:</span><span class="sxs-lookup"><span data-stu-id="af98c-107">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="af98c-108">Для "document1" процесс вывода создает **набор данных** с именем "documentElement" и таблицу с именем "Element1", так как "Element1" является повторяющимся элементом.</span><span class="sxs-lookup"><span data-stu-id="af98c-108">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="af98c-109">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="af98c-109">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="af98c-110">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="af98c-110">**Table:** Element1</span></span>  
  
|<span data-ttu-id="af98c-111">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="af98c-111">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="af98c-112">Text1</span><span class="sxs-lookup"><span data-stu-id="af98c-112">Text1</span></span>|  
|<span data-ttu-id="af98c-113">Text2</span><span class="sxs-lookup"><span data-stu-id="af98c-113">Text2</span></span>|  
  
 <span data-ttu-id="af98c-114">Однако для "Document2" процесс вывода создает **набор данных** с именем "невдатасет" и таблицу с именем "documentElement".</span><span class="sxs-lookup"><span data-stu-id="af98c-114">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="af98c-115">Element1 выводится в виде столбца, потому что не имеет атрибутов и дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="af98c-115">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="af98c-116">**Набор данных:** невдатасет</span><span class="sxs-lookup"><span data-stu-id="af98c-116">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="af98c-117">**Таблица:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="af98c-117">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="af98c-118">Element1</span><span class="sxs-lookup"><span data-stu-id="af98c-118">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="af98c-119">Text1</span><span class="sxs-lookup"><span data-stu-id="af98c-119">Text1</span></span>|  
  
 <span data-ttu-id="af98c-120">Эти два XML-документа, возможно, должны были выдавать одну и ту же схему, но процесс вывода дает значительно различающиеся результаты в зависимости от элементов, содержащихся в каждом документе.</span><span class="sxs-lookup"><span data-stu-id="af98c-120">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="af98c-121">Чтобы избежать расхождений, которые могут возникнуть при формировании схемы из XML-документа, рекомендуется явно указать схему с помощью языка определения схемы XML (XSD) или XML-Data Reduced (XDR) при загрузке **набора данных** из XML.</span><span class="sxs-lookup"><span data-stu-id="af98c-121">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="af98c-122">Дополнительные сведения о явном указании схемы **набора данных** с XML-схемой см. [в разделе Наследование реляционной структуры набора данных из схемы XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="af98c-122">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af98c-123">См. также</span><span class="sxs-lookup"><span data-stu-id="af98c-123">See also</span></span>

- [<span data-ttu-id="af98c-124">Определение реляционной структуры набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="af98c-124">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="af98c-125">Загрузка набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="af98c-125">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="af98c-126">Загрузка сведений о схеме набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="af98c-126">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="af98c-127">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="af98c-127">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="af98c-128">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="af98c-128">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="af98c-129">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="af98c-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
