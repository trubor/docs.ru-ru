---
description: 'Дополнительные сведения: применение преобразования XSLT к набору данных'
title: Применение преобразования XSLT к набору данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: c7fc25441091112f7fbb7e4c1f8dd210d8cd0c5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725120"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="14136-103">Применение преобразования XSLT к набору данных</span><span class="sxs-lookup"><span data-stu-id="14136-103">Applying an XSLT Transform to a DataSet</span></span>

<span data-ttu-id="14136-104">Метод **WriteXml** объекта <xref:System.Data.DataSet> позволяет записывать содержимое **набора** данных в виде XML-данных.</span><span class="sxs-lookup"><span data-stu-id="14136-104">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="14136-105">После этого типичной задачей является преобразование этого XML в другой формат с помощью XSLT-преобразования (XSLT).</span><span class="sxs-lookup"><span data-stu-id="14136-105">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="14136-106">Однако синхронизация **набора данных** с помощью <xref:System.Xml.XmlDataDocument> позволяет применить таблицу стилей XSLT к содержимому **набора данных** без необходимости сначала писать содержимое **набора** данных в виде XML-данных с помощью метода **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="14136-106">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="14136-107">Следующий пример заполняет **набор данных** таблицами и связями, синхронизирует **набор** данных с объектом **XmlDataDocument** и записывает часть **набора данных** в виде файла HTML с помощью таблицы стилей XSLT.</span><span class="sxs-lookup"><span data-stu-id="14136-107">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="14136-108">Ниже приведено содержимое таблицы стилей XSLT.</span><span class="sxs-lookup"><span data-stu-id="14136-108">The following are the contents of the XSLT stylesheet:</span></span>
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="14136-109">Следующий код заполняет **набор данных** и применяет таблицу стилей XSLT.</span><span class="sxs-lookup"><span data-stu-id="14136-109">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14136-110">При применении таблицы стилей XSLT к **набору данных** , содержащему связи, обеспечивается лучшая производительность, если для свойства **Nested** элемента имеет значение <xref:System.Data.DataRelation> **true** для каждого вложенного отношения.</span><span class="sxs-lookup"><span data-stu-id="14136-110">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="14136-111">Это позволяет использовать таблицы стилей XSLT, реализующие естественную нисходящую обработку для перемещения по иерархии и преобразования данных, в отличие от ресурсоемких осей расположения XPath (например, предшествующий одноуровневый элемент и следующий элемент того же уровня в тестовых выражениях узла таблицы стилей).</span><span class="sxs-lookup"><span data-stu-id="14136-111">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="14136-112">Дополнительные сведения о вложенных отношениях см. в разделе [вложенность связей](nesting-datarelations.md)данных.</span><span class="sxs-lookup"><span data-stu-id="14136-112">For more information on nested relations, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="14136-113">См. также</span><span class="sxs-lookup"><span data-stu-id="14136-113">See also</span></span>

- [<span data-ttu-id="14136-114">Синхронизация DataSet и XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="14136-114">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="14136-115">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="14136-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
