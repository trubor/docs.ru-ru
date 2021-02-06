---
description: 'Дополнительные сведения: запись сведений о схеме набора данных в формате XSD'
title: Запись сведений о схеме набора данных как XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: e05188c74ca21e73ee5151da817e143102640a13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651357"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="ccad5-103">Запись сведений о схеме набора данных как XSD</span><span class="sxs-lookup"><span data-stu-id="ccad5-103">Writing DataSet Schema Information as XSD</span></span>

<span data-ttu-id="ccad5-104">Можно записать схему набора данных <xref:System.Data.DataSet> в виде схемы на языке XSD, чтобы можно было передать ее в XML-документ с взаимосвязанными данными или без них.</span><span class="sxs-lookup"><span data-stu-id="ccad5-104">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="ccad5-105">XML-схема может быть записана в файл, в поток, в <xref:System.Xml.XmlWriter> или строку; она полезна для создания строго типизированного **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="ccad5-105">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="ccad5-106">Дополнительные сведения о строго типизированных объектах DataSet см. в разделе [типизированные наборы](typed-datasets.md) **данных** .</span><span class="sxs-lookup"><span data-stu-id="ccad5-106">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="ccad5-107">Можно указать способ представления столбца таблицы в XML-схеме с помощью свойства **ColumnMapping** <xref:System.Data.DataColumn> объекта.</span><span class="sxs-lookup"><span data-stu-id="ccad5-107">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="ccad5-108">Дополнительные сведения см. в разделе «Сопоставление столбцов с XML-элементами, атрибутами и текстом» [статьи запись содержимого набора данных в виде XML-данных](writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="ccad5-108">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="ccad5-109">Для записи схемы **набора данных** в виде XML-схемы в файл, поток или **XmlWriter** используйте метод **вритексмлсчема** **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="ccad5-109">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="ccad5-110">**Вритексмлсчема** принимает один параметр, который задает назначение результирующей схемы XML.</span><span class="sxs-lookup"><span data-stu-id="ccad5-110">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="ccad5-111">В следующих примерах кода показано, как записать XML-схему **набора данных** в файл, передав строку, содержащую имя файла и <xref:System.IO.StreamWriter> объект.</span><span class="sxs-lookup"><span data-stu-id="ccad5-111">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 <span data-ttu-id="ccad5-112">Чтобы получить схему **набора данных** и записать ее в виде строки XML-схемы, **используйте метод GetString** , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ccad5-112">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccad5-113">См. также</span><span class="sxs-lookup"><span data-stu-id="ccad5-113">See also</span></span>

- [<span data-ttu-id="ccad5-114">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="ccad5-114">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="ccad5-115">Запись содержимого набора как данных XML</span><span class="sxs-lookup"><span data-stu-id="ccad5-115">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)
- [<span data-ttu-id="ccad5-116">Типизированные наборы данных</span><span class="sxs-lookup"><span data-stu-id="ccad5-116">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="ccad5-117">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="ccad5-117">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ccad5-118">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ccad5-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
