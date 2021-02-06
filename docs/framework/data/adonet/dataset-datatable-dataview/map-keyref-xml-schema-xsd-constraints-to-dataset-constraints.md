---
description: Дополнительные сведения см. в статье преобразование ограничений XML-схемы keyref (XSD) в ограничения набора данных.
title: Сопоставление ограничений XML-схемы (XSD) keyref с ограничениями набора данных
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: f9925cf68e0c8fd1258eeeb509664e0527e58526
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651981"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="6a26f-103">Сопоставление ограничений XML-схемы (XSD) keyref с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="6a26f-103">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="6a26f-104">Элемент **keyref** позволяет устанавливать связи между элементами в документе.</span><span class="sxs-lookup"><span data-stu-id="6a26f-104">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="6a26f-105">Это похоже на связь по внешнему ключу в реляционной базе данных.</span><span class="sxs-lookup"><span data-stu-id="6a26f-105">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="6a26f-106">Если схема указывает элемент **keyref** , элемент преобразуется в процессе сопоставления схемы в соответствующее ограничение FOREIGN KEY для столбцов в таблицах <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="6a26f-106">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6a26f-107">По умолчанию элемент **keyref** также создает отношение со свойствами **паренттабле**, **ChildTable**, **парентколумн** и **чилдколумн** , указанными для отношения.</span><span class="sxs-lookup"><span data-stu-id="6a26f-107">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="6a26f-108">В следующей таблице описаны атрибуты **msdata** , которые можно указать в элементе **keyref** .</span><span class="sxs-lookup"><span data-stu-id="6a26f-108">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="6a26f-109">Имя атрибута</span><span class="sxs-lookup"><span data-stu-id="6a26f-109">Attribute name</span></span>|<span data-ttu-id="6a26f-110">Описание</span><span class="sxs-lookup"><span data-stu-id="6a26f-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6a26f-111">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="6a26f-111">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="6a26f-112">Если для элемента **keyref** схемы задано **значение констраинтонли = "true"** , то создается ограничение, но связь не создается.</span><span class="sxs-lookup"><span data-stu-id="6a26f-112">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="6a26f-113">Если этот атрибут не задан (или имеет значение **false**), в **наборе данных** создается и ограничение, и отношение.</span><span class="sxs-lookup"><span data-stu-id="6a26f-113">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="6a26f-114">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="6a26f-114">**msdata:ConstraintName**</span></span>|<span data-ttu-id="6a26f-115">Если указан атрибут **ConstraintName** , его значение используется в качестве имени ограничения.</span><span class="sxs-lookup"><span data-stu-id="6a26f-115">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="6a26f-116">В противном случае атрибут **Name** элемента **keyref** в схеме предоставляет имя ограничения в **наборе данных**.</span><span class="sxs-lookup"><span data-stu-id="6a26f-116">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="6a26f-117">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="6a26f-117">**msdata:UpdateRule**</span></span>|<span data-ttu-id="6a26f-118">Если атрибут **UpdateRule** указан в элементе **keyref** схемы, его значение присваивается свойству ограничения **UpdateRule** в **наборе данных**.</span><span class="sxs-lookup"><span data-stu-id="6a26f-118">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="6a26f-119">В противном случае свойство **UpdateRule** имеет значение **CASCADE**.</span><span class="sxs-lookup"><span data-stu-id="6a26f-119">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="6a26f-120">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="6a26f-120">**msdata:DeleteRule**</span></span>|<span data-ttu-id="6a26f-121">Если атрибут **DeleteRule** указан в элементе **keyref** схемы, его значение присваивается свойству ограничения **DeleteRule** в **наборе данных**.</span><span class="sxs-lookup"><span data-stu-id="6a26f-121">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="6a26f-122">В противном случае свойство **DeleteRule** имеет значение **CASCADE**.</span><span class="sxs-lookup"><span data-stu-id="6a26f-122">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="6a26f-123">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="6a26f-123">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="6a26f-124">Если атрибут **акцептрежектруле** указан в элементе **keyref** схемы, его значение присваивается свойству ограничения **акцептрежектруле** в **наборе данных**.</span><span class="sxs-lookup"><span data-stu-id="6a26f-124">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="6a26f-125">В противном случае свойство **акцептрежектруле** имеет значение **None**.</span><span class="sxs-lookup"><span data-stu-id="6a26f-125">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="6a26f-126">В следующем примере показана схема, указывающая **ключ** и связи **keyref** между дочерним элементом **OrderNumber** элемента **Order** и дочерним элементом **ордерно** элемента **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="6a26f-126">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="6a26f-127">В этом примере дочерний элемент **OrderNumber** элемента **OrderDetail** ссылается на дочерний элемент ключа **ордерно** элемента **Order** .</span><span class="sxs-lookup"><span data-stu-id="6a26f-127">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="6a26f-128">Процесс сопоставления схем на языке определения схем XML (XSD) создает следующий **набор данных** с двумя таблицами:</span><span class="sxs-lookup"><span data-stu-id="6a26f-128">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="6a26f-129">Кроме того, **набор данных** определяет следующие ограничения.</span><span class="sxs-lookup"><span data-stu-id="6a26f-129">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="6a26f-130">Ограничение UNIQUE для таблицы **Order** .</span><span class="sxs-lookup"><span data-stu-id="6a26f-130">A unique constraint on the **Order** table.</span></span>  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="6a26f-131">Связь между таблицами **Order** и **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="6a26f-131">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="6a26f-132">**Вложенное** свойство имеет значение **false** , так как два элемента не вложены в схему.</span><span class="sxs-lookup"><span data-stu-id="6a26f-132">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="6a26f-133">Ограничение внешнего ключа для таблицы **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="6a26f-133">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6a26f-134">См. также</span><span class="sxs-lookup"><span data-stu-id="6a26f-134">See also</span></span>

- [<span data-ttu-id="6a26f-135">Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="6a26f-135">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="6a26f-136">Создание отношений наборов данных из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="6a26f-136">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="6a26f-137">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6a26f-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
