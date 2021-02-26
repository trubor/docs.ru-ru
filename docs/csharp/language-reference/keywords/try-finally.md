---
description: Справочник по C#. Оператор try-finally
title: Справочник по C#. Оператор try-finally
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 03e5fa46cef6b30a0af15c113ec6b141a61bee47
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639420"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="0f236-103">try-finally (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="0f236-103">try-finally (C# Reference)</span></span>

<span data-ttu-id="0f236-104">С помощью блока `finally` можно выполнить очистку всех ресурсов, выделенных в блоке [try](try-catch.md), и запускать код даже при возникновении исключения в блоке `try`.</span><span class="sxs-lookup"><span data-stu-id="0f236-104">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="0f236-105">Как правило, операторы блока `finally` выполняются, когда элемент управления покидает оператор `try`.</span><span class="sxs-lookup"><span data-stu-id="0f236-105">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="0f236-106">Передача управления может возникать в результате нормального выполнения, выполнения операторов `break`, `continue`, `goto` или `return` или распространения исключения из оператора `try`.</span><span class="sxs-lookup"><span data-stu-id="0f236-106">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="0f236-107">Внутри обработанного исключения гарантируется выполнение связанного блока `finally`.</span><span class="sxs-lookup"><span data-stu-id="0f236-107">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="0f236-108">Однако если исключение не обработано, то выполнение блока `finally` зависит от того, как запускается операция развертывания исключения.</span><span class="sxs-lookup"><span data-stu-id="0f236-108">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="0f236-109">Это, в свою очередь, зависит от способа настройки компьютера.</span><span class="sxs-lookup"><span data-stu-id="0f236-109">That, in turn, is dependent on how your computer is set up.</span></span> <span data-ttu-id="0f236-110">Единственные случаи, когда предложения `finally` не выполняются — немедленная остановка программы.</span><span class="sxs-lookup"><span data-stu-id="0f236-110">The only cases where `finally` clauses don't run involve a program being immediately stopped.</span></span> <span data-ttu-id="0f236-111">Например, это может произойти при вызове исключения <xref:System.InvalidProgramException> из-за повреждения инструкций IL.</span><span class="sxs-lookup"><span data-stu-id="0f236-111">An example of this would be when <xref:System.InvalidProgramException> gets thrown because of the IL statements being corrupt.</span></span> <span data-ttu-id="0f236-112">В большинстве операционных систем при остановке и выгрузке процесса будет выполняться обоснованная очистка ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0f236-112">On most operating systems, reasonable resource cleanup will take place as part of stopping and unloading the process.</span></span>

<span data-ttu-id="0f236-113">Как правило, когда необработанное исключение приводит к завершению работы приложения, выполнение блока `finally` не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="0f236-113">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="0f236-114">Однако если в блоке `finally` есть операторы, которые необходимо запускать даже в такой ситуации, одним из решений является добавление блока `catch` в оператор `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="0f236-114">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="0f236-115">Кроме того, можно перехватить исключение, которое может создаваться в блоке `try` оператора `try`-`finally` выше в стеке вызовов.</span><span class="sxs-lookup"><span data-stu-id="0f236-115">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="0f236-116">То есть можно перехватить исключение в методе, который вызывает метод, содержащий оператор `try`-`finally`, или в методе, который вызывает этот метод, или в любом методе в стеке вызовов.</span><span class="sxs-lookup"><span data-stu-id="0f236-116">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="0f236-117">Если исключение не перехвачено, выполнение блока `finally` зависит от того, активирует ли операционная система операцию развертывания исключения.</span><span class="sxs-lookup"><span data-stu-id="0f236-117">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="0f236-118">Пример</span><span class="sxs-lookup"><span data-stu-id="0f236-118">Example</span></span>

<span data-ttu-id="0f236-119">В следующем примере недопустимый оператор преобразования вызывает исключение `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="0f236-119">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="0f236-120">Исключение не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="0f236-120">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="0f236-121">В следующем примере исключение из метода `TryCast` перехватывается в методе выше в стеке вызовов.</span><span class="sxs-lookup"><span data-stu-id="0f236-121">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="0f236-122">Дополнительные сведения о `finally` см. в разделе [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="0f236-122">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="0f236-123">C# также содержит [оператор using](using-statement.md), который предоставляет аналогичную функциональность для объектов <xref:System.IDisposable> в удобном синтаксисе.</span><span class="sxs-lookup"><span data-stu-id="0f236-123">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0f236-124">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="0f236-124">C# language specification</span></span>

<span data-ttu-id="0f236-125">Дополнительные сведения см. в разделе [Оператор try](~/_csharplang/spec/statements.md#the-try-statement) в документации [Спецификация C# 6.0](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0f236-125">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f236-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0f236-126">See also</span></span>

- [<span data-ttu-id="0f236-127">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="0f236-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0f236-128">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="0f236-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0f236-129">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="0f236-129">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0f236-130">Операторы try, throw и catch (C++)</span><span class="sxs-lookup"><span data-stu-id="0f236-130">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="0f236-131">throw</span><span class="sxs-lookup"><span data-stu-id="0f236-131">throw</span></span>](throw.md)
- [<span data-ttu-id="0f236-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="0f236-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="0f236-133">Практическое руководство. Явное создание исключений</span><span class="sxs-lookup"><span data-stu-id="0f236-133">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
