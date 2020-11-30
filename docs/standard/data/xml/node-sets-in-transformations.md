---
title: Наборы узлов в преобразованиях
ms.date: 03/30/2017
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
ms.openlocfilehash: 2ace103d9721b2adecb08a25ab89cf9b0f05bb93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734118"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="56c89-102">Наборы узлов в преобразованиях</span><span class="sxs-lookup"><span data-stu-id="56c89-102">Node Sets in Transformations</span></span>

<span data-ttu-id="56c89-103">Наборы узлов - это один из четырех базовых типов данных, возвращаемых из выражений на языке XPath.</span><span class="sxs-lookup"><span data-stu-id="56c89-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="56c89-104">Набор узлов, представляющий собой неупорядоченную коллекцию узлов без повторов, созданную в порядке документа, может быть назначен переменной в таблице стилей.</span><span class="sxs-lookup"><span data-stu-id="56c89-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56c89-105">Класс <xref:System.Xml.Xsl.XslTransform> явлется устаревшим в версии .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="56c89-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="56c89-106">Можно выполнять XSLT-преобразование, используя класс <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="56c89-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="56c89-107">См. дополнительные сведения об [использовании класса XslCompiledTransform](using-the-xslcompiledtransform-class.md) и [миграции из класса XslTransform](migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="56c89-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="56c89-108">Наборы узлов - это один из четырех базовых типов данных, возвращаемых из выражений на языке XPath.</span><span class="sxs-lookup"><span data-stu-id="56c89-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="56c89-109">Набор узлов, представляющий собой неупорядоченную коллекцию узлов без повторов, созданную в порядке документа, может быть назначен переменной в таблице стилей.</span><span class="sxs-lookup"><span data-stu-id="56c89-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="56c89-110">Этот набор узлов, являющийся результатом выражения XPath, которое используется в атрибуте `select` при преобразовании, имеет такое же поведение, как и набор узлов из модели DOM.</span><span class="sxs-lookup"><span data-stu-id="56c89-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="56c89-111">[Перемещаться по набору узлов можно с помощью XPathNavigator](node-set-navigation-using-xpathnavigator.md), в отличие от фрагментов результирующего дерева, которые для перехода используют <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="56c89-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="56c89-112">Следующий образец кода демонстрирует, как проходить по набору узлов, если результатом вычисления элемента `variable` или `parameter` в таблице стилей является набор узлов.</span><span class="sxs-lookup"><span data-stu-id="56c89-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="56c89-113">Таблица стилей</span><span class="sxs-lookup"><span data-stu-id="56c89-113">Style Sheet</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a><span data-ttu-id="56c89-114">Входные данные</span><span class="sxs-lookup"><span data-stu-id="56c89-114">Input</span></span>  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a><span data-ttu-id="56c89-115">Вывод</span><span class="sxs-lookup"><span data-stu-id="56c89-115">Output</span></span>  
  
```output  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a><span data-ttu-id="56c89-116">См. также</span><span class="sxs-lookup"><span data-stu-id="56c89-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="56c89-117">XSLT-преобразования с помощью класса XslTransform</span><span class="sxs-lookup"><span data-stu-id="56c89-117">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="56c89-118">Реализация классом XslTransform XSLT-процессора</span><span class="sxs-lookup"><span data-stu-id="56c89-118">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
