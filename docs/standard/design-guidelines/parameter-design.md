---
description: 'Узнайте подробнее о: Разработка параметров'
title: Разработка параметров
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 9663ef8146054985374fdb3e2974fcd996fd1402
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731829"
---
# <a name="parameter-design"></a><span data-ttu-id="76e44-103">Разработка параметров</span><span class="sxs-lookup"><span data-stu-id="76e44-103">Parameter Design</span></span>

<span data-ttu-id="76e44-104">В этом разделе приведены общие рекомендации по проектированию параметров, а также сведения о проверке аргументов.</span><span class="sxs-lookup"><span data-stu-id="76e44-104">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="76e44-105">Кроме того, ознакомьтесь с рекомендациями, описанными в статье [Именования параметров](naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="76e44-105">In addition, you should refer to the guidelines described in [Naming Parameters](naming-parameters.md).</span></span>

 <span data-ttu-id="76e44-106">✔️ ИСПОЛЬЗУЙТЕ наименее производный тип параметра, который предоставляет функции, необходимые для элемента.</span><span class="sxs-lookup"><span data-stu-id="76e44-106">✔️ DO use the least derived parameter type that provides the functionality required by the member.</span></span>

 <span data-ttu-id="76e44-107">Например, предположим, что требуется разработать метод, который перечисляет коллекцию и выводит каждый элемент на консоль.</span><span class="sxs-lookup"><span data-stu-id="76e44-107">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="76e44-108">Например, такой метод должен принимать <xref:System.Collections.IEnumerable> в качестве параметра, а не <xref:System.Collections.ArrayList> или <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="76e44-108">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>

 <span data-ttu-id="76e44-109">❌ НЕ используйте зарезервированные параметры.</span><span class="sxs-lookup"><span data-stu-id="76e44-109">❌ DO NOT use reserved parameters.</span></span>

 <span data-ttu-id="76e44-110">Если в какой-либо будущей версии для элемента требуется больше входных данных, можно добавить новую перегрузку.</span><span class="sxs-lookup"><span data-stu-id="76e44-110">If more input to a member is needed in some future version, a new overload can be added.</span></span>

 <span data-ttu-id="76e44-111">❌ НЕ используйте общедоступные методы, которые принимают указатели, массивы указателей или многомерные массивы в качестве параметров.</span><span class="sxs-lookup"><span data-stu-id="76e44-111">❌ DO NOT have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>

 <span data-ttu-id="76e44-112">Указатели и многомерные массивы достаточно сложно правильно использовать.</span><span class="sxs-lookup"><span data-stu-id="76e44-112">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="76e44-113">В большинстве случаев можно переработать интерфейс API, чтобы не использовать эти типы в качестве параметров.</span><span class="sxs-lookup"><span data-stu-id="76e44-113">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>

 <span data-ttu-id="76e44-114">✔️ РАЗМЕЩАЙТЕ все параметры `out` после всех параметров по значению и `ref` (исключая массивы параметров), даже если это приведет к несогласованности упорядочения параметров между перегрузками (см. статью [Перегрузка элементов](member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="76e44-114">✔️ DO place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](member-overloading.md)).</span></span>

 <span data-ttu-id="76e44-115">Параметры `out` могут рассматриваться как дополнительные возвращаемые значения. Объедините их вместе, чтобы лучше понять сигнатуру метода.</span><span class="sxs-lookup"><span data-stu-id="76e44-115">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>

 <span data-ttu-id="76e44-116">✔️ БУДЬТЕ последовательны в именовании параметров при переопределении элементов или реализации элементов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="76e44-116">✔️ DO be consistent in naming parameters when overriding members or implementing interface members.</span></span>

 <span data-ttu-id="76e44-117">Это улучшает связь между методами.</span><span class="sxs-lookup"><span data-stu-id="76e44-117">This better communicates the relationship between the methods.</span></span>

### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="76e44-118">Выбор между параметрами перечисления и логическими параметрами</span><span class="sxs-lookup"><span data-stu-id="76e44-118">Choosing Between Enum and Boolean Parameters</span></span>  

 <span data-ttu-id="76e44-119">✔ ИСПОЛЬЗУЙТЕ перечисления, чтобы не использовать в элементе два или более логических параметра.</span><span class="sxs-lookup"><span data-stu-id="76e44-119">✔️ DO use enums if a member would otherwise have two or more Boolean parameters.</span></span>

 <span data-ttu-id="76e44-120">❌ НЕ используйте логические параметры, если вы абсолютно не уверены, что вам никогда не понадобится больше двух значений.</span><span class="sxs-lookup"><span data-stu-id="76e44-120">❌ DO NOT use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>

 <span data-ttu-id="76e44-121">Перечисления предоставляют возможность добавить значения в будущем. Но следует помнить о всех последствиях добавления значений к перечислениям, которые описаны в разделе [Разработка перечислений](enum.md).</span><span class="sxs-lookup"><span data-stu-id="76e44-121">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](enum.md).</span></span>

 <span data-ttu-id="76e44-122">✔️ Рассмотрите возможность использования логических значений для параметров конструктора, которые действительно являются значениями с двумя состояниями и просто используются для инициализации логических свойств.</span><span class="sxs-lookup"><span data-stu-id="76e44-122">✔️ CONSIDER using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>

