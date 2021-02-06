---
description: 'Дополнительные сведения: сопоставьте ключевые ограничения XML-схемы (XSD) с ограничениями набора данных'
title: Сопоставление ключевых ограничений XML-схемы (XSD) с ограничениями набора данных
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 0c07b53e06dc6b80395764b2bdd76045ee80bffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651994"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="cecbf-103">Сопоставление ключевых ограничений XML-схемы (XSD) с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="cecbf-103">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="cecbf-104">В схеме можно указать ограничение ключа для элемента или атрибута с помощью элемента **Key** .</span><span class="sxs-lookup"><span data-stu-id="cecbf-104">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="cecbf-105">Элемент или атрибут, в котором указывается ограничение ключа, должен иметь уникальные значения во всех экземплярах схемы, не равные NULL.</span><span class="sxs-lookup"><span data-stu-id="cecbf-105">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="cecbf-106">Ограничение ключа похоже на ограничение уникальности за исключением того, что столбец, в котором определяется ограничение ключа, не может принимать значения NULL.</span><span class="sxs-lookup"><span data-stu-id="cecbf-106">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="cecbf-107">В следующей таблице описаны атрибуты **msdata** , которые можно указать в элементе **Key** .</span><span class="sxs-lookup"><span data-stu-id="cecbf-107">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="cecbf-108">Имя атрибута</span><span class="sxs-lookup"><span data-stu-id="cecbf-108">Attribute name</span></span>|<span data-ttu-id="cecbf-109">Описание</span><span class="sxs-lookup"><span data-stu-id="cecbf-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="cecbf-110">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="cecbf-110">**msdata:ConstraintName**</span></span>|<span data-ttu-id="cecbf-111">Если этот атрибут указан, его значение используется в качестве имени ограничения.</span><span class="sxs-lookup"><span data-stu-id="cecbf-111">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="cecbf-112">В противном случае атрибут **Name** предоставляет значение имени ограничения.</span><span class="sxs-lookup"><span data-stu-id="cecbf-112">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="cecbf-113">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="cecbf-113">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="cecbf-114">Если имеется `PrimaryKey="true"` , свойство Constraint **IsPrimaryKey имеют значение** имеет значение **true**, делая его первичным ключом.</span><span class="sxs-lookup"><span data-stu-id="cecbf-114">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="cecbf-115">Свойство **AllowDbNull** column имеет значение **false**, так как первичные ключи не могут иметь значения NULL.</span><span class="sxs-lookup"><span data-stu-id="cecbf-115">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="cecbf-116">При преобразовании схемы, в которой указано ограничение по ключу, в процессе сопоставления создается ограничение уникальности для таблицы со свойством **AllowDbNull** столбца, установленным в **значение false** для каждого столбца в ограничении.</span><span class="sxs-lookup"><span data-stu-id="cecbf-116">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="cecbf-117">Свойство **IsPrimaryKey имеют значение** ограничения UNIQUE также имеет значение **false** , если `msdata:PrimaryKey="true"` для элемента **Key** не задано значение.</span><span class="sxs-lookup"><span data-stu-id="cecbf-117">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="cecbf-118">Это равнозначно ограничению уникальности в схеме, где `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="cecbf-118">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="cecbf-119">В следующем примере схемы элемент **Key** указывает ограничение ключа для элемента **CustomerID** .</span><span class="sxs-lookup"><span data-stu-id="cecbf-119">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 <span data-ttu-id="cecbf-120">Элемент **Key** указывает, что значения дочернего элемента **CustomerID** элемента **Customers** должны иметь уникальные значения и не могут иметь значения NULL.</span><span class="sxs-lookup"><span data-stu-id="cecbf-120">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="cecbf-121">При преобразовании схемы XSD процесс сопоставления создает следующую таблицу.</span><span class="sxs-lookup"><span data-stu-id="cecbf-121">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="cecbf-122">Сопоставление схемы XML также создает **UniqueConstraint** в столбце **CustomerID** , как показано ниже <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cecbf-122">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cecbf-123">(Для простоты показаны только значимые свойства.)</span><span class="sxs-lookup"><span data-stu-id="cecbf-123">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="cecbf-124">В созданном **наборе данных** свойству **IsPrimaryKey имеют значение** **UniqueConstraint** присваивается **значение true** , поскольку схема указывает `msdata:PrimaryKey="true"` в элементе **Key** .</span><span class="sxs-lookup"><span data-stu-id="cecbf-124">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="cecbf-125">Значением свойства **ConstraintName** объекта **UniqueConstraint** в **наборе данных** является значение атрибута **msdata: ConstraintName** , указанного в элементе **Key** схемы.</span><span class="sxs-lookup"><span data-stu-id="cecbf-125">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecbf-126">См. также</span><span class="sxs-lookup"><span data-stu-id="cecbf-126">See also</span></span>

- [<span data-ttu-id="cecbf-127">Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="cecbf-127">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="cecbf-128">Создание отношений наборов данных из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="cecbf-128">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="cecbf-129">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cecbf-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
