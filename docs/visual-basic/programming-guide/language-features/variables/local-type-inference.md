---
description: 'Дополнительные сведения: определение локального типа (Visual Basic)'
title: Вывод локального типа
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 50be8544229360287d2aef27f31360d7140640ac
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481705"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="5a98f-103">Вывод локального типа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a98f-103">Local Type Inference (Visual Basic)</span></span>

<span data-ttu-id="5a98f-104">Компилятор Visual Basic использует *Определение типа* для определения типов данных локальных переменных, объявленных без `As` предложения.</span><span class="sxs-lookup"><span data-stu-id="5a98f-104">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="5a98f-105">Компилятор выводит тип переменной из типа выражения инициализации.</span><span class="sxs-lookup"><span data-stu-id="5a98f-105">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="5a98f-106">Это позволяет объявлять переменные без явного указания типа, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="5a98f-106">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="5a98f-107">В результате объявления `num1` и, и `num2` , строго типизированы как целые числа.</span><span class="sxs-lookup"><span data-stu-id="5a98f-107">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="5a98f-108">Если вы не хотите `num2` , чтобы в предыдущем примере была введена как `Integer` , можно указать другой тип с помощью объявления, например `Dim num3 As Object = 3` или `Dim num4 As Double = 3` .</span><span class="sxs-lookup"><span data-stu-id="5a98f-108">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>

> [!NOTE]
> <span data-ttu-id="5a98f-109">Определение типа может использоваться только для нестатических локальных переменных. его нельзя использовать для определения типа полей, свойств или функций класса.</span><span class="sxs-lookup"><span data-stu-id="5a98f-109">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>

<span data-ttu-id="5a98f-110">Локальное определение типа применяется на уровне процедуры.</span><span class="sxs-lookup"><span data-stu-id="5a98f-110">Local type inference applies at procedure level.</span></span> <span data-ttu-id="5a98f-111">Его нельзя использовать для объявления переменных на уровне модуля (внутри класса, структуры, модуля или интерфейса, но не внутри процедуры или блока).</span><span class="sxs-lookup"><span data-stu-id="5a98f-111">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="5a98f-112">Если `num2` в предыдущем примере было бы поле класса, а не локальная переменная в процедуре, объявление приведет к ошибке с параметром `Option Strict` On и будет классифицироваться `num2` как `Object` с `Option Strict` Off.</span><span class="sxs-lookup"><span data-stu-id="5a98f-112">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="5a98f-113">Аналогичным образом, локальное определение типа не применяется к переменным уровня процедуры, объявленным как `Static` .</span><span class="sxs-lookup"><span data-stu-id="5a98f-113">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>

## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="5a98f-114">Определение типа и позднее связывание</span><span class="sxs-lookup"><span data-stu-id="5a98f-114">Type Inference vs. Late Binding</span></span>

<span data-ttu-id="5a98f-115">Код, использующий вывод типа, напоминает код, основанный на позднем связывании.</span><span class="sxs-lookup"><span data-stu-id="5a98f-115">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="5a98f-116">Однако вывод типа строго вводит переменную вместо того, чтобы покинуть ее как `Object` .</span><span class="sxs-lookup"><span data-stu-id="5a98f-116">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="5a98f-117">Компилятор использует инициализатор переменной для определения типа переменной во время компиляции для создания кода с ранней привязкой.</span><span class="sxs-lookup"><span data-stu-id="5a98f-117">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="5a98f-118">В предыдущем примере, `num2` Like `num1` имеет тип `Integer` .</span><span class="sxs-lookup"><span data-stu-id="5a98f-118">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>

<span data-ttu-id="5a98f-119">Поведение переменных с ранней привязкой отличается от поведения переменных с поздним связыванием, для которых тип известен только во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5a98f-119">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="5a98f-120">Знание типа на раннем этапе позволяет компилятору определить проблемы перед выполнением, выделить память точно и выполнить другие оптимизации.</span><span class="sxs-lookup"><span data-stu-id="5a98f-120">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="5a98f-121">Раннее связывание также включает Visual Basic интегрированную среду разработки (IDE) для предоставления справки IntelliSense об элементах объекта.</span><span class="sxs-lookup"><span data-stu-id="5a98f-121">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="5a98f-122">Раннее связывание также предпочтительно для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="5a98f-122">Early binding is also preferred for performance.</span></span> <span data-ttu-id="5a98f-123">Это связано с тем, что все данные, хранящиеся в переменной с поздним связыванием, должны быть упакованы как тип `Object` , а доступ к элементам типа во время выполнения значительно замедляет работу программы.</span><span class="sxs-lookup"><span data-stu-id="5a98f-123">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>

