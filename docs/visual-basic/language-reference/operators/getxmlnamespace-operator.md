---
description: 'Дополнительные сведения о операторе: GetXmlNamespace (Visual Basic)'
title: Оператор GetXmlNamespace
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 704ac22493a0d6ce1255d171ae3b418313b74f09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665917"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="b5835-103">Оператор GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5835-103">GetXmlNamespace Operator (Visual Basic)</span></span>

<span data-ttu-id="b5835-104">Возвращает <xref:System.Xml.Linq.XNamespace> объект, соответствующий указанному префиксу пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="b5835-104">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5835-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b5835-105">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="b5835-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="b5835-106">Parts</span></span>  

 `xmlNamespacePrefix`  
 <span data-ttu-id="b5835-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b5835-107">Optional.</span></span> <span data-ttu-id="b5835-108">Строка, определяющая префикс пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="b5835-108">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="b5835-109">Если указано, эта строка должна быть допустимым идентификатором XML.</span><span class="sxs-lookup"><span data-stu-id="b5835-109">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="b5835-110">Дополнительные сведения см. в разделе [Имена объявленных XML-элементов и атрибутов](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b5835-110">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="b5835-111">Если префикс не указан, возвращается пространство имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b5835-111">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="b5835-112">Если пространство имен по умолчанию не указано, возвращается пустое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="b5835-112">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5835-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b5835-113">Return Value</span></span>  

 <span data-ttu-id="b5835-114"><xref:System.Xml.Linq.XNamespace>Объект, соответствующий префиксу пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="b5835-114">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5835-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="b5835-115">Remarks</span></span>  

 <span data-ttu-id="b5835-116">`GetXmlNamespace`Оператор возвращает <xref:System.Xml.Linq.XNamespace> объект, соответствующий префиксу пространства имен XML `xmlNamespacePrefix` .</span><span class="sxs-lookup"><span data-stu-id="b5835-116">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="b5835-117">Префиксы пространства имен XML можно использовать непосредственно в XML-литералах и свойствах осей XML.</span><span class="sxs-lookup"><span data-stu-id="b5835-117">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="b5835-118">Однако необходимо использовать `GetXmlNamespace` оператор для преобразования префикса пространства имен в <xref:System.Xml.Linq.XNamespace> объект, прежде чем его можно будет использовать в коде.</span><span class="sxs-lookup"><span data-stu-id="b5835-118">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="b5835-119">К объекту можно добавить неполное имя элемента <xref:System.Xml.Linq.XNamespace> для получения полного <xref:System.Xml.Linq.XName> объекта, который [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] требуется многим методам.</span><span class="sxs-lookup"><span data-stu-id="b5835-119">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5835-120">Пример</span><span class="sxs-lookup"><span data-stu-id="b5835-120">Example</span></span>  

 <span data-ttu-id="b5835-121">В следующем примере `ns` выполняется импорт в виде префикса пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="b5835-121">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b5835-122">Затем он использует префикс пространства имен для создания XML-литерала и доступа к первому дочернему узлу с полным именем `ns:phone` .</span><span class="sxs-lookup"><span data-stu-id="b5835-122">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="b5835-123">Затем он передает этот дочерний узел в `ShowName` подпрограммы, которая конструирует полное имя с помощью `GetXmlNamespace` оператора.</span><span class="sxs-lookup"><span data-stu-id="b5835-123">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="b5835-124">`ShowName`Затем подподпрограмма передает полное имя <xref:System.Xml.Linq.XNode.Ancestors%2A> методу, чтобы получить родительский `ns:contact` узел.</span><span class="sxs-lookup"><span data-stu-id="b5835-124">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="b5835-125">При вызове `TestGetXmlNamespace.RunSample()` отображается окно сообщения, содержащее следующий текст:</span><span class="sxs-lookup"><span data-stu-id="b5835-125">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="b5835-126">См. также</span><span class="sxs-lookup"><span data-stu-id="b5835-126">See also</span></span>

- [<span data-ttu-id="b5835-127">Оператор Imports (пространство имен XML)</span><span class="sxs-lookup"><span data-stu-id="b5835-127">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="b5835-128">Доступ к XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5835-128">Accessing XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/accessing-xml.md)
