---
title: 'Зарезервированные атрибуты C#: Conditional, Obsolete, AttributeUsage'
ms.date: 04/09/2020
description: Компилятор интерпретирует эти атрибуты, чтобы они могли влиять на создаваемый им код.
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2020
ms.locfileid: "82021765"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="c64e7-103">Зарезервированные атрибуты: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="c64e7-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="c64e7-104">Эти атрибуты можно применять к элементам в коде.</span><span class="sxs-lookup"><span data-stu-id="c64e7-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="c64e7-105">Они добавляют к ним семантическое значение.</span><span class="sxs-lookup"><span data-stu-id="c64e7-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="c64e7-106">Компилятор использует эти семантические значения для изменения выходных данных и сообщения о возможных ошибках разработчиков, использующих код.</span><span class="sxs-lookup"><span data-stu-id="c64e7-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="c64e7-107">Атрибут `Conditional`</span><span class="sxs-lookup"><span data-stu-id="c64e7-107">`Conditional` attribute</span></span>

<span data-ttu-id="c64e7-108">Атрибут `Conditional` определяет зависимость выполнения метода от идентификатора предварительной обработки.</span><span class="sxs-lookup"><span data-stu-id="c64e7-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="c64e7-109">Атрибут `Conditional` является псевдонимом для <xref:System.Diagnostics.ConditionalAttribute> и может применяться к методу или классу атрибута.</span><span class="sxs-lookup"><span data-stu-id="c64e7-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="c64e7-110">В следующем примере атрибут `Conditional` применяется к методу для включения и отключения отображения диагностической информации для конкретной программы.</span><span class="sxs-lookup"><span data-stu-id="c64e7-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="c64e7-111">Если идентификатор `TRACE_ON` не определен, выходные данные трассировки не отображаются.</span><span class="sxs-lookup"><span data-stu-id="c64e7-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="c64e7-112">Поэкспериментируйте в интерактивном окне.</span><span class="sxs-lookup"><span data-stu-id="c64e7-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="c64e7-113">Атрибут `Conditional` часто используется с идентификатором `DEBUG` для включения функций трассировки и ведения журнала для отладочных сборок (но не сборок выпуска), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c64e7-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="c64e7-114">Когда вызывается метод, помеченный как условный, наличие или отсутствие заданного символа предварительной обработки определяет, включается вызов или пропускается.</span><span class="sxs-lookup"><span data-stu-id="c64e7-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="c64e7-115">Если этот символ определен, вызов включается; в противном случае вызов пропускается.</span><span class="sxs-lookup"><span data-stu-id="c64e7-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="c64e7-116">Условный метод должен быть методом в объявлении класса или структуры и должен иметь тип возвращаемого значения `void`.</span><span class="sxs-lookup"><span data-stu-id="c64e7-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="c64e7-117">Использование атрибута `Conditional` — это более понятная, элегантная и менее подверженная ошибкам альтернатива вложению методов в блоки `#if…#endif`.</span><span class="sxs-lookup"><span data-stu-id="c64e7-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="c64e7-118">Если метод содержит несколько атрибутов `Conditional`, вызов метода включается, если определен один условный символ или несколько (символы логически связаны с помощью оператора ИЛИ).</span><span class="sxs-lookup"><span data-stu-id="c64e7-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="c64e7-119">В следующем примере наличие `A` или `B` приведет к вызову метода.</span><span class="sxs-lookup"><span data-stu-id="c64e7-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="c64e7-120">Использование `Conditional` с классами атрибутов</span><span class="sxs-lookup"><span data-stu-id="c64e7-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="c64e7-121">Атрибут `Conditional` также может применяться к определению класса атрибута.</span><span class="sxs-lookup"><span data-stu-id="c64e7-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="c64e7-122">В следующем примере настраиваемый атрибут `Documentation` добавит сведения в метаданные, только если задано значение `DEBUG`.</span><span class="sxs-lookup"><span data-stu-id="c64e7-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="c64e7-123">Атрибут `Obsolete`</span><span class="sxs-lookup"><span data-stu-id="c64e7-123">`Obsolete` attribute</span></span>

