---
description: 'Дополнительные сведения об инструкции: Imports (пространство имен XML)'
title: Оператор Imports — пространство имен XML
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 2ca285c9104c5a03b265dd15ce38a378e66d6916
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768965"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="079e9-103">Оператор Imports (пространство имен XML)</span><span class="sxs-lookup"><span data-stu-id="079e9-103">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="079e9-104">Импортирует префиксы пространства имен XML для использования в XML-литералах и свойствах осей XML.</span><span class="sxs-lookup"><span data-stu-id="079e9-104">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="079e9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="079e9-105">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="079e9-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="079e9-106">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="079e9-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="079e9-107">Optional.</span></span> <span data-ttu-id="079e9-108">Строка, с помощью которой можно ссылаться на элементы и атрибуты XML `xmlNamespaceName` .</span><span class="sxs-lookup"><span data-stu-id="079e9-108">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="079e9-109">Если `xmlNamespacePrefix` аргумент не указан, импортированное пространство имен XML является пространством имен XML по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="079e9-109">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="079e9-110">Должен быть допустимым идентификатором XML.</span><span class="sxs-lookup"><span data-stu-id="079e9-110">Must be a valid XML identifier.</span></span> <span data-ttu-id="079e9-111">Дополнительные сведения см. в разделе [Имена объявленных XML-элементов и атрибутов](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="079e9-111">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="079e9-112">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="079e9-112">Required.</span></span> <span data-ttu-id="079e9-113">Строка, идентифицирующая импортируемое пространство имен XML.</span><span class="sxs-lookup"><span data-stu-id="079e9-113">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="079e9-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="079e9-114">Remarks</span></span>

<span data-ttu-id="079e9-115">Оператор можно использовать `Imports` для определения глобальных пространств имен XML, которые можно использовать с XML-литералами и свойствами осей XML, или как параметры, передаваемые `GetXmlNamespace` оператору.</span><span class="sxs-lookup"><span data-stu-id="079e9-115">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="079e9-116">(Сведения об использовании `Imports` инструкции для импорта псевдонима, который можно использовать при использовании имен типов в коде, см. в разделе [оператор Imports (пространство имен .NET и тип)](imports-statement-net-namespace-and-type.md).) Синтаксис объявления пространства имен XML с помощью `Imports` оператора идентичен синтаксису, используемому в XML.</span><span class="sxs-lookup"><span data-stu-id="079e9-116">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="079e9-117">Таким образом, можно скопировать объявление пространства имен из XML-файла и использовать его в `Imports` инструкции.</span><span class="sxs-lookup"><span data-stu-id="079e9-117">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="079e9-118">Префиксы пространства имен XML полезны, если требуется многократно создавать XML-элементы из одного и того же пространства имен.</span><span class="sxs-lookup"><span data-stu-id="079e9-118">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="079e9-119">Префикс пространства имен XML, объявленный с помощью `Imports` инструкции, является глобальным в том смысле, что он доступен для всего кода в файле.</span><span class="sxs-lookup"><span data-stu-id="079e9-119">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="079e9-120">Его можно использовать при создании литералов XML-элементов и при доступе к свойствам осей XML.</span><span class="sxs-lookup"><span data-stu-id="079e9-120">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="079e9-121">Дополнительные сведения см. в разделе [литерал XML-элемента](../xml-literals/xml-element-literal.md) и [Свойства оси XML](../xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="079e9-121">For more information, see [XML Element Literal](../xml-literals/xml-element-literal.md) and [XML Axis Properties](../xml-axis/index.md).</span></span>

<span data-ttu-id="079e9-122">Если определено глобальное пространство имен XML без префикса пространства имен (например, `Imports <xmlns="http://SomeNameSpace>"` ), это пространство имен считается пространством имен XML по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="079e9-122">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="079e9-123">Пространство имен XML по умолчанию используется для любых литералов XML-элементов или свойств оси атрибутов XML, которые явно не задают пространство имен.</span><span class="sxs-lookup"><span data-stu-id="079e9-123">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="079e9-124">Пространство имен по умолчанию также используется, если указанное пространство имен представляет собой пустое пространство имен (то есть `xmlns=""` ).</span><span class="sxs-lookup"><span data-stu-id="079e9-124">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="079e9-125">Пространство имен XML по умолчанию не применяется к атрибутам XML в XML-литералах или к свойствам оси атрибутов XML, не имеющим пространства имен.</span><span class="sxs-lookup"><span data-stu-id="079e9-125">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="079e9-126">Пространства имен XML, определенные в XML-литерале, которые называются *локальными пространствами имен XML*, имеют приоритет над пространствами имен XML, которые определены `Imports` инструкцией как глобальные.</span><span class="sxs-lookup"><span data-stu-id="079e9-126">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="079e9-127">Пространства имен XML, определенные `Imports` инструкцией, имеют приоритет над пространствами имен XML, импортированными для проекта Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="079e9-127">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="079e9-128">Если XML-литерал определяет пространство имен XML, это локальное пространство имен не применяется к внедренным выражениям.</span><span class="sxs-lookup"><span data-stu-id="079e9-128">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="079e9-129">Глобальные пространства имен XML следуют тем же правилам области и определения, что и платформа .NET Framework пространства имен.</span><span class="sxs-lookup"><span data-stu-id="079e9-129">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="079e9-130">В результате можно включить `Imports` инструкцию для определения глобального пространства имен XML в любом месте, где можно импортировать платформа .NET Framework пространство имен.</span><span class="sxs-lookup"><span data-stu-id="079e9-130">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="079e9-131">Сюда входят файлы кода и импортированные пространства имен на уровне проекта.</span><span class="sxs-lookup"><span data-stu-id="079e9-131">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="079e9-132">Сведения об импортированных пространствах имен на уровне проекта см. в разделе [Страница "ссылки" в конструкторе проектов (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="079e9-132">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="079e9-133">Каждый исходный файл может содержать любое количество `Imports` инструкций.</span><span class="sxs-lookup"><span data-stu-id="079e9-133">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="079e9-134">Они должны следовать объявлениям параметров, таким как `Option Strict` оператор, и должны предшествовать объявлениям элементов программирования, таким как `Module` операторы или `Class` .</span><span class="sxs-lookup"><span data-stu-id="079e9-134">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="079e9-135">Пример</span><span class="sxs-lookup"><span data-stu-id="079e9-135">Example</span></span>

<span data-ttu-id="079e9-136">В следующем примере выполняется импорт пространства имен XML по умолчанию и пространства имен XML, определенного префиксом `ns` .</span><span class="sxs-lookup"><span data-stu-id="079e9-136">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="079e9-137">Затем он создает литералы XML, которые используют оба пространства имен.</span><span class="sxs-lookup"><span data-stu-id="079e9-137">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="079e9-138">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="079e9-138">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="079e9-139">Пример</span><span class="sxs-lookup"><span data-stu-id="079e9-139">Example</span></span>

<span data-ttu-id="079e9-140">В следующем примере выполняется импорт префикса пространства имен XML `ns` .</span><span class="sxs-lookup"><span data-stu-id="079e9-140">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="079e9-141">Затем он создает XML-литерал, использующий префикс пространства имен, и отображает окончательную форму элемента.</span><span class="sxs-lookup"><span data-stu-id="079e9-141">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="079e9-142">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="079e9-142">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="079e9-143">Обратите внимание, что компилятор преобразует префикс пространства имен XML из глобального префикса в локальное определение префикса.</span><span class="sxs-lookup"><span data-stu-id="079e9-143">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="079e9-144">Пример</span><span class="sxs-lookup"><span data-stu-id="079e9-144">Example</span></span>

<span data-ttu-id="079e9-145">В следующем примере выполняется импорт префикса пространства имен XML `ns` .</span><span class="sxs-lookup"><span data-stu-id="079e9-145">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="079e9-146">Затем префикс пространства имен используется для создания литерала XML и доступа к первому дочернему узлу с полным именем `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="079e9-146">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="079e9-147">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="079e9-147">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="079e9-148">См. также</span><span class="sxs-lookup"><span data-stu-id="079e9-148">See also</span></span>

- [<span data-ttu-id="079e9-149">XML-литерал элемента</span><span class="sxs-lookup"><span data-stu-id="079e9-149">XML Element Literal</span></span>](../xml-literals/xml-element-literal.md)
- [<span data-ttu-id="079e9-150">Свойства оси XML</span><span class="sxs-lookup"><span data-stu-id="079e9-150">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="079e9-151">Имена объявленных элементов и атрибутов XML</span><span class="sxs-lookup"><span data-stu-id="079e9-151">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="079e9-152">Оператор GetXmlNamespace</span><span class="sxs-lookup"><span data-stu-id="079e9-152">GetXmlNamespace Operator</span></span>](../operators/getxmlnamespace-operator.md)
