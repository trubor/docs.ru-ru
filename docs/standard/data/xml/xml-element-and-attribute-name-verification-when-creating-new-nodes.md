---
title: Проверка имен XML-элементов и атрибутов при создании новых узлов
ms.date: 03/30/2017
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 5bad0faf8aec2f6f1d2395477867fbdaeea4a97a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733065"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="ceaac-102">Проверка имен XML-элементов и атрибутов при создании новых узлов</span><span class="sxs-lookup"><span data-stu-id="ceaac-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>

<span data-ttu-id="ceaac-103">Модель XML DOM проверяет допустимость имен при создании новых узлов элементов или узлов атрибутов.</span><span class="sxs-lookup"><span data-stu-id="ceaac-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="ceaac-104">Если имена содержат недопустимые символы, возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="ceaac-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="ceaac-105">Чтобы гарантировать допустимость и правильную кодировку имен, необходимо использовать класс **XmlConvert** для кодирования и декодирования имен на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="ceaac-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="ceaac-106">Класс **XmlWriter** содержит методы, которые выполняют дополнительную работу, чтобы обеспечить формирование XML-документов правильного формата.</span><span class="sxs-lookup"><span data-stu-id="ceaac-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceaac-107">См. также</span><span class="sxs-lookup"><span data-stu-id="ceaac-107">See also</span></span>

- [<span data-ttu-id="ceaac-108">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="ceaac-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