## <a name="examples"></a><span data-ttu-id="5a98f-124">Примеры</span><span class="sxs-lookup"><span data-stu-id="5a98f-124">Examples</span></span>

<span data-ttu-id="5a98f-125">Определение типа происходит, когда локальная переменная объявлена без `As` предложения и не инициализирована.</span><span class="sxs-lookup"><span data-stu-id="5a98f-125">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="5a98f-126">Компилятор использует тип присвоенного начального значения в качестве типа переменной.</span><span class="sxs-lookup"><span data-stu-id="5a98f-126">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="5a98f-127">Например, каждая из следующих строк кода объявляет переменную типа `String` .</span><span class="sxs-lookup"><span data-stu-id="5a98f-127">For example, each of the following lines of code declares a variable of type `String`.</span></span>

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

<span data-ttu-id="5a98f-128">В следующем коде показаны два эквивалентных способа создания массива целых чисел.</span><span class="sxs-lookup"><span data-stu-id="5a98f-128">The following code demonstrates two equivalent ways to create an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

<span data-ttu-id="5a98f-129">Для определения типа управляющей переменной цикла удобно использовать определение типа.</span><span class="sxs-lookup"><span data-stu-id="5a98f-129">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="5a98f-130">В следующем коде компилятор выводит, что является, `number` `Integer` поскольку `someNumbers2` из предыдущего примера представлен массив целых чисел.</span><span class="sxs-lookup"><span data-stu-id="5a98f-130">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

<span data-ttu-id="5a98f-131">Локальное определение типа может использоваться в `Using` инструкциях для определения типа имени ресурса, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="5a98f-131">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

<span data-ttu-id="5a98f-132">Тип переменной также может выводиться из возвращаемых значений функций, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="5a98f-132">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="5a98f-133">`pList1`И `pList2` , и являются массивами процессов, так как `Process.GetProcesses` возвращает массив процессов.</span><span class="sxs-lookup"><span data-stu-id="5a98f-133">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a><span data-ttu-id="5a98f-134">Option Infer</span><span class="sxs-lookup"><span data-stu-id="5a98f-134">Option Infer</span></span>

<span data-ttu-id="5a98f-135">`Option Infer` позволяет указать, разрешено ли определение локального типа в конкретном файле.</span><span class="sxs-lookup"><span data-stu-id="5a98f-135">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="5a98f-136">Чтобы включить или заблокировать параметр, введите одну из следующих инструкций в начале файла.</span><span class="sxs-lookup"><span data-stu-id="5a98f-136">To enable or to block the option, type one of the following statements at the start of the file.</span></span>

`Option Infer On`

`Option Infer Off`

<span data-ttu-id="5a98f-137">Если в коде не указано значение `Option Infer` , по умолчанию используется компилятор `Option Infer On` .</span><span class="sxs-lookup"><span data-stu-id="5a98f-137">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span>

<span data-ttu-id="5a98f-138">Если значение, заданное для `Option Infer` в файле, конфликтует со значением, заданным в среде разработки или в командной строке, приоритет имеет значение в файле.</span><span class="sxs-lookup"><span data-stu-id="5a98f-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="5a98f-139">Дополнительные сведения см. в статьях [выборка инструкций](../../../language-reference/statements/option-infer-statement.md) и [компиляции в конструкторе проектов (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5a98f-139">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a98f-140">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5a98f-140">See also</span></span>

- [<span data-ttu-id="5a98f-141">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="5a98f-141">Anonymous Types</span></span>](../objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="5a98f-142">Раннее и позднее связывание</span><span class="sxs-lookup"><span data-stu-id="5a98f-142">Early and Late Binding</span></span>](../early-late-binding/index.md)
- [<span data-ttu-id="5a98f-143">Оператор For Each…Next</span><span class="sxs-lookup"><span data-stu-id="5a98f-143">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="5a98f-144">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="5a98f-144">For...Next Statement</span></span>](../../../language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="5a98f-145">Оператор Option Infer</span><span class="sxs-lookup"><span data-stu-id="5a98f-145">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="5a98f-146">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="5a98f-146">-optioninfer</span></span>](../../../reference/command-line-compiler/optioninfer.md)
- <span data-ttu-id="5a98f-147">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a98f-147">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md)</span></span>
