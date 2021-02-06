---
description: Дополнительные сведения о создании связей наборов данных из XML-схемы (XSD)
title: Создание отношений наборов данных из схемы XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: e18ae451085f536e7fe35053fadab35e30dbc225
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652462"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="6fce5-103">Создание отношений наборов данных из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="6fce5-103">Generating DataSet Relations from XML Schema (XSD)</span></span>

<span data-ttu-id="6fce5-104">В <xref:System.Data.DataSet> взаимосвязь между двумя или несколькими столбцами формируется путем создания отношения «родитель-потомок».</span><span class="sxs-lookup"><span data-stu-id="6fce5-104">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="6fce5-105">Существует три способа представления связи **набора данных** в схеме языка определения схемы XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="6fce5-105">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="6fce5-106">Задайте вложенные сложные типы.</span><span class="sxs-lookup"><span data-stu-id="6fce5-106">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="6fce5-107">Используйте аннотацию **msdata: relationship** .</span><span class="sxs-lookup"><span data-stu-id="6fce5-107">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="6fce5-108">Укажите **xs: keyref** без аннотации **msdata: констраинтонли** .</span><span class="sxs-lookup"><span data-stu-id="6fce5-108">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="6fce5-109">Вложенные сложные типы</span><span class="sxs-lookup"><span data-stu-id="6fce5-109">Nested Complex Types</span></span>  

 <span data-ttu-id="6fce5-110">Определения вложенных сложных типов в схеме указывают на связь элементов по модели «родитель-потомок».</span><span class="sxs-lookup"><span data-stu-id="6fce5-110">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="6fce5-111">Следующий фрагмент схемы XML показывает, что элемент **OrderDetail** является дочерним элементом элемента **Order** .</span><span class="sxs-lookup"><span data-stu-id="6fce5-111">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>
       <xs:element name="OrderDetail" />  
           <xs:complexType>
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="6fce5-112">Процесс сопоставления схем XML создает таблицы в **наборе данных** , соответствующие вложенным сложным типам в схеме.</span><span class="sxs-lookup"><span data-stu-id="6fce5-112">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="6fce5-113">Он также создает дополнительные столбцы, которые используются в качестве родительских **-** дочерних столбцов для создаваемых таблиц.</span><span class="sxs-lookup"><span data-stu-id="6fce5-113">It also creates additional columns that are used as parent **-** child columns for the generated tables.</span></span> <span data-ttu-id="6fce5-114">Обратите внимание, что эти родительские **-** дочерние столбцы задают связи, которые не совпадают с указанием ограничений первичного и внешнего ключей.</span><span class="sxs-lookup"><span data-stu-id="6fce5-114">Note that these parent **-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="6fce5-115">Заметка msdata:Relationship</span><span class="sxs-lookup"><span data-stu-id="6fce5-115">msdata:Relationship Annotation</span></span>  

 <span data-ttu-id="6fce5-116">Аннотация **msdata: relationship** позволяет явно указать связи типа «родители-потомки» между элементами схемы, которые не являются вложенными.</span><span class="sxs-lookup"><span data-stu-id="6fce5-116">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="6fce5-117">В следующем примере показана структура элемента **Relationship** .</span><span class="sxs-lookup"><span data-stu-id="6fce5-117">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="6fce5-118">Атрибуты заметки **msdata: relationship** указывают элементы, участвующие в связи типа «родители-потомки», а также элементы и атрибуты **родительскими** и **чилдкэй** , участвующие в связи.</span><span class="sxs-lookup"><span data-stu-id="6fce5-118">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="6fce5-119">Процесс сопоставления использует эти сведения для создания таблиц в **наборе данных** и для создания связи первичного и внешнего ключей между этими таблицами.</span><span class="sxs-lookup"><span data-stu-id="6fce5-119">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="6fce5-120">Например, в следующем фрагменте схемы элементы **Order** и **OrderDetail** указываются на одном и том же уровне (не вложенном).</span><span class="sxs-lookup"><span data-stu-id="6fce5-120">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="6fce5-121">Схема задает аннотацию **msdata: relationship** , которая указывает связь типа «родители-потомки» между этими двумя элементами.</span><span class="sxs-lookup"><span data-stu-id="6fce5-121">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="6fce5-122">В этом случае необходимо указать явную связь с помощью аннотации **msdata: relationship** .</span><span class="sxs-lookup"><span data-stu-id="6fce5-122">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="6fce5-123">В процессе сопоставления используется элемент **Relationship** для создания связи типа «родители-потомки» между столбцом **OrderNumber** в таблице **Order** и столбцом **Ордерно** в таблице **OrderDetail** в **наборе данных**.</span><span class="sxs-lookup"><span data-stu-id="6fce5-123">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="6fce5-124">Процесс сопоставления только указывает связь, он не задает автоматически ограничения значений в этих столбцах подобно ограничениям первичного/внешнего ключа в реляционных базах данных.</span><span class="sxs-lookup"><span data-stu-id="6fce5-124">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="6fce5-125">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="6fce5-125">In This Section</span></span>  

 [<span data-ttu-id="6fce5-126">Сопоставление неявных отношений между вложенными элементами схемы</span><span class="sxs-lookup"><span data-stu-id="6fce5-126">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="6fce5-127">Описывает ограничения и связи, которые неявно создаются в **наборе данных** при обнаружении вложенных элементов в схеме XML.</span><span class="sxs-lookup"><span data-stu-id="6fce5-127">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="6fce5-128">Сопоставление отношений, заданных для вложенных элементов</span><span class="sxs-lookup"><span data-stu-id="6fce5-128">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="6fce5-129">Описывает, как явно задать связи в **наборе данных** для вложенных элементов в схеме XML.</span><span class="sxs-lookup"><span data-stu-id="6fce5-129">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="6fce5-130">Указание отношений между элементами без вложенности</span><span class="sxs-lookup"><span data-stu-id="6fce5-130">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="6fce5-131">Описывает создание связей в **наборе данных** между невложенными ЭЛЕМЕНТАМИ XML-схемы.</span><span class="sxs-lookup"><span data-stu-id="6fce5-131">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="6fce5-132">См. также</span><span class="sxs-lookup"><span data-stu-id="6fce5-132">Related Sections</span></span>  

 [<span data-ttu-id="6fce5-133">Наследование реляционной структуры набора данных от схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="6fce5-133">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="6fce5-134">Описывает реляционную структуру или схему **набора данных** , созданного из схемы языка определения схемы XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="6fce5-134">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="6fce5-135">Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="6fce5-135">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="6fce5-136">Описывает элементы XML-схемы, используемые для создания ограничений UNIQUE и FOREIGN KEY в **наборе данных**.</span><span class="sxs-lookup"><span data-stu-id="6fce5-136">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fce5-137">См. также</span><span class="sxs-lookup"><span data-stu-id="6fce5-137">See also</span></span>

- [<span data-ttu-id="6fce5-138">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6fce5-138">ADO.NET Overview</span></span>](../ado-net-overview.md)
