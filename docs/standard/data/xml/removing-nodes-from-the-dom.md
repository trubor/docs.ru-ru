---
title: Удаление узлов из DOM
ms.date: 03/30/2017
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: 5b1a6dfb2da4556e0332441a8e56679aee37a091
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686661"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="91153-102">Удаление узлов из DOM</span><span class="sxs-lookup"><span data-stu-id="91153-102">Removing Nodes from the DOM</span></span>

<span data-ttu-id="91153-103">Для удаления узла из модели DOM XML-документа используется метод <xref:System.Xml.XmlNode.RemoveChild%2A>, с помощью которого удаляется конкретный узел.</span><span class="sxs-lookup"><span data-stu-id="91153-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="91153-104">При удалении узла метод удаляет поддерево, принадлежащее удаляемому узлу т.е. если это не конечный узел.</span><span class="sxs-lookup"><span data-stu-id="91153-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="91153-105">Для удаления нескольких узлов из DOM используется метод <xref:System.Xml.XmlNode.RemoveAll%2A>, удаляющий все дочерние узлы и атрибуты (если применимо) текущего узла.</span><span class="sxs-lookup"><span data-stu-id="91153-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="91153-106">При работе с классом <xref:System.Xml.XmlNamedNodeMap> можно удалить узел с помощью метода <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="91153-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="91153-107">См. дополнительные сведения оь [удалении атрибутов из узла элемента в DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="91153-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91153-108">См. также</span><span class="sxs-lookup"><span data-stu-id="91153-108">See also</span></span>

- [<span data-ttu-id="91153-109">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="91153-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
