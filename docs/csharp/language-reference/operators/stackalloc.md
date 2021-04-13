---
description: выражение stackalloc справочнике по C#
title: выражение stackalloc справочнике по C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 42867ff1b5acffaf62639a31a5bdd3b4055e252a
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497467"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="4682b-103">выражение stackalloc (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="4682b-103">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="4682b-104">Выражение `stackalloc` выделяет блок памяти в стеке.</span><span class="sxs-lookup"><span data-stu-id="4682b-104">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="4682b-105">Выделенный в стеке блок памяти, который создает этот метод, автоматически удаляется по завершении выполнения метода.</span><span class="sxs-lookup"><span data-stu-id="4682b-105">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="4682b-106">Вы не можете явным образом освободить память, выделенную `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="4682b-106">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="4682b-107">Выделенный в стеке блок памяти не подвергается [сборке мусора](../../../standard/garbage-collection/index.md), поэтому его не нужно закреплять с помощью [инструкции `fixed`](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4682b-107">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="4682b-108">Результат выполнения выражения `stackalloc` можно присвоить переменной любого из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="4682b-108">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="4682b-109">Начиная с версии C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> или <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="4682b-109">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/shared/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="4682b-110">Нет необходимости использовать [небезопасный](../keywords/unsafe.md) контекст при назначении выделенного в стеке блока памяти переменной <xref:System.Span%601> или <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="4682b-110">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="4682b-111">При работе с такими типами вы можете использовать выражение `stackalloc` в [условном](conditional-operator.md) выражении или выражении присваивания, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="4682b-111">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/shared/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="4682b-112">Начиная с версии C# 8.0, можно использовать выражение `stackalloc` внутри других выражений, если разрешена переменная <xref:System.Span%601> или <xref:System.ReadOnlySpan%601>, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="4682b-112">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/shared/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="4682b-113">Мы рекомендуем везде, где это возможно, использовать для работы с выделенной в стеке памятью типы <xref:System.Span%601> или <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="4682b-113">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="4682b-114">[Тип указателя](../unsafe-code.md#pointer-types), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4682b-114">A [pointer type](../unsafe-code.md#pointer-types), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/shared/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="4682b-115">Как демонстрирует пример выше, при работе с типами указателей необходимо использовать контекст `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="4682b-115">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="4682b-116">В случае типов указателей можно использовать выражение `stackalloc` только в объявлении локальной переменной для инициализации переменной.</span><span class="sxs-lookup"><span data-stu-id="4682b-116">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="4682b-117">Объем доступной памяти в стеке ограничен.</span><span class="sxs-lookup"><span data-stu-id="4682b-117">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="4682b-118">При выделении слишком большого объема памяти в стеке возникает исключение <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="4682b-118">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="4682b-119">Чтобы избежать этого, следуйте приведенным ниже правилам.</span><span class="sxs-lookup"><span data-stu-id="4682b-119">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="4682b-120">Ограничьте объем памяти, выделенный `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="4682b-120">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/shared/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="4682b-121">Поскольку объем доступной памяти на стеке зависит от среды, в которой выполняется код, при определении фактического предельного значения следует использовать консервативное значение.</span><span class="sxs-lookup"><span data-stu-id="4682b-121">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="4682b-122">Старайтесь не использовать `stackalloc` в циклах.</span><span class="sxs-lookup"><span data-stu-id="4682b-122">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="4682b-123">Выделяйте блок памяти за пределами цикла и используйте его повторно внутри цикла.</span><span class="sxs-lookup"><span data-stu-id="4682b-123">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="4682b-124">Содержимое только что выделенной памяти не определено.</span><span class="sxs-lookup"><span data-stu-id="4682b-124">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="4682b-125">Его следует инициализировать перед использованием.</span><span class="sxs-lookup"><span data-stu-id="4682b-125">You should initialize it before the use.</span></span> <span data-ttu-id="4682b-126">Например, вы можете использовать метод <xref:System.Span%601.Clear%2A?displayProperty=nameWithType>, который задает для всех элементов значение по умолчанию типа `T`.</span><span class="sxs-lookup"><span data-stu-id="4682b-126">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="4682b-127">Начиная с версии C# 7.3, вы можете использовать синтаксис инициализатора массива, чтобы определить содержимое для только что выделенной памяти.</span><span class="sxs-lookup"><span data-stu-id="4682b-127">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="4682b-128">В следующем примере показано несколько способов сделать это:</span><span class="sxs-lookup"><span data-stu-id="4682b-128">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/shared/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="4682b-129">В выражении `stackalloc T[E]` `T` должен иметь [неуправляемый тип](../builtin-types/unmanaged-types.md), а `E` — неотрицательное значение [int](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="4682b-129">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="4682b-130">Безопасность</span><span class="sxs-lookup"><span data-stu-id="4682b-130">Security</span></span>

<span data-ttu-id="4682b-131">При использовании `stackalloc` в среде CLR автоматически включается контроль переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="4682b-131">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="4682b-132">Если буфер переполнен, процесс незамедлительно прерывается — это позволяет минимизировать риск исполнения вредоносного кода.</span><span class="sxs-lookup"><span data-stu-id="4682b-132">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4682b-133">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="4682b-133">C# language specification</span></span>

<span data-ttu-id="4682b-134">См. сведения о [выделении памяти в стеке](~/_csharplang/spec/unsafe-code.md#stack-allocation) в [спецификации языка C#](~/_csharplang/spec/introduction.md) и [разрешении `stackalloc` во вложенных контекстах](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) в примечании.</span><span class="sxs-lookup"><span data-stu-id="4682b-134">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="4682b-135">См. также</span><span class="sxs-lookup"><span data-stu-id="4682b-135">See also</span></span>

- [<span data-ttu-id="4682b-136">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="4682b-136">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4682b-137">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="4682b-137">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="4682b-138">Операторы, связанные с указателем</span><span class="sxs-lookup"><span data-stu-id="4682b-138">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="4682b-139">Типы указателей</span><span class="sxs-lookup"><span data-stu-id="4682b-139">Pointer types</span></span>](../unsafe-code.md#pointer-types)
- [<span data-ttu-id="4682b-140">Типы, связанные с памятью и диапазонами</span><span class="sxs-lookup"><span data-stu-id="4682b-140">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="4682b-141">Правила stackalloc</span><span class="sxs-lookup"><span data-stu-id="4682b-141">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