<span data-ttu-id="c64e7-124">Атрибут `Obsolete` помечает элемент кода как больше не рекомендуемый для использования.</span><span class="sxs-lookup"><span data-stu-id="c64e7-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="c64e7-125">Использование сущности, помеченной как устаревшая, приводит к возникновению предупреждения или ошибки.</span><span class="sxs-lookup"><span data-stu-id="c64e7-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="c64e7-126">Атрибут `Obsolete` является атрибутом однократного использования и может применяться к любой сущности, допускающей использование атрибутов.</span><span class="sxs-lookup"><span data-stu-id="c64e7-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="c64e7-127">`Obsolete` является псевдонимом для <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c64e7-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="c64e7-128">В следующем примере атрибут `Obsolete` применяется к классу `A` и к методу `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="c64e7-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="c64e7-129">Поскольку для второго аргумента конструктора атрибутов, примененного к `B.OldMethod`, задано значение `true`, этот метод будет вызывать ошибку компилятора, тогда как при использовании класса `A` будет просто создаваться предупреждение.</span><span class="sxs-lookup"><span data-stu-id="c64e7-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="c64e7-130">При этом вызов `B.NewMethod` не создает предупреждений или ошибок.</span><span class="sxs-lookup"><span data-stu-id="c64e7-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="c64e7-131">Например, при использовании с предыдущими определениями следующий код создает два предупреждения и одну ошибку:</span><span class="sxs-lookup"><span data-stu-id="c64e7-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="c64e7-132">Строка, предоставленная в качестве первого аргумента конструктору атрибута, будет отображаться как часть предупреждения или ошибки.</span><span class="sxs-lookup"><span data-stu-id="c64e7-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="c64e7-133">Создается два предупреждения для класса `A`: одно для объявления ссылки на класс, а второе — для конструктора класса.</span><span class="sxs-lookup"><span data-stu-id="c64e7-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="c64e7-134">Атрибут `Obsolete` может использоваться без аргументов, однако рекомендуется включать пояснение о том, что следует использовать вместо него.</span><span class="sxs-lookup"><span data-stu-id="c64e7-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="c64e7-135">Атрибут `AttributeUsage`</span><span class="sxs-lookup"><span data-stu-id="c64e7-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="c64e7-136">Атрибут `AttributeUsage` определяет, как можно использовать пользовательский класс атрибутов.</span><span class="sxs-lookup"><span data-stu-id="c64e7-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="c64e7-137"><xref:System.AttributeUsageAttribute> — это атрибут, примененный к определениям настраиваемого атрибута.</span><span class="sxs-lookup"><span data-stu-id="c64e7-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="c64e7-138">С помощью атрибута `AttributeUsage` можно контролировать:</span><span class="sxs-lookup"><span data-stu-id="c64e7-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="c64e7-139">Какой атрибут элементов программы можно применить.</span><span class="sxs-lookup"><span data-stu-id="c64e7-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="c64e7-140">Если вы не ограничите использование, атрибут можно применить к любому из следующих элементов программы:</span><span class="sxs-lookup"><span data-stu-id="c64e7-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="c64e7-141">сборка</span><span class="sxs-lookup"><span data-stu-id="c64e7-141">assembly</span></span>
  - <span data-ttu-id="c64e7-142">module</span><span class="sxs-lookup"><span data-stu-id="c64e7-142">module</span></span>
  - <span data-ttu-id="c64e7-143">поле</span><span class="sxs-lookup"><span data-stu-id="c64e7-143">field</span></span>
  - <span data-ttu-id="c64e7-144">event</span><span class="sxs-lookup"><span data-stu-id="c64e7-144">event</span></span>
  - <span data-ttu-id="c64e7-145">method</span><span class="sxs-lookup"><span data-stu-id="c64e7-145">method</span></span>
  - <span data-ttu-id="c64e7-146">param</span><span class="sxs-lookup"><span data-stu-id="c64e7-146">param</span></span>
  - <span data-ttu-id="c64e7-147">свойство;</span><span class="sxs-lookup"><span data-stu-id="c64e7-147">property</span></span>
  - <span data-ttu-id="c64e7-148">return</span><span class="sxs-lookup"><span data-stu-id="c64e7-148">return</span></span>
  - <span data-ttu-id="c64e7-149">type</span><span class="sxs-lookup"><span data-stu-id="c64e7-149">type</span></span>
- <span data-ttu-id="c64e7-150">Можно ли применить атрибут к одному элементу программы несколько раз.</span><span class="sxs-lookup"><span data-stu-id="c64e7-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="c64e7-151">Могут ли атрибуты наследоваться производными классами.</span><span class="sxs-lookup"><span data-stu-id="c64e7-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="c64e7-152">При явном применении параметры по умолчанию выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c64e7-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="c64e7-153">В этом примере класс `NewAttribute` можно применить к любому поддерживаемому элементу программы.</span><span class="sxs-lookup"><span data-stu-id="c64e7-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="c64e7-154">Но он применяется к каждому объекту только один раз.</span><span class="sxs-lookup"><span data-stu-id="c64e7-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="c64e7-155">Атрибут наследуется производными классами при применении к базовому классу.</span><span class="sxs-lookup"><span data-stu-id="c64e7-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="c64e7-156">Аргументы <xref:System.AttributeUsageAttribute.AllowMultiple> и <xref:System.AttributeUsageAttribute.Inherited> являются необязательными, так что следующий код имеет тот же результат:</span><span class="sxs-lookup"><span data-stu-id="c64e7-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="c64e7-157">Первый аргумент <xref:System.AttributeUsageAttribute> должен состоять из одного или нескольких элементов перечисления <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="c64e7-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="c64e7-158">Несколько типов целевого объекта можно связать с помощью оператора OR, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="c64e7-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="c64e7-159">Начиная с C# 7.3 атрибуты могут применяться либо к свойству, либо к резервному полю для автоматически реализуемого свойства.</span><span class="sxs-lookup"><span data-stu-id="c64e7-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="c64e7-160">Атрибут применяется к свойству, если не указан описатель `field` для атрибута.</span><span class="sxs-lookup"><span data-stu-id="c64e7-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="c64e7-161">Оба случая показаны в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="c64e7-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="c64e7-162">Если аргументу <xref:System.AttributeUsageAttribute.AllowMultiple> присвоено значение `true`, то результирующий атрибут можно применить несколько раз к одной сущности, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="c64e7-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="c64e7-163">В этом случае `MultiUseAttribute` можно применять несколько раз, так как `AllowMultiple` имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="c64e7-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="c64e7-164">Для применения нескольких атрибутов допускаются оба показанных формата.</span><span class="sxs-lookup"><span data-stu-id="c64e7-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="c64e7-165">Если <xref:System.AttributeUsageAttribute.Inherited> — `false`, атрибут не наследуется классами, производными от класса атрибутов.</span><span class="sxs-lookup"><span data-stu-id="c64e7-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="c64e7-166">Пример:</span><span class="sxs-lookup"><span data-stu-id="c64e7-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="c64e7-167">В этом случае `NonInheritedAttribute` не применяется к `DClass` путем наследования.</span><span class="sxs-lookup"><span data-stu-id="c64e7-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="c64e7-168">См. также</span><span class="sxs-lookup"><span data-stu-id="c64e7-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="c64e7-169">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c64e7-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="c64e7-170">Отражение</span><span class="sxs-lookup"><span data-stu-id="c64e7-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
