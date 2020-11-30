---
title: Обработка событий в XML-документе с помощью XmlNodeChangedEventArgs
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
ms.openlocfilehash: 78984c74b6e7eedf4214506dec36509ece7ae48d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676690"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a><span data-ttu-id="a62dc-102">Обработка событий в XML-документе с помощью XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="a62dc-102">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>

<span data-ttu-id="a62dc-103">Класс **XmlNodeChangedEventArgs** инкапсулирует аргументы, передаваемые обработчикам событий, которые зарегистрированы в объекте **XmlDocument** для обработки событий.</span><span class="sxs-lookup"><span data-stu-id="a62dc-103">The **XmlNodeChangedEventArgs** encapsulates the arguments passed to the event handlers registered on the **XmlDocument** object for handling events.</span></span> <span data-ttu-id="a62dc-104">События и описания условий их срабатывания приведены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="a62dc-104">The events and a description of when they are fired is given in the following table.</span></span>  
  
|<span data-ttu-id="a62dc-105">событие</span><span class="sxs-lookup"><span data-stu-id="a62dc-105">Event</span></span>|<span data-ttu-id="a62dc-106">Срабатывание</span><span class="sxs-lookup"><span data-stu-id="a62dc-106">Fired</span></span>|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|<span data-ttu-id="a62dc-107">Перед вставкой узла, принадлежащего текущему документу, в другой узел.</span><span class="sxs-lookup"><span data-stu-id="a62dc-107">When a node belonging to the current document is about to be inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeInserted>|<span data-ttu-id="a62dc-108">После вставки узла, принадлежащего текущему документу, в другой узел.</span><span class="sxs-lookup"><span data-stu-id="a62dc-108">When a node belonging to the current document has been inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|<span data-ttu-id="a62dc-109">Перед удалением узла, принадлежащего этому документу, из документа.</span><span class="sxs-lookup"><span data-stu-id="a62dc-109">When a node belonging to this document is about to be removed from the document.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|<span data-ttu-id="a62dc-110">После удаления узла, принадлежащего этому документу, из родителя.</span><span class="sxs-lookup"><span data-stu-id="a62dc-110">When a node belonging to this document has been removed from its parent.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanging>|<span data-ttu-id="a62dc-111">Перед изменением значения узла.</span><span class="sxs-lookup"><span data-stu-id="a62dc-111">When the value of a node is about to be changed.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanged>|<span data-ttu-id="a62dc-112">После изменения значения узла.</span><span class="sxs-lookup"><span data-stu-id="a62dc-112">When the value of a node has been changed.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a62dc-113">Если использование памяти **XmlDataDocument** полностью оптимизировано для работы хранилища **DataSet**, **XmlDataDocument** может не инициировать приведенные выше события при внесении изменений в базовом хранилище **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a62dc-113">If the **XmlDataDocument** memory usage is fully optimized to use **DataSet** storage, the **XmlDataDocument** might not raise any of the events listed above when changes are made to the underlying **DataSet**.</span></span> <span data-ttu-id="a62dc-114">Если вам нужны эти события, просмотрите один раз весь **XmlDocument**, чтобы полностью оптимизировать использование памяти.</span><span class="sxs-lookup"><span data-stu-id="a62dc-114">If you need these events, you must traverse the whole **XmlDocument** once to make the memory usage non-fully optimized.</span></span>  
  
 <span data-ttu-id="a62dc-115">В следующем примере кода показано, как определить обработчик событий, и как добавить его к событию.</span><span class="sxs-lookup"><span data-stu-id="a62dc-115">The following code example shows how to define an event handler and how to add the event handler to an event.</span></span>  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)
AddHandler doc.NodeInserted, XmlNodeChgEHdlr
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 <span data-ttu-id="a62dc-116">Некоторые операции модели DOM представляют собой составные операции, которые могут вызвать срабатывание нескольких событий.</span><span class="sxs-lookup"><span data-stu-id="a62dc-116">Some XML Document Object Model (DOM) operations are compound operations that can result in multiple events being fired.</span></span> <span data-ttu-id="a62dc-117">Например, **AppendChild** может также удалить узел, добавляемый из его предыдущего родительского узла.</span><span class="sxs-lookup"><span data-stu-id="a62dc-117">For example, **AppendChild** may also have to remove the node being appended from its previous parent.</span></span> <span data-ttu-id="a62dc-118">В этом случае сначала активируется событие **NodeRemoved**, а затем — событие **NodeInserted**.</span><span class="sxs-lookup"><span data-stu-id="a62dc-118">In this case, you see a **NodeRemoved** event fired first, followed by a **NodeInserted** event.</span></span> <span data-ttu-id="a62dc-119">Такие операции, как настройка **InnerXml**, могут вызывать активацию нескольких событий.</span><span class="sxs-lookup"><span data-stu-id="a62dc-119">Operations like setting **InnerXml** could result in multiple events.</span></span>  
  
 <span data-ttu-id="a62dc-120">В следующем примере кода показано создание обработчика события и обработка события **NodeInserted**.</span><span class="sxs-lookup"><span data-stu-id="a62dc-120">The following code example shows the creation of the event handler and the handling of the **NodeInserted** event.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class
```  
  
 <span data-ttu-id="a62dc-121">Дополнительные сведения см. в разделах <xref:System.Xml.XmlNodeChangedEventArgs> и <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="a62dc-121">For more information, see <xref:System.Xml.XmlNodeChangedEventArgs> and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62dc-122">См. также</span><span class="sxs-lookup"><span data-stu-id="a62dc-122">See also</span></span>

- [<span data-ttu-id="a62dc-123">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="a62dc-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
