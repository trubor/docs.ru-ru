---
description: Дополнительные сведения см. в статье как загрузить XML из файла, строки или потока (Visual Basic)
title: Практическое руководство. Загрузка XML-кода из файла, строки или потока
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 375190642c93d929abe2ae10bb6ccba927e3bc8a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480067"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="9144e-103">Практическое руководство. Загрузка XML-кода из файла, строки или потока (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9144e-103">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="9144e-104">Можно создать [XML-литералы](../../../language-reference/xml-literals/index.md) и заполнить их содержимым из внешнего источника, например файла, строки или потока, с помощью нескольких методов.</span><span class="sxs-lookup"><span data-stu-id="9144e-104">You can create [XML Literals](../../../language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="9144e-105">Эти методы показаны в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="9144e-105">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="9144e-106">Загрузка XML из файла</span><span class="sxs-lookup"><span data-stu-id="9144e-106">To load XML from a file</span></span>

<span data-ttu-id="9144e-107">Чтобы заполнить XML-литерал <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> , например объект или, из файла, используйте `Load` метод.</span><span class="sxs-lookup"><span data-stu-id="9144e-107">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="9144e-108">Этот метод может принимать в качестве входных данных путь к файлу, поток текста или поток XML.</span><span class="sxs-lookup"><span data-stu-id="9144e-108">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="9144e-109">В следующем примере кода показано использование <xref:System.Xml.Linq.XDocument.Load%28System.String%29> метода для заполнения <xref:System.Xml.Linq.XDocument> объекта XML из текстового файла.</span><span class="sxs-lookup"><span data-stu-id="9144e-109">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="9144e-110">Загрузка XML из строки</span><span class="sxs-lookup"><span data-stu-id="9144e-110">To load XML from a string</span></span>

<span data-ttu-id="9144e-111">Для заполнения XML-литерала, такого как <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> объект или, из строки можно использовать `Parse` метод.</span><span class="sxs-lookup"><span data-stu-id="9144e-111">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="9144e-112">В следующем примере кода показано использование <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> метода для заполнения <xref:System.Xml.Linq.XDocument> объекта XML из строки.</span><span class="sxs-lookup"><span data-stu-id="9144e-112">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="9144e-113">Загрузка XML из потока</span><span class="sxs-lookup"><span data-stu-id="9144e-113">To load XML from a stream</span></span>

<span data-ttu-id="9144e-114">Для заполнения XML-литерала, такого как <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> объект или, из потока можно использовать `Load` метод или <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9144e-114">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9144e-115">В следующем примере кода показано использование <xref:System.Xml.Linq.XNode.ReadFrom%2A> метода для заполнения <xref:System.Xml.Linq.XDocument> объекта XML-потоком из XML-потока.</span><span class="sxs-lookup"><span data-stu-id="9144e-115">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="9144e-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9144e-116">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9144e-117">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="9144e-117">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="9144e-118">XML</span><span class="sxs-lookup"><span data-stu-id="9144e-118">XML</span></span>](index.md)
- [<span data-ttu-id="9144e-119">Обработка XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9144e-119">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
