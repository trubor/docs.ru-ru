---
description: Дополнительные сведения см. в статье как изменить литералы XML (Visual Basic)
title: Практическое руководство. Изменение XML-литералов
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 23b900c3da5864ac7a91e6c7a43f44a0d4ab1a21
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483616"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="8c34c-103">Практическое руководство. Изменение XML-литералов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c34c-103">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="8c34c-104">Visual Basic предоставляет удобные способы изменения XML-литералов.</span><span class="sxs-lookup"><span data-stu-id="8c34c-104">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="8c34c-105">Можно добавлять или удалять элементы и атрибуты. Кроме того, можно заменить существующий элемент новым XML-элементом.</span><span class="sxs-lookup"><span data-stu-id="8c34c-105">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="8c34c-106">В этом разделе приводится несколько примеров изменения существующего XML-литерала.</span><span class="sxs-lookup"><span data-stu-id="8c34c-106">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="8c34c-107">Изменение значения XML-литерала</span><span class="sxs-lookup"><span data-stu-id="8c34c-107">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="8c34c-108">Чтобы изменить значение XML-литерала, получите ссылку на XML-литерал и задайте `Value` для свойства нужное значение.</span><span class="sxs-lookup"><span data-stu-id="8c34c-108">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="8c34c-109">В следующем примере кода обновляются значения всех \<Price> элементов в XML-документе.</span><span class="sxs-lookup"><span data-stu-id="8c34c-109">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="8c34c-110">Ниже приведен пример исходного XML и измененный XML-код из этого примера кода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-110">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="8c34c-111">Исходный XML-код:</span><span class="sxs-lookup"><span data-stu-id="8c34c-111">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="8c34c-112">Измененный XML:</span><span class="sxs-lookup"><span data-stu-id="8c34c-112">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > <span data-ttu-id="8c34c-113">`Value`Свойство ссылается на первый элемент XML в коллекции.</span><span class="sxs-lookup"><span data-stu-id="8c34c-113">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="8c34c-114">Если в коллекции имеется несколько элементов с одинаковым именем, установка `Value` свойства влияет только на первый элемент в коллекции.</span><span class="sxs-lookup"><span data-stu-id="8c34c-114">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="8c34c-115">Добавление атрибута к XML-литералу</span><span class="sxs-lookup"><span data-stu-id="8c34c-115">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="8c34c-116">Чтобы добавить атрибут к XML-литералу, сначала получите ссылку на XML-литерал.</span><span class="sxs-lookup"><span data-stu-id="8c34c-116">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="8c34c-117">Затем можно добавить атрибут, добавив новое свойство оси атрибутов XML.</span><span class="sxs-lookup"><span data-stu-id="8c34c-117">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="8c34c-118">Можно также добавить новый <xref:System.Xml.Linq.XAttribute> объект в XML-литерал с помощью <xref:System.Xml.Linq.XContainer.Add%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-118">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="8c34c-119">В следующем примере показаны оба варианта.</span><span class="sxs-lookup"><span data-stu-id="8c34c-119">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="8c34c-120">Ниже приведен пример исходного XML и измененный XML-код из этого примера кода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-120">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="8c34c-121">Исходный XML-код:</span><span class="sxs-lookup"><span data-stu-id="8c34c-121">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="8c34c-122">Измененный XML:</span><span class="sxs-lookup"><span data-stu-id="8c34c-122">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="8c34c-123">Дополнительные сведения о свойствах осей атрибутов XML см. в разделе [свойство оси атрибутов XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="8c34c-123">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="8c34c-124">Добавление элемента в XML-литерал</span><span class="sxs-lookup"><span data-stu-id="8c34c-124">To add an element to an XML literal</span></span>

