---
title: Сохранение и запись документа
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 14497bb5b027209c4707eab9bcf1b60f85740dfd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697562"
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="76a51-102">Сохранение и запись документа</span><span class="sxs-lookup"><span data-stu-id="76a51-102">Saving and Writing a Document</span></span>

<span data-ttu-id="76a51-103">При загрузке и сохранении <xref:System.Xml.XmlDocument> между сохраненным и исходным документами возможны следующие различия:</span><span class="sxs-lookup"><span data-stu-id="76a51-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
- <span data-ttu-id="76a51-104">Если свойство <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> имеет значение `true` перед вызовом метода <xref:System.Xml.XmlDocument.Save%2A>, то пробелы в документе при выводе сохраняются. Если свойство имеет значение `false`, то <xref:System.Xml.XmlDocument> автоматически вставляет отступы в выходные данные.</span><span class="sxs-lookup"><span data-stu-id="76a51-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
- <span data-ttu-id="76a51-105">Все пробелы между атрибутами сокращаются до одного символа пробела.</span><span class="sxs-lookup"><span data-stu-id="76a51-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
- <span data-ttu-id="76a51-106">Пробелы между элементами изменяются.</span><span class="sxs-lookup"><span data-stu-id="76a51-106">The white space between elements is changed.</span></span> <span data-ttu-id="76a51-107">Значащие пробелы сохраняются, а незначащие - нет.</span><span class="sxs-lookup"><span data-stu-id="76a51-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="76a51-108">Но при сохранении документа по умолчанию используется режим <xref:System.Xml.XmlTextWriter> **Отступ**, обеспечивающий аккуратный внешний вид при печати и удобство чтения.</span><span class="sxs-lookup"><span data-stu-id="76a51-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
- <span data-ttu-id="76a51-109">Символ кавычки вокруг значений атрибута по умолчанию заменяется символом двойной кавычки.</span><span class="sxs-lookup"><span data-stu-id="76a51-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="76a51-110">Выбрать в качестве символа кавычки двойную кавычку или одинарную кавычку можно с помощью свойства <xref:System.Xml.XmlTextReader.QuoteChar%2A> класса <xref:System.Xml.XmlTextWriter>.</span><span class="sxs-lookup"><span data-stu-id="76a51-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
- <span data-ttu-id="76a51-111">По умолчанию символы числовых сущностей, например `{`, развертываются.</span><span class="sxs-lookup"><span data-stu-id="76a51-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
- <span data-ttu-id="76a51-112">Значение отметки порядка байт во входном документе не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="76a51-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="76a51-113">UCS-2 сохраняется как UTF-8, если явно не создана XML-декларация, указывающая другую кодировку.</span><span class="sxs-lookup"><span data-stu-id="76a51-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
- <span data-ttu-id="76a51-114">Если требуется записать <xref:System.Xml.XmlDocument> в файл или поток, то записываемые выходные данные не будут отличаться от содержимого документа.</span><span class="sxs-lookup"><span data-stu-id="76a51-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="76a51-115">То есть, <xref:System.Xml.XmlDeclaration> записывается только если объявление содержится в документе, а кодировка, используемая при записи документа, совпадает с указанной в узле декларации.</span><span class="sxs-lookup"><span data-stu-id="76a51-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="76a51-116">Запись XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="76a51-116">Writing an XmlDeclaration</span></span>  

 <span data-ttu-id="76a51-117">XML-декларацию создают члены <xref:System.Xml.XmlDocument> и элементы <xref:System.Xml.XmlDeclaration> классов <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, метод <xref:System.Xml.XmlNode.WriteTo%2A>, а также методы <xref:System.Xml.XmlDocument> и <xref:System.Xml.XmlDocument.Save%2A> класса <xref:System.Xml.XmlDocument.WriteContentTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="76a51-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="76a51-118">Для свойств <xref:System.Xml.XmlDocument> методов <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, а также методов <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A> и <xref:System.Xml.XmlDocument.WriteContentTo%2A> кодировка, записываемая в XML-декларацию, берется из узла <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="76a51-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="76a51-119">Если узел <xref:System.Xml.XmlDeclaration> отсутствует, то <xref:System.Xml.XmlDeclaration> не записывается. Если в узле <xref:System.Xml.XmlDeclaration> нет кодировки, то кодировка не записывается в XML-декларацию.</span><span class="sxs-lookup"><span data-stu-id="76a51-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="76a51-120">Методы <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> и <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> всегда записывают <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="76a51-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="76a51-121">Они получают кодировку из модуля, в который производится запись.</span><span class="sxs-lookup"><span data-stu-id="76a51-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="76a51-122">То есть, кодовое значение модуля записи переопределяет кодировку в документе и в <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="76a51-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="76a51-123">Например, приведенный ниже код не записывает кодировку в XML-декларацию, находящуюся в выходном файле `out.xml`.</span><span class="sxs-lookup"><span data-stu-id="76a51-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="76a51-124">Для метода <xref:System.Xml.XmlDocument.Save%2A> XML-декларация записывается с помощью метода <xref:System.Xml.XmlWriter.WriteStartDocument%2A> класса <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="76a51-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="76a51-125">Поэтому при перезаписи метода <xref:System.Xml.XmlWriter.WriteStartDocument%2A> изменяется способ записи начала документа.</span><span class="sxs-lookup"><span data-stu-id="76a51-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="76a51-126">Если для элементов <xref:System.Xml.XmlDeclaration> в <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A> и <xref:System.Xml.XmlNode.InnerXml%2A> не установлено свойство <xref:System.Xml.XmlDeclaration.Encoding%2A>, то кодировка не записывается. В противном случае кодировка, записанная в XML-декларацию, не отличается от кодировки в свойстве <xref:System.Xml.XmlDeclaration.Encoding%2A>.</span><span class="sxs-lookup"><span data-stu-id="76a51-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="76a51-127">Запись содержимого документа с помощью свойства OuterXml</span><span class="sxs-lookup"><span data-stu-id="76a51-127">Writing Document Content Using the OuterXml Property</span></span>  

 <span data-ttu-id="76a51-128">Свойство <xref:System.Xml.XmlNode.OuterXml%2A> является расширением Майкрософт для стандартов объектной модели DOM XML-документа консорциума W3C.</span><span class="sxs-lookup"><span data-stu-id="76a51-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="76a51-129">Свойство <xref:System.Xml.XmlNode.OuterXml%2A> позволяет получить разметку как полного XML-документа, так и единичного узла вместе с его дочерними узлами.</span><span class="sxs-lookup"><span data-stu-id="76a51-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="76a51-130">Свойство <xref:System.Xml.XmlNode.OuterXml%2A> возвращает разметку, предоставляющую заданный узел и все его дочерние узлы.</span><span class="sxs-lookup"><span data-stu-id="76a51-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="76a51-131">В приведенном ниже образце кода показано сохранение документа целиком в виде строки.</span><span class="sxs-lookup"><span data-stu-id="76a51-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="76a51-132">В следующем образце кода показано, как сохранить только отдельный элемент документа.</span><span class="sxs-lookup"><span data-stu-id="76a51-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="76a51-133">Однако если требуется содержимое дочерних узлов, можно использовать свойство <xref:System.Xml.XmlNode.InnerText%2A>.</span><span class="sxs-lookup"><span data-stu-id="76a51-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a51-134">См. также</span><span class="sxs-lookup"><span data-stu-id="76a51-134">See also</span></span>

- [<span data-ttu-id="76a51-135">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="76a51-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
