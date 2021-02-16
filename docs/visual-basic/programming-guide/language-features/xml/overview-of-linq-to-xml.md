---
description: Дополнительные сведения см. в статье Общие сведения о LINQ to XML в Visual Basic
title: Общие сведения о LINQ to XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: e70998706f62076a2528ac646df29e0c7081cb3d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480223"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="4dec0-103">Общие сведения о LINQ to XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4dec0-103">Overview of LINQ to XML in Visual Basic</span></span>

<span data-ttu-id="4dec0-104">Visual Basic обеспечивает поддержку [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] через литералы XML и свойства осей XML.</span><span class="sxs-lookup"><span data-stu-id="4dec0-104">Visual Basic provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="4dec0-105">Это позволяет использовать знакомый, удобный синтаксис для работы с XML в коде Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4dec0-105">This enables you to use a familiar, convenient syntax for working with XML in your Visual Basic code.</span></span> <span data-ttu-id="4dec0-106">*XML-литералы* позволяют включать XML непосредственно в код.</span><span class="sxs-lookup"><span data-stu-id="4dec0-106">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="4dec0-107">*Свойства оси XML* позволяют получать доступ к дочерним узлам, узлам-потомкам и атрибутам XML.</span><span class="sxs-lookup"><span data-stu-id="4dec0-107">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="4dec0-108">Дополнительные сведения см. в статьях [Общие сведения о XML-литералах](xml-literals-overview.md) и [доступ к XML в Visual Basic](accessing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4dec0-108">For more information, see [XML Literals Overview](xml-literals-overview.md) and [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="4dec0-109">— API программирования XML в памяти, предназначенный специально для использования преимуществ Language-Integrated query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="4dec0-109">is an in-memory XML programming API designed specifically to take advantage of Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="4dec0-110">Хотя интерфейсы API LINQ можно вызывать напрямую, только Visual Basic позволяет объявлять литералы XML и напрямую обращаться к свойствам осей XML.</span><span class="sxs-lookup"><span data-stu-id="4dec0-110">Although you can call the LINQ APIs directly, only Visual Basic enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4dec0-111">XML-литералы и свойства осей XML не поддерживаются в декларативном коде на странице ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4dec0-111">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="4dec0-112">Чтобы использовать функции Visual Basic XML, разместите код на странице кода программной части в приложении ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4dec0-112">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="4dec0-113">[Кнопка "Воспроизвести"](./media/overview-of-linq-to-xml/play-video-icon-example.gif) Связанные демонстрационные видеоролики см [. в разделе как начать работу с LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) и [как создать электронные таблицы Excel с помощью LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).</span><span class="sxs-lookup"><span data-stu-id="4dec0-113">[Play button](./media/overview-of-linq-to-xml/play-video-icon-example.gif) For related video demonstrations, see [How Do I Get Started with LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) and [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).</span></span>
  
## <a name="creating-xml"></a><span data-ttu-id="4dec0-114">Создание XML</span><span class="sxs-lookup"><span data-stu-id="4dec0-114">Creating XML</span></span>  

 <span data-ttu-id="4dec0-115">Существует два способа создания деревьев XML в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4dec0-115">There are two ways to create XML trees in Visual Basic.</span></span> <span data-ttu-id="4dec0-116">Вы можете объявить XML-литерал непосредственно в коде или использовать API LINQ для создания дерева.</span><span class="sxs-lookup"><span data-stu-id="4dec0-116">You can declare an XML literal directly in code, or you can use the LINQ APIs to create the tree.</span></span> <span data-ttu-id="4dec0-117">Оба процесса позволяют коду отражать окончательную структуру XML-дерева.</span><span class="sxs-lookup"><span data-stu-id="4dec0-117">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="4dec0-118">Например, в следующем примере кода создается XML-элемент:</span><span class="sxs-lookup"><span data-stu-id="4dec0-118">For example, the following code example creates an XML element:</span></span>  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 <span data-ttu-id="4dec0-119">Дополнительные сведения см. [в разделе Создание XML в Visual Basic](creating-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4dec0-119">For more information, see [Creating XML in Visual Basic](creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="4dec0-120">Доступ и Навигация по XML</span><span class="sxs-lookup"><span data-stu-id="4dec0-120">Accessing and Navigating XML</span></span>  

 <span data-ttu-id="4dec0-121">Visual Basic предоставляет свойства осей XML для доступа и навигации по XML-структурам.</span><span class="sxs-lookup"><span data-stu-id="4dec0-121">Visual Basic provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="4dec0-122">Эти свойства позволяют получить доступ к XML-элементам и атрибутам, указывая имена дочерних XML-элементов.</span><span class="sxs-lookup"><span data-stu-id="4dec0-122">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="4dec0-123">Кроме того, можно явно вызвать методы LINQ для перемещения и поиска элементов и атрибутов.</span><span class="sxs-lookup"><span data-stu-id="4dec0-123">Alternatively, you can explicitly call the LINQ methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="4dec0-124">Например, в следующем примере кода свойства оси XML используются для ссылки на атрибуты и дочерние элементы XML-элемента.</span><span class="sxs-lookup"><span data-stu-id="4dec0-124">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="4dec0-125">В примере кода используется запрос LINQ для получения дочерних элементов и их вывода в виде XML-элементов, фактически выполняющего преобразование.</span><span class="sxs-lookup"><span data-stu-id="4dec0-125">The code example uses a LINQ query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 <span data-ttu-id="4dec0-126">Дополнительные сведения см. [в разделе доступ к XML в Visual Basic](accessing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4dec0-126">For more information, see [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="4dec0-127">Пространства имен XML</span><span class="sxs-lookup"><span data-stu-id="4dec0-127">XML Namespaces</span></span>  

 <span data-ttu-id="4dec0-128">Visual Basic позволяет указать псевдоним для глобального пространства имен XML с помощью `Imports` инструкции.</span><span class="sxs-lookup"><span data-stu-id="4dec0-128">Visual Basic enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="4dec0-129">В следующем примере показано, как использовать `Imports` инструкцию для импорта пространства имен XML:</span><span class="sxs-lookup"><span data-stu-id="4dec0-129">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 <span data-ttu-id="4dec0-130">При доступе к свойствам осей XML и объявлении XML-литералов для XML-документов и элементов можно использовать псевдоним пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="4dec0-130">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="4dec0-131"><xref:System.Xml.Linq.XNamespace>Объект для определенного префикса пространства имен можно получить с помощью [оператора GetXmlNamespace](../../../language-reference/operators/getxmlnamespace-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4dec0-131">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="4dec0-132">Дополнительные сведения см. в разделе [оператор Imports (пространство имен XML)](../../../language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="4dec0-132">For more information, see [Imports Statement (XML Namespace)](../../../language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="4dec0-133">Использование пространств имен XML в XML-литералах</span><span class="sxs-lookup"><span data-stu-id="4dec0-133">Using XML Namespaces in XML Literals</span></span>  

 <span data-ttu-id="4dec0-134">В следующем примере показано, как создать <xref:System.Xml.Linq.XElement> объект, использующий глобальное пространство имен `ns` :</span><span class="sxs-lookup"><span data-stu-id="4dec0-134">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 <span data-ttu-id="4dec0-135">Компилятор Visual Basic преобразует литералы XML, содержащие псевдонимы пространства имен XML, в эквивалентный код, использующий XML-нотацию для использования пространств имен XML с `xmlns` атрибутом.</span><span class="sxs-lookup"><span data-stu-id="4dec0-135">The Visual Basic compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="4dec0-136">При компиляции код в примере предыдущего раздела создает фактически тот же исполняемый код, что и в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="4dec0-136">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="4dec0-137">Использование пространств имен XML в свойствах оси XML</span><span class="sxs-lookup"><span data-stu-id="4dec0-137">Using XML Namespaces in XML Axis Properties</span></span>  

 <span data-ttu-id="4dec0-138">Пространства имен XML, объявленные в XML-литералах, недоступны для использования в свойствах осей XML.</span><span class="sxs-lookup"><span data-stu-id="4dec0-138">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="4dec0-139">Однако глобальные пространства имен можно использовать со свойствами осей XML.</span><span class="sxs-lookup"><span data-stu-id="4dec0-139">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="4dec0-140">Используйте двоеточие для отделения префикса пространства имен XML от имени локального элемента.</span><span class="sxs-lookup"><span data-stu-id="4dec0-140">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="4dec0-141">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="4dec0-141">Following is an example:</span></span>  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4dec0-142">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4dec0-142">See also</span></span>

- [<span data-ttu-id="4dec0-143">XML</span><span class="sxs-lookup"><span data-stu-id="4dec0-143">XML</span></span>](index.md)
- [<span data-ttu-id="4dec0-144">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4dec0-144">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="4dec0-145">Доступ к XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4dec0-145">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="4dec0-146">Обработка XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4dec0-146">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