### <a name="validating-arguments"></a><span data-ttu-id="76e44-123">Проверка аргументов</span><span class="sxs-lookup"><span data-stu-id="76e44-123">Validating Arguments</span></span>

 <span data-ttu-id="76e44-124">✔️ ПРОВЕРЯЙТЕ аргументы, переданные общедоступным, защищенным или явно реализованным элементам.</span><span class="sxs-lookup"><span data-stu-id="76e44-124">✔️ DO validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="76e44-125">Вызовите исключение <xref:System.ArgumentException?displayProperty=nameWithType> или один из его подклассов, если проверка завершается неудачно.</span><span class="sxs-lookup"><span data-stu-id="76e44-125">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>

 <span data-ttu-id="76e44-126">Обратите внимание, что фактическая проверка не обязательно должна выполняться в самом общедоступном или защищенном элементе.</span><span class="sxs-lookup"><span data-stu-id="76e44-126">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="76e44-127">Это может произойти на более низком уровне, например в частных или внутренних подпрограммах.</span><span class="sxs-lookup"><span data-stu-id="76e44-127">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="76e44-128">Главным моментом является то, что вся контактная зона, предоставляемая конечным пользователям, проверяет аргументы.</span><span class="sxs-lookup"><span data-stu-id="76e44-128">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>

 <span data-ttu-id="76e44-129">✔️ ВЫЗОВИТЕ <xref:System.ArgumentNullException>, если передается нулевой аргумент, а элемент его не поддерживает.</span><span class="sxs-lookup"><span data-stu-id="76e44-129">✔️ DO throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>

 <span data-ttu-id="76e44-130">✔️ ПРОВЕРЯЙТЕ параметры перечисления.</span><span class="sxs-lookup"><span data-stu-id="76e44-130">✔️ DO validate enum parameters.</span></span>

 <span data-ttu-id="76e44-131">Не рассчитывайте на то, что аргументы перечисления будут находиться в диапазоне, определенном перечислением.</span><span class="sxs-lookup"><span data-stu-id="76e44-131">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="76e44-132">Среда CLR позволяет привести любое целочисленное значение в значение перечисления, даже если это значение не определено в перечислении.</span><span class="sxs-lookup"><span data-stu-id="76e44-132">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>

 <span data-ttu-id="76e44-133">❌ НЕ используйте <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> для проверки диапазона перечислений.</span><span class="sxs-lookup"><span data-stu-id="76e44-133">❌ DO NOT use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>

 <span data-ttu-id="76e44-134">✔️ ИМЕЙТЕ В ВИДУ, что изменяемые аргументы могли измениться после проверки.</span><span class="sxs-lookup"><span data-stu-id="76e44-134">✔️ DO be aware that mutable arguments might have changed after they were validated.</span></span>

 <span data-ttu-id="76e44-135">Если элемент, требует особых мер безопасности, рекомендуется создать копию, а затем проверить и обработать аргумент.</span><span class="sxs-lookup"><span data-stu-id="76e44-135">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>

