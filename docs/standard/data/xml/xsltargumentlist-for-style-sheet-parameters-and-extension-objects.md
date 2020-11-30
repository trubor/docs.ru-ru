---
title: XsltArgumentList для параметров таблицы стилей и объектов расширения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
ms.openlocfilehash: fe227a2d3efc5c36b818b7f4431896e6f62b1f26
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685049"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="cd89d-102">XsltArgumentList для параметров таблицы стилей и объектов расширения</span><span class="sxs-lookup"><span data-stu-id="cd89d-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>

<span data-ttu-id="cd89d-103">Класс <xref:System.Xml.Xsl.XsltArgumentList> содержит параметры языка XSLT и объекты расширения XSLT.</span><span class="sxs-lookup"><span data-stu-id="cd89d-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="cd89d-104">При передаче в метод <xref:System.Xml.Xsl.XslTransform.Transform%2A> эти параметры и объекты расширения могут вызываться из таблиц стилей.</span><span class="sxs-lookup"><span data-stu-id="cd89d-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd89d-105">Классы <xref:System.Xml.Xsl.XslTransform> и <xref:System.Xml.Xsl.XsltArgumentList> являются устаревшими в версии платформы NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="cd89d-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="cd89d-106">Преобразования XSLT можно выполнять с помощью класса <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="cd89d-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="cd89d-107">См. дополнительные сведения об [использовании класса XslCompiledTransform](using-the-xslcompiledtransform-class.md) и [миграции из класса XslTransform](migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="cd89d-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="cd89d-108">Класс <xref:System.Xml.Xsl.XsltArgumentList> содержит параметры XSLT и объекты расширения XSLT.</span><span class="sxs-lookup"><span data-stu-id="cd89d-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="cd89d-109">При передаче в метод <xref:System.Xml.Xsl.XslTransform.Transform%2A> эти параметры и объекты расширения могут вызываться из таблиц стилей.</span><span class="sxs-lookup"><span data-stu-id="cd89d-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="cd89d-110">Далее перечислены преимущества передачи объектов по сравнению с использованием внедренного скрипта.</span><span class="sxs-lookup"><span data-stu-id="cd89d-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
- <span data-ttu-id="cd89d-111">Обеспечивает улучшенную инкапсуляцию и повторное использование классов.</span><span class="sxs-lookup"><span data-stu-id="cd89d-111">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="cd89d-112">Уменьшает размер и улучшает обслуживание таблиц стилей.</span><span class="sxs-lookup"><span data-stu-id="cd89d-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
- <span data-ttu-id="cd89d-113">Поддерживает вызов методов из классов, принадлежащих пространствам имен, не определенным в наборе поддерживаемых пространств имен <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="cd89d-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
- <span data-ttu-id="cd89d-114">Поддерживает передачу фрагментов результирующего дерева в таблицу стилей с помощью <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="cd89d-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="cd89d-115">Параметры таблицы стилей XSLT</span><span class="sxs-lookup"><span data-stu-id="cd89d-115">XSLT Style Sheet Parameters</span></span>  

 <span data-ttu-id="cd89d-116">Параметры XSLT добавляются в <xref:System.Xml.Xsl.XsltArgumentList> с помощью метода <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd89d-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="cd89d-117">В это время с объектом параметра связываются полное имя и URI-код пространства имен.</span><span class="sxs-lookup"><span data-stu-id="cd89d-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="cd89d-118">Объект параметра должен соответствовать типу W3C.</span><span class="sxs-lookup"><span data-stu-id="cd89d-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="cd89d-119">В следующей таблице показано соответствие типов W3C и классов (типов) .NET Framework. Также показано, является ли тип W3C типом XPath или типом XSLT.</span><span class="sxs-lookup"><span data-stu-id="cd89d-119">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="cd89d-120">Тип W3C</span><span class="sxs-lookup"><span data-stu-id="cd89d-120">W3C Type</span></span>|<span data-ttu-id="cd89d-121">Эквивалентный класс (тип) .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cd89d-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="cd89d-122">Тип XPath или тип XSLT</span><span class="sxs-lookup"><span data-stu-id="cd89d-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="cd89d-123">Строка</span><span class="sxs-lookup"><span data-stu-id="cd89d-123">String</span></span>|<span data-ttu-id="cd89d-124">System.String</span><span class="sxs-lookup"><span data-stu-id="cd89d-124">System.String</span></span>|<span data-ttu-id="cd89d-125">XPath</span><span class="sxs-lookup"><span data-stu-id="cd89d-125">XPath</span></span>|  