1. <span data-ttu-id="8c34c-125">Чтобы добавить элемент в XML-литерал, сначала получите ссылку на XML-литерал.</span><span class="sxs-lookup"><span data-stu-id="8c34c-125">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="8c34c-126">Затем можно добавить новый <xref:System.Xml.Linq.XElement> объект как последний вложенный элемент элемента с помощью <xref:System.Xml.Linq.XContainer.Add%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-126">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="8c34c-127">Новый объект можно добавить в <xref:System.Xml.Linq.XElement> качестве первого вложенного элемента с помощью <xref:System.Xml.Linq.XContainer.AddFirst%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-127">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="8c34c-128">Чтобы добавить новый элемент в определенном месте относительно других вложенных элементов, сначала получите ссылку на смежный вложенный элемент.</span><span class="sxs-lookup"><span data-stu-id="8c34c-128">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="8c34c-129">Затем можно добавить новый <xref:System.Xml.Linq.XElement> объект перед соседним вложенным элементом с помощью <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-129">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="8c34c-130">Новый объект также можно добавить <xref:System.Xml.Linq.XElement> после соседнего вложенного элемента с помощью <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-130">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="8c34c-131">В следующем примере показаны примеры каждого из этих методов.</span><span class="sxs-lookup"><span data-stu-id="8c34c-131">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="8c34c-132">Ниже приведен пример исходного XML и измененный XML-код из этого примера кода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-132">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="8c34c-133">Исходный XML-код:</span><span class="sxs-lookup"><span data-stu-id="8c34c-133">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="8c34c-134">Измененный XML:</span><span class="sxs-lookup"><span data-stu-id="8c34c-134">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="8c34c-135">Удаление элемента или атрибута из XML-литерала</span><span class="sxs-lookup"><span data-stu-id="8c34c-135">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="8c34c-136">Чтобы удалить элемент или атрибут из XML-литерала, получите ссылку на элемент или атрибут и вызовите `Remove` метод, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8c34c-136">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="8c34c-137">Ниже приведен пример исходного XML и измененный XML-код из этого примера кода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-137">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="8c34c-138">Исходный XML-код:</span><span class="sxs-lookup"><span data-stu-id="8c34c-138">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    <span data-ttu-id="8c34c-139">Измененный XML:</span><span class="sxs-lookup"><span data-stu-id="8c34c-139">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    <span data-ttu-id="8c34c-140">Чтобы удалить все элементы или атрибуты из XML-литерала, получите ссылку на XML-литерал и вызовите <xref:System.Xml.Linq.XElement.RemoveAll%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="8c34c-140">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="8c34c-141">Изменение XML-литерала</span><span class="sxs-lookup"><span data-stu-id="8c34c-141">To modify an XML literal</span></span>

1. <span data-ttu-id="8c34c-142">Чтобы изменить имя XML-элемента, сначала получите ссылку на элемент.</span><span class="sxs-lookup"><span data-stu-id="8c34c-142">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="8c34c-143">Затем можно создать новый объект с <xref:System.Xml.Linq.XElement> новым именем и передать новый <xref:System.Xml.Linq.XElement> объект <xref:System.Xml.Linq.XNode.ReplaceWith%2A> методу существующего <xref:System.Xml.Linq.XElement> объекта.</span><span class="sxs-lookup"><span data-stu-id="8c34c-143">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="8c34c-144">Если заменяемый элемент содержит вложенные элементы, которые должны быть сохранены, установите значение нового <xref:System.Xml.Linq.XElement> объекта в <xref:System.Xml.Linq.XContainer.Nodes%2A> свойство существующего элемента.</span><span class="sxs-lookup"><span data-stu-id="8c34c-144">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="8c34c-145">При этом значение нового элемента будет присвоено внутреннему XML существующего элемента.</span><span class="sxs-lookup"><span data-stu-id="8c34c-145">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="8c34c-146">В противном случае можно присвоить значение нового элемента `Value` свойству существующего элемента.</span><span class="sxs-lookup"><span data-stu-id="8c34c-146">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="8c34c-147">В следующем примере кода все элементы заменяются \<Description> \<Abstract> элементом.</span><span class="sxs-lookup"><span data-stu-id="8c34c-147">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="8c34c-148">Содержимое \<Description> элемента сохраняется в новом \<Abstract> элементе с помощью <xref:System.Xml.Linq.XContainer.Nodes%2A> свойства \<Description> <xref:System.Xml.Linq.XElement> объекта.</span><span class="sxs-lookup"><span data-stu-id="8c34c-148">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="8c34c-149">Ниже приведен пример исходного XML и измененный XML-код из этого примера кода.</span><span class="sxs-lookup"><span data-stu-id="8c34c-149">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="8c34c-150">Исходный XML-код:</span><span class="sxs-lookup"><span data-stu-id="8c34c-150">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
        <Description>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Description>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <Description>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="8c34c-151">Измененный XML:</span><span class="sxs-lookup"><span data-stu-id="8c34c-151">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a><span data-ttu-id="8c34c-152">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8c34c-152">See also</span></span>

- [<span data-ttu-id="8c34c-153">Обработка XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c34c-153">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="8c34c-154">XML</span><span class="sxs-lookup"><span data-stu-id="8c34c-154">XML</span></span>](index.md)
- [<span data-ttu-id="8c34c-155">Практическое руководство. Загрузка XML-кода из файла, строки или потока</span><span class="sxs-lookup"><span data-stu-id="8c34c-155">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="8c34c-156">LINQ</span><span class="sxs-lookup"><span data-stu-id="8c34c-156">LINQ</span></span>](../linq/index.md)
- <span data-ttu-id="8c34c-157">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c34c-157">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md)</span></span>
