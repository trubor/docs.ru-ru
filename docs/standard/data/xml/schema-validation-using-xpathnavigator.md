---
title: Проверка по схеме с помощью XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: 1c91dfa63723cc087662630232376e74394c7b13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734703"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="cc18a-102">Проверка по схеме с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cc18a-102">Schema Validation using XPathNavigator</span></span>

<span data-ttu-id="cc18a-103">С помощью класса <xref:System.Xml.XmlDocument> можно проверять XML-содержимое в объекте <xref:System.Xml.XmlDocument> двумя способами.</span><span class="sxs-lookup"><span data-stu-id="cc18a-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="cc18a-104">Первый способ проверки XML- содержимого заключается в использовании проверяющего объекта <xref:System.Xml.XmlReader>, а второй - в вызове метода <xref:System.Xml.XmlDocument.Validate%2A> класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="cc18a-105">Можно также выполнить проверку XML-содержимого «только для чтения» с помощью класса <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="cc18a-106">Проверка XML-данных</span><span class="sxs-lookup"><span data-stu-id="cc18a-106">Validating XML Data</span></span>  

 <span data-ttu-id="cc18a-107">Класс <xref:System.Xml.XmlDocument> по умолчанию не выполняет проверку XML-документа с помощью определения DTD или XSD.</span><span class="sxs-lookup"><span data-stu-id="cc18a-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="cc18a-108">Он только проверяет правильность формата XML-документа.</span><span class="sxs-lookup"><span data-stu-id="cc18a-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="cc18a-109">Первый способ проверки XML-документа заключается в его проверке при загрузке в объект <xref:System.Xml.XmlDocument> с помощью проверяющего объекта <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="cc18a-110">Второй способ состоит в проверке ранее нетипизированного XML-документа с помощью метода <xref:System.Xml.XmlDocument.Validate%2A> класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="cc18a-111">В обоих случаях изменения в проверяемом XML-документе можно проверить повторно с помощью метода <xref:System.Xml.XmlDocument.Validate%2A> класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="cc18a-112">Проверка документа при загрузке</span><span class="sxs-lookup"><span data-stu-id="cc18a-112">Validating a Document as it is Loaded</span></span>  

 <span data-ttu-id="cc18a-113">Проверочный объект <xref:System.Xml.XmlReader> создается путем передачи объекта <xref:System.Xml.XmlReaderSettings> методу <xref:System.Xml.XmlReader.Create%2A> класса <xref:System.Xml.XmlReader>, который принимает объект <xref:System.Xml.XmlReaderSettings> в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="cc18a-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="cc18a-114">Свойство <xref:System.Xml.XmlReaderSettings> объекта <xref:System.Xml.XmlReaderSettings.ValidationType%2A>, переданного в качестве параметра, имеет значение `Schema`, а схема XML для XML-документа, содержащегося в объекте <xref:System.Xml.XmlDocument>, добавляется к его свойству <xref:System.Xml.XmlReaderSettings.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="cc18a-115">После этого проверочный объект <xref:System.Xml.XmlReader> используется для создания объекта <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="cc18a-116">В следующем примере выполняется проверка файла `contosoBooks.xml`, загруженного в объект <xref:System.Xml.XmlDocument> путем создания объекта <xref:System.Xml.XmlDocument> с помощью проверяющего объекта <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="cc18a-117">Поскольку XML-документ допустим в соответствии со своей схемой, ошибки или предупреждения проверки не формируются.</span><span class="sxs-lookup"><span data-stu-id="cc18a-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cc18a-118">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="cc18a-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="cc18a-119">В примере также в качестве входных данных используется `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="cc18a-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="cc18a-120">В приведенном выше примере при вызове метода <xref:System.Xml.Schema.XmlSchemaValidationException> возникает исключение <xref:System.Xml.XmlDocument.Load%2A>, если какой-либо атрибут или тип элемента не соответствует типу, указанному в проверочной схеме.</span><span class="sxs-lookup"><span data-stu-id="cc18a-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="cc18a-121">Если <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> установлен на проверяющий объект <xref:System.Xml.XmlReader>, метод <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> будет вызываться для каждого недопустимого типа.</span><span class="sxs-lookup"><span data-stu-id="cc18a-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="cc18a-122">Исключение <xref:System.Xml.Schema.XmlSchemaException> возникает, если объект <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> выполняет доступ к атрибуту или элементу, у которого свойство `invalid` имеет значение <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="cc18a-123">Свойство <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> можно использовать для определения допустимости отдельного атрибута или элемента при их оценке с помощью объекта <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc18a-124">Если XML-документ загружается в объект <xref:System.Xml.XmlDocument> со связанной схемой, определяющей значения по умолчанию, объект <xref:System.Xml.XmlDocument> рассматривает их как значения по умолчанию XML-документа.</span><span class="sxs-lookup"><span data-stu-id="cc18a-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="cc18a-125">Это означает, что свойство <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> всегда возвращает значение `false` для элемента, получившего значения по умолчанию из схемы, даже если в XML-документе это был пустой элемент.</span><span class="sxs-lookup"><span data-stu-id="cc18a-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="cc18a-126">Проверка документа с помощью метода Validate</span><span class="sxs-lookup"><span data-stu-id="cc18a-126">Validating a Document using the Validate Method</span></span>  

 <span data-ttu-id="cc18a-127">Метод <xref:System.Xml.XmlDocument.Validate%2A> класса <xref:System.Xml.XmlDocument> проверяет XML-документ, содержащийся в объекте <xref:System.Xml.XmlDocument>, по схеме, указанной в свойстве <xref:System.Xml.XmlDocument> объекта <xref:System.Xml.XmlDocument.Schemas%2A>, и выполняет приращение информационного набора.</span><span class="sxs-lookup"><span data-stu-id="cc18a-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="cc18a-128">Результатом является замена в объекте <xref:System.Xml.XmlDocument> ранее нетипизированного XML-документа типизированным документом.</span><span class="sxs-lookup"><span data-stu-id="cc18a-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="cc18a-129">Объект <xref:System.Xml.XmlDocument> сообщает об ошибках и предупреждениях проверки схемы с помощью делегата <xref:System.Xml.Schema.ValidationEventHandler>, передаваемого в качестве параметра методу <xref:System.Xml.XmlDocument.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="cc18a-130">Следующий пример проверяет файл `contosoBooks.xml`, содержащийся в объекте <xref:System.Xml.XmlDocument> по схеме `contosoBooks.xsd`, содержащейся в свойстве <xref:System.Xml.XmlDocument> объекта <xref:System.Xml.XmlDocument.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cc18a-131">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="cc18a-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="cc18a-132">В примере также в качестве входных данных используется `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="cc18a-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="cc18a-133">Проверка изменений</span><span class="sxs-lookup"><span data-stu-id="cc18a-133">Validating Modifications</span></span>  

 <span data-ttu-id="cc18a-134">После внесения изменений в XML-документ можно проверить эти изменения по схеме XML-документа с помощью метода <xref:System.Xml.XmlDocument.Validate%2A> класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="cc18a-135">В следующем примере выполняется проверка файла `contosoBooks.xml`, загруженного в объект <xref:System.Xml.XmlDocument> путем создания объекта <xref:System.Xml.XmlDocument> с помощью проверяющего объекта <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="cc18a-136">XML-документ успешно проходит проверку во время загрузки без формирования ошибок и предупреждений проверки схемы.</span><span class="sxs-lookup"><span data-stu-id="cc18a-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="cc18a-137">Затем пример выполняет два изменения в XML-документе, недопустимых по схеме `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="cc18a-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="cc18a-138">Первое изменение вставляет недопустимый дочерний элемент, что приводит к ошибке проверки схемы. Второе изменение присваивает значение типизированному узлу, недопустимое с точки зрения типа узла, что вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="cc18a-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cc18a-139">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="cc18a-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="cc18a-140">В примере также в качестве входных данных используется `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="cc18a-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="cc18a-141">В приведенном выше примере в XML-документ, содержащийся в объекте <xref:System.Xml.XmlDocument>, вносятся два изменения.</span><span class="sxs-lookup"><span data-stu-id="cc18a-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="cc18a-142">Во время загрузки этого XML-документа все ошибки проверки схемы будут обрабатываться методом обработчика события проверки и выводиться на консоль.</span><span class="sxs-lookup"><span data-stu-id="cc18a-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="cc18a-143">В этом примере ошибки проверки возникли после загрузки XML-документа и были обнаружены методом <xref:System.Xml.XmlDocument.Validate%2A> класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="cc18a-144">Изменения, сделанные методом <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> класса <xref:System.Xml.XPath.XPathNavigator>, вызвали исключение <xref:System.InvalidCastException>, поскольку новое значение недопустимо с точки зрения типа схемы узла.</span><span class="sxs-lookup"><span data-stu-id="cc18a-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="cc18a-145">Дополнительные сведения об изменении значений с помощью метода <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> см. в руководстве по [изменению данных XML с помощью XPathNavigator](modify-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="cc18a-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="cc18a-146">Проверка «только для чтения»</span><span class="sxs-lookup"><span data-stu-id="cc18a-146">Read-Only Validation</span></span>  

 <span data-ttu-id="cc18a-147">Класс <xref:System.Xml.XPath.XPathDocument> является доступным только для чтения, хранящимся в памяти представлением XML-документа.</span><span class="sxs-lookup"><span data-stu-id="cc18a-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="cc18a-148">Классы <xref:System.Xml.XPath.XPathDocument> и <xref:System.Xml.XmlDocument> создают объекты <xref:System.Xml.XPath.XPathNavigator> для перехода по XML-документам и их изменения.</span><span class="sxs-lookup"><span data-stu-id="cc18a-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="cc18a-149">Поскольку класс <xref:System.Xml.XPath.XPathDocument> доступен только для чтения, объект <xref:System.Xml.XPath.XPathNavigator>, возвращенный из объекта <xref:System.Xml.XPath.XPathDocument>, не может изменять XML-документ, содержащийся в объекте <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc18a-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="cc18a-150">Для проверки можно создать объект <xref:System.Xml.XPath.XPathDocument> точно так же, как создается объект <xref:System.Xml.XmlDocument>, используя проверяющий объект <xref:System.Xml.XmlReader>, как описано выше в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="cc18a-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="cc18a-151">Объект <xref:System.Xml.XPath.XPathDocument> проверяет XML-документ во время загрузки, но, поскольку в объекте <xref:System.Xml.XPath.XPathDocument> нельзя изменять XML-данные, повторно проверить этот XML-документ невозможно.</span><span class="sxs-lookup"><span data-stu-id="cc18a-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="cc18a-152">Дополнительные сведения о доступных только для чтения и изменяемых объектах <xref:System.Xml.XPath.XPathNavigator> см. в руководстве по [чтению данных XML с помощью XPathDocument и XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="cc18a-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc18a-153">См. также</span><span class="sxs-lookup"><span data-stu-id="cc18a-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="cc18a-154">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="cc18a-154">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="cc18a-155">Чтение XML-данных с помощью XPathDocument и XmlDocument</span><span class="sxs-lookup"><span data-stu-id="cc18a-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="cc18a-156">Выбор, вычисление и отбор XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cc18a-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="cc18a-157">Доступ к XML-данным с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cc18a-157">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="cc18a-158">Изменение XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cc18a-158">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
