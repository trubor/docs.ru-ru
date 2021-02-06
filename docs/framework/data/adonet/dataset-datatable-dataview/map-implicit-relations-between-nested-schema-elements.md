---
description: 'Дополнительные сведения: Сопоставление неявных отношений между вложенными элементами схемы'
title: Сопоставление неявных отношений между вложенными элементами схемы
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 418dd1210674b2c592cf96c6d369bc43f8dcab9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652020"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="3aaf1-103">Сопоставление неявных отношений между вложенными элементами схемы</span><span class="sxs-lookup"><span data-stu-id="3aaf1-103">Map Implicit Relations Between Nested Schema Elements</span></span>

<span data-ttu-id="3aaf1-104">Схема на языке XSD может иметь сложные типы, вложенные друг в друга.</span><span class="sxs-lookup"><span data-stu-id="3aaf1-104">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="3aaf1-105">В этом случае процесс сопоставления применяет сопоставление по умолчанию и создает в объекте <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="3aaf1-105">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="3aaf1-106">одну таблицу для каждого сложного типа (родительского и дочернего);</span><span class="sxs-lookup"><span data-stu-id="3aaf1-106">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="3aaf1-107">Если для родителя не существует ограничений UNIQUE, по одному дополнительному первичному ключевому столбцу для определения таблицы с именем *tablename* _Id, где *TableName* — это имя родительской таблицы.</span><span class="sxs-lookup"><span data-stu-id="3aaf1-107">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName* _Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="3aaf1-108">Ограничение первичного ключа в родительской таблице, определяющее дополнительный столбец в качестве первичного ключа (путем присвоения свойству **IsPrimaryKey имеют значение** значения **true**).</span><span class="sxs-lookup"><span data-stu-id="3aaf1-108">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="3aaf1-109">Ограничению назначается имя Constraint\#, где \# - это 1, 2, 3 и т. д.</span><span class="sxs-lookup"><span data-stu-id="3aaf1-109">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="3aaf1-110">Например, имя первого ограничения по умолчанию - Constraint1;</span><span class="sxs-lookup"><span data-stu-id="3aaf1-110">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="3aaf1-111">ограничение внешнего ключа для дочерней таблицы, определяющее дополнительный столбец как внешний ключ, ссылающийся на первичный ключ родительской таблицы.</span><span class="sxs-lookup"><span data-stu-id="3aaf1-111">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="3aaf1-112">Ограничение называется *ParentTable_ChildTable* , где *паренттабле* — имя родительской таблицы, а *ChildTable* — имя дочерней таблицы.</span><span class="sxs-lookup"><span data-stu-id="3aaf1-112">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="3aaf1-113">связи данных между родительскими и дочерними таблицами.</span><span class="sxs-lookup"><span data-stu-id="3aaf1-113">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="3aaf1-114">В следующем примере показана схема, в которой **OrderDetail** является дочерним элементом **Order**.</span><span class="sxs-lookup"><span data-stu-id="3aaf1-114">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
   <xs:complexType>  
     <xs:choice maxOccurs="unbounded">  
       <xs:element name="Order">  
         <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="3aaf1-115">Процесс сопоставления схем XML создает в **наборе данных** следующее:</span><span class="sxs-lookup"><span data-stu-id="3aaf1-115">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="3aaf1-116">**Заказ** и таблица **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="3aaf1-116">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="3aaf1-117">Ограничение UNIQUE для таблицы **Order** .</span><span class="sxs-lookup"><span data-stu-id="3aaf1-117">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="3aaf1-118">Обратите внимание, что свойство **IsPrimaryKey имеют значение** имеет значение **true**.</span><span class="sxs-lookup"><span data-stu-id="3aaf1-118">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="3aaf1-119">Ограничение внешнего ключа для таблицы **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="3aaf1-119">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="3aaf1-120">Связь между таблицами **Order** и **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="3aaf1-120">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="3aaf1-121">**Вложенному** свойству для этой связи присваивается **значение true** , поскольку элементы **Order** и **OrderDetail** вложены в схему.</span><span class="sxs-lookup"><span data-stu-id="3aaf1-121">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3aaf1-122">См. также</span><span class="sxs-lookup"><span data-stu-id="3aaf1-122">See also</span></span>

- [<span data-ttu-id="3aaf1-123">Создание отношений наборов данных из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="3aaf1-123">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="3aaf1-124">Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="3aaf1-124">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="3aaf1-125">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3aaf1-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
