---
description: 'Дополнительные сведения: литерал XML-элемента (Visual Basic)'
title: XML-литерал элемента
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: dfc78beded5c6f472b67fa272835ef0aa29d0187
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787543"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="744e5-103">Литеральное представление XML-элемента (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="744e5-103">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="744e5-104">Литерал, представляющий <xref:System.Xml.Linq.XElement> объект.</span><span class="sxs-lookup"><span data-stu-id="744e5-104">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="744e5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="744e5-105">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="744e5-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="744e5-106">Parts</span></span>

- `<`

  <span data-ttu-id="744e5-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-107">Required.</span></span> <span data-ttu-id="744e5-108">Открывает начальный тег элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-108">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="744e5-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-109">Required.</span></span> <span data-ttu-id="744e5-110">Имя элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-110">Name of the element.</span></span> <span data-ttu-id="744e5-111">Формат может быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="744e5-111">The format is one of the following:</span></span>

  - <span data-ttu-id="744e5-112">Литеральный текст для имени элемента в форме `[ePrefix:]eName` , где:</span><span class="sxs-lookup"><span data-stu-id="744e5-112">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="744e5-113">Отделение</span><span class="sxs-lookup"><span data-stu-id="744e5-113">Part</span></span>|<span data-ttu-id="744e5-114">Описание</span><span class="sxs-lookup"><span data-stu-id="744e5-114">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="744e5-115">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-115">Optional.</span></span> <span data-ttu-id="744e5-116">Префикс пространства имен XML для элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-116">XML namespace prefix for the element.</span></span> <span data-ttu-id="744e5-117">Должно быть глобальным пространством имен XML, которое определено с помощью `Imports` инструкции в файле или на уровне проекта, или локального пространства имен XML, определенного в этом элементе или в родительском элементе.</span><span class="sxs-lookup"><span data-stu-id="744e5-117">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="744e5-118">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-118">Required.</span></span> <span data-ttu-id="744e5-119">Имя элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-119">Name of the element.</span></span> <span data-ttu-id="744e5-120">Формат может быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="744e5-120">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="744e5-121">— Литеральный текст.</span><span class="sxs-lookup"><span data-stu-id="744e5-121">- Literal text.</span></span> <span data-ttu-id="744e5-122">См. [Имена объявленных XML-элементов и атрибутов](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="744e5-122">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="744e5-123">— Внедренное выражение формы `<%= eNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="744e5-123">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="744e5-124">Тип `eNameExp` должен быть `String` или типом, неявно преобразуемым в <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="744e5-124">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="744e5-125">Внедренное выражение формы `<%= nameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="744e5-125">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="744e5-126">Тип `nameExp` должен быть `String` или типом, неявно преобразуемым в <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="744e5-126">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="744e5-127">Внедренное выражение не допускается в закрывающем теге элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-127">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="744e5-128">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-128">Optional.</span></span> <span data-ttu-id="744e5-129">Список атрибутов, объявленных в литерале.</span><span class="sxs-lookup"><span data-stu-id="744e5-129">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="744e5-130">Каждый `attribute` из них имеет один из следующих синтаксисов:</span><span class="sxs-lookup"><span data-stu-id="744e5-130">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="744e5-131">Назначение атрибута в форме `[aPrefix:]aName=aValue` , где:</span><span class="sxs-lookup"><span data-stu-id="744e5-131">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="744e5-132">Отделение</span><span class="sxs-lookup"><span data-stu-id="744e5-132">Part</span></span>|<span data-ttu-id="744e5-133">Описание</span><span class="sxs-lookup"><span data-stu-id="744e5-133">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="744e5-134">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-134">Optional.</span></span> <span data-ttu-id="744e5-135">Префикс пространства имен XML для атрибута.</span><span class="sxs-lookup"><span data-stu-id="744e5-135">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="744e5-136">Должно быть глобальным пространством имен XML, определенным `Imports` в операторе, или локальным пространством имен XML, которое определено в этом элементе или в родительском элементе.</span><span class="sxs-lookup"><span data-stu-id="744e5-136">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="744e5-137">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-137">Required.</span></span> <span data-ttu-id="744e5-138">Имя атрибута.</span><span class="sxs-lookup"><span data-stu-id="744e5-138">Name of the attribute.</span></span> <span data-ttu-id="744e5-139">Формат может быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="744e5-139">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="744e5-140">— Литеральный текст.</span><span class="sxs-lookup"><span data-stu-id="744e5-140">- Literal text.</span></span> <span data-ttu-id="744e5-141">См. [Имена объявленных XML-элементов и атрибутов](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="744e5-141">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="744e5-142">— Внедренное выражение формы `<%= aNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="744e5-142">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="744e5-143">Тип `aNameExp` должен быть `String` или типом, неявно преобразуемым в <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="744e5-143">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="744e5-144">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-144">Optional.</span></span> <span data-ttu-id="744e5-145">Значение атрибута.</span><span class="sxs-lookup"><span data-stu-id="744e5-145">Value of the attribute.</span></span> <span data-ttu-id="744e5-146">Формат может быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="744e5-146">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="744e5-147">— Литеральный текст, заключенный в кавычки.</span><span class="sxs-lookup"><span data-stu-id="744e5-147">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="744e5-148">— Внедренное выражение формы `<%= aValueExp %>` .</span><span class="sxs-lookup"><span data-stu-id="744e5-148">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="744e5-149">Разрешен любой тип.</span><span class="sxs-lookup"><span data-stu-id="744e5-149">Any type is allowed.</span></span>|

  - <span data-ttu-id="744e5-150">Внедренное выражение формы `<%= aExp %>` .</span><span class="sxs-lookup"><span data-stu-id="744e5-150">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="744e5-151">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-151">Optional.</span></span> <span data-ttu-id="744e5-152">Указывает, что элемент является пустым элементом без содержимого.</span><span class="sxs-lookup"><span data-stu-id="744e5-152">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="744e5-153">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-153">Required.</span></span> <span data-ttu-id="744e5-154">Завершает начальный или пустой тег элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-154">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="744e5-155">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-155">Optional.</span></span> <span data-ttu-id="744e5-156">Содержимое элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-156">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="744e5-157">Каждый `content` из них может быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="744e5-157">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="744e5-158">Текст литерала.</span><span class="sxs-lookup"><span data-stu-id="744e5-158">Literal text.</span></span> <span data-ttu-id="744e5-159">Все пробелы в `elementContents` значительной мере имеют литеральный текст.</span><span class="sxs-lookup"><span data-stu-id="744e5-159">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="744e5-160">Внедренное выражение формы `<%= contentExp %>` .</span><span class="sxs-lookup"><span data-stu-id="744e5-160">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="744e5-161">Литерал XML-элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-161">XML element literal.</span></span>

  - <span data-ttu-id="744e5-162">XML-литерал комментария.</span><span class="sxs-lookup"><span data-stu-id="744e5-162">XML comment literal.</span></span> <span data-ttu-id="744e5-163">См. [XML-литерал комментария](xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="744e5-163">See [XML Comment Literal](xml-comment-literal.md).</span></span>

  - <span data-ttu-id="744e5-164">Литерал инструкции обработки XML.</span><span class="sxs-lookup"><span data-stu-id="744e5-164">XML processing instruction literal.</span></span> <span data-ttu-id="744e5-165">См. раздел [XML-текст инструкции по обработке](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="744e5-165">See [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="744e5-166">XML-литерал CDATA.</span><span class="sxs-lookup"><span data-stu-id="744e5-166">XML CDATA literal.</span></span> <span data-ttu-id="744e5-167">См. [XML CDATA Literal](xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="744e5-167">See [XML CDATA Literal](xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="744e5-168">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="744e5-168">Optional.</span></span> <span data-ttu-id="744e5-169">Представляет закрывающий тег для элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-169">Represents the closing tag for the element.</span></span> <span data-ttu-id="744e5-170">Необязательный `name` параметр не допускается, если он является результатом внедренного выражения.</span><span class="sxs-lookup"><span data-stu-id="744e5-170">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="744e5-171">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="744e5-171">Return Value</span></span>

<span data-ttu-id="744e5-172">Объект <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="744e5-172">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="744e5-173">Remarks</span><span class="sxs-lookup"><span data-stu-id="744e5-173">Remarks</span></span>

<span data-ttu-id="744e5-174">Для создания объектов в коде можно использовать синтаксис литерала XML-элемента <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="744e5-174">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="744e5-175">XML-литерал может охватывать несколько строк без использования символов продолжения строки.</span><span class="sxs-lookup"><span data-stu-id="744e5-175">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="744e5-176">Эта функция позволяет копировать содержимое из XML-документа и вставлять его непосредственно в Visual Basic программу.</span><span class="sxs-lookup"><span data-stu-id="744e5-176">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="744e5-177">Внедренные выражения формы `<%= exp %>` позволяют добавлять динамическую информацию в литерал XML-элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-177">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="744e5-178">Дополнительные сведения см. [в разделе внедренные выражения в XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="744e5-178">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="744e5-179">Компилятор Visual Basic преобразует литерал XML-элемента в вызовы <xref:System.Xml.Linq.XElement.%23ctor%2A> конструктора и, если это необходимо, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> конструктор.</span><span class="sxs-lookup"><span data-stu-id="744e5-179">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="744e5-180">Пространства имен XML</span><span class="sxs-lookup"><span data-stu-id="744e5-180">XML Namespaces</span></span>

<span data-ttu-id="744e5-181">Префиксы пространства имен XML полезны, когда необходимо создать XML-литералы с элементами из одного и того же пространства имен много раз в коде.</span><span class="sxs-lookup"><span data-stu-id="744e5-181">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="744e5-182">Можно использовать глобальные префиксы пространства имен XML, которые определяются с помощью `Imports` инструкции или локальных префиксов, которые определяются с помощью `xmlns:xmlPrefix="xmlNamespace"` синтаксиса атрибута.</span><span class="sxs-lookup"><span data-stu-id="744e5-182">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="744e5-183">Дополнительные сведения см. в разделе [оператор Imports (пространство имен XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="744e5-183">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="744e5-184">В соответствии с правилами области для пространств имен XML локальные префиксы имеют приоритет над глобальными префиксами.</span><span class="sxs-lookup"><span data-stu-id="744e5-184">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="744e5-185">Однако если XML-литерал определяет пространство имен XML, это пространство имен недоступно для выражений, которые отображаются во внедренном выражении.</span><span class="sxs-lookup"><span data-stu-id="744e5-185">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="744e5-186">Внедренное выражение может обращаться только к глобальному пространству имен XML.</span><span class="sxs-lookup"><span data-stu-id="744e5-186">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="744e5-187">Компилятор Visual Basic преобразует каждое глобальное пространство имен XML, используемое XML-литералом, в одно локальное определение пространства имен в созданном коде.</span><span class="sxs-lookup"><span data-stu-id="744e5-187">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="744e5-188">Глобальные пространства имен XML, которые не используются, не отображаются в созданном коде.</span><span class="sxs-lookup"><span data-stu-id="744e5-188">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="744e5-189">Пример</span><span class="sxs-lookup"><span data-stu-id="744e5-189">Example</span></span>

<span data-ttu-id="744e5-190">В следующем примере показано, как создать простой XML-элемент с двумя вложенными пустыми элементами.</span><span class="sxs-lookup"><span data-stu-id="744e5-190">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="744e5-191">В примере отображается следующий текст.</span><span class="sxs-lookup"><span data-stu-id="744e5-191">The example displays the following text.</span></span> <span data-ttu-id="744e5-192">Обратите внимание, что литерал сохраняет структуру пустых элементов.</span><span class="sxs-lookup"><span data-stu-id="744e5-192">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="744e5-193">Пример</span><span class="sxs-lookup"><span data-stu-id="744e5-193">Example</span></span>

<span data-ttu-id="744e5-194">В следующем примере показано, как использовать внедренные выражения для именования элемента и создания атрибутов.</span><span class="sxs-lookup"><span data-stu-id="744e5-194">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="744e5-195">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="744e5-195">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="744e5-196">Пример</span><span class="sxs-lookup"><span data-stu-id="744e5-196">Example</span></span>

<span data-ttu-id="744e5-197">В следующем примере `ns` объявляется как префикс пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="744e5-197">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="744e5-198">Затем он использует префикс пространства имен для создания XML-литерала и отображает окончательную форму элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-198">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="744e5-199">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="744e5-199">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="744e5-200">Обратите внимание, что компилятор преобразует префикс глобального пространства имен XML в определение префикса для пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="744e5-200">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="744e5-201">\<ns:middle>Элемент переопределяет префикс пространства имен XML для \<ns:inner1> элемента.</span><span class="sxs-lookup"><span data-stu-id="744e5-201">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="744e5-202">Однако \<ns:inner2> элемент использует пространство имен, определенное `Imports` инструкцией.</span><span class="sxs-lookup"><span data-stu-id="744e5-202">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="744e5-203">См. также</span><span class="sxs-lookup"><span data-stu-id="744e5-203">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="744e5-204">Имена объявленных элементов и атрибутов XML</span><span class="sxs-lookup"><span data-stu-id="744e5-204">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="744e5-205">XML-литерал комментария</span><span class="sxs-lookup"><span data-stu-id="744e5-205">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="744e5-206">XML-литерал CDATA</span><span class="sxs-lookup"><span data-stu-id="744e5-206">XML CDATA Literal</span></span>](xml-cdata-literal.md)
- [<span data-ttu-id="744e5-207">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="744e5-207">XML Literals</span></span>](index.md)
- [<span data-ttu-id="744e5-208">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="744e5-208">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="744e5-209">Встроенные выражения в XML</span><span class="sxs-lookup"><span data-stu-id="744e5-209">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="744e5-210">Оператор Imports (пространство имен XML)</span><span class="sxs-lookup"><span data-stu-id="744e5-210">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
