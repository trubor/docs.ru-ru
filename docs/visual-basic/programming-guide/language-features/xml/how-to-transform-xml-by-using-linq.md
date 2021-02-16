---
description: Дополнительные сведения см. в статье как преобразовать XML с помощью LINQ (Visual Basic).
title: Практическое руководство. Преобразование XML с помощью LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 67e6f5f94cd71d960f742b660d3f223137bbd6d4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483642"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="c0e2a-103">Практическое руководство. Преобразование XML с помощью LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0e2a-103">How to: Transform XML by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="c0e2a-104">[XML-литералы](../../../language-reference/xml-literals/index.md) позволяют легко считывать XML-код из одного источника и преобразовывать его в новый формат XML.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-104">[XML Literals](../../../language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="c0e2a-105">Можно использовать запросы LINQ для получения содержимого для преобразования или изменения содержимого существующего документа в новый формат XML.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-105">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>

<span data-ttu-id="c0e2a-106">Пример в этом разделе преобразует содержимое из исходного документа XML в HTML для просмотра в браузере.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-106">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a><span data-ttu-id="c0e2a-107">Преобразование XML-документа</span><span class="sxs-lookup"><span data-stu-id="c0e2a-107">To transform an XML document</span></span>

1. <span data-ttu-id="c0e2a-108">В Visual Studio создайте новый проект Visual Basic в шаблоне проекта **консольное приложение** .</span><span class="sxs-lookup"><span data-stu-id="c0e2a-108">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>

2. <span data-ttu-id="c0e2a-109">Дважды щелкните файл Module1. vb, созданный в проекте, чтобы изменить код Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-109">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="c0e2a-110">Добавьте следующий код в `Sub Main` `Module1` модуль.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-110">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="c0e2a-111">Этот код создает исходный XML-документ в виде <xref:System.Xml.Linq.XDocument> объекта.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-111">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>

    ```vb
    Dim catalog =
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
              Get the expert insights, practical code samples,
              and best practices you need
              to advance your expertise with <technology>Visual
              Basic .NET</technology>.
              Learn how to create faster, more reliable applications
              based on professional,
              pragmatic guidance by today's top <audience>developers</audience>.
            </Description>
          </Book>
        </Catalog>
    ```

     <span data-ttu-id="c0e2a-112">[Как загрузить XML из файла, строки или потока](how-to-load-xml-from-a-file-string-or-stream.md).</span><span class="sxs-lookup"><span data-stu-id="c0e2a-112">[How to: Load XML from a File, String, or Stream](how-to-load-xml-from-a-file-string-or-stream.md).</span></span>

3. <span data-ttu-id="c0e2a-113">После создания исходного XML-документа добавьте следующий код, чтобы получить все \<Book> элементы из объекта и преобразовать их в HTML-документ.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-113">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="c0e2a-114">Список \<Book> элементов создается с помощью запроса LINQ, возвращающего коллекцию <xref:System.Xml.Linq.XElement> объектов, содержащих преобразованный HTML-код.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-114">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="c0e2a-115">Внедренные выражения можно использовать для размещения значений из исходного документа в новом XML-формате.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-115">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>

     <span data-ttu-id="c0e2a-116">Полученный HTML-документ записывается в файл с помощью <xref:System.Xml.Linq.XElement.Save%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-116">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>

    ```vb
    Dim htmlOutput =
      <html>
        <body>
          <%= From book In catalog.<Catalog>.<Book>
              Select <div>
                       <h1><%= book.<Title>.Value %></h1>
                       <h3><%= "By " & book.<Author>.Value %></h3>
                        <h3><%= "Price = " & book.<Price>.Value %></h3>
                        <h2>Description</h2>
                        <%= TransformDescription(book.<Description>(0)) %>
                        <hr/>
                      </div> %>
        </body>
      </html>

    htmlOutput.Save("BookDescription.html")
    ```

