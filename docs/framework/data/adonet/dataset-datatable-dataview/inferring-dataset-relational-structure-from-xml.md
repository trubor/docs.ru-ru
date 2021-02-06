---
description: 'Дополнительные сведения: вывод реляционной структуры набора данных из XML'
title: Определение реляционной структуры набора данных из XML
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: d89b6a42e7e1bc3d7514f180329e9c1d877a67ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652228"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a><span data-ttu-id="86549-103">Определение реляционной структуры набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="86549-103">Inferring DataSet Relational Structure from XML</span></span>

<span data-ttu-id="86549-104">Реляционная структура (или схема) набора данных <xref:System.Data.DataSet> состоит из таблиц, столбцов, ограничений и связей.</span><span class="sxs-lookup"><span data-stu-id="86549-104">The relational structure, or schema, of a <xref:System.Data.DataSet> is made up of tables, columns, constraints, and relations.</span></span> <span data-ttu-id="86549-105">При загрузке <xref:System.Data.DataSet> из кода XML схема может быть определена заранее или создана, либо явно, либо с помощью вывода, на основании загружаемого кода XML.</span><span class="sxs-lookup"><span data-stu-id="86549-105">When loading a <xref:System.Data.DataSet> from XML, the schema can be predefined, or it can be created, either explicitly or through inference, from the XML being loaded.</span></span> <span data-ttu-id="86549-106">Дополнительные сведения о загрузке схемы и содержимого <xref:System.Data.DataSet> из XML-кода см. в разделе [Загрузка набора данных из XML](loading-a-dataset-from-xml.md) и [Загрузка данных схемы набора данных из XML](loading-dataset-schema-information-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="86549-106">For more information about loading the schema and contents of a <xref:System.Data.DataSet> from XML, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md) and [Loading DataSet Schema Information from XML](loading-dataset-schema-information-from-xml.md).</span></span>  
  
 <span data-ttu-id="86549-107">Если схема <xref:System.Data.DataSet> создается из XML, предпочтительным методом является явное указание схемы с помощью языка определения схемы XML (XSD) (как описано в разделе [наследование реляционной структуры набора данных из схемы XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)) или XML-Data Reduced (XDR).</span><span class="sxs-lookup"><span data-stu-id="86549-107">If the schema of a <xref:System.Data.DataSet> is being created from XML, the preferred method is to explicitly specify the schema using either the XML Schema definition language (XSD) (as described in [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)) or the XML-Data Reduced (XDR).</span></span> <span data-ttu-id="86549-108">Если в коде XML отсутствуют схемы XSD или XDR , то схема <xref:System.Data.DataSet> может быть выведена на основании структуры элементов и атрибутов XML.</span><span class="sxs-lookup"><span data-stu-id="86549-108">If no XML Schema or XDR schema is available in the XML, the schema of the <xref:System.Data.DataSet> can be inferred from the structure of the XML elements and attributes.</span></span>  
  
 <span data-ttu-id="86549-109">В настоящем разделе описаны правила вывода схемы <xref:System.Data.DataSet>; для этого показаны элементы, атрибуты XML и их структура, а затем схема <xref:System.Data.DataSet>, полученная путем вывода.</span><span class="sxs-lookup"><span data-stu-id="86549-109">This section describes the rules for <xref:System.Data.DataSet> schema inference by showing XML elements and attributes and their structure, and the resulting inferred <xref:System.Data.DataSet> schema.</span></span>  
  
 <span data-ttu-id="86549-110">Не все атрибуты, присутствующие в XML-документе, должны быть включены в процесс вывода.</span><span class="sxs-lookup"><span data-stu-id="86549-110">Not all attributes present in an XML document should be included in the inference process.</span></span> <span data-ttu-id="86549-111">Атрибуты с уточнением в виде пространств имен могут включать метаданные, которые являются значимыми для XML-документа, но не для схемы <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="86549-111">Namespace-qualified attributes can include metadata that is important for the XML document but not for the <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="86549-112">Используя <xref:System.Data.DataSet.InferXmlSchema%2A>, можно указывать пространства имен, которые не должны учитываться в процессе вывода.</span><span class="sxs-lookup"><span data-stu-id="86549-112">Using <xref:System.Data.DataSet.InferXmlSchema%2A>, you can specify namespaces to be ignored during the inference process.</span></span> <span data-ttu-id="86549-113">Дополнительные сведения см. [в разделе Загрузка данных схемы набора данных из XML](loading-dataset-schema-information-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="86549-113">For more information, see [Loading DataSet Schema Information from XML](loading-dataset-schema-information-from-xml.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86549-114">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="86549-114">In This Section</span></span>  

 [<span data-ttu-id="86549-115">Общие сведения о процессе определения схемы набора данных</span><span class="sxs-lookup"><span data-stu-id="86549-115">Summary of the DataSet Schema Inference Process</span></span>](summary-of-the-dataset-schema-inference-process.md)  
 <span data-ttu-id="86549-116">Предоставляет высокоуровневую сводку правил для вывода схемы <xref:System.Data.DataSet> с использованием кода XML.</span><span class="sxs-lookup"><span data-stu-id="86549-116">Provides a high-level summary of the rules for inferring the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="86549-117">Определение таблиц</span><span class="sxs-lookup"><span data-stu-id="86549-117">Inferring Tables</span></span>](inferring-tables.md)  
 <span data-ttu-id="86549-118">Описывает элементы XML, которые в результате вывода становятся основанием для создания таблиц в <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="86549-118">Describes the XML elements that are inferred as tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="86549-119">Определение столбцов</span><span class="sxs-lookup"><span data-stu-id="86549-119">Inferring Columns</span></span>](inferring-columns.md)  
 <span data-ttu-id="86549-120">Описывает элементы и атрибуты XML, которые в результате вывода становятся основанием для создания столбцов таблиц.</span><span class="sxs-lookup"><span data-stu-id="86549-120">Describes the XML elements and attributes that are inferred as table columns.</span></span>  
  
 [<span data-ttu-id="86549-121">Определение отношений</span><span class="sxs-lookup"><span data-stu-id="86549-121">Inferring Relationships</span></span>](inferring-relationships.md)  
 <span data-ttu-id="86549-122">Описывает объекты <xref:System.Data.DataRelation> и <xref:System.Data.ForeignKeyConstraint>, создаваемые для вложенных таблиц, полученных на основании вывода.</span><span class="sxs-lookup"><span data-stu-id="86549-122">Describes the <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects created for nested, inferred tables.</span></span>  
  
 [<span data-ttu-id="86549-123">Определение текста элемента</span><span class="sxs-lookup"><span data-stu-id="86549-123">Inferring Element Text</span></span>](inferring-element-text.md)  
 <span data-ttu-id="86549-124">Описывает столбцы, которые создаются для текста в элементах XML, и поясняет условия, при которых текст в элементах XML не учитываются.</span><span class="sxs-lookup"><span data-stu-id="86549-124">Describes the columns that are created for text in XML elements, and explains when text in XML elements is ignored.</span></span>  
  
 [<span data-ttu-id="86549-125">Ограничения определения</span><span class="sxs-lookup"><span data-stu-id="86549-125">Inference Limitations</span></span>](inference-limitations.md)  
 <span data-ttu-id="86549-126">Обсуждает ограничения вывода схемы.</span><span class="sxs-lookup"><span data-stu-id="86549-126">Discusses the limitations of schema inference.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="86549-127">См. также</span><span class="sxs-lookup"><span data-stu-id="86549-127">Related Sections</span></span>  

 [<span data-ttu-id="86549-128">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="86549-128">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="86549-129">Описывает, как объект <xref:System.Data.DataSet> взаимодействует с XML-данными.</span><span class="sxs-lookup"><span data-stu-id="86549-129">Describes how the <xref:System.Data.DataSet> object interacts with XML data.</span></span>  
  
 [<span data-ttu-id="86549-130">Наследование реляционной структуры набора данных от схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="86549-130">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="86549-131">Описывает реляционную структуру (или схему) набора данных <xref:System.Data.DataSet>, которая создается с помощью схемы XSD.</span><span class="sxs-lookup"><span data-stu-id="86549-131">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="86549-132">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="86549-132">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="86549-133">Описывает архитектуру, компоненты ADO.NET и способы их использования для доступа к существующим источникам данных и управления данными приложения.</span><span class="sxs-lookup"><span data-stu-id="86549-133">Describes the ADO.NET architecture and components and how to use them to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86549-134">См. также</span><span class="sxs-lookup"><span data-stu-id="86549-134">See also</span></span>

- [<span data-ttu-id="86549-135">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="86549-135">ADO.NET Overview</span></span>](../ado-net-overview.md)
