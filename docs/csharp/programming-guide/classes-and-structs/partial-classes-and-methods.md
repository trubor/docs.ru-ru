---
title: Руководство по программированию на C#. Разделяемые классы и методы
description: Разделяемые классы и методы в C# разделяют определение класса, структуры, интерфейса или метода между двумя исходными файлами или более.
ms.date: 03/23/2021
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 2132dd8e729725f0dd9bcb4477a3a604aa7065a0
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111053"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="79188-103">Разделяемые классы и методы (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="79188-103">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="79188-104">Можно разделить определение [класса](../../language-reference/keywords/class.md), [структуры](../../language-reference/builtin-types/struct.md), [интерфейса](../../language-reference/keywords/interface.md) или метода между двумя или более исходными файлами.</span><span class="sxs-lookup"><span data-stu-id="79188-104">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="79188-105">Каждый исходный файл содержит часть определения класса или метода, а во время компиляции приложения все части объединяются.</span><span class="sxs-lookup"><span data-stu-id="79188-105">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="79188-106">Разделяемые классы</span><span class="sxs-lookup"><span data-stu-id="79188-106">Partial Classes</span></span>

<span data-ttu-id="79188-107">Существует несколько ситуаций, когда желательно разделение определения класса.</span><span class="sxs-lookup"><span data-stu-id="79188-107">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="79188-108">При работе над большими проектами распределение класса между различными файлами позволяет нескольким программистам работать с ним одновременно.</span><span class="sxs-lookup"><span data-stu-id="79188-108">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="79188-109">При работе с использованием автоматически создаваемого источника код можно добавлять в класс без повторного создания файла источника.</span><span class="sxs-lookup"><span data-stu-id="79188-109">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="79188-110">Visual Studio использует этот подход при создании форм Windows Forms, кода оболочки веб-службы и т. д.</span><span class="sxs-lookup"><span data-stu-id="79188-110">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="79188-111">Можно создать код, который использует эти классы, без необходимости изменения файла, созданного в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79188-111">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="79188-112">Чтобы разделить определение класса, используйте модификатор ключевого слова [partial](../../language-reference/keywords/partial-type.md), как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="79188-112">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[EmployeeExample#1](snippets/partial-classes-and-methods/Program.cs#1)]

