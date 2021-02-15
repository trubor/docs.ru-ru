---
description: Дополнительные сведения о переносе приложения из Магазина Windows в .NET Native
title: Миграция приложения для магазина Windows в машинный код .NET
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 7a9e8f7108ca21dbbae7ca0097b15af078c8c6bb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464681"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a><span data-ttu-id="c6f51-103">Перенос приложения из Магазина Windows в .NET Native</span><span class="sxs-lookup"><span data-stu-id="c6f51-103">Migrate Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="c6f51-104">.NET Native обеспечивает статическую компиляцию приложений в магазине Windows или на компьютере разработчика.</span><span class="sxs-lookup"><span data-stu-id="c6f51-104">.NET Native provides static compilation of apps in the Windows Store or on the developer's computer.</span></span> <span data-ttu-id="c6f51-105">В отличие от динамической компиляции, выполняемой JIT-компилятором для приложений магазина Windows или [Генератором машинных образов (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) на устройстве.</span><span class="sxs-lookup"><span data-stu-id="c6f51-105">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="c6f51-106">Несмотря на различия, .NET Native пытается обеспечить совместимость с [.NET для приложений Магазина Windows](/previous-versions/windows/apps/br230302(v=vs.140)).</span><span class="sxs-lookup"><span data-stu-id="c6f51-106">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](/previous-versions/windows/apps/br230302(v=vs.140)).</span></span> <span data-ttu-id="c6f51-107">В большинстве случаев все, что работает с .NET для приложений Магазина Windows, также работает с .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-107">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="c6f51-108">Тем не менее в некоторых случаях могут произойти изменения поведения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-108">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="c6f51-109">В этом документе обсуждаются различия между стандартом .NET для приложений Магазина Windows и .NET Native в следующих областях:</span><span class="sxs-lookup"><span data-stu-id="c6f51-109">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="c6f51-110">Общие различия среды выполнения</span><span class="sxs-lookup"><span data-stu-id="c6f51-110">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="c6f51-111">Различия динамического программирования</span><span class="sxs-lookup"><span data-stu-id="c6f51-111">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="c6f51-112">Другие различия, связанным с отражением</span><span class="sxs-lookup"><span data-stu-id="c6f51-112">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="c6f51-113">Неподдерживаемые сценарии и API-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c6f51-113">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="c6f51-114">Различия в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c6f51-114">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="c6f51-115">Общие различия среды выполнения</span><span class="sxs-lookup"><span data-stu-id="c6f51-115">General runtime differences</span></span>

- <span data-ttu-id="c6f51-116">Исключения, такие как <xref:System.TypeLoadException> , которые вызываются JIT-компилятором при выполнении приложения в среде CLR, обычно приводят к ошибкам во время компиляции при обработке .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-116">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="c6f51-117">Не вызывайте метод <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> из потока пользовательского интерфейса приложения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-117">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="c6f51-118">Это может привести к взаимоблокировке .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-118">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="c6f51-119">Не полагайтесь на порядок вызова конструктора статического класса.</span><span class="sxs-lookup"><span data-stu-id="c6f51-119">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="c6f51-120">В .NET Native порядок вызова отличается от порядка в стандартной среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-120">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="c6f51-121">(Даже со стандартной средой выполнения, не следует рассчитывать на порядок выполнения конструкторов статических классов.)</span><span class="sxs-lookup"><span data-stu-id="c6f51-121">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="c6f51-122">Бесконечный цикл без вызовов (например, `while(true);`) на любом потоке может привести к остановке приложения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-122">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="c6f51-123">Аналогичным образом, большие или бесконечные ожидания могут также привести приложение к остановке.</span><span class="sxs-lookup"><span data-stu-id="c6f51-123">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="c6f51-124">Некоторые базовые циклы инициализации не создают исключения в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-124">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="c6f51-125">Например, следующий код создает исключение <xref:System.TypeLoadException> исключений в стандартной среде CLR.</span><span class="sxs-lookup"><span data-stu-id="c6f51-125">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="c6f51-126">В .NET Native это не так.</span><span class="sxs-lookup"><span data-stu-id="c6f51-126">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="c6f51-127">В некоторых случаях .NET Native предоставляет различные реализации библиотек классов платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6f51-127">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="c6f51-128">Объект, возвращенный из метода, всегда будет реализовать члены возвращаемого типа.</span><span class="sxs-lookup"><span data-stu-id="c6f51-128">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="c6f51-129">Тем не менее, поскольку его резервная реализация отличается, может оказаться невозможным привести его к тому же набору типов, как это можно было бы сделать на платформах .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6f51-129">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="c6f51-130">Например, в некоторых случаях может оказаться невозможным привести объект интерфейса <xref:System.Collections.Generic.IEnumerable%601> , возвращенный такими методами как <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> или <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> , к `T[]`.</span><span class="sxs-lookup"><span data-stu-id="c6f51-130">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="c6f51-131">Кэш WinInet не включен по умолчанию в .NET для приложений Магазина Windows, но находится на .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-131">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="c6f51-132">Это повышает производительность, но сказывается на рабочем наборе.</span><span class="sxs-lookup"><span data-stu-id="c6f51-132">This improves performance but has working set implications.</span></span> <span data-ttu-id="c6f51-133">Не требуется никаких действий разработчика.</span><span class="sxs-lookup"><span data-stu-id="c6f51-133">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="c6f51-134">Различия динамического программирования</span><span class="sxs-lookup"><span data-stu-id="c6f51-134">Dynamic programming differences</span></span>