4. <span data-ttu-id="c0e2a-117">После `Sub Main` `Module1` добавьте новый метод ( `Sub` ) для преобразования \<Description> узла в указанный формат HTML.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-117">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="c0e2a-118">Этот метод вызывается кодом на предыдущем шаге и используется для сохранения формата \<Description> элементов.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-118">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>

     <span data-ttu-id="c0e2a-119">Этот метод заменяет вложенные элементы \<Description> элемента HTML.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-119">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="c0e2a-120">`ReplaceWith`Метод используется для сохранения расположения вложенных элементов.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-120">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="c0e2a-121">Преобразованное содержимое \<Description> элемента включается в элемент HTML-Абзац ( \<p> ).</span><span class="sxs-lookup"><span data-stu-id="c0e2a-121">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="c0e2a-122"><xref:System.Xml.Linq.XContainer.Nodes%2A>Свойство используется для получения преобразованного содержимого \<Description> элемента.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-122">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="c0e2a-123">Это гарантирует, что вложенные элементы будут включены в преобразованное содержимое.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-123">This ensures that sub-elements are included in the transformed content.</span></span>

     <span data-ttu-id="c0e2a-124">Добавьте следующий код после `Sub Main` `Module1` .</span><span class="sxs-lookup"><span data-stu-id="c0e2a-124">Add the following code after `Sub Main` of `Module1`.</span></span>

    ```vb
    Public Function TransformDescription(ByVal desc As XElement) As XElement

      ' Replace <technology> elements with <b>.
      Dim content = (From element In desc...<technology>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)
        Next
      End If

      ' Replace <audience> elements with <i>.
      content = (From element In desc...<audience>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)
        Next
      End If

      ' Return the updated contents of the <Description> element.
      Return <p><%= desc.Nodes %></p>
    End Function
    ```

5. <span data-ttu-id="c0e2a-125">Сохраните изменения.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-125">Save your changes.</span></span>

6. <span data-ttu-id="c0e2a-126">Нажмите клавишу F5, чтобы выполнить код.</span><span class="sxs-lookup"><span data-stu-id="c0e2a-126">Press F5 to run the code.</span></span> <span data-ttu-id="c0e2a-127">Полученный сохраненный документ будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c0e2a-127">The resulting saved document will resemble the following:</span></span>

    ```html
    <?xml version="1.0"?>
    <html>
      <body>
        <div>
          <h1>XML Developer's Guide</h1>
          <h3>By Garghentini, Davide</h3>
          <h3>Price = 44.95</h3>
          <h2>Description</h2>
          <p>
            An in-depth look at creating applications
            with <b>XML</b>. For
            <i>beginners</i> or
            <i>advanced</i> developers.
          </p>
          <hr />
        </div>
        <div>
          <h1>Developing Applications with Visual Basic .NET</h1>
          <h3>By Spencer, Phil</h3>
          <h3>Price = 45.95</h3>
          <h2>Description</h2>
          <p>
            Get the expert insights, practical code
            samples, and best practices you need
            to advance your expertise with <b>Visual
            Basic .NET</b>. Learn how to create faster,
            more reliable applications based on
            professional, pragmatic guidance by today's
            top <i>developers</i>.
          </p>
          <hr />
        </div>
      </body>
    </html>
    ```

## <a name="see-also"></a><span data-ttu-id="c0e2a-128">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c0e2a-128">See also</span></span>

- [<span data-ttu-id="c0e2a-129">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="c0e2a-129">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="c0e2a-130">Обработка XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0e2a-130">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="c0e2a-131">XML</span><span class="sxs-lookup"><span data-stu-id="c0e2a-131">XML</span></span>](index.md)
- [<span data-ttu-id="c0e2a-132">Практическое руководство. Загрузка XML-кода из файла, строки или потока</span><span class="sxs-lookup"><span data-stu-id="c0e2a-132">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="c0e2a-133">LINQ</span><span class="sxs-lookup"><span data-stu-id="c0e2a-133">LINQ</span></span>](../linq/index.md)
- <span data-ttu-id="c0e2a-134">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0e2a-134">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md)</span></span>
