---
title: Считывание XML-документа в DOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 61275e9232b3d9e516636869d7153f33133cbd03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686869"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="014bd-102">Считывание XML-документа в DOM</span><span class="sxs-lookup"><span data-stu-id="014bd-102">Reading an XML Document into the DOM</span></span>

<span data-ttu-id="014bd-103">XML-данные считываются в память из разных форматов.</span><span class="sxs-lookup"><span data-stu-id="014bd-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="014bd-104">Они могут быть считаны из строки, URL-адреса, модуля чтения текста или класса, производного от класса <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="014bd-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="014bd-105">Метод <xref:System.Xml.XmlDocument.Load%2A> загружает документ в память и имеет перегруженные методы для получения данных из разных форматов.</span><span class="sxs-lookup"><span data-stu-id="014bd-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="014bd-106">Существует также метод <xref:System.Xml.XmlDocument.LoadXml%2A>, который считывает XML-данные из строки.</span><span class="sxs-lookup"><span data-stu-id="014bd-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="014bd-107">Разные методы <xref:System.Xml.XmlDocument.Load%2A> влияют на то, какие узлы создаются при загрузке модели DOM.</span><span class="sxs-lookup"><span data-stu-id="014bd-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="014bd-108">В следующей таблице приведены различия между некоторыми методами <xref:System.Xml.XmlDocument.Load%2A>, а также ссылки на разделы, описывающие их.</span><span class="sxs-lookup"><span data-stu-id="014bd-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="014bd-109">Субъект</span><span class="sxs-lookup"><span data-stu-id="014bd-109">Subject</span></span>|<span data-ttu-id="014bd-110">Раздел</span><span class="sxs-lookup"><span data-stu-id="014bd-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="014bd-111">Создание узлов пробелов</span><span class="sxs-lookup"><span data-stu-id="014bd-111">Creation of white space nodes</span></span>|<span data-ttu-id="014bd-112">Объект, используемый для загрузки модели DOM, влияет на узлы пробелов и значащих пробелов, формируемые в модели DOM.</span><span class="sxs-lookup"><span data-stu-id="014bd-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="014bd-113">Дополнительные сведения см. в руководстве по [обработке незначимых и значимых пробелов при загрузке модели DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="014bd-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="014bd-114">Загрузка XML-данных, начиная с определенного узла, или загрузка всего XML-документа</span><span class="sxs-lookup"><span data-stu-id="014bd-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="014bd-115">С помощью метода <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> данные в модель DOM можно загружать с определенного узла.</span><span class="sxs-lookup"><span data-stu-id="014bd-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="014bd-116">Дополнительные сведения см. в руководстве по [загрузке данных из модуля чтения](load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="014bd-116">For more information, see [Load Data from a Reader](load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="014bd-117">Проверка XML-данных по мере загрузки</span><span class="sxs-lookup"><span data-stu-id="014bd-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="014bd-118">Можно проводить проверку XML-данных, загружаемых в модель DOM, по мере их загрузки.</span><span class="sxs-lookup"><span data-stu-id="014bd-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="014bd-119">Делается это с помощью проверяющего объекта <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="014bd-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="014bd-120">Дополнительные сведения о проверке XML-данных по мере их загрузки см. в руководстве по [проверке документа XML в модели DOM](validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="014bd-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="014bd-121">В следующем примере показаны XML-данные, загружаемые с помощью метода <xref:System.Xml.XmlDocument.LoadXml%2A>, а также данные, которые затем сохраняются в текстовый файл `data.xml`.</span><span class="sxs-lookup"><span data-stu-id="014bd-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="014bd-122">См. также</span><span class="sxs-lookup"><span data-stu-id="014bd-122">See also</span></span>

- [<span data-ttu-id="014bd-123">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="014bd-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
