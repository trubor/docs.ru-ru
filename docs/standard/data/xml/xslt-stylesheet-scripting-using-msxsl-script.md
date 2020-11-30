---
title: Создание скриптов таблиц стилей XSLT с помощью <msxsl:script>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 206a659656f1019af1540b9b2476ae7fe9ba93eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685114"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="63618-102">Использование скриптов таблиц стилей XSLT\<msxsl:script></span><span class="sxs-lookup"><span data-stu-id="63618-102">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>

<span data-ttu-id="63618-103">Класс <xref:System.Xml.Xsl.XslTransform> поддерживает внедрение скриптов с помощью элемента `script`.</span><span class="sxs-lookup"><span data-stu-id="63618-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63618-104">Класс <xref:System.Xml.Xsl.XslTransform> явлется устаревшим в версии .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="63618-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="63618-105">Можно выполнять XSLT-преобразование, используя класс <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="63618-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="63618-106">См. дополнительные сведения об [использовании класса XslCompiledTransform](using-the-xslcompiledtransform-class.md) и [миграции из класса XslTransform](migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="63618-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="63618-107">Класс <xref:System.Xml.Xsl.XslTransform> поддерживает внедрение скриптов с помощью элемента `script`.</span><span class="sxs-lookup"><span data-stu-id="63618-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="63618-108">При загрузке таблицы стилей любые определенные функции компилируются на язык MSIL путем помещения в определение класса и в результате не имеют потерь производительности.</span><span class="sxs-lookup"><span data-stu-id="63618-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="63618-109">Элемент `<msxsl:script>` определен ниже:</span><span class="sxs-lookup"><span data-stu-id="63618-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="63618-110">, где `msxsl` является префиксом, привязанным к пространству имен `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="63618-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="63618-111">Атрибут `language` не является обязательным, но если он указан, его значение должно быть одним из следующих: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic` или `CSharp`.</span><span class="sxs-lookup"><span data-stu-id="63618-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="63618-112">Если не указан, значение по умолчанию - JScript.</span><span class="sxs-lookup"><span data-stu-id="63618-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="63618-113">Атрибут `language-name` нечувствителен к регистру, так что значения «JavaScript» и «javascript» не различаются.</span><span class="sxs-lookup"><span data-stu-id="63618-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="63618-114">Атрибут `implements-prefix` обязателен.</span><span class="sxs-lookup"><span data-stu-id="63618-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="63618-115">Этот атрибут используется для объявления пространства имен и связывания его с блоком скрипта.</span><span class="sxs-lookup"><span data-stu-id="63618-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="63618-116">Значением этого атрибута является префикс, соответствующий пространству имен.</span><span class="sxs-lookup"><span data-stu-id="63618-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="63618-117">Пространство имен может быть определено где-то в таблице стилей.</span><span class="sxs-lookup"><span data-stu-id="63618-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="63618-118">Так как элемент `msxsl:script` принадлежит пространству имен `urn:schemas-microsoft-com:xslt`, таблица стилей должна включать в себя декларацию пространства имен `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="63618-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="63618-119">Если вызывающий скрипт не имеет разрешения доступа <xref:System.Security.Permissions.SecurityPermissionFlag>, скрипт в таблице стилей никогда не будет скомпилирован и при вызове метода <xref:System.Xml.Xsl.XslTransform.Load%2A> произойдет ошибка.</span><span class="sxs-lookup"><span data-stu-id="63618-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="63618-120">Если вызывающий имеет разрешение доступа `UnmanagedCode`, скрипт компилируется, но разрешенные операции зависят от свидетельства, которое указывается во время загрузки.</span><span class="sxs-lookup"><span data-stu-id="63618-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="63618-121">При использовании одного из методов <xref:System.Xml.Xsl.XslTransform.Load%2A>, которые принимают объект <xref:System.Xml.XmlReader> или объект <xref:System.Xml.XPath.XPathNavigator> для загрузки таблицы стилей, необходимо использовать перегрузку метода <xref:System.Xml.Xsl.XslTransform.Load%2A>, который принимает параметр <xref:System.Security.Policy.Evidence> как один из аргументов.</span><span class="sxs-lookup"><span data-stu-id="63618-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="63618-122">Чтобы получить свидетельство, вызывающий должен иметь разрешение <xref:System.Security.Permissions.SecurityPermissionFlag>, чтобы предоставить `Evidence` сборке скрипта.</span><span class="sxs-lookup"><span data-stu-id="63618-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="63618-123">Если вызывающий не имеет данного разрешения, то он может задать для параметра `Evidence` значение `null`.</span><span class="sxs-lookup"><span data-stu-id="63618-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="63618-124">Это приводит к ошибке при вызове функции <xref:System.Xml.Xsl.XslTransform.Load%2A>, если функция находит скрипт.</span><span class="sxs-lookup"><span data-stu-id="63618-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="63618-125">Разрешение `ControlEvidence` считается очень важным разрешением, которое должно предоставляться только коду с высокой степенью доверия.</span><span class="sxs-lookup"><span data-stu-id="63618-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="63618-126">Чтобы получить свидетельство из сборки используется метод `this.GetType().Assembly.Evidence`.</span><span class="sxs-lookup"><span data-stu-id="63618-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="63618-127">Чтобы получить свидетельство из универсального идентификатора ресурсов (URI) используется метод `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span><span class="sxs-lookup"><span data-stu-id="63618-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="63618-128">При использовании методов <xref:System.Xml.Xsl.XslTransform.Load%2A>, которые принимают объект <xref:System.Xml.XmlResolver>, но не объект `Evidence`, зона безопасности для сборки имеет по умолчанию полный уровень доверия.</span><span class="sxs-lookup"><span data-stu-id="63618-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="63618-129">Дополнительные сведения см. в статьях <xref:System.Security.SecurityZone> и [Именованные наборы разрешений](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="63618-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="63618-130">Функции можно объявлять внутри элемента `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="63618-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="63618-131">В следующей таблице показаны пространства имен, поддерживаемые по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="63618-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="63618-132">Можно использовать классы вне перечисленных пространств имен.</span><span class="sxs-lookup"><span data-stu-id="63618-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="63618-133">Однако эти классы должны указываться полными именами.</span><span class="sxs-lookup"><span data-stu-id="63618-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="63618-134">Пространства имен по умолчанию</span><span class="sxs-lookup"><span data-stu-id="63618-134">Default Namespaces</span></span>|<span data-ttu-id="63618-135">Описание</span><span class="sxs-lookup"><span data-stu-id="63618-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="63618-136">Система</span><span class="sxs-lookup"><span data-stu-id="63618-136">System</span></span>|<span data-ttu-id="63618-137">Системный класс.</span><span class="sxs-lookup"><span data-stu-id="63618-137">System class.</span></span>|  
|<span data-ttu-id="63618-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="63618-138">System.Collection</span></span>|<span data-ttu-id="63618-139">Классы коллекций.</span><span class="sxs-lookup"><span data-stu-id="63618-139">Collection classes.</span></span>|  
|<span data-ttu-id="63618-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="63618-140">System.Text</span></span>|<span data-ttu-id="63618-141">Классы текста.</span><span class="sxs-lookup"><span data-stu-id="63618-141">Text classes.</span></span>|  
|<span data-ttu-id="63618-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="63618-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="63618-143">Классы регулярных выражений.</span><span class="sxs-lookup"><span data-stu-id="63618-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="63618-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="63618-144">System.Xml</span></span>|<span data-ttu-id="63618-145">Основные классы XML.</span><span class="sxs-lookup"><span data-stu-id="63618-145">Core XML classes.</span></span>|  
|<span data-ttu-id="63618-146">System.Xml.Xsl;</span><span class="sxs-lookup"><span data-stu-id="63618-146">System.Xml.Xsl</span></span>|<span data-ttu-id="63618-147">Классы XSLT.</span><span class="sxs-lookup"><span data-stu-id="63618-147">XSLT classes.</span></span>|  
|<span data-ttu-id="63618-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="63618-148">System.Xml.XPath</span></span>|<span data-ttu-id="63618-149">Классы языка XPath.</span><span class="sxs-lookup"><span data-stu-id="63618-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="63618-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="63618-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="63618-151">Классы для скриптов Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="63618-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="63618-152">При объявлении функции она заключается в блок скрипта.</span><span class="sxs-lookup"><span data-stu-id="63618-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="63618-153">Таблицы стилей могут содержать несколько блоков скриптов, каждый из которых работает независимо от других.</span><span class="sxs-lookup"><span data-stu-id="63618-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="63618-154">Это значит, что в одном блоке скрипта нельзя вызвать функцию, определенную в другом блоке, если в них не объявлены одно и то же пространство имен и один и тот же язык скрипта.</span><span class="sxs-lookup"><span data-stu-id="63618-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="63618-155">Так как каждый блок скрипта может быть написан на своем языке, и блок анализируется в соответствии с грамматическими правилами средств синтаксического анализа языка, необходимо соблюдать правильный синтаксис используемого языка.</span><span class="sxs-lookup"><span data-stu-id="63618-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="63618-156">Например, в блоке скрипта C# будет ошибкой использовать узлы комментариев XML `<!-- an XML comment -->`.</span><span class="sxs-lookup"><span data-stu-id="63618-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="63618-157">Указанные аргументы и возвращаемые значения, определенные функциями скрипта, должны представлять собой один из типов XPath консорциума W3C или XSLT.</span><span class="sxs-lookup"><span data-stu-id="63618-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="63618-158">В следующей таблице приведены соответствующие типы W3C, эквивалентные классы (или типы) платформы .NET Framework, а также показано, является ли тип W3C типом XPath или типом XSLT.</span><span class="sxs-lookup"><span data-stu-id="63618-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="63618-159">Type</span><span class="sxs-lookup"><span data-stu-id="63618-159">Type</span></span>|<span data-ttu-id="63618-160">Эквивалентный класс (или тип) .NET Framework</span><span class="sxs-lookup"><span data-stu-id="63618-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="63618-161">Тип XPath или тип XSLT</span><span class="sxs-lookup"><span data-stu-id="63618-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="63618-162">Строка</span><span class="sxs-lookup"><span data-stu-id="63618-162">String</span></span>|<span data-ttu-id="63618-163">System.String</span><span class="sxs-lookup"><span data-stu-id="63618-163">System.String</span></span>|<span data-ttu-id="63618-164">XPath</span><span class="sxs-lookup"><span data-stu-id="63618-164">XPath</span></span>|  
|<span data-ttu-id="63618-165">логический</span><span class="sxs-lookup"><span data-stu-id="63618-165">Boolean</span></span>|<span data-ttu-id="63618-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="63618-166">System.Boolean</span></span>|<span data-ttu-id="63618-167">XPath</span><span class="sxs-lookup"><span data-stu-id="63618-167">XPath</span></span>|  
|<span data-ttu-id="63618-168">Число</span><span class="sxs-lookup"><span data-stu-id="63618-168">Number</span></span>|<span data-ttu-id="63618-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="63618-169">System.Double</span></span>|<span data-ttu-id="63618-170">XPath</span><span class="sxs-lookup"><span data-stu-id="63618-170">XPath</span></span>|  
|<span data-ttu-id="63618-171">Фрагмент дерева результатов</span><span class="sxs-lookup"><span data-stu-id="63618-171">Result Tree Fragment</span></span>|<span data-ttu-id="63618-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="63618-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="63618-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="63618-173">XSLT</span></span>|  
|<span data-ttu-id="63618-174">Набор узлов</span><span class="sxs-lookup"><span data-stu-id="63618-174">Node Set</span></span>|<span data-ttu-id="63618-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="63618-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="63618-176">XPath</span><span class="sxs-lookup"><span data-stu-id="63618-176">XPath</span></span>|  
  
 <span data-ttu-id="63618-177">Если функция скрипта использует один из следующих числовых типов: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single или Decimal, — они приводятся к типу Double, который преобразуется в тип number W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="63618-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="63618-178">Все другие типы принудительно приводятся к типу string с помощью метода `ToString`.</span><span class="sxs-lookup"><span data-stu-id="63618-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="63618-179">Если функция скрипта использует тип, отличный от перечисленных выше, или функция не компилируется при загрузке таблицы стилей в объект <xref:System.Xml.Xsl.XslTransform>, возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="63618-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="63618-180">При использовании элемента `msxsl:script` мы настоятельно рекомендуем размещать скрипт, независимо от языка, в раздел CDATA.</span><span class="sxs-lookup"><span data-stu-id="63618-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="63618-181">Например, следующий код XML показывает шаблон раздела CDATA, куда помещается код пользователя.</span><span class="sxs-lookup"><span data-stu-id="63618-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="63618-182">Настоятельно рекомендуется помещать все содержимое скрипта в секцию CDATA, так как операторы, идентификаторы или разделители для данного языка могут быть ошибочно интерпретированы как XML.</span><span class="sxs-lookup"><span data-stu-id="63618-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="63618-183">В следующем примере показано, как использовать логический оператор AND в скрипт.</span><span class="sxs-lookup"><span data-stu-id="63618-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="63618-184">Этот код вызывает исключение, так как амперсанды не экранированы.</span><span class="sxs-lookup"><span data-stu-id="63618-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="63618-185">Документ загружается как XML, и к тексту между тегами элемента `msxsl:script` не применяется никакая специальная обработка.</span><span class="sxs-lookup"><span data-stu-id="63618-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63618-186">Пример</span><span class="sxs-lookup"><span data-stu-id="63618-186">Example</span></span>  

 <span data-ttu-id="63618-187">В следующем примере используется внедренный скрипт для вычисления длины окружности по заданному радиусу.</span><span class="sxs-lookup"><span data-stu-id="63618-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a><span data-ttu-id="63618-188">Входные данные</span><span class="sxs-lookup"><span data-stu-id="63618-188">Input</span></span>  

 <span data-ttu-id="63618-189">number.xml</span><span class="sxs-lookup"><span data-stu-id="63618-189">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="63618-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="63618-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="63618-191">Вывод</span><span class="sxs-lookup"><span data-stu-id="63618-191">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>
```  
  
## <a name="see-also"></a><span data-ttu-id="63618-192">См. также</span><span class="sxs-lookup"><span data-stu-id="63618-192">See also</span></span>

- [<span data-ttu-id="63618-193">Реализация классом XslTransform XSLT-процессора</span><span class="sxs-lookup"><span data-stu-id="63618-193">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
