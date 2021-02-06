---
description: 'Дополнительные сведения: указание связей между элементами без вложения'
title: Указание отношений между элементами без вложенности
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 68f6edad0c282091529bf9182f5161d0808a47aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651630"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="df9d9-103">Указание отношений между элементами без вложенности</span><span class="sxs-lookup"><span data-stu-id="df9d9-103">Specify Relations Between Elements with No Nesting</span></span>

<span data-ttu-id="df9d9-104">Если элементы не вложены, какие-либо неявные связи не создаются.</span><span class="sxs-lookup"><span data-stu-id="df9d9-104">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="df9d9-105">Однако можно явно указать связи между элементами, которые не вложены с помощью аннотации **msdata: relationship** .</span><span class="sxs-lookup"><span data-stu-id="df9d9-105">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="df9d9-106">В следующем примере показана схема XML, в которой заметка **msdata: relationship** задается между элементами **Order** и **OrderDetail** , которые не являются вложенными.</span><span class="sxs-lookup"><span data-stu-id="df9d9-106">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="df9d9-107">Аннотация **msdata: relationship** указывается как дочерний элемент элемента **Schema** .</span><span class="sxs-lookup"><span data-stu-id="df9d9-107">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"
                            msdata:child="OrderDetail"
                            msdata:parentkey="OrderNumber"
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 <span data-ttu-id="df9d9-108">В процессе сопоставления схемы языка определения схемы XML (XSD) создаются <xref:System.Data.DataSet> таблицы **Order** и **OrderDetail** и связь, указанная между этими двумя таблицами, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="df9d9-108">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="df9d9-109">См. также</span><span class="sxs-lookup"><span data-stu-id="df9d9-109">See also</span></span>

- [<span data-ttu-id="df9d9-110">Создание отношений наборов данных из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="df9d9-110">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="df9d9-111">Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="df9d9-111">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="df9d9-112">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="df9d9-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
