---
description: 'Дополнительные сведения: наследование реляционной структуры набора данных из схемы XML (XSD)'
title: Наследование реляционной структуры набора данных от схемы XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: c2d2dc8ab9c8a1cf77c79fbde38a06de6f120c82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652527"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="0f83c-103">Наследование реляционной структуры набора данных от схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="0f83c-103">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>

<span data-ttu-id="0f83c-104">В этом разделе приведены общие сведения о построении реляционной схемы `DataSet` на основе документа схемы на языке XSD.</span><span class="sxs-lookup"><span data-stu-id="0f83c-104">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="0f83c-105">Как правило, для каждого `complexType` дочернего элемента в элементе Schema создается таблица в `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="0f83c-105">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="0f83c-106">Структура таблицы задается определением сложного типа.</span><span class="sxs-lookup"><span data-stu-id="0f83c-106">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="0f83c-107">Таблицы создаются в `DataSet` для элементов верхнего уровня схемы.</span><span class="sxs-lookup"><span data-stu-id="0f83c-107">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="0f83c-108">Однако таблица создается только для элемента верхнего уровня `complexType` `complexType` , если элемент вложен в другой `complexType` элемент. в этом случае вложенный `complexType` элемент сопоставляется с элементом в `DataTable` `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="0f83c-108">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="0f83c-109">Дополнительные сведения о XSD см. в разделе консорциум W3C (W3C) [XML-схема, часть 0: рекомендации по основам](https://www.w3.org/TR/xmlschema-0/), [рекомендации по схеме XML Part 1:](https://www.w3.org/TR/xmlschema-1/)Structures и [XML Schema, часть 2: рекомендации по типам](https://www.w3.org/TR/xmlschema-2/)данных.</span><span class="sxs-lookup"><span data-stu-id="0f83c-109">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="0f83c-110">В следующем примере показана схема XML `customers` , где — это дочерний элемент `MyDataSet` элемента DataSet, который является элементом **набора данных** .</span><span class="sxs-lookup"><span data-stu-id="0f83c-110">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="0f83c-111">В предыдущем примере элемент `customers` является элементом сложного типа.</span><span class="sxs-lookup"><span data-stu-id="0f83c-111">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="0f83c-112">Поэтому проводится синтаксический анализ определения сложного типа, а процесс сопоставления создает следующую таблицу.</span><span class="sxs-lookup"><span data-stu-id="0f83c-112">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="0f83c-113">Тип данных каждого столбца в таблице получается из типа схемы XML соответствующего элемента или указанного атрибута.</span><span class="sxs-lookup"><span data-stu-id="0f83c-113">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f83c-114">Если элемент `customers` имеет простой тип данных схемы XML, такой как **Integer**, таблица не создается.</span><span class="sxs-lookup"><span data-stu-id="0f83c-114">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="0f83c-115">Таблицы создаются только для элементов верхнего уровня, которые являются сложными типами.</span><span class="sxs-lookup"><span data-stu-id="0f83c-115">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="0f83c-116">В следующей схеме XML элемент **Schema** имеет два дочерних элемента, `InStateCustomers` и `OutOfStateCustomers` .</span><span class="sxs-lookup"><span data-stu-id="0f83c-116">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="0f83c-117">Дочерние элементы `InStateCustomers` и `OutOfStateCustomers` являются элементами сложного типа (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="0f83c-117">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="0f83c-118">Таким образом, процесс сопоставления создает следующие две идентичные таблицы в `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="0f83c-118">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="0f83c-119">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="0f83c-119">In This Section</span></span>  

 [<span data-ttu-id="0f83c-120">Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="0f83c-120">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="0f83c-121">Описывает элементы XML-схемы, используемые для создания ограничений UNIQUE и FOREIGN KEY в `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="0f83c-121">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="0f83c-122">Создание отношений наборов данных из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="0f83c-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="0f83c-123">Описывает элементы XML-схемы, используемые для создания связей между столбцами таблицы в `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="0f83c-123">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="0f83c-124">Ограничения и отношения схемы XML</span><span class="sxs-lookup"><span data-stu-id="0f83c-124">XML Schema Constraints and Relationships</span></span>](xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="0f83c-125">Описывает, как неявным образом создаются связи при использовании элементов схемы XML для создания ограничений в `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="0f83c-125">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0f83c-126">См. также</span><span class="sxs-lookup"><span data-stu-id="0f83c-126">Related Sections</span></span>  

 [<span data-ttu-id="0f83c-127">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="0f83c-127">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="0f83c-128">Описывает загрузку и сохранение реляционной структуры и данных в `DataSet` виде XML-данных.</span><span class="sxs-lookup"><span data-stu-id="0f83c-128">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f83c-129">См. также</span><span class="sxs-lookup"><span data-stu-id="0f83c-129">See also</span></span>

- [<span data-ttu-id="0f83c-130">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0f83c-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