### <a name="parameter-passing"></a><span data-ttu-id="76e44-136">Передача параметров</span><span class="sxs-lookup"><span data-stu-id="76e44-136">Parameter Passing</span></span>

 <span data-ttu-id="76e44-137">С точки зрения конструктора инфраструктуры существуют три основные группы параметров: параметры по значению, параметры `ref` и параметры `out`.</span><span class="sxs-lookup"><span data-stu-id="76e44-137">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>

 <span data-ttu-id="76e44-138">Когда аргумент передается через параметр по значению, элемент получает копию фактического переданного аргумента.</span><span class="sxs-lookup"><span data-stu-id="76e44-138">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="76e44-139">Если аргумент является типом значения, в стек помещается копия аргумента.</span><span class="sxs-lookup"><span data-stu-id="76e44-139">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="76e44-140">Если аргумент является ссылочным типом, в стек помещается копия ссылки.</span><span class="sxs-lookup"><span data-stu-id="76e44-140">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="76e44-141">Наиболее популярные языки среды CLR, такие как C#, VB.NET и C++, по умолчанию передают параметры по значению.</span><span class="sxs-lookup"><span data-stu-id="76e44-141">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>

 <span data-ttu-id="76e44-142">Когда аргумент передается через параметр `ref`, элемент получает ссылку на фактически переданный аргумент.</span><span class="sxs-lookup"><span data-stu-id="76e44-142">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="76e44-143">Если аргумент является типом значения, в стек помещается ссылка на аргумент.</span><span class="sxs-lookup"><span data-stu-id="76e44-143">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="76e44-144">Если аргумент является ссылочным типом, в стек помещается ссылка на ссылку.</span><span class="sxs-lookup"><span data-stu-id="76e44-144">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="76e44-145">Параметры `Ref` можно использовать, чтобы разрешить элементу изменять аргументы, передаваемые вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="76e44-145">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>

 <span data-ttu-id="76e44-146">Параметры `Out` аналогичны параметрам `ref`, с некоторыми небольшими отличиями.</span><span class="sxs-lookup"><span data-stu-id="76e44-146">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="76e44-147">Изначально считается, что параметр не назначен и не может быть прочитан в теле элемента до того, как ему будет присвоено какое-либо значение.</span><span class="sxs-lookup"><span data-stu-id="76e44-147">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="76e44-148">Кроме того, параметру необходимо назначить значение перед возвратом элемента.</span><span class="sxs-lookup"><span data-stu-id="76e44-148">Also, the parameter has to be assigned some value before the member returns.</span></span>

 <span data-ttu-id="76e44-149">❌ НЕ используйте параметры `out` и `ref`.</span><span class="sxs-lookup"><span data-stu-id="76e44-149">❌ AVOID using `out` or `ref` parameters.</span></span>

 <span data-ttu-id="76e44-150">Чтобы использовать параметры `out` и `ref`, требуется опыт работы с указателями, понимание отличия между типами значения и ссылочными типами и умение работать с методами с несколькими возвращаемыми значениями.</span><span class="sxs-lookup"><span data-stu-id="76e44-150">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="76e44-151">Кроме того, далеко не все понимают разницу между параметрами `out` и `ref`.</span><span class="sxs-lookup"><span data-stu-id="76e44-151">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="76e44-152">Архитекторам платформ, разрабатывающим библиотеки для широкого использования, не следует рассчитывать, что пользователи прекрасно разбираются в использовании параметров `out` и `ref`.</span><span class="sxs-lookup"><span data-stu-id="76e44-152">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>

 <span data-ttu-id="76e44-153">❌ НЕ передавайте ссылочные типы по ссылке.</span><span class="sxs-lookup"><span data-stu-id="76e44-153">❌ DO NOT pass reference types by reference.</span></span>

 <span data-ttu-id="76e44-154">Есть некоторые исключения из этого правила. К ним относится метод, который можно использовать для обмена ссылками.</span><span class="sxs-lookup"><span data-stu-id="76e44-154">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>

### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="76e44-155">Элементы с переменным числом параметров</span><span class="sxs-lookup"><span data-stu-id="76e44-155">Members with Variable Number of Parameters</span></span>

 <span data-ttu-id="76e44-156">Элементы, которые могут принимать переменное число аргументов, выражаются путем предоставления параметра массива.</span><span class="sxs-lookup"><span data-stu-id="76e44-156">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="76e44-157">Например, <xref:System.String> предоставляет следующий метод:</span><span class="sxs-lookup"><span data-stu-id="76e44-157">For example, <xref:System.String> provides the following method:</span></span>

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 <span data-ttu-id="76e44-158">Затем пользователь может вызвать метод <xref:System.String.Format%2A?displayProperty=nameWithType> следующим образом:</span><span class="sxs-lookup"><span data-stu-id="76e44-158">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 <span data-ttu-id="76e44-159">Если добавить ключевое слово C# params в параметр массива, параметр будет изменен на так называемый параметр массива params. Будет предоставлен быстрый способ создания временного массива.</span><span class="sxs-lookup"><span data-stu-id="76e44-159">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 <span data-ttu-id="76e44-160">Это позволяет пользователю вызывать метод, передавая элементы массива непосредственно в список аргументов.</span><span class="sxs-lookup"><span data-stu-id="76e44-160">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>

 `String.Format("File {0} not found in {1}",filename,directory);`

 <span data-ttu-id="76e44-161">Обратите внимание, что ключевое слово params можно добавить только к последнему параметру в списке.</span><span class="sxs-lookup"><span data-stu-id="76e44-161">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>

 <span data-ttu-id="76e44-162">✔️ РЕКОМЕНДУЕТСЯ добавить ключевое слово params к параметрам массива, если предполагается, что пользователи будут передавать массивы с небольшим числом элементов.</span><span class="sxs-lookup"><span data-stu-id="76e44-162">✔️ CONSIDER adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="76e44-163">Если предполагается, что множество элементов будут передаваться с помощью стандартного сценария, пользователи, вероятно, не будут передавать эти элементы в любом случае, поэтому ключевое слово params не требуется.</span><span class="sxs-lookup"><span data-stu-id="76e44-163">If it's expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>

 <span data-ttu-id="76e44-164">❌ НЕ используйте массивы params, если у вызывающего объекта почти всегда есть входные данные, которые уже находятся в массиве.</span><span class="sxs-lookup"><span data-stu-id="76e44-164">❌ AVOID using params arrays if the caller would almost always have the input already in an array.</span></span>

 <span data-ttu-id="76e44-165">Например, элементы с параметрами массива байтов почти никогда не вызываются путем передачи отдельных байтов.</span><span class="sxs-lookup"><span data-stu-id="76e44-165">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="76e44-166">По этой причине для параметров массива байтов на платформе .NET Framework не используется ключевое слово params.</span><span class="sxs-lookup"><span data-stu-id="76e44-166">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>

 <span data-ttu-id="76e44-167">❌ НЕ используйте массивы params, если элемент, принимающий параметр массива params, изменяет массив.</span><span class="sxs-lookup"><span data-stu-id="76e44-167">❌ DO NOT use params arrays if the array is modified by the member taking the params array parameter.</span></span>

 <span data-ttu-id="76e44-168">Из-за того что многие компиляторы превращают аргументы элемента во временный массив в месте вызова, массив может быть временным объектом и поэтому любые внесенные в него изменения будут потеряны.</span><span class="sxs-lookup"><span data-stu-id="76e44-168">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>

 <span data-ttu-id="76e44-169">✔️ РАССМОТРИТЕ возможность использования ключевого слова params в простой перегрузке, даже если более сложная перегрузка не может его использовать.</span><span class="sxs-lookup"><span data-stu-id="76e44-169">✔️ CONSIDER using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>

 <span data-ttu-id="76e44-170">Решите, оценят ли пользователи наличие массива params в одной перегрузке, даже если он будет не во всех перегрузках.</span><span class="sxs-lookup"><span data-stu-id="76e44-170">Ask yourself if users would value having the params array in one overload even if it wasn't in all overloads.</span></span>

 <span data-ttu-id="76e44-171">✔️ ПОПЫТАЙТЕСЬ упорядочить параметры, чтобы можно было использовать ключевое слово params.</span><span class="sxs-lookup"><span data-stu-id="76e44-171">✔️ DO try to order parameters to make it possible to use the params keyword.</span></span>

 <span data-ttu-id="76e44-172">✔️ Рассмотрите возможность предоставления специальных перегрузок и путей кода для вызовов с небольшим количеством аргументов в чрезвычайно чувствительных к производительности API-интерфейсах.</span><span class="sxs-lookup"><span data-stu-id="76e44-172">✔️ CONSIDER providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>

 <span data-ttu-id="76e44-173">Это позволяет избежать создания объектов массива, когда API вызывается с небольшим количеством аргументов.</span><span class="sxs-lookup"><span data-stu-id="76e44-173">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="76e44-174">Сформируйте имена параметров, взяв единственную форму параметра массива и добавив числовой суффикс.</span><span class="sxs-lookup"><span data-stu-id="76e44-174">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>

 <span data-ttu-id="76e44-175">Это следует делать только в том случае, если вы собираетесь использовать весь путь к коду, а не просто создаете массив и вызываете более общий метод.</span><span class="sxs-lookup"><span data-stu-id="76e44-175">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>

 <span data-ttu-id="76e44-176">✔️ ПОМНИТЕ, что значение NULL можно передать как аргумент массива params.</span><span class="sxs-lookup"><span data-stu-id="76e44-176">✔️ DO be aware that null could be passed as a params array argument.</span></span>

 <span data-ttu-id="76e44-177">Перед обработкой необходимо убедиться, что массив не равен NULL.</span><span class="sxs-lookup"><span data-stu-id="76e44-177">You should validate that the array is not null before processing.</span></span>

 <span data-ttu-id="76e44-178">❌ НЕ используйте методы `varargs` также известные как многоточия.</span><span class="sxs-lookup"><span data-stu-id="76e44-178">❌ DO NOT use the `varargs` methods, otherwise known as the ellipsis.</span></span>

 <span data-ttu-id="76e44-179">Некоторые языки среды CLR, такие как C++, поддерживают альтернативное соглашение для передачи списков параметров переменных, именуемых методами `varargs`.</span><span class="sxs-lookup"><span data-stu-id="76e44-179">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="76e44-180">Это соглашение не должно использоваться на платформах, так как оно несовместимо с CLS.</span><span class="sxs-lookup"><span data-stu-id="76e44-180">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>

