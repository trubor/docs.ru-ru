---
description: 'Узнайте подробнее о: Использование System.Xml'
title: Использование System.Xml
ms.date: 10/22/2008
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 51886c07f0b68bb329c258daa93e809d94839341
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641854"
---
# <a name="systemxml-usage"></a><span data-ttu-id="04ea4-103">Использование System.Xml</span><span class="sxs-lookup"><span data-stu-id="04ea4-103">System.Xml Usage</span></span>

<span data-ttu-id="04ea4-104">В этом разделе описывается использование нескольких типов, располагающихся в пространствах имен <xref:System.Xml?displayProperty=nameWithType>, с помощью которых можно представлять XML-данные.</span><span class="sxs-lookup"><span data-stu-id="04ea4-104">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="04ea4-105">❌ НЕ СЛЕДУЕТ использовать <xref:System.Xml.XmlNode> или <xref:System.Xml.XmlDocument> для представления XML-данных.</span><span class="sxs-lookup"><span data-stu-id="04ea4-105">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="04ea4-106">Предпочтительнее использовать экземпляры <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> или подтипы <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="04ea4-106">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="04ea4-107">`XmlNode` и `XmlDocument` не предназначены для предоставления в общедоступных API.</span><span class="sxs-lookup"><span data-stu-id="04ea4-107">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="04ea4-108">✔️ СЛЕДУЕТ использовать `XmlReader`, `IXPathNavigable` или подтипы `XNode` в качестве входных или выходных данных членов, которые принимают или возвращают XML-данные.</span><span class="sxs-lookup"><span data-stu-id="04ea4-108">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="04ea4-109">Используйте эти абстракции вместо `XmlDocument`, `XmlNode` или <xref:System.Xml.XPath.XPathDocument>, так как это позволяет отделить методы от конкретных реализаций XML-документа в памяти и позволяет им работать с виртуальными источниками XML-данных, которые предоставляют `XNode`, `XmlReader` или <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="04ea4-109">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="04ea4-110">❌ НЕ СЛЕДУЕТ создавать подкласс `XmlDocument`, если вы хотите создать тип, представляющий представление XML-данных для базовой модели объектов или источника данных.</span><span class="sxs-lookup"><span data-stu-id="04ea4-110">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="04ea4-111">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="04ea4-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="04ea4-112">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="04ea4-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="04ea4-113">См. также</span><span class="sxs-lookup"><span data-stu-id="04ea4-113">See also</span></span>

- [<span data-ttu-id="04ea4-114">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="04ea4-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="04ea4-115">Правила использования</span><span class="sxs-lookup"><span data-stu-id="04ea4-115">Usage Guidelines</span></span>](usage-guidelines.md)