<span data-ttu-id="79188-113">Ключевое слово `partial` указывает, что другие части класса, структуры или интерфейса могут быть определены в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="79188-113">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="79188-114">Все части должны использовать ключевое слово `partial`.</span><span class="sxs-lookup"><span data-stu-id="79188-114">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="79188-115">Для формирования окончательного типа все части должны быть доступны во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="79188-115">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="79188-116">Все части должны иметь одинаковые модификаторы доступа, например `public`, `private` и т. д.</span><span class="sxs-lookup"><span data-stu-id="79188-116">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="79188-117">Если какая-либо из частей объявлена абстрактной, то весь тип будет считаться абстрактным.</span><span class="sxs-lookup"><span data-stu-id="79188-117">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="79188-118">Если какая-либо из частей объявлена запечатанной, то весь тип будет считаться запечатанным.</span><span class="sxs-lookup"><span data-stu-id="79188-118">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="79188-119">Если какая-либо из частей объявляет базовый тип, то весь тип будет наследовать данный класс.</span><span class="sxs-lookup"><span data-stu-id="79188-119">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="79188-120">Все части, указывающие базовый класс, должны быть согласованы друг с другом, а части, не использующие базовый класс, все равно наследуют базовый тип.</span><span class="sxs-lookup"><span data-stu-id="79188-120">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="79188-121">Части могут указывать различные базовые интерфейсы, и окончательный тип будет реализовывать все интерфейсы, перечисленные во всех разделяемых объявлениях.</span><span class="sxs-lookup"><span data-stu-id="79188-121">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="79188-122">Любые члены класса, структуры или интерфейса, объявленные в разделяемом объявлении, доступны для всех остальных частей.</span><span class="sxs-lookup"><span data-stu-id="79188-122">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="79188-123">Окончательный тип представляет собой комбинацию всех частей, выполненную во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="79188-123">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="79188-124">Модификатор `partial` недоступен в объявлениях делегатов или перечислений.</span><span class="sxs-lookup"><span data-stu-id="79188-124">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="79188-125">В следующем примере показано, что вложенные типы могут быть разделяемыми, даже если тип, в который они вложены, не является разделяемым.</span><span class="sxs-lookup"><span data-stu-id="79188-125">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[NestedPartialTypes#2](snippets/partial-classes-and-methods/Program.cs#2)]

<span data-ttu-id="79188-126">Во время компиляции атрибуты определений разделяемого типа объединяются.</span><span class="sxs-lookup"><span data-stu-id="79188-126">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="79188-127">В качестве примера рассмотрим следующие объявления:</span><span class="sxs-lookup"><span data-stu-id="79188-127">For example, consider the following declarations:</span></span>

[!code-csharp[PartialMoonDeclarations#3](snippets/partial-classes-and-methods/Program.cs#3)]

<span data-ttu-id="79188-128">Они эквивалентны следующим объявлениям:</span><span class="sxs-lookup"><span data-stu-id="79188-128">They are equivalent to the following declarations:</span></span>

[!code-csharp[SingleMoonDeclaration#4](snippets/partial-classes-and-methods/Program.cs#4)]

<span data-ttu-id="79188-129">Следующие элементы объединяются из всех определений разделяемого типа:</span><span class="sxs-lookup"><span data-stu-id="79188-129">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="79188-130">XML-комментарии</span><span class="sxs-lookup"><span data-stu-id="79188-130">XML comments</span></span>

- <span data-ttu-id="79188-131">интерфейсы</span><span class="sxs-lookup"><span data-stu-id="79188-131">interfaces</span></span>

- <span data-ttu-id="79188-132">атрибуты параметров универсального параметра</span><span class="sxs-lookup"><span data-stu-id="79188-132">generic-type parameter attributes</span></span>

- <span data-ttu-id="79188-133">атрибуты классов</span><span class="sxs-lookup"><span data-stu-id="79188-133">class attributes</span></span>

- <span data-ttu-id="79188-134">члены</span><span class="sxs-lookup"><span data-stu-id="79188-134">members</span></span>

<span data-ttu-id="79188-135">В качестве примера рассмотрим следующие объявления:</span><span class="sxs-lookup"><span data-stu-id="79188-135">For example, consider the following declarations:</span></span>

[!code-csharp[PartialEarthDeclarations#5](snippets/partial-classes-and-methods/Program.cs#5)]

<span data-ttu-id="79188-136">Они эквивалентны следующим объявлениям:</span><span class="sxs-lookup"><span data-stu-id="79188-136">They are equivalent to the following declarations:</span></span>

[!code-csharp[SingleEarthDeclaration#6](snippets/partial-classes-and-methods/Program.cs#6)]

### <a name="restrictions"></a><span data-ttu-id="79188-137">Ограничения</span><span class="sxs-lookup"><span data-stu-id="79188-137">Restrictions</span></span>

<span data-ttu-id="79188-138">Имеется несколько правил, которые необходимо выполнять при работе с определениями разделяемого класса.</span><span class="sxs-lookup"><span data-stu-id="79188-138">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="79188-139">Все определения разделяемого типа, являющиеся частями одного типа, должны изменяться с использованием типа `partial`.</span><span class="sxs-lookup"><span data-stu-id="79188-139">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="79188-140">Например, следующие объявления класса приведут к появлению ошибки:</span><span class="sxs-lookup"><span data-stu-id="79188-140">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[AllDefinitionsMustBePartials#7](snippets/partial-classes-and-methods/Program.cs#7)]

- <span data-ttu-id="79188-141">Модификатор `partial` должен находиться непосредственно перед ключевыми словами `class`, `struct` или `interface`.</span><span class="sxs-lookup"><span data-stu-id="79188-141">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="79188-142">В определениях разделяемого типа могут присутствовать вложенные разделяемые типы, что показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="79188-142">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[NestedPartialTypes#8](snippets/partial-classes-and-methods/Program.cs#8)]

- <span data-ttu-id="79188-143">Все определения разделяемого типа, являющиеся частями одного и того же типа, должны быть определены в одной сборке и в одном модуле (EXE-файл или DLL-файл).</span><span class="sxs-lookup"><span data-stu-id="79188-143">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="79188-144">Разделяемые определения не могут находиться в разных модулях.</span><span class="sxs-lookup"><span data-stu-id="79188-144">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="79188-145">Имя класса и параметры универсального типа должны соответствовать всем определениям разделяемого типа.</span><span class="sxs-lookup"><span data-stu-id="79188-145">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="79188-146">Универсальные типы могут быть разделяемыми.</span><span class="sxs-lookup"><span data-stu-id="79188-146">Generic types can be partial.</span></span> <span data-ttu-id="79188-147">Все объявления разделяемого типа должны использовать одинаковые имена параметров в одном и том же порядке.</span><span class="sxs-lookup"><span data-stu-id="79188-147">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="79188-148">Приведенные ниже ключевые слова необязательно должны присутствовать в определении разделяемого типа, но если они присутствуют в одном определении разделяемого типа, то не должны конфликтовать с ключевыми словами, указанными в других определениях того же разделяемого типа.</span><span class="sxs-lookup"><span data-stu-id="79188-148">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="79188-149">public</span><span class="sxs-lookup"><span data-stu-id="79188-149">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="79188-150">private</span><span class="sxs-lookup"><span data-stu-id="79188-150">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="79188-151">protected</span><span class="sxs-lookup"><span data-stu-id="79188-151">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="79188-152">internal</span><span class="sxs-lookup"><span data-stu-id="79188-152">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="79188-153">abstract</span><span class="sxs-lookup"><span data-stu-id="79188-153">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="79188-154">sealed</span><span class="sxs-lookup"><span data-stu-id="79188-154">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="79188-155">базовый класс</span><span class="sxs-lookup"><span data-stu-id="79188-155">base class</span></span>

  - <span data-ttu-id="79188-156">модификатор [new](../../language-reference/keywords/new-modifier.md) (вложенные части)</span><span class="sxs-lookup"><span data-stu-id="79188-156">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="79188-157">универсальные ограничения</span><span class="sxs-lookup"><span data-stu-id="79188-157">generic constraints</span></span>

<span data-ttu-id="79188-158">Дополнительные сведения см. в разделе [Ограничения параметров типа](../generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="79188-158">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="79188-159">Пример 1</span><span class="sxs-lookup"><span data-stu-id="79188-159">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="79188-160">Описание</span><span class="sxs-lookup"><span data-stu-id="79188-160">Description</span></span>

<span data-ttu-id="79188-161">В следующем примере поля и конструктор класса `Coords` объявлены в одном определении разделяемого класса, а член `PrintCoords` — в другом определении разделяемого класса.</span><span class="sxs-lookup"><span data-stu-id="79188-161">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="79188-162">Код</span><span class="sxs-lookup"><span data-stu-id="79188-162">Code</span></span>

[!code-csharp[CoordsExample#9](snippets/partial-classes-and-methods/Program.cs#9)]

## <a name="example-2"></a><span data-ttu-id="79188-163">Пример 2</span><span class="sxs-lookup"><span data-stu-id="79188-163">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="79188-164">Описание</span><span class="sxs-lookup"><span data-stu-id="79188-164">Description</span></span>

<span data-ttu-id="79188-165">В следующем примере показано, что можно также разработать разделяемые структуры и интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="79188-165">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="79188-166">Код</span><span class="sxs-lookup"><span data-stu-id="79188-166">Code</span></span>

[!code-csharp[PartialStructsAndInterfaces#10](snippets/partial-classes-and-methods/Program.cs#10)]

## <a name="partial-methods"></a><span data-ttu-id="79188-167">Разделяемые методы</span><span class="sxs-lookup"><span data-stu-id="79188-167">Partial Methods</span></span>

<span data-ttu-id="79188-168">Разделяемый класс или структура могут содержать разделяемый метод.</span><span class="sxs-lookup"><span data-stu-id="79188-168">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="79188-169">Одна часть класса содержит сигнатуру метода.</span><span class="sxs-lookup"><span data-stu-id="79188-169">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="79188-170">В той же или в другой части можно определить реализацию.</span><span class="sxs-lookup"><span data-stu-id="79188-170">An implementation can be defined in the same part or another part.</span></span> <span data-ttu-id="79188-171">Если реализация не предоставлена, метод и все вызовы метода удаляются во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="79188-171">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span> <span data-ttu-id="79188-172">Реализация может потребоваться в зависимости от сигнатуры метода.</span><span class="sxs-lookup"><span data-stu-id="79188-172">Implementation may be required depending on method signature.</span></span>

<span data-ttu-id="79188-173">Разделяемые методы позволяют разработчику одной части класса определить метод, схожий с событием.</span><span class="sxs-lookup"><span data-stu-id="79188-173">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="79188-174">Разработчик другой части класса может решить, реализовывать этот метод или нет.</span><span class="sxs-lookup"><span data-stu-id="79188-174">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="79188-175">Если метод не реализован, то компилятор удаляет сигнатуру метода и все вызовы этого метода.</span><span class="sxs-lookup"><span data-stu-id="79188-175">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="79188-176">Вызовы метода, включая любые результаты, которые могли бы произойти от оценки аргументов в вызовах, не имеют эффекта во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="79188-176">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="79188-177">Таким образом, любой код в разделяемом классе может свободно использовать разделяемый метод, даже если реализация не предоставлена.</span><span class="sxs-lookup"><span data-stu-id="79188-177">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="79188-178">Во время компиляции и выполнения программы не возникнут никакие ошибки, если метод будет вызван, но не реализован.</span><span class="sxs-lookup"><span data-stu-id="79188-178">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="79188-179">Разделяемые методы особенно полезны для настройки автоматически созданного кода.</span><span class="sxs-lookup"><span data-stu-id="79188-179">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="79188-180">Они позволяют зарезервировать имя и сигнатуру метода, чтобы автоматически созданный код мог вызвать метод, а разработчик мог сам решить, реализовывать этот метод или нет.</span><span class="sxs-lookup"><span data-stu-id="79188-180">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="79188-181">Как и разделяемые классы, разделяемые методы позволяют организовать совместную работу автоматически созданного кода и кода, созданного человеком, без дополнительных затрат во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="79188-181">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="79188-182">Объявление разделяемого метода состоит из двух частей: определения и реализации.</span><span class="sxs-lookup"><span data-stu-id="79188-182">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="79188-183">Они могут находиться в разных частях или в одной и той же части разделяемого класса.</span><span class="sxs-lookup"><span data-stu-id="79188-183">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="79188-184">Если объявление реализации отсутствует, то компилятор оптимизирует код, удаляя как объявление определения, так и все вызовы метода.</span><span class="sxs-lookup"><span data-stu-id="79188-184">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void OnNameChanged();

// Implementation in file2.cs
partial void OnNameChanged()
{
  // method body
}
```

- <span data-ttu-id="79188-185">Объявления разделяемого метода должны начинаться с контекстного ключевого слова [partial](../../language-reference/keywords/partial-type.md).</span><span class="sxs-lookup"><span data-stu-id="79188-185">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md).</span></span>

- <span data-ttu-id="79188-186">Сигнатуры разделяемого метода в обеих частях разделяемого типа должны совпадать.</span><span class="sxs-lookup"><span data-stu-id="79188-186">Partial method signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="79188-187">Разделяемые методы могут иметь модификаторы [static](../../language-reference/keywords/static.md) и [unsafe](../../language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="79188-187">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="79188-188">Разделяемые методы могут быть универсальными.</span><span class="sxs-lookup"><span data-stu-id="79188-188">Partial methods can be generic.</span></span> <span data-ttu-id="79188-189">Ограничения налагаются на ту часть объявления разделяемого метода, где находится определение, и могут дополнительно повторяться в разделе реализации.</span><span class="sxs-lookup"><span data-stu-id="79188-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="79188-190">Имена параметров и типов параметров необязательно должны совпадать в объявлении реализации и в объявлении определения.</span><span class="sxs-lookup"><span data-stu-id="79188-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="79188-191">Можно использовать [делегат](../../language-reference/builtin-types/reference-types.md) в качестве определенного и реализованного разделяемого метода, но его нельзя использовать в качестве разделяемого метода, который только определен.</span><span class="sxs-lookup"><span data-stu-id="79188-191">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

<span data-ttu-id="79188-192">Разделяемый метод может не иметь реализацию в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="79188-192">A partial method isn't required to have an implementation in the following cases:</span></span>

- <span data-ttu-id="79188-193">У него нет модификаторов доступа (включая [private](../../language-reference/keywords/private.md) по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="79188-193">It doesn't have any accessibility modifiers (including the default [private](../../language-reference/keywords/private.md)).</span></span>

- <span data-ttu-id="79188-194">Он возвращает значение [void](../../language-reference/builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="79188-194">It returns [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="79188-195">У него нет параметров [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="79188-195">It doesn't have any [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="79188-196">У него нет ни одного из следующих модификаторов: [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), [sealed](../../language-reference/keywords/sealed.md), [new](../../language-reference/keywords/new-modifier.md) или [extern](../../language-reference/keywords/extern.md).</span><span class="sxs-lookup"><span data-stu-id="79188-196">It doesn't have any of the following modifiers [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), [sealed](../../language-reference/keywords/sealed.md), [new](../../language-reference/keywords/new-modifier.md), or [extern](../../language-reference/keywords/extern.md).</span></span>

<span data-ttu-id="79188-197">Любой метод, не соответствующий всем этим ограничениям (например, метод `public virtual partial void`), должен предоставлять реализацию.</span><span class="sxs-lookup"><span data-stu-id="79188-197">Any method that doesn't conform to all those restrictions (for example, `public virtual partial void` method), must provide an implementation.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="79188-198">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="79188-198">C# Language Specification</span></span>

<span data-ttu-id="79188-199">Дополнительные сведения см. в разделе [Разделяемые типы](~/_csharplang/spec/classes.md#partial-types) в [Спецификации языка C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="79188-199">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="79188-200">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="79188-200">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="79188-201">См. также</span><span class="sxs-lookup"><span data-stu-id="79188-201">See also</span></span>

- [<span data-ttu-id="79188-202">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="79188-202">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="79188-203">Классы</span><span class="sxs-lookup"><span data-stu-id="79188-203">Classes</span></span>](./classes.md)
- [<span data-ttu-id="79188-204">Типы структур</span><span class="sxs-lookup"><span data-stu-id="79188-204">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="79188-205">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="79188-205">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="79188-206">partial (тип)</span><span class="sxs-lookup"><span data-stu-id="79188-206">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
