---
description: 'Дополнительные сведения: запись содержимого набора данных в виде XML-данных'
title: Запись содержимого набора как данных XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 0ad232f744f69f822d09c0af6c4374b6e5f0147d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651370"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="bb43f-103">Запись содержимого набора как данных XML</span><span class="sxs-lookup"><span data-stu-id="bb43f-103">Writing DataSet Contents as XML Data</span></span>

<span data-ttu-id="bb43f-104">В ADO.NET можно записать XML-представление объекта <xref:System.Data.DataSet> вместе со схемой или без нее.</span><span class="sxs-lookup"><span data-stu-id="bb43f-104">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="bb43f-105">Если информация схемы встраивается внутрь XML, она записываются на языке XSD.</span><span class="sxs-lookup"><span data-stu-id="bb43f-105">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="bb43f-106">Схема содержит определения таблиц для <xref:System.Data.DataSet>, а также определения связей и ограничений.</span><span class="sxs-lookup"><span data-stu-id="bb43f-106">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="bb43f-107">Если <xref:System.Data.DataSet> записан как XML-данные, строки в <xref:System.Data.DataSet> записываются в своей текущей версии.</span><span class="sxs-lookup"><span data-stu-id="bb43f-107">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="bb43f-108">Однако <xref:System.Data.DataSet> может быть записан как DiffGram, так что будут включены и текущие, и исходные данные строк.</span><span class="sxs-lookup"><span data-stu-id="bb43f-108">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="bb43f-109">XML-представление <xref:System.Data.DataSet> может быть записано в файл, в поток, в **XmlWriter** или в строку.</span><span class="sxs-lookup"><span data-stu-id="bb43f-109">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="bb43f-110">Эти возможности обеспечивают большую гибкость способа переноса XML-представления для <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="bb43f-110">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="bb43f-111">Чтобы получить XML-представление в <xref:System.Data.DataSet> виде строки, используйте метод **getXML** , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="bb43f-111">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="bb43f-112">**GetXML** возвращает XML-представление <xref:System.Data.DataSet> без сведений о схеме.</span><span class="sxs-lookup"><span data-stu-id="bb43f-112">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="bb43f-113">Чтобы записать сведения о схеме из <xref:System.Data.DataSet> (в виде XML-схемы) в строку, используйте параметр GetSchema.</span><span class="sxs-lookup"><span data-stu-id="bb43f-113">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="bb43f-114">Для записи в <xref:System.Data.DataSet> файл, поток или **XmlWriter** используйте метод **WriteXml** .</span><span class="sxs-lookup"><span data-stu-id="bb43f-114">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="bb43f-115">Первым параметром, который передается в **WriteXml** , является назначение выходных данных в формате XML.</span><span class="sxs-lookup"><span data-stu-id="bb43f-115">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="bb43f-116">Например, передайте строку, содержащую имя файла, объект **System. IO. TextWriter** и т. д.</span><span class="sxs-lookup"><span data-stu-id="bb43f-116">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="bb43f-117">Можно передать необязательный второй параметр **ксмлвритемоде** , чтобы указать способ записи выходных данных XML.</span><span class="sxs-lookup"><span data-stu-id="bb43f-117">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="bb43f-118">В следующей таблице показаны параметры для **ксмлвритемоде**.</span><span class="sxs-lookup"><span data-stu-id="bb43f-118">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="bb43f-119">Параметр XmlWriteMode</span><span class="sxs-lookup"><span data-stu-id="bb43f-119">XmlWriteMode option</span></span>|<span data-ttu-id="bb43f-120">Описание</span><span class="sxs-lookup"><span data-stu-id="bb43f-120">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="bb43f-121">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="bb43f-121">**IgnoreSchema**</span></span>|<span data-ttu-id="bb43f-122">Записывает текущее содержимое <xref:System.Data.DataSet> как XML-данные, без схемы XML.</span><span class="sxs-lookup"><span data-stu-id="bb43f-122">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="bb43f-123">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bb43f-123">This is the default.</span></span>|  
|<span data-ttu-id="bb43f-124">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="bb43f-124">**WriteSchema**</span></span>|<span data-ttu-id="bb43f-125">Записывает текущее содержимое <xref:System.Data.DataSet> в виде XML-данных с реляционной структурой в виде встроенной схемы XML.</span><span class="sxs-lookup"><span data-stu-id="bb43f-125">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="bb43f-126">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="bb43f-126">**DiffGram**</span></span>|<span data-ttu-id="bb43f-127">Записывает весь <xref:System.Data.DataSet> как DiffGram, включая исходные и текущие значения.</span><span class="sxs-lookup"><span data-stu-id="bb43f-127">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="bb43f-128">Дополнительные сведения см. в разделе [дельтами](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="bb43f-128">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="bb43f-129">При написании XML-представления объекта <xref:System.Data.DataSet> , содержащего объекты **DataRelation** , скорее всего потребуется, чтобы результирующий XML имели дочерние строки каждой связи, вложенные в соответствующие им родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="bb43f-129">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="bb43f-130">Для этого присвойте свойству **Nested** объекта **DataRelation** значение **true** при добавлении объекта **DataRelation** в коллекцию <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="bb43f-130">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="bb43f-131">Дополнительные сведения см. в разделе [вложенность связей](nesting-datarelations.md)данных.</span><span class="sxs-lookup"><span data-stu-id="bb43f-131">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="bb43f-132">Ниже приведены два примера того, как записать XML-представление в <xref:System.Data.DataSet> файл.</span><span class="sxs-lookup"><span data-stu-id="bb43f-132">The following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="bb43f-133">В первом примере имя файла для результирующего XML передается в **WriteXml** в виде строки.</span><span class="sxs-lookup"><span data-stu-id="bb43f-133">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="bb43f-134">Во втором примере передается объект **System. IO. StreamWriter** .</span><span class="sxs-lookup"><span data-stu-id="bb43f-134">The second example passes a **System.IO.StreamWriter** object.</span></span>
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="bb43f-135">Сопоставление столбцов с XML-элементами, атрибутами и текстом</span><span class="sxs-lookup"><span data-stu-id="bb43f-135">Mapping Columns to XML Elements, Attributes, and Text</span></span>  

 <span data-ttu-id="bb43f-136">Можно указать способ представления столбца таблицы в XML с помощью свойства **ColumnMapping** объекта **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="bb43f-136">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="bb43f-137">В следующей таблице показаны различные значения **MappingType** для свойства **ColumnMapping** столбца таблицы и результирующий XML.</span><span class="sxs-lookup"><span data-stu-id="bb43f-137">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="bb43f-138">Значение MappingType</span><span class="sxs-lookup"><span data-stu-id="bb43f-138">MappingType value</span></span>|<span data-ttu-id="bb43f-139">Описание</span><span class="sxs-lookup"><span data-stu-id="bb43f-139">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="bb43f-140">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bb43f-140">**Element**</span></span>|<span data-ttu-id="bb43f-141">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bb43f-141">This is the default.</span></span> <span data-ttu-id="bb43f-142">Столбец записывается как XML-элемент, где ColumnName - имя элемента, а содержимое столбца записывается как текст элемента.</span><span class="sxs-lookup"><span data-stu-id="bb43f-142">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="bb43f-143">Пример:</span><span class="sxs-lookup"><span data-stu-id="bb43f-143">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="bb43f-144">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="bb43f-144">**Attribute**</span></span>|<span data-ttu-id="bb43f-145">Столбец записывается как XML-атрибут XML-элемента для текущей строки, где ColumnName - это имя атрибута, а содержимое столбца записывается как значение атрибута.</span><span class="sxs-lookup"><span data-stu-id="bb43f-145">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="bb43f-146">Пример:</span><span class="sxs-lookup"><span data-stu-id="bb43f-146">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="bb43f-147">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="bb43f-147">**SimpleContent**</span></span>|<span data-ttu-id="bb43f-148">Содержимое столбца записывается как текст в XML-элементе для текущей строки.</span><span class="sxs-lookup"><span data-stu-id="bb43f-148">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="bb43f-149">Пример:</span><span class="sxs-lookup"><span data-stu-id="bb43f-149">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="bb43f-150">Обратите внимание, что значение **SimpleContent** не может быть задано для столбца таблицы, имеющей столбцы **элементов** или вложенные отношения.</span><span class="sxs-lookup"><span data-stu-id="bb43f-150">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="bb43f-151">**Скрыта**</span><span class="sxs-lookup"><span data-stu-id="bb43f-151">**Hidden**</span></span>|<span data-ttu-id="bb43f-152">Столбец не записывается в выводимый XML.</span><span class="sxs-lookup"><span data-stu-id="bb43f-152">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb43f-153">См. также</span><span class="sxs-lookup"><span data-stu-id="bb43f-153">See also</span></span>

- [<span data-ttu-id="bb43f-154">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="bb43f-154">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="bb43f-155">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="bb43f-155">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="bb43f-156">Вложение отношений DataRelation</span><span class="sxs-lookup"><span data-stu-id="bb43f-156">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="bb43f-157">Запись сведений о схеме набора данных как XSD</span><span class="sxs-lookup"><span data-stu-id="bb43f-157">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="bb43f-158">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="bb43f-158">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="bb43f-159">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bb43f-159">ADO.NET Overview</span></span>](../ado-net-overview.md)
