---
title: Написание настраиваемых атрибутов
description: Разработка настраиваемых атрибутов в .NET. Настраиваемые атрибуты — это классы, прямо или косвенно наследуемые от System.Attribute.
ms.date: 07/17/2018
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
ms.openlocfilehash: e3c97f28a05f2e5396872fe808cae0d48d5a4824
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727007"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="f9ec3-104">Написание настраиваемых атрибутов</span><span class="sxs-lookup"><span data-stu-id="f9ec3-104">Writing Custom Attributes</span></span>

<span data-ttu-id="f9ec3-105">Чтобы создавать собственные атрибуты, совсем не обязательно в совершенстве овладевать множеством новых понятий.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-105">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="f9ec3-106">Если вы знакомы с объектно-ориентированным программированием и знаете, как создавать классы, вы уже обладаете почти всеми нужными знаниями.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-106">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="f9ec3-107">Настраиваемые атрибуты, в сущности, представляют собой традиционные классы, прямо или косвенно наследующие от <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-107">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f9ec3-108">Подобно традиционным классам настраиваемые атрибуты содержат методы, хранящие и извлекающие данные.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-108">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="f9ec3-109">Ниже приведены основные этапы правильно выстроенного процесса разработки классов настраиваемых атрибутов.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-109">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="f9ec3-110">Применение атрибута AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="f9ec3-110">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="f9ec3-111">Объявление класса атрибута</span><span class="sxs-lookup"><span data-stu-id="f9ec3-111">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="f9ec3-112">Объявление конструкторов</span><span class="sxs-lookup"><span data-stu-id="f9ec3-112">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="f9ec3-113">Объявление свойств</span><span class="sxs-lookup"><span data-stu-id="f9ec3-113">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="f9ec3-114">В этом разделе описано каждое из этих действий. В конце приведен [пример настраиваемого атрибута](#custom-attribute-example).</span><span class="sxs-lookup"><span data-stu-id="f9ec3-114">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="f9ec3-115">Применение атрибута AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="f9ec3-115">Applying the AttributeUsageAttribute</span></span>  

 <span data-ttu-id="f9ec3-116">Объявление настраиваемого атрибута начинается с <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, что определяет некоторые ключевые характеристики класса атрибута.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-116">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="f9ec3-117">Например, можно указать, может ли атрибут быть унаследован другими классами, или указать элементы языка, к которым может применяться этот атрибут.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-117">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="f9ec3-118">В следующем фрагменте кода демонстрируется использование <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-118">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="f9ec3-119">В <xref:System.AttributeUsageAttribute> есть три члена, которые важны для создания настраиваемых атрибутов: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property) и [AllowMultiple](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="f9ec3-119">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="f9ec3-120">Член AttributeTargets</span><span class="sxs-lookup"><span data-stu-id="f9ec3-120">AttributeTargets Member</span></span>  

 <span data-ttu-id="f9ec3-121">В предыдущем примере использовался элемент <xref:System.AttributeTargets.All?displayProperty=nameWithType>, указывающий, что этот атрибут может применяться ко всем элементам программы.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-121">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="f9ec3-122">Можно также задать <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, чтобы атрибут применялся только к классам, или <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, чтобы атрибут применялся только к методам.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-122">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="f9ec3-123">Подобным образом с помощью настраиваемых атрибутов можно выделить любые элементы программы с целью их последующего описания.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-123">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="f9ec3-124">Вы также можете передать несколько значений <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-124">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="f9ec3-125">В следующем фрагменте кода задается применение настраиваемого атрибута к любому классу или методу.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-125">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="f9ec3-126">Свойство Inherited</span><span class="sxs-lookup"><span data-stu-id="f9ec3-126">Inherited Property</span></span>  

 <span data-ttu-id="f9ec3-127">Свойство <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> указывает, может ли атрибут быть унаследован классами, производными от класса, к которому этот атрибут применен.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-127">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="f9ec3-128">Это свойство принимает флаг `true` (по умолчанию) или `false`.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-128">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="f9ec3-129">В следующем примере в классе `MyAttribute` для свойства <xref:System.AttributeUsageAttribute.Inherited%2A> по умолчанию указано значение `true`, а в классе `YourAttribute` для свойства <xref:System.AttributeUsageAttribute.Inherited%2A> указано значение `false`.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-129">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="f9ec3-130">Затем эти два атрибута применяются к методу в базовом классе `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-130">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="f9ec3-131">Наконец, класс `YourClass` наследуется от базового класса `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-131">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="f9ec3-132">Метод `MyMethod` использует атрибут `MyAttribute`, но не `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-132">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="f9ec3-133">Свойство AllowMultiple</span><span class="sxs-lookup"><span data-stu-id="f9ec3-133">AllowMultiple Property</span></span>  

 <span data-ttu-id="f9ec3-134">Свойство <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> указывает, можно ли применять к элементу несколько экземпляров атрибута.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-134">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="f9ec3-135">Если его значение равно `true`, допускается существование нескольких экземпляров. Если значение равно `false` (по умолчанию), можно использовать только один экземпляр.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-135">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="f9ec3-136">В следующем примере в классе `MyAttribute` для свойства <xref:System.AttributeUsageAttribute.AllowMultiple%2A> задано значение `false`, а для `YourAttribute` — `true`.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-136">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="f9ec3-137">При применении нескольких экземпляров этих атрибутов атрибут `MyAttribute` вызывает ошибку компилятора.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-137">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="f9ec3-138">В следующем примере кода показано правильное использование атрибута `YourAttribute` и неправильное использование атрибута `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-138">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="f9ec3-139">Если оба свойства <xref:System.AttributeUsageAttribute.AllowMultiple%2A> и <xref:System.AttributeUsageAttribute.Inherited%2A> имеют значение `true`, то класс, наследуемый от другого класса, может наследовать атрибуты и иметь дополнительные экземпляры атрибута, применяемого в этом же дочернем классе.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-139">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="f9ec3-140">Если <xref:System.AttributeUsageAttribute.AllowMultiple%2A> имеет значение `false`, значения атрибутов в родительском классе будут перезаписаны новыми экземплярами того же самого атрибута в дочернем классе.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-140">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="f9ec3-141">Объявление класса атрибута</span><span class="sxs-lookup"><span data-stu-id="f9ec3-141">Declaring the Attribute Class</span></span>  

 <span data-ttu-id="f9ec3-142">После применения <xref:System.AttributeUsageAttribute>можно начать определение характеристик атрибута.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-142">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="f9ec3-143">Объявление класса атрибута выглядит аналогично объявлению традиционного класса, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-143">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="f9ec3-144">В этом определении атрибута демонстрируются следующие моменты.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-144">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="f9ec3-145">Классы атрибутов должны объявляться как открытые классы.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-145">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="f9ec3-146">В соответствии с соглашением имя класса атрибута должно завершаться словом **Attribute**.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-146">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="f9ec3-147">Это условие не обязательно, но рекомендуется для повышения удобства чтения.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-147">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="f9ec3-148">При применении атрибута использование слова Attribute является необязательным.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-148">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="f9ec3-149">Все классы атрибутов должны прямо или косвенно наследовать от класса <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-149">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f9ec3-150">В Microsoft Visual Basic все классы настраиваемых атрибутов должны иметь атрибут <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-150">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="f9ec3-151">Объявление конструкторов</span><span class="sxs-lookup"><span data-stu-id="f9ec3-151">Declaring Constructors</span></span>  

 <span data-ttu-id="f9ec3-152">Атрибуты инициализируются с помощью конструкторов точно так же, как и традиционные классы.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-152">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="f9ec3-153">В следующем фрагменте кода показан типичный конструктор атрибута.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-153">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="f9ec3-154">Этот открытый конструктор получает параметр и устанавливает его значение равным переменной-члену.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-154">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="f9ec3-155">Чтобы использовать различные сочетания значений, можно выполнить перегрузку конструктора.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-155">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="f9ec3-156">Если для класса настраиваемого атрибута также определяется и [свойство](/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) , при инициализации атрибута можно использовать сочетание именованных и позиционных параметров.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-156">If you also define a [property](/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="f9ec3-157">Как правило, все обязательные параметры определяются как позиционные, а все необязательные — как именованные.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-157">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="f9ec3-158">В этом случае атрибут нельзя инициализировать без обязательного параметра.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-158">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="f9ec3-159">Все остальные параметры являются необязательными.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-159">All other parameters are optional.</span></span> <span data-ttu-id="f9ec3-160">Обратите внимание, что в Visual Basic конструкторы для классов атрибутов не могут использовать аргумент ParamArray.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-160">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="f9ec3-161">В следующем примере кода показано, как атрибут, использующий приведенный выше конструктор, можно использовать с обязательными и необязательными параметрами.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-161">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="f9ec3-162">Предполагается, что этот атрибут имеет один обязательный логический параметр и одно необязательное строковое свойство.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-162">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="f9ec3-163">Объявление свойств</span><span class="sxs-lookup"><span data-stu-id="f9ec3-163">Declaring Properties</span></span>  

 <span data-ttu-id="f9ec3-164">Если необходимо определить именованный параметр или предоставить простой способ получения значений, хранящихся в атрибуте, можно объявить [свойство](/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="f9ec3-164">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="f9ec3-165">Свойства атрибута следует объявлять как открытые сущности с описанием типа данных, который будет возвращен.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-165">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="f9ec3-166">Определите переменную, которая будет хранить значение свойства, и свяжите ее с методами **get** и **set** .</span><span class="sxs-lookup"><span data-stu-id="f9ec3-166">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="f9ec3-167">В следующем примере кода показана реализация простого свойства в атрибуте.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-167">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="f9ec3-168">пример настраиваемого атрибута</span><span class="sxs-lookup"><span data-stu-id="f9ec3-168">Custom Attribute Example</span></span>  

 <span data-ttu-id="f9ec3-169">В этом разделе используются приведенные выше сведения и демонстрируется пример создания простого атрибута, содержащего данные об авторе раздела кода.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-169">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="f9ec3-170">Атрибут в этом примере хранит имя и уровень программиста, а также данные об изменениях, внесенных в код.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-170">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="f9ec3-171">Для хранения текущих сохраняемых значений в нем используются три закрытые переменные.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-171">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="f9ec3-172">Каждая переменная представлена открытым свойством, которое возвращает и задает значения.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-172">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="f9ec3-173">Наконец, в примере определяется конструктор с двумя обязательными параметрами.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-173">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="f9ec3-174">Этот атрибут можно применять с помощью полного имени `DeveloperAttribute`или сокращенного имени `Developer`одним из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-174">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="f9ec3-175">В первом примере этот атрибут применяется только с обязательными именованными параметрами, а во втором примере атрибут применяется и с обязательными, и с необязательными параметрами.</span><span class="sxs-lookup"><span data-stu-id="f9ec3-175">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ec3-176">См. также</span><span class="sxs-lookup"><span data-stu-id="f9ec3-176">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="f9ec3-177">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f9ec3-177">Attributes</span></span>](index.md)