|<span data-ttu-id="cd89d-126">логический</span><span class="sxs-lookup"><span data-stu-id="cd89d-126">Boolean</span></span>|<span data-ttu-id="cd89d-127">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="cd89d-127">System.Boolean</span></span>|<span data-ttu-id="cd89d-128">XPath</span><span class="sxs-lookup"><span data-stu-id="cd89d-128">XPath</span></span>|  
|<span data-ttu-id="cd89d-129">Число</span><span class="sxs-lookup"><span data-stu-id="cd89d-129">Number</span></span>|<span data-ttu-id="cd89d-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="cd89d-130">System.Double</span></span>|<span data-ttu-id="cd89d-131">XPath</span><span class="sxs-lookup"><span data-stu-id="cd89d-131">XPath</span></span>|  
|<span data-ttu-id="cd89d-132">Фрагмент дерева результатов</span><span class="sxs-lookup"><span data-stu-id="cd89d-132">Result Tree Fragment</span></span>|<span data-ttu-id="cd89d-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cd89d-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="cd89d-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="cd89d-134">XSLT</span></span>|  
|<span data-ttu-id="cd89d-135">Набор узлов</span><span class="sxs-lookup"><span data-stu-id="cd89d-135">Node Set</span></span>|<span data-ttu-id="cd89d-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="cd89d-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="cd89d-137">XPath</span><span class="sxs-lookup"><span data-stu-id="cd89d-137">XPath</span></span>|  
  
 <span data-ttu-id="cd89d-138">Если объект параметра не принадлежит ни к одному из классов выше, он принудительно преобразуется в тип Double или String.</span><span class="sxs-lookup"><span data-stu-id="cd89d-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="cd89d-139">Типы Int16, UInt16, Int32, UInt32, Int64, UInt64, Single и Decimal преобразуются в Double.</span><span class="sxs-lookup"><span data-stu-id="cd89d-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="cd89d-140">Все остальные типы преобразуются в тип String с помощью метода `ToString`.</span><span class="sxs-lookup"><span data-stu-id="cd89d-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="cd89d-141">Чтобы использовать параметр XSLT, пользователь должен выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="cd89d-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="cd89d-142">Создать объект <xref:System.Xml.Xsl.XsltArgumentList> и добавить объекты с помощью метода <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd89d-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2. <span data-ttu-id="cd89d-143">Вызвать параметры из таблицы стилей.</span><span class="sxs-lookup"><span data-stu-id="cd89d-143">Call the parameters from the style sheet.</span></span>  
  
