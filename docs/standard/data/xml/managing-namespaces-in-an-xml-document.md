---
title: Управление пространствами имен в XML-документе
description: Узнайте, как управлять пространствами имен в XML-документе. Пространства имен XML связывают имена элементов и атрибутов в XML-документе с пользовательскими и стандартными URI.
ms.date: 03/30/2017
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 120493de430c2372f3f71d1d1498ba880feda3d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720156"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="3a27f-104">Управление пространствами имен в XML-документе</span><span class="sxs-lookup"><span data-stu-id="3a27f-104">Managing Namespaces in an XML Document</span></span>

<span data-ttu-id="3a27f-105">Пространства имен XML связывают имена элементов и атрибутов в XML-документе с пользовательскими и стандартными URI.</span><span class="sxs-lookup"><span data-stu-id="3a27f-105">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="3a27f-106">Для создания этих связей определяются префиксы для URI пространства имен, с помощью которых затем квалифицируются имена элементов и атрибутов в XML-данных.</span><span class="sxs-lookup"><span data-stu-id="3a27f-106">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="3a27f-107">Пространства имен предотвращают конфликты имен элементов и атрибутов, а также позволяют обрабатывать и проверять элементы и атрибуты с одним и тем же именем.</span><span class="sxs-lookup"><span data-stu-id="3a27f-107">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>