<span data-ttu-id="c6f51-135">.NET Native статические ссылки в коде из платформа .NET Framework, чтобы сделать код локальным для приложения, чтобы обеспечить максимальную производительность.</span><span class="sxs-lookup"><span data-stu-id="c6f51-135">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="c6f51-136">Тем не менее, двоичные размеры должны оставаться небольшими, поэтому не удается подключить всю платформу .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6f51-136">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="c6f51-137">Компилятор .NET Native разрешает это ограничение с помощью средства уменьшения зависимостей, которое удаляет ссылки на неиспользуемый код.</span><span class="sxs-lookup"><span data-stu-id="c6f51-137">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="c6f51-138">Однако .NET Native может не поддерживать или генерировать некоторую информацию о типе и код, если эти сведения не могут быть выводиться статически во время компиляции, а вместо этого извлекаются динамически в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-138">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="c6f51-139">.NET Native включает отражение и динамическое программирование.</span><span class="sxs-lookup"><span data-stu-id="c6f51-139">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="c6f51-140">При этом, не все типы могут быть помечены для отражения, так как это сделает размер созданного кода слишком большим (особенно потому, что поддерживается отражение на общедоступных API в платформе .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="c6f51-140">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="c6f51-141">Компилятор .NET Native делает разумные варианты того, какие типы должны поддерживать отражение, и сохраняет метаданные и создает код только для этих типов.</span><span class="sxs-lookup"><span data-stu-id="c6f51-141">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="c6f51-142">Например, привязка данных требует, чтобы приложение обеспечивало сопоставление имен свойств с функциями.</span><span class="sxs-lookup"><span data-stu-id="c6f51-142">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="c6f51-143">В приложениях .NET для магазина Windows среда CLR автоматически использует отражение для обеспечения этой возможности для управляемых и общедоступных собственных типов.</span><span class="sxs-lookup"><span data-stu-id="c6f51-143">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="c6f51-144">В .NET Native компилятор автоматически включает метаданные для типов, к которым привязываются данные.</span><span class="sxs-lookup"><span data-stu-id="c6f51-144">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="c6f51-145">Компилятор .NET Native также может работать с часто используемыми универсальными типами <xref:System.Collections.Generic.List%601> , такими как и <xref:System.Collections.Generic.Dictionary%602> , которые работают без указания каких либо указаний или директив.</span><span class="sxs-lookup"><span data-stu-id="c6f51-145">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="c6f51-146">Ключевое слово [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) также поддерживается в заданных пределах.</span><span class="sxs-lookup"><span data-stu-id="c6f51-146">The [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="c6f51-147">При переносе приложения в .NET Native необходимо тщательно протестировать все динамические пути к коду.</span><span class="sxs-lookup"><span data-stu-id="c6f51-147">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="c6f51-148">Конфигурация по умолчанию для .NET Native достаточна для большинства разработчиков, но некоторым разработчикам может потребоваться точная настройка конфигурации с помощью файла директив среды выполнения (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="c6f51-148">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="c6f51-149">Кроме того, в некоторых случаях компилятору .NET Native не удается определить, какие метаданные должны быть доступны для отражения, и полагаются на указания, особенно в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="c6f51-149">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="c6f51-150">Некоторые конструкции, такие как <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> и <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> не удается определить статически.</span><span class="sxs-lookup"><span data-stu-id="c6f51-150">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="c6f51-151">Поскольку компилятор не может определить экземпляры, универсальный тип, который требуется отразить на нем должен быть указан директивами среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-151">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="c6f51-152">Это необходимо не только потому, что весь код должен быть включен, но так же и вследствие того, что отражение на универсальных типах могут образовывать бесконечный цикл (например, при вызове универсального метода для универсального типа).</span><span class="sxs-lookup"><span data-stu-id="c6f51-152">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="c6f51-153">Директивы среды выполнения определяются в файле директив среды выполнения (. rd.xml).</span><span class="sxs-lookup"><span data-stu-id="c6f51-153">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="c6f51-154">Общие сведения об использовании этого файла см. в разделе [Приступая к работе](getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="c6f51-154">For general information about using this file, see [Getting Started](getting-started-with-net-native.md).</span></span> <span data-ttu-id="c6f51-155">Сведения о директивах среды выполнения см. в разделе [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="c6f51-155">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="c6f51-156">.NET Native также включает средства профилирования, помогающие разработчику определить, какие типы за пределами набора по умолчанию должны поддерживать отражение.</span><span class="sxs-lookup"><span data-stu-id="c6f51-156">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="c6f51-157">Другие различия, связанным с отражением</span><span class="sxs-lookup"><span data-stu-id="c6f51-157">Other reflection-related differences</span></span>

<span data-ttu-id="c6f51-158">Существует ряд других отличий, связанных с отражением в работе .NET для приложений Магазина Windows и .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-158">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="c6f51-159">В .NET Native:</span><span class="sxs-lookup"><span data-stu-id="c6f51-159">In .NET Native:</span></span>

- <span data-ttu-id="c6f51-160">Отражение закрытых типов и членов в библиотеке классов платформы .NET Framework не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c6f51-160">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="c6f51-161">Тем не менее, можно выполнить отражение на собственных закрытых типах и членах, а также типах и членах библиотек сторонних поставщиков.</span><span class="sxs-lookup"><span data-stu-id="c6f51-161">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="c6f51-162">Свойство <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> корректно возвращает `false` для объекта <xref:System.Reflection.ParameterInfo> , который представляет возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="c6f51-162">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="c6f51-163">В приложениях .NET для магазина Windows, будет возвращено значение `true`.</span><span class="sxs-lookup"><span data-stu-id="c6f51-163">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="c6f51-164">Промежуточный язык (IL) не поддерживает это напрямую, и интерпретация остается в языке.</span><span class="sxs-lookup"><span data-stu-id="c6f51-164">Intermediate language (IL) doesn't support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="c6f51-165">Открытые члены на структурах <xref:System.RuntimeFieldHandle> и <xref:System.RuntimeMethodHandle> не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="c6f51-165">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="c6f51-166">Эти типы поддерживаются только для LINQ, деревьев выражений и инициализации статического массива.</span><span class="sxs-lookup"><span data-stu-id="c6f51-166">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="c6f51-167"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> и <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> включают скрытые члены в базовых классах и поэтому могут переопределяться без явного переопределения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-167"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="c6f51-168">Это также справедливо для других методов [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) .</span><span class="sxs-lookup"><span data-stu-id="c6f51-168">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="c6f51-169"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> и <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> не завершаются ошибкой при попытке создать определенные сочетания (например, массив `byref` объектов).</span><span class="sxs-lookup"><span data-stu-id="c6f51-169"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of `byref` objects).</span></span>

- <span data-ttu-id="c6f51-170">Нельзя использовать отражение для вызова членов, которые содержат параметры указателя.</span><span class="sxs-lookup"><span data-stu-id="c6f51-170">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="c6f51-171">Чтобы получить или задать поле указателя, нельзя использовать отражение.</span><span class="sxs-lookup"><span data-stu-id="c6f51-171">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="c6f51-172">Если счетчик аргументов неправильный и тип одного из аргументов неверен, .NET Native создает исключение <xref:System.ArgumentException> вместо <xref:System.Reflection.TargetParameterCountException> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-172">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="c6f51-173">Обычно двоичная сериализация исключений не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c6f51-173">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="c6f51-174">В результате несериализуемые объекты могут быть добавлены к словарю <xref:System.Exception.Data%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-174">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="c6f51-175">Неподдерживаемые сценарии и API-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c6f51-175">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="c6f51-176">В следующих разделах перечислены неподдерживаемые сценарии и интерфейсы API для общей разработки, взаимодействия и таких технологий, как HTTPClient и Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="c6f51-176">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="c6f51-177">Общая разработка</span><span class="sxs-lookup"><span data-stu-id="c6f51-177">General development</span></span>](#General)

- [<span data-ttu-id="c6f51-178">HttpClient</span><span class="sxs-lookup"><span data-stu-id="c6f51-178">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="c6f51-179">Interop</span><span class="sxs-lookup"><span data-stu-id="c6f51-179">Interop</span></span>](#Interop)

- [<span data-ttu-id="c6f51-180">Неподдерживаемые API</span><span class="sxs-lookup"><span data-stu-id="c6f51-180">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="c6f51-181">Различия общей разработки</span><span class="sxs-lookup"><span data-stu-id="c6f51-181">General development differences</span></span>

<span data-ttu-id="c6f51-182">**Типы значений**</span><span class="sxs-lookup"><span data-stu-id="c6f51-182">**Value types**</span></span>

- <span data-ttu-id="c6f51-183">При переопределении методов <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> и <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> для типа значения не вызывайте реализации базового класса.</span><span class="sxs-lookup"><span data-stu-id="c6f51-183">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="c6f51-184">В приложениях .NET для магазина Windows эти методы основаны на отражении.</span><span class="sxs-lookup"><span data-stu-id="c6f51-184">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="c6f51-185">Во время компиляции .NET Native создает реализацию, которая не зависит от отражения среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-185">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="c6f51-186">Это означает, что если вы не переопределяете эти два метода, они будут работать должным образом, так как .NET Native создает реализацию во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="c6f51-186">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="c6f51-187">Однако, переопределение этих методов с помощью вызова реализации базового класса приводит к возникновению исключения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-187">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="c6f51-188">Типы значений больше 1 МБ не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="c6f51-188">Value types larger than 1 megabyte aren't supported.</span></span>

- <span data-ttu-id="c6f51-189">Типы значений не могут иметь конструктор без параметров в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-189">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="c6f51-190">(В C# и Visual Basic запрещены конструкторы без параметров для типов значений.</span><span class="sxs-lookup"><span data-stu-id="c6f51-190">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="c6f51-191">Тем не менее их можно создать в IL.)</span><span class="sxs-lookup"><span data-stu-id="c6f51-191">However, these can be created in IL.)</span></span>

<span data-ttu-id="c6f51-192">**Массивы**</span><span class="sxs-lookup"><span data-stu-id="c6f51-192">**Arrays**</span></span>

- <span data-ttu-id="c6f51-193">Массивы с нижней границей, отличной от нуля, не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="c6f51-193">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="c6f51-194">Как правило, эти массивы создаются путем вызова перегрузки <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-194">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="c6f51-195">Динамическое создание многомерных массивов не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c6f51-195">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="c6f51-196">Такие массивы обычно создаются путем вызова перегрузки метода <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> , который включает в себя параметр `lengths` , или же путем вызова метода <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-196">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="c6f51-197">Многомерные массивы, имеющие четыре или более измерений не поддерживаются; т.е. их значение свойства <xref:System.Array.Rank%2A?displayProperty=nameWithType> равно или больше четырех.</span><span class="sxs-lookup"><span data-stu-id="c6f51-197">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="c6f51-198">Вместо этого используйте [ступенчатые массивы](../../csharp/programming-guide/arrays/jagged-arrays.md) (массива массивов).</span><span class="sxs-lookup"><span data-stu-id="c6f51-198">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="c6f51-199">Например `array[x,y,z]` является недопустимым, но `array[x][y][z]` нет.</span><span class="sxs-lookup"><span data-stu-id="c6f51-199">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="c6f51-200">Вариативность для многомерных массивов не поддерживается и вызывает исключение <xref:System.InvalidCastException> во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-200">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="c6f51-201">**Универсальные шаблоны**</span><span class="sxs-lookup"><span data-stu-id="c6f51-201">**Generics**</span></span>

- <span data-ttu-id="c6f51-202">Расширения бесконечного универсального типа приводят к ошибке компилятора.</span><span class="sxs-lookup"><span data-stu-id="c6f51-202">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="c6f51-203">Например, этот код вызывает ошибку при компиляции:</span><span class="sxs-lookup"><span data-stu-id="c6f51-203">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="c6f51-204">**Указатели**</span><span class="sxs-lookup"><span data-stu-id="c6f51-204">**Pointers**</span></span>

- <span data-ttu-id="c6f51-205">Массивы указателей не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c6f51-205">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="c6f51-206">Чтобы получить или задать поле указателя, нельзя использовать отражение.</span><span class="sxs-lookup"><span data-stu-id="c6f51-206">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="c6f51-207">**Сериализация**</span><span class="sxs-lookup"><span data-stu-id="c6f51-207">**Serialization**</span></span>

<span data-ttu-id="c6f51-208">Атрибут <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c6f51-208">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="c6f51-209">Вместо этого используйте атрибут <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-209">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="c6f51-210">**Ресурсы**</span><span class="sxs-lookup"><span data-stu-id="c6f51-210">**Resources**</span></span>

<span data-ttu-id="c6f51-211">Использование локализованных ресурсов с классом <xref:System.Diagnostics.Tracing.EventSource> не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c6f51-211">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="c6f51-212">Свойство <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> не определяет локализованные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="c6f51-212">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="c6f51-213">**Делегаты**</span><span class="sxs-lookup"><span data-stu-id="c6f51-213">**Delegates**</span></span>

<span data-ttu-id="c6f51-214">`Delegate.BeginInvoke` и `Delegate.EndInvoke` не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="c6f51-214">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="c6f51-215">**Различные API**</span><span class="sxs-lookup"><span data-stu-id="c6f51-215">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="c6f51-216">Свойство [typeInfo. GUID](xref:System.Type.GUID) создает исключение, <xref:System.PlatformNotSupportedException> Если <xref:System.Runtime.InteropServices.GuidAttribute> атрибут не применяется к типу.</span><span class="sxs-lookup"><span data-stu-id="c6f51-216">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="c6f51-217">Идентификатор GUID используется в основном для поддержки модели COM.</span><span class="sxs-lookup"><span data-stu-id="c6f51-217">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="c6f51-218"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType>Метод правильно выполняет синтаксический анализ строк, содержащих короткие даты в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-218">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="c6f51-219">Однако он не поддерживает совместимость с определенными изменениями в анализе даты и времени.</span><span class="sxs-lookup"><span data-stu-id="c6f51-219">However, it doesn't maintain compatibility with certain changes in date and time parsing.</span></span>

- <span data-ttu-id="c6f51-220"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")`правильно округляется в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-220"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="c6f51-221">В некоторых версиях среды CLR, результирующая строка усекается вместо округления.</span><span class="sxs-lookup"><span data-stu-id="c6f51-221">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="c6f51-222">Различия HttpClient</span><span class="sxs-lookup"><span data-stu-id="c6f51-222">HttpClient differences</span></span>

<span data-ttu-id="c6f51-223">В .NET Native <xref:System.Net.Http.HttpClientHandler> класс внутренне использует WinInet (через <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> класс) вместо <xref:System.Net.WebRequest> классов и, <xref:System.Net.WebResponse> используемых в стандартном .NET для приложений Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="c6f51-223">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="c6f51-224">WinINet не поддерживает все параметры конфигурации, которые поддерживает класс <xref:System.Net.Http.HttpClientHandler> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-224">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="c6f51-225">В результате имеем следующее:</span><span class="sxs-lookup"><span data-stu-id="c6f51-225">As a result:</span></span>

- <span data-ttu-id="c6f51-226">Некоторые свойства возможностей <xref:System.Net.Http.HttpClientHandler> возвращают `false` .NET Native, тогда как они возвращаются `true` в стандартном .NET для приложений Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="c6f51-226">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="c6f51-227">Некоторые `get` методы доступа к свойствам конфигурации всегда возвращают фиксированное значение для .NET Native, которое отличается от настраиваемого значения по умолчанию в .NET для приложений Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="c6f51-227">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="c6f51-228">В следующих подразделах описаны некоторые дополнительные различия в поведении.</span><span class="sxs-lookup"><span data-stu-id="c6f51-228">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="c6f51-229">**Прокси**</span><span class="sxs-lookup"><span data-stu-id="c6f51-229">**Proxy**</span></span>

<span data-ttu-id="c6f51-230"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>Класс не поддерживает настройку или переопределение прокси-сервера для каждого запроса.</span><span class="sxs-lookup"><span data-stu-id="c6f51-230">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="c6f51-231">Это означает, что все запросы на .NET Native используют настроенный в системе прокси-сервер или не использует прокси-сервер в зависимости от значения <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> Свойства.</span><span class="sxs-lookup"><span data-stu-id="c6f51-231">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="c6f51-232">В приложениях .NET для магазина Windows, прокси-сервер определяется свойством <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-232">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="c6f51-233">В .NET Native при присвоении параметру значения, отличного <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> от, `null` вызывается <xref:System.PlatformNotSupportedException> исключение.</span><span class="sxs-lookup"><span data-stu-id="c6f51-233">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="c6f51-234"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType>Свойство возвращается `false` в .NET Native, тогда как оно возвращается `true` в стандартном платформа .NET Framework для приложений Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="c6f51-234">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="c6f51-235">**Автоматическое перенаправление**</span><span class="sxs-lookup"><span data-stu-id="c6f51-235">**Automatic redirection**</span></span>

<span data-ttu-id="c6f51-236"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>Класс не допускает настройку максимального числа автоматических перенаправлений.</span><span class="sxs-lookup"><span data-stu-id="c6f51-236">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="c6f51-237">Значение свойства <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> равно 50 по умолчанию в стандартных приложениях .NET для магазина Windows и может быть изменено.</span><span class="sxs-lookup"><span data-stu-id="c6f51-237">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="c6f51-238">В .NET Native значение этого свойства равно 10, и при попытке изменить его будет создано <xref:System.PlatformNotSupportedException> исключение.</span><span class="sxs-lookup"><span data-stu-id="c6f51-238">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="c6f51-239"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType>Свойство возвращается `false` в .NET Native, тогда как оно возвращается `true` в .NET для приложений Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="c6f51-239">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="c6f51-240">**Автоматическая распаковка**</span><span class="sxs-lookup"><span data-stu-id="c6f51-240">**Automatic decompression**</span></span>

<span data-ttu-id="c6f51-241">Приложения .NET для магазина Windows позволяют задать свойство <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> на <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, оба <xref:System.Net.DecompressionMethods.Deflate> и <xref:System.Net.DecompressionMethods.GZip>или <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="c6f51-241">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="c6f51-242">.NET Native поддерживает только <xref:System.Net.DecompressionMethods.Deflate> совместно с <xref:System.Net.DecompressionMethods.GZip> , или <xref:System.Net.DecompressionMethods.None> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-242">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="c6f51-243">При попытке задать свойство <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> только на <xref:System.Net.DecompressionMethods.Deflate> или <xref:System.Net.DecompressionMethods.GZip> происходит его автоматическое задание на оба <xref:System.Net.DecompressionMethods.Deflate> и <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="c6f51-243">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="c6f51-244">**Файлы "cookie"**</span><span class="sxs-lookup"><span data-stu-id="c6f51-244">**Cookies**</span></span>

<span data-ttu-id="c6f51-245">Обработка файлов cookie выполняется одновременно с <xref:System.Net.Http.HttpClient> и WinINet.</span><span class="sxs-lookup"><span data-stu-id="c6f51-245">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="c6f51-246">Файлы cookie из <xref:System.Net.CookieContainer> объединяются вместе файла cookie в кэше WinINet cookie.</span><span class="sxs-lookup"><span data-stu-id="c6f51-246">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="c6f51-247">Удаление файла cookie из <xref:System.Net.CookieContainer> запрещает <xref:System.Net.Http.HttpClient> отправлять файл cookie, но если файл cookie уже был просмотрен WinINet и файлы "cookie" не были удалены пользователем, WinINet отправляет его.</span><span class="sxs-lookup"><span data-stu-id="c6f51-247">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="c6f51-248">Не существует средств программного удаления файла cookie из WinINet с использованием API <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>или <xref:System.Net.CookieContainer> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-248">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="c6f51-249">Задание свойства <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> на `false` вызывает только <xref:System.Net.Http.HttpClient> , чтобы остановить отправку файлов "cookie"; WinINet может по-прежнему включить свои файлы cookie в запрос.</span><span class="sxs-lookup"><span data-stu-id="c6f51-249">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="c6f51-250">**Учетные данные**</span><span class="sxs-lookup"><span data-stu-id="c6f51-250">**Credentials**</span></span>

<span data-ttu-id="c6f51-251">В приложениях .NET для магазина Windows свойства <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> и <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> работают независимо друг от друга.</span><span class="sxs-lookup"><span data-stu-id="c6f51-251">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="c6f51-252">Кроме того, свойство <xref:System.Net.Http.HttpClientHandler.Credentials%2A> принимает любой объект, реализующий интерфейс <xref:System.Net.ICredentials> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-252">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="c6f51-253">В .NET Native значение <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> свойства будет `true` приводить к тому, что <xref:System.Net.Http.HttpClientHandler.Credentials%2A> свойство станет равным `null` .</span><span class="sxs-lookup"><span data-stu-id="c6f51-253">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="c6f51-254">Кроме этого, свойство <xref:System.Net.Http.HttpClientHandler.Credentials%2A> может быть задано только в `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>или объект типа <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="c6f51-254">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="c6f51-255">Назначение любого другого объекта <xref:System.Net.ICredentials> , наиболее популярный из которых <xref:System.Net.CredentialCache>, свойству <xref:System.Net.Http.HttpClientHandler.Credentials%2A> вызывает исключение <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="c6f51-255">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="c6f51-256">**Другие неподдерживаемые и ненастраиваемые функции**</span><span class="sxs-lookup"><span data-stu-id="c6f51-256">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="c6f51-257">В .NET Native:</span><span class="sxs-lookup"><span data-stu-id="c6f51-257">In .NET Native:</span></span>

- <span data-ttu-id="c6f51-258">Значение свойства <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> всегда <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="c6f51-258">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="c6f51-259">В приложения .NET для магазина Windows, по умолчанию используется <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="c6f51-259">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="c6f51-260">Свойство <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> не настраивается.</span><span class="sxs-lookup"><span data-stu-id="c6f51-260">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="c6f51-261">Свойство <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> всегда имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="c6f51-261">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="c6f51-262">В приложения .NET для магазина Windows, по умолчанию используется `false`.</span><span class="sxs-lookup"><span data-stu-id="c6f51-262">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="c6f51-263">Заголовок `SetCookie2` в ответах игнорируется как устаревший.</span><span class="sxs-lookup"><span data-stu-id="c6f51-263">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>

### <a name="interop-differences"></a><span data-ttu-id="c6f51-264">Различия взаимодействия</span><span class="sxs-lookup"><span data-stu-id="c6f51-264">Interop differences</span></span>

 <span data-ttu-id="c6f51-265">**Устаревшие интерфейсы API**</span><span class="sxs-lookup"><span data-stu-id="c6f51-265">**Deprecated APIs**</span></span>

 <span data-ttu-id="c6f51-266">Не рекомендуется использовать несколько редко применяемых API-интерфейсов для взаимодействия с управляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="c6f51-266">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="c6f51-267">При использовании с .NET Native эти API-интерфейсы могут вызывать <xref:System.NotImplementedException> <xref:System.PlatformNotSupportedException> исключение или или привести к ошибке компилятора.</span><span class="sxs-lookup"><span data-stu-id="c6f51-267">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="c6f51-268">В приложениях .NET для магазина Windows эти API-интерфейсы отмечены как устаревшие, хотя их вызов создает предупреждение компилятора, а не ошибку компилятора.</span><span class="sxs-lookup"><span data-stu-id="c6f51-268">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="c6f51-269">Устаревшие API для `VARIANT` маршалирования включают:</span><span class="sxs-lookup"><span data-stu-id="c6f51-269">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="c6f51-270"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> поддерживается, но в некоторых сценариях возникает исключение, например, если оно используется с [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) или `byref` Variant.</span><span class="sxs-lookup"><span data-stu-id="c6f51-270"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or `byref` variants.</span></span>

 <span data-ttu-id="c6f51-271">Устаревшие API-интерфейсы для поддержки [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) включают:</span><span class="sxs-lookup"><span data-stu-id="c6f51-271">Deprecated APIs for [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="c6f51-272">Устаревшие API-интерфейсы для классических событий COM включают:</span><span class="sxs-lookup"><span data-stu-id="c6f51-272">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="c6f51-273">Устаревшие интерфейсы API в <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> интерфейсе, которые не поддерживаются в .NET Native, включают:</span><span class="sxs-lookup"><span data-stu-id="c6f51-273">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="c6f51-274"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (все члены)</span><span class="sxs-lookup"><span data-stu-id="c6f51-274"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="c6f51-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (все члены)</span><span class="sxs-lookup"><span data-stu-id="c6f51-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="c6f51-276"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (все члены)</span><span class="sxs-lookup"><span data-stu-id="c6f51-276"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="c6f51-277">К другим неподдерживаемым функциям взаимодействия относятся:</span><span class="sxs-lookup"><span data-stu-id="c6f51-277">Other unsupported interop features include:</span></span>

- <span data-ttu-id="c6f51-278"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (все члены)</span><span class="sxs-lookup"><span data-stu-id="c6f51-278"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="c6f51-279"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (все члены)</span><span class="sxs-lookup"><span data-stu-id="c6f51-279"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="c6f51-280">Редко используемые API-интерфейсы для маршалирования:</span><span class="sxs-lookup"><span data-stu-id="c6f51-280">Rarely used marshaling APIs:</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 <span data-ttu-id="c6f51-281">**Вызов неуправляемого кода и совместимость взаимодействия COM**</span><span class="sxs-lookup"><span data-stu-id="c6f51-281">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="c6f51-282">В .NET Native по-прежнему поддерживаются большинство сценариев вызова неуправляемого кода и COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="c6f51-282">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="c6f51-283">В частности, поддерживаются все взаимодействия с API среды выполнения Windows (WinRT) и весь необходимый маршалинг для среды выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="c6f51-283">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="c6f51-284">Это включает поддержку маршалинга:</span><span class="sxs-lookup"><span data-stu-id="c6f51-284">This includes marshaling support for:</span></span>

- <span data-ttu-id="c6f51-285">Массивы (включая <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="c6f51-285">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="c6f51-286">Делегаты</span><span class="sxs-lookup"><span data-stu-id="c6f51-286">Delegates</span></span>

- <span data-ttu-id="c6f51-287">Строки (Юникод, ANSI и HSTRING)</span><span class="sxs-lookup"><span data-stu-id="c6f51-287">Strings (Unicode, ANSI, and HSTRING)</span></span>

- <span data-ttu-id="c6f51-288">Структуры (`byref` и `byval`)</span><span class="sxs-lookup"><span data-stu-id="c6f51-288">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="c6f51-289">Объединения</span><span class="sxs-lookup"><span data-stu-id="c6f51-289">Unions</span></span>

- <span data-ttu-id="c6f51-290">Дескрипторы Win32</span><span class="sxs-lookup"><span data-stu-id="c6f51-290">Win32 handles</span></span>

- <span data-ttu-id="c6f51-291">Все конструкции WinRT</span><span class="sxs-lookup"><span data-stu-id="c6f51-291">All WinRT constructs</span></span>

- <span data-ttu-id="c6f51-292">Частичная поддержка маршалинга типов variant.</span><span class="sxs-lookup"><span data-stu-id="c6f51-292">Partial support for marshaling variant types.</span></span> <span data-ttu-id="c6f51-293">Поддерживаются следующие конструкции:</span><span class="sxs-lookup"><span data-stu-id="c6f51-293">The following are supported:</span></span>

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [<span data-ttu-id="c6f51-294">IUnknown</span><span class="sxs-lookup"><span data-stu-id="c6f51-294">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="c6f51-295">Однако .NET Native не поддерживает следующие действия:</span><span class="sxs-lookup"><span data-stu-id="c6f51-295">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="c6f51-296">использование классических COM-событий</span><span class="sxs-lookup"><span data-stu-id="c6f51-296">Using classic COM events</span></span>

- <span data-ttu-id="c6f51-297">Реализация интерфейса <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> на управляемом типе</span><span class="sxs-lookup"><span data-stu-id="c6f51-297">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="c6f51-298">Реализация интерфейса [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) в управляемом типе через атрибут <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-298">Implementing the [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="c6f51-299">Однако нельзя вызывать COM-объекты с помощью `IDispatch` , а управляемый объект не может реализовать `IDispatch` .</span><span class="sxs-lookup"><span data-stu-id="c6f51-299">However, you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="c6f51-300">Использование отражения для вызова метода неуправляемого кода не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c6f51-300">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="c6f51-301">Это ограничение можно обойти путем заключения вызова метода в другой метод, вместо этого используя вызов оболочки.</span><span class="sxs-lookup"><span data-stu-id="c6f51-301">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="c6f51-302">Другие отличия от API-интерфейсов приложений .NET для магазина Windows</span><span class="sxs-lookup"><span data-stu-id="c6f51-302">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="c6f51-303">В этом разделе перечислены остальные API, которые не поддерживаются в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-303">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="c6f51-304">Самым большим набором неподдерживаемых API являются API-интерфейсы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c6f51-304">The largest set of the unsupported APIs is the Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="c6f51-305">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="c6f51-305">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="c6f51-306">Типы в <xref:System.ComponentModel.DataAnnotations> <xref:System.ComponentModel.DataAnnotations.Schema> пространствах имен и не поддерживаются в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-306">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="c6f51-307">К ним относятся следующие типы, которые имеются в .NET для приложений Магазина Windows для Windows 8:</span><span class="sxs-lookup"><span data-stu-id="c6f51-307">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 <span data-ttu-id="c6f51-308">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="c6f51-308">**Visual Basic**</span></span>

<span data-ttu-id="c6f51-309">Visual Basic в настоящее время не поддерживается в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-309">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="c6f51-310">Следующие типы в <xref:Microsoft.VisualBasic> <xref:Microsoft.VisualBasic.CompilerServices> пространствах имен и недоступны в .NET Native:</span><span class="sxs-lookup"><span data-stu-id="c6f51-310">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

<span data-ttu-id="c6f51-311">**Контекст отражения (пространство имен System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="c6f51-311">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="c6f51-312"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType>Класс не поддерживается в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-312">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="c6f51-313">**Часы реального времени (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="c6f51-313">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="c6f51-314">`System.Net.Http.RtcRequestFactory`Класс не поддерживается в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-314">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="c6f51-315">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="c6f51-315">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="c6f51-316">Типы в [пространствах имен System. ServiceModel. \*](xref:System.ServiceModel) не поддерживаются в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6f51-316">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="c6f51-317">К ним относятся следующие типы:</span><span class="sxs-lookup"><span data-stu-id="c6f51-317">These include the following types:</span></span>

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a><span data-ttu-id="c6f51-318">Различия в сериализаторах</span><span class="sxs-lookup"><span data-stu-id="c6f51-318">Differences in serializers</span></span>

<span data-ttu-id="c6f51-319">Существуют следующие различия, касающиеся сериализации и десериализации с классами <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>и <xref:System.Xml.Serialization.XmlSerializer> :</span><span class="sxs-lookup"><span data-stu-id="c6f51-319">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="c6f51-320">В .NET Native <xref:System.Runtime.Serialization.DataContractSerializer> и <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> не удается сериализовать или десериализовать производный класс, имеющий член базового класса, тип которого не является корневым типом сериализации.</span><span class="sxs-lookup"><span data-stu-id="c6f51-320">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="c6f51-321">Например, в следующем коде при сериализации или десериализации `Y` возникает ошибка:</span><span class="sxs-lookup"><span data-stu-id="c6f51-321">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="c6f51-322">Тип `InnerType` не известен сериализатору, так как члены базового класса не передаются во время сериализации.</span><span class="sxs-lookup"><span data-stu-id="c6f51-322">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="c6f51-323"><xref:System.Runtime.Serialization.DataContractSerializer> и <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> не удается сериализовать класс или структуру, которая реализует интерфейс <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-323"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="c6f51-324">Например, не удается сериализовать или десериализовать следующие типы:</span><span class="sxs-lookup"><span data-stu-id="c6f51-324">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="c6f51-325"><xref:System.Xml.Serialization.XmlSerializer> не удается сериализовать следующие значения объекта, так как он не знает точный тип объекта для сериализации:</span><span class="sxs-lookup"><span data-stu-id="c6f51-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="c6f51-326"><xref:System.Xml.Serialization.XmlSerializer> не удается сериализация или десериализация, если тип сериализованного объекта <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="c6f51-326"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="c6f51-327">Все сериализаторам (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>и <xref:System.Xml.Serialization.XmlSerializer>) не удается создать код сериализации для типа <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> или типа, содержащего <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c6f51-327">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c6f51-328">Вместо этого они отображают ошибки во время построения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-328">They display build-time errors instead.</span></span>

- <span data-ttu-id="c6f51-329">Следующие конструкторы типов сериализации не обязательно работают, как должны:</span><span class="sxs-lookup"><span data-stu-id="c6f51-329">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <span data-ttu-id="c6f51-330"><xref:System.Xml.Serialization.XmlSerializer> не удается создать код для типа, который содержит методы, определенные любым из следующих атрибутов:</span><span class="sxs-lookup"><span data-stu-id="c6f51-330"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="c6f51-331"><xref:System.Xml.Serialization.XmlSerializer> не поддерживает настраиваемый интерфейс сериализации <xref:System.Xml.Serialization.IXmlSerializable> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-331"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="c6f51-332">Если имеется класс, реализующий этот интерфейс, <xref:System.Xml.Serialization.XmlSerializer> рассматривает тип, как тип объекта (POCO) простой старой среды CLR и сериализует только его открытые свойства.</span><span class="sxs-lookup"><span data-stu-id="c6f51-332">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="c6f51-333">Сериализация простого <xref:System.Exception> объекта отлично работает с <xref:System.Runtime.Serialization.DataContractSerializer> и <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="c6f51-333">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="c6f51-334">Различия в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c6f51-334">Visual Studio differences</span></span>

<span data-ttu-id="c6f51-335">**Исключения и отладка**</span><span class="sxs-lookup"><span data-stu-id="c6f51-335">**Exceptions and debugging**</span></span>

<span data-ttu-id="c6f51-336">При запуске приложений, скомпилированных с помощью .NET Native в отладчике, для исключений First-шанса включаются следующие типы исключений:</span><span class="sxs-lookup"><span data-stu-id="c6f51-336">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="c6f51-337">**Создание приложений**</span><span class="sxs-lookup"><span data-stu-id="c6f51-337">**Building apps**</span></span>

<span data-ttu-id="c6f51-338">Используйте средства построения x 86, которые используются по умолчанию в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6f51-338">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="c6f51-339">Не рекомендуется использование средств AMD64 MSBuild, которые находятся в C:\Program Files (x86)\MSBuild\12.0\bin\amd64; Это может создать проблемы построения.</span><span class="sxs-lookup"><span data-stu-id="c6f51-339">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="c6f51-340">**Профилировщики**</span><span class="sxs-lookup"><span data-stu-id="c6f51-340">**Profilers**</span></span>

- <span data-ttu-id="c6f51-341">Профилировщик ЦП в Visual Studio и профилировщик памяти XAML неправильно отображают «только мой код».</span><span class="sxs-lookup"><span data-stu-id="c6f51-341">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="c6f51-342">Профилировщик памяти XAML неточно отображает данные управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="c6f51-342">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="c6f51-343">Профилировщик ЦП неправильно идентифицирует модули и отображает имена функций с префиксами.</span><span class="sxs-lookup"><span data-stu-id="c6f51-343">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="c6f51-344">**Проекты модульных тестов библиотеки**</span><span class="sxs-lookup"><span data-stu-id="c6f51-344">**Unit Test Library projects**</span></span>

<span data-ttu-id="c6f51-345">Включение .NET Native в библиотеке модульных тестов для проекта приложений Магазина Windows не поддерживается и приводит к сбою сборки проекта.</span><span class="sxs-lookup"><span data-stu-id="c6f51-345">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6f51-346">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c6f51-346">See also</span></span>

- [<span data-ttu-id="c6f51-347">Начало работы</span><span class="sxs-lookup"><span data-stu-id="c6f51-347">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="c6f51-348">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="c6f51-348">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- <span data-ttu-id="c6f51-349">[Общие сведения о приложениях .NET для Магазина Windows](/previous-versions/windows/apps/br230302(v=vs.140))</span><span class="sxs-lookup"><span data-stu-id="c6f51-349">[.NET For Windows Store apps overview](/previous-versions/windows/apps/br230302(v=vs.140))</span></span>
- [<span data-ttu-id="c6f51-350">Поддержка платформы .NET Framework для приложений магазина Windows и среды выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="c6f51-350">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