3. <span data-ttu-id="cd89d-144">Передать <xref:System.Xml.Xsl.XsltArgumentList> методу <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd89d-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="cd89d-145">Пример</span><span class="sxs-lookup"><span data-stu-id="cd89d-145">Example</span></span>  

 <span data-ttu-id="cd89d-146">В следующем примере используется метод <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> для создания параметра, хранящего вычисленную дату скидки.</span><span class="sxs-lookup"><span data-stu-id="cd89d-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="cd89d-147">Дата скидки вычисляется как 20 дней после даты заказа.</span><span class="sxs-lookup"><span data-stu-id="cd89d-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="cd89d-148">Входные данные</span><span class="sxs-lookup"><span data-stu-id="cd89d-148">Input</span></span>  

 <span data-ttu-id="cd89d-149">order.xml</span><span class="sxs-lookup"><span data-stu-id="cd89d-149">order.xml</span></span>  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 <span data-ttu-id="cd89d-150">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="cd89d-150">discount.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="cd89d-151">Вывод</span><span class="sxs-lookup"><span data-stu-id="cd89d-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>
   15% discount if paid by: 5/6/2001 5:01:15 PM
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="cd89d-152">Объекты расширения XSLT</span><span class="sxs-lookup"><span data-stu-id="cd89d-152">XSLT Extension Objects</span></span>  

 <span data-ttu-id="cd89d-153">Объекты расширения XSLT добавляются в объект <xref:System.Xml.Xsl.XsltArgumentList> с помощью метода <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd89d-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="cd89d-154">В это время с объектом расширения связываются полное имя и URI-код пространства имен.</span><span class="sxs-lookup"><span data-stu-id="cd89d-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="cd89d-155">Во время добавления объекта вызывающий объект метода <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> должен иметь полное доверие в политике безопасности.</span><span class="sxs-lookup"><span data-stu-id="cd89d-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="cd89d-156">Если вызывающий объект обладает только частичным доверием, добавление объекта завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="cd89d-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="cd89d-157">Объект добавляется успешно, однако не гарантируется успешность его выполнения.</span><span class="sxs-lookup"><span data-stu-id="cd89d-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="cd89d-158">Во время вызова метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> вычисляются разрешения по свидетельству, указанному во время вызова метода <xref:System.Xml.Xsl.XslTransform.Load%2A>, и этот набор разрешений назначается для всего процесса преобразования.</span><span class="sxs-lookup"><span data-stu-id="cd89d-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="cd89d-159">Если объект расширения запускает действие, для которого необходимы разрешения, отсутствующие в наборе, вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="cd89d-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="cd89d-160">Объекты расширения возвращают один из четырех базовых типов данных XPath: number, string, Boolean и node set.</span><span class="sxs-lookup"><span data-stu-id="cd89d-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="cd89d-161">Чтобы использовать объект расширения XSLT, пользователь должен выполнить следующие действия</span><span class="sxs-lookup"><span data-stu-id="cd89d-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="cd89d-162">Создать объект <xref:System.Xml.Xsl.XsltArgumentList> и добавить объект расширения с помощью метода <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd89d-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2. <span data-ttu-id="cd89d-163">Вызвать объект расширения из таблицы стилей.</span><span class="sxs-lookup"><span data-stu-id="cd89d-163">Invoke the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="cd89d-164">Передать <xref:System.Xml.Xsl.XsltArgumentList> методу <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd89d-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="cd89d-165">Пример</span><span class="sxs-lookup"><span data-stu-id="cd89d-165">Example</span></span>  

 <span data-ttu-id="cd89d-166">В следующем примере вычисляется длина окружности по заданному радиусу.</span><span class="sxs-lookup"><span data-stu-id="cd89d-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="cd89d-167">Входные данные</span><span class="sxs-lookup"><span data-stu-id="cd89d-167">Input</span></span>  

 <span data-ttu-id="cd89d-168">number.xml</span><span class="sxs-lookup"><span data-stu-id="cd89d-168">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>
```  
  
 <span data-ttu-id="cd89d-169">circle.xsl</span><span class="sxs-lookup"><span data-stu-id="cd89d-169">circle.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="cd89d-170">Вывод</span><span class="sxs-lookup"><span data-stu-id="cd89d-170">Output</span></span>  

 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a><span data-ttu-id="cd89d-171">См. также</span><span class="sxs-lookup"><span data-stu-id="cd89d-171">See also</span></span>

- [<span data-ttu-id="cd89d-172">Реализация классом XslTransform XSLT-процессора</span><span class="sxs-lookup"><span data-stu-id="cd89d-172">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