## <a name="declaring-namespaces"></a><span data-ttu-id="3a27f-108">Объявление пространств имен</span><span class="sxs-lookup"><span data-stu-id="3a27f-108">Declaring namespaces</span></span>  

 <span data-ttu-id="3a27f-109">Пространство имен для элемента объявляется с помощью атрибута `xmlns:`:</span><span class="sxs-lookup"><span data-stu-id="3a27f-109">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="3a27f-110">где `<name>` — это префикс пространства имен, а `<"uri">` — это URI, который определяет это пространство имен.</span><span class="sxs-lookup"><span data-stu-id="3a27f-110">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="3a27f-111">После объявления префикса его можно использовать для уточнения имен элементов и атрибутов в XML-документе и связывания их с URI-кодом пространства имен.</span><span class="sxs-lookup"><span data-stu-id="3a27f-111">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="3a27f-112">Так как этот префикс пространства имен используется во всем документе, он должен быть коротким.</span><span class="sxs-lookup"><span data-stu-id="3a27f-112">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="3a27f-113">В данном примере определяются два элемента `BOOK`.</span><span class="sxs-lookup"><span data-stu-id="3a27f-113">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="3a27f-114">Первый элемент квалифицируется префиксом `mybook`, а второй — префиксом `bb`.</span><span class="sxs-lookup"><span data-stu-id="3a27f-114">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="3a27f-115">Каждый префикс связан с разными URI-кодами пространств имен:</span><span class="sxs-lookup"><span data-stu-id="3a27f-115">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 <span data-ttu-id="3a27f-116">Чтобы указать, что элемент принадлежит к определенному пространству имен, добавьте к нему префикс пространства имен.</span><span class="sxs-lookup"><span data-stu-id="3a27f-116">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="3a27f-117">Например, если элемент `Author` принадлежит пространству имен `mybook`, то он объявляется как `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="3a27f-117">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>

## <a name="declaration-scope"></a><span data-ttu-id="3a27f-118">Область видимости объявления</span><span class="sxs-lookup"><span data-stu-id="3a27f-118">Declaration scope</span></span>  

 <span data-ttu-id="3a27f-119">Пространство имен действует от точки объявления до конца элемента, где оно было объявлено.</span><span class="sxs-lookup"><span data-stu-id="3a27f-119">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="3a27f-120">В этом примере пространство имен, определенное в элементе `BOOK`, не применяется к элементам, которые находятся за пределами элемента `BOOK`, например к элементу `Publisher`:</span><span class="sxs-lookup"><span data-stu-id="3a27f-120">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 <span data-ttu-id="3a27f-121">Пространство имен можно использовать только после его объявления, однако это не значит, что объявление пространства имен должно располагаться в самом начале XML-документа.</span><span class="sxs-lookup"><span data-stu-id="3a27f-121">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="3a27f-122">Если в XML-документе используются несколько пространств имен, можно определить одно из них как пространство по умолчанию, чтобы упростить чтение документа.</span><span class="sxs-lookup"><span data-stu-id="3a27f-122">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="3a27f-123">Пространство имен по умолчанию объявляется в корневом элементе и применяется ко всем элементам в документе, которые не квалифицированы.</span><span class="sxs-lookup"><span data-stu-id="3a27f-123">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="3a27f-124">Пространства имен по умолчанию применяются только к элементам и не применяются к атрибутам.</span><span class="sxs-lookup"><span data-stu-id="3a27f-124">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="3a27f-125">Для использования пространства имен по умолчанию не указывайте префикс и двоеточие в объявлении элемента:</span><span class="sxs-lookup"><span data-stu-id="3a27f-125">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="3a27f-126">Управление пространствами имен</span><span class="sxs-lookup"><span data-stu-id="3a27f-126">Managing namespaces</span></span>  

 <span data-ttu-id="3a27f-127">В классе <xref:System.Xml.XmlNamespaceManager> хранится коллекция URI пространств имен и их префиксов. С его помощью можно искать, добавлять и удалять пространства имен из этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="3a27f-127">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="3a27f-128">В некоторых контекстах этот класс необходим для повышения производительности обработки XML.</span><span class="sxs-lookup"><span data-stu-id="3a27f-128">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="3a27f-129">Например, класс <xref:System.Xml.Xsl.XsltContext> используется классом <xref:System.Xml.XmlNamespaceManager> для обеспечения поддержки XPath.</span><span class="sxs-lookup"><span data-stu-id="3a27f-129">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="3a27f-130">Диспетчер пространств имен не выполняет проверку пространств имен, так как предполагается, что префиксы и пространства имен уже проверены и соответствуют спецификации [W3C для пространств имен](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="3a27f-130">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a27f-131">Интерфейс LINQ to XML [в C#](../../linq/linq-xml-overview.md) и [Visual Basic](../../linq/linq-xml-overview.md) использует <xref:System.Xml.XmlNamespaceManager> для управления пространствами имен.</span><span class="sxs-lookup"><span data-stu-id="3a27f-131">LINQ TO XML in [C#](../../linq/linq-xml-overview.md) and [Visual Basic](../../linq/linq-xml-overview.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="3a27f-132">Дополнительные сведения об управлении пространствами имен в случае использования LINQ to XML см. в документации по LINQ, в разделах [Работа с пространствами имен XML (C#)](../../linq/namespaces-overview.md) и [Работа с пространствами имен XML (Visual Basic)](../../linq/namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a27f-132">See [Working with XML Namespaces (C#)](../../linq/namespaces-overview.md) and [Working with XML Namespaces (Visual Basic)](../../linq/namespaces-overview.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="3a27f-133">Вот некоторые из задач по управлению и подстановке, которые можно выполнить с помощью класса <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="3a27f-133">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="3a27f-134">Дополнительные сведения и примеры см. в разделах справочника, посвященных каждому методу или свойству.</span><span class="sxs-lookup"><span data-stu-id="3a27f-134">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="3a27f-135">Кому</span><span class="sxs-lookup"><span data-stu-id="3a27f-135">To</span></span>|<span data-ttu-id="3a27f-136">Использовать</span><span class="sxs-lookup"><span data-stu-id="3a27f-136">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="3a27f-137">Добавление пространства имен</span><span class="sxs-lookup"><span data-stu-id="3a27f-137">Add a namespace</span></span>|<span data-ttu-id="3a27f-138">Метод <xref:System.Xml.XmlNamespaceManager.AddNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="3a27f-138"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="3a27f-139">Удаление пространства имен</span><span class="sxs-lookup"><span data-stu-id="3a27f-139">Remove a namespace</span></span>|<span data-ttu-id="3a27f-140">Метод <xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="3a27f-140"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="3a27f-141">Поиск URI для пространства имен по умолчанию</span><span class="sxs-lookup"><span data-stu-id="3a27f-141">Find the URI for the default namespace</span></span>|<span data-ttu-id="3a27f-142">Свойство<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="3a27f-142"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="3a27f-143">Поиск URI для префикса пространства имен</span><span class="sxs-lookup"><span data-stu-id="3a27f-143">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="3a27f-144">Метод <xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="3a27f-144"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="3a27f-145">Поиск префикса для URI-кодов пространства имен</span><span class="sxs-lookup"><span data-stu-id="3a27f-145">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="3a27f-146">Метод <xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A></span><span class="sxs-lookup"><span data-stu-id="3a27f-146"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="3a27f-147">Получение списка пространств имен, которые есть на текущем узле</span><span class="sxs-lookup"><span data-stu-id="3a27f-147">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="3a27f-148">Метод <xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A></span><span class="sxs-lookup"><span data-stu-id="3a27f-148"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="3a27f-149">Задание области видимости пространства имен</span><span class="sxs-lookup"><span data-stu-id="3a27f-149">Scope a namespace</span></span>|<span data-ttu-id="3a27f-150">Методы <xref:System.Xml.XmlNamespaceManager.PushScope%2A> и <xref:System.Xml.XmlNamespaceManager.PopScope%2A></span><span class="sxs-lookup"><span data-stu-id="3a27f-150"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="3a27f-151">Проверка того, определен ли префикс в текущей области</span><span class="sxs-lookup"><span data-stu-id="3a27f-151">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="3a27f-152">Метод <xref:System.Xml.XmlNamespaceManager.HasNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="3a27f-152"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="3a27f-153">Получение таблицы имен используется для поиска префиксов и URI</span><span class="sxs-lookup"><span data-stu-id="3a27f-153">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="3a27f-154">Свойство<xref:System.Xml.XmlNamespaceManager.NameTable%2A></span><span class="sxs-lookup"><span data-stu-id="3a27f-154"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a27f-155">См. также</span><span class="sxs-lookup"><span data-stu-id="3a27f-155">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="3a27f-156">XML-документы и данные</span><span class="sxs-lookup"><span data-stu-id="3a27f-156">XML Documents and Data</span></span>](index.md)
