---
title: Выбор, вычисление и отбор XML-данных с помощью XPathNavigator
ms.date: 03/30/2017
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
ms.openlocfilehash: 3096582055dc17d5724cebd79e74d2aa24154bcb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734677"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="ca268-102">Выбор, вычисление и отбор XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ca268-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>

<span data-ttu-id="ca268-103">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет методы для выбора узлов в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> с помощью запроса XPath, проверки и анализа результатов выражения XPath и определения соответствия узла в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> данному выражению XPath.</span><span class="sxs-lookup"><span data-stu-id="ca268-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="ca268-104">Эти и другие основные понятия, связанные с выбором, оценкой и сопоставлением узлов в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument>, описаны в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="ca268-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca268-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="ca268-105">In This Section</span></span>  

 [<span data-ttu-id="ca268-106">Выборка XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ca268-106">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="ca268-107">Описывает набор методов класса <xref:System.Xml.XPath.XPathNavigator>, используемых для выбора набора узлов в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> с помощью выражения XPath.</span><span class="sxs-lookup"><span data-stu-id="ca268-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="ca268-108">Вычисление выражения XPath с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ca268-108">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="ca268-109">Описывает метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> класса <xref:System.Xml.XPath.XPathNavigator>, используемый для оценки выражения XPath.</span><span class="sxs-lookup"><span data-stu-id="ca268-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="ca268-110">Соответствие узлов с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ca268-110">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="ca268-111">Описывает метод <xref:System.Xml.XPath.XPathNavigator.Matches%2A> класса <xref:System.Xml.XPath.XPathNavigator>, используемый, чтобы определить соответствие узла выражению XPath.</span><span class="sxs-lookup"><span data-stu-id="ca268-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="ca268-112">Типы узлов, распознаваемые запросами XPath</span><span class="sxs-lookup"><span data-stu-id="ca268-112">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="ca268-113">Описывает типы узлов, распознаваемых в запросе XPath.</span><span class="sxs-lookup"><span data-stu-id="ca268-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="ca268-114">Запросы XPath и пространства имен</span><span class="sxs-lookup"><span data-stu-id="ca268-114">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)  
 <span data-ttu-id="ca268-115">Описывает типы пространств имен в запросе XPath.</span><span class="sxs-lookup"><span data-stu-id="ca268-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="ca268-116">Скомпилированные выражения XPath</span><span class="sxs-lookup"><span data-stu-id="ca268-116">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)  
 <span data-ttu-id="ca268-117">Описывает класс <xref:System.Xml.XPath.XPathExpression>, который представляет скомпилированный запрос XPath.</span><span class="sxs-lookup"><span data-stu-id="ca268-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca268-118">См. также</span><span class="sxs-lookup"><span data-stu-id="ca268-118">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="ca268-119">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="ca268-119">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="ca268-120">Чтение XML-данных с помощью XPathDocument и XmlDocument</span><span class="sxs-lookup"><span data-stu-id="ca268-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="ca268-121">Доступ к XML-данным с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ca268-121">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="ca268-122">Изменение XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ca268-122">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="ca268-123">Проверка по схеме с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ca268-123">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
