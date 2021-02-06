---
description: Дополнительные сведения о сопоставлении связей, указанных для вложенных элементов.
title: Сопоставление отношений, заданных для вложенных элементов
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: a625ad5bfd590794d0362a991dc22f756f043f2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651942"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="f7b18-103">Сопоставление отношений, заданных для вложенных элементов</span><span class="sxs-lookup"><span data-stu-id="f7b18-103">Map Relations Specified for Nested Elements</span></span>

<span data-ttu-id="f7b18-104">Схема может включать аннотацию **msdata: relationship** для явного указания сопоставления между любыми двумя элементами в схеме.</span><span class="sxs-lookup"><span data-stu-id="f7b18-104">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="f7b18-105">Два элемента, указанные в **msdata: relationship** , могут быть вложены в схему, но не обязательно должны быть.</span><span class="sxs-lookup"><span data-stu-id="f7b18-105">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="f7b18-106">Процесс сопоставления использует **msdata: relationship** в схеме для создания связи «первичный-внешний ключ» между двумя столбцами.</span><span class="sxs-lookup"><span data-stu-id="f7b18-106">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="f7b18-107">В следующем примере показана схема XML, в которой элемент **OrderDetail** является дочерним элементом **Order**.</span><span class="sxs-lookup"><span data-stu-id="f7b18-107">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="f7b18-108">Элемент **msdata: relationship** определяет эту связь типа «родители-потомки» и указывает, что столбец **OrderNumber** результирующей таблицы **Order** связан со столбцом **ордерно** результирующей таблицы **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="f7b18-108">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 <span data-ttu-id="f7b18-109">Процесс сопоставления схем XML создает в объекте <xref:System.Data.DataSet> следующее.</span><span class="sxs-lookup"><span data-stu-id="f7b18-109">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="f7b18-110">**Заказ** и таблица **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="f7b18-110">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="f7b18-111">Связь между таблицами **Order** и **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="f7b18-111">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="f7b18-112">**Вложенному** свойству для этой связи присваивается **значение true** , поскольку элементы **Order** и **OrderDetail** вложены в схему.</span><span class="sxs-lookup"><span data-stu-id="f7b18-112">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="f7b18-113">Процесс сопоставления не создает никаких ограничений.</span><span class="sxs-lookup"><span data-stu-id="f7b18-113">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7b18-114">См. также</span><span class="sxs-lookup"><span data-stu-id="f7b18-114">See also</span></span>

- [<span data-ttu-id="f7b18-115">Создание отношений наборов данных из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="f7b18-115">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="f7b18-116">Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="f7b18-116">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="f7b18-117">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f7b18-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