### <a name="pointer-parameters"></a><span data-ttu-id="76e44-181">Параметры указателя</span><span class="sxs-lookup"><span data-stu-id="76e44-181">Pointer Parameters</span></span>

 <span data-ttu-id="76e44-182">Как правило, указатели не должны отображаться в общедоступной области хорошо спроектированной инфраструктуры управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="76e44-182">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="76e44-183">В большинстве случаев указатели следует инкапсулировать.</span><span class="sxs-lookup"><span data-stu-id="76e44-183">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="76e44-184">Однако в некоторых случаях указатели необходимы по причинам совместимости, и их использование в таких случаях целесообразно.</span><span class="sxs-lookup"><span data-stu-id="76e44-184">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>

 <span data-ttu-id="76e44-185">✔️ ПРЕДОСТАВЬТЕ альтернативу для любого элемента, который принимает аргумент указателя, потому что указатели не соответствуют CLS.</span><span class="sxs-lookup"><span data-stu-id="76e44-185">✔️ DO provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>

 <span data-ttu-id="76e44-186">❌ ИЗБЕГАЙТЕ использования дорогостоящей проверки аргументов указателей.</span><span class="sxs-lookup"><span data-stu-id="76e44-186">❌ AVOID doing expensive argument checking of pointer arguments.</span></span>

 <span data-ttu-id="76e44-187">✔️ СЛЕДУЙТЕ общепринятым соглашениям по указателям при разработке элементов с указателями.</span><span class="sxs-lookup"><span data-stu-id="76e44-187">✔️ DO follow common pointer-related conventions when designing members with pointers.</span></span>

 <span data-ttu-id="76e44-188">Например, нет необходимости передавать начальный индекс, так как для достижения того же результата можно использовать простые арифметические операции с указателями.</span><span class="sxs-lookup"><span data-stu-id="76e44-188">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>

 <span data-ttu-id="76e44-189">*Фрагменты: &copy; Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="76e44-189">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="76e44-190">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="76e44-190">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="76e44-191">См. также</span><span class="sxs-lookup"><span data-stu-id="76e44-191">See also</span></span>

- [<span data-ttu-id="76e44-192">Правила разработки членов</span><span class="sxs-lookup"><span data-stu-id="76e44-192">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="76e44-193">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="76e44-193">Framework Design Guidelines</span></span>](index.md)
