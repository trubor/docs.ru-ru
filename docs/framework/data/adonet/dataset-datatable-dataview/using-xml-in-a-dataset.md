---
description: Дополнительные сведения см. в статье Использование XML в наборе данных.
title: Использование XML в наборах данных
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: 5c4216fce9c1512c95da8e27a622ba228411b641
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651422"
---
# <a name="using-xml-in-a-dataset"></a><span data-ttu-id="8ef36-103">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="8ef36-103">Using XML in a DataSet</span></span>

<span data-ttu-id="8ef36-104">В ADO.NET можно заполнить <xref:System.Data.DataSet> из XML-потока или документа.</span><span class="sxs-lookup"><span data-stu-id="8ef36-104">With ADO.NET you can fill a <xref:System.Data.DataSet> from an XML stream or document.</span></span> <span data-ttu-id="8ef36-105">XML-поток или XML-документ можно использовать для предоставления объекту <xref:System.Data.DataSet> данных, информации о схеме или того и другого.</span><span class="sxs-lookup"><span data-stu-id="8ef36-105">You can use the XML stream or document to supply to the <xref:System.Data.DataSet> either data, schema information, or both.</span></span> <span data-ttu-id="8ef36-106">Данные из XML-потока или документа можно комбинировать с существующими в <xref:System.Data.DataSet> данными или сведениями о схеме.</span><span class="sxs-lookup"><span data-stu-id="8ef36-106">The information supplied from the XML stream or document can be combined with existing data or schema information already present in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="8ef36-107">ADO.NET также позволяет создавать XML-представление <xref:System.Data.DataSet> с его схемой или без нее с целью передать <xref:System.Data.DataSet> по HTTP для использования в другом приложении или на платформе, поддерживающей XML.</span><span class="sxs-lookup"><span data-stu-id="8ef36-107">ADO.NET also allows you to create an XML representation of a <xref:System.Data.DataSet>, with or without its schema, in order to transport the <xref:System.Data.DataSet> across HTTP for use by another application or XML-enabled platform.</span></span> <span data-ttu-id="8ef36-108">В XML-представлении набора данных <xref:System.Data.DataSet> данные записываются на языке XML, а схема, если она встроена в представление, записывается на языке XSD.</span><span class="sxs-lookup"><span data-stu-id="8ef36-108">In an XML representation of a <xref:System.Data.DataSet>, the data is written in XML and the schema, if it is included inline in the representation, is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="8ef36-109">XML и схема XML предоставляют удобный формат для передачи содержимого объекта <xref:System.Data.DataSet> удаленному клиенту и обратно.</span><span class="sxs-lookup"><span data-stu-id="8ef36-109">XML and XML Schema provide a convenient format for transferring the contents of a <xref:System.Data.DataSet> to and from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ef36-110">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="8ef36-110">In This Section</span></span>  

 [<span data-ttu-id="8ef36-111">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="8ef36-111">DiffGrams</span></span>](diffgrams.md)  
 <span data-ttu-id="8ef36-112">Содержит подробные сведения о DiffGram, XML-формате, который используется для чтения и записи содержимого класса <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8ef36-112">Provides details on the DiffGram, an XML format used to read and write the contents of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="8ef36-113">Загрузка набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="8ef36-113">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)  
 <span data-ttu-id="8ef36-114">Объясняет различные параметры, которые следует учитывать при загрузке содержимого класса <xref:System.Data.DataSet> из XML-документа.</span><span class="sxs-lookup"><span data-stu-id="8ef36-114">Discusses different options to consider when loading the contents of a <xref:System.Data.DataSet> from an XML document.</span></span>  
  
 [<span data-ttu-id="8ef36-115">Запись содержимого набора как данных XML</span><span class="sxs-lookup"><span data-stu-id="8ef36-115">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="8ef36-116">Объясняет способы создания содержимого класса <xref:System.Data.DataSet> в виде XML-данных и различные доступные параметры XML-формата.</span><span class="sxs-lookup"><span data-stu-id="8ef36-116">Discusses how to generate the contents of a <xref:System.Data.DataSet> as XML data, and the different XML format options you can use.</span></span>  
  
 [<span data-ttu-id="8ef36-117">Загрузка сведений о схеме набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="8ef36-117">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="8ef36-118">Объясняет методы класса <xref:System.Data.DataSet>, которые используются для загрузки схемы <xref:System.Data.DataSet> из XML.</span><span class="sxs-lookup"><span data-stu-id="8ef36-118">Discusses the <xref:System.Data.DataSet> methods used to load the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="8ef36-119">Запись сведений о схеме набора данных как XSD</span><span class="sxs-lookup"><span data-stu-id="8ef36-119">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)  
 <span data-ttu-id="8ef36-120">Объясняет использование схемы XML и ее создание из класса <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8ef36-120">Discusses the uses for an XML Schema and how to generate one from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="8ef36-121">Синхронизация DataSet и XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="8ef36-121">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="8ef36-122">Объясняет доступные в .NET Framework возможности синхронного доступа как к реляционным, так и иерархическим представлениям одного набора данных, а также демонстрирует создание синхронных связей между <xref:System.Data.DataSet> и <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="8ef36-122">Discusses the capability available in the .NET Framework of synchronous access to both relational and hierarchical views of a single set of data, and shows how to create a synchronous relationship between a <xref:System.Data.DataSet> and an <xref:System.Xml.XmlDataDocument>.</span></span>  
  
 [<span data-ttu-id="8ef36-123">Вложение отношений DataRelation</span><span class="sxs-lookup"><span data-stu-id="8ef36-123">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="8ef36-124">Объясняет значение вложенных объектов <xref:System.Data.DataRelation> при представлении содержимого класса <xref:System.Data.DataSet> как XML-данных и описывает создание этих объектов.</span><span class="sxs-lookup"><span data-stu-id="8ef36-124">Discusses the importance of nested <xref:System.Data.DataRelation> objects when representing the contents of a <xref:System.Data.DataSet> as XML data, and describes how to create them.</span></span>  
  
 [<span data-ttu-id="8ef36-125">Наследование реляционной структуры набора данных от схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="8ef36-125">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="8ef36-126">Объясняет реляционную структуру (схему) класса <xref:System.Data.DataSet>, созданную из схемы XML.</span><span class="sxs-lookup"><span data-stu-id="8ef36-126">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema.</span></span>  
  
 [<span data-ttu-id="8ef36-127">Определение реляционной структуры набора данных из XML</span><span class="sxs-lookup"><span data-stu-id="8ef36-127">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)  
 <span data-ttu-id="8ef36-128">Объясняет полученную реляционную структуру (или схему) класса <xref:System.Data.DataSet>, созданную при использовании XML-элементов.</span><span class="sxs-lookup"><span data-stu-id="8ef36-128">Describes the resulting relational structure, or schema, of a <xref:System.Data.DataSet> that is created when inferred from XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8ef36-129">См. также</span><span class="sxs-lookup"><span data-stu-id="8ef36-129">Related Sections</span></span>  

 [<span data-ttu-id="8ef36-130">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8ef36-130">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="8ef36-131">Описывает архитектуру и компоненты ADO.NET, а также способы их использования для доступа к существующим источникам данных и управления данными приложения.</span><span class="sxs-lookup"><span data-stu-id="8ef36-131">Describes the ADO.NET architecture and components, and how to use them to access existing data sources as well as to manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef36-132">См. также</span><span class="sxs-lookup"><span data-stu-id="8ef36-132">See also</span></span>

- [<span data-ttu-id="8ef36-133">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="8ef36-133">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8ef36-134">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8ef36-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
