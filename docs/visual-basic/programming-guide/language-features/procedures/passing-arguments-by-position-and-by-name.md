---
description: 'Дополнительные сведения: Передача аргументов по положению и по имени (Visual Basic)'
title: Передача аргументов по позиции и по имени
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: 2938638bbdeb411bec53f338371d4215140dc4a0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466696"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="9d11a-103">Передача аргументов по позиции и по имени (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d11a-103">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="9d11a-104">При вызове `Sub` процедуры или `Function` можно передавать аргументы *по положению* , в том порядке, в котором они отображаются в определении процедуры, или передавать их *по имени*, не обращаясь к положению.</span><span class="sxs-lookup"><span data-stu-id="9d11a-104">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="9d11a-105">При передаче аргумента по имени указывается объявленное имя аргумента, за которым следует двоеточие и знак равенства ( `:=` ), за которым следует значение аргумента.</span><span class="sxs-lookup"><span data-stu-id="9d11a-105">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="9d11a-106">Именованные аргументы можно указывать в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="9d11a-106">You can supply named arguments in any order.</span></span>

<span data-ttu-id="9d11a-107">Например, следующая `Sub` процедура принимает три аргумента:</span><span class="sxs-lookup"><span data-stu-id="9d11a-107">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="9d11a-108">При вызове этой процедуры аргументы можно указать по положению, по имени или с помощью сочетания обоих типов.</span><span class="sxs-lookup"><span data-stu-id="9d11a-108">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="9d11a-109">Передача аргументов по положению</span><span class="sxs-lookup"><span data-stu-id="9d11a-109">Passing Arguments by Position</span></span>

<span data-ttu-id="9d11a-110">Метод можно вызвать `Display` с аргументами, передаваемыми по положению и разделенным запятыми, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="9d11a-110">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="9d11a-111">Если необязательный аргумент не указан в списке позиционированных аргументов, необходимо держать его место с запятой.</span><span class="sxs-lookup"><span data-stu-id="9d11a-111">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="9d11a-112">В следующем примере вызывается `Display` метод без `age` аргумента:</span><span class="sxs-lookup"><span data-stu-id="9d11a-112">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="9d11a-113">Передача аргументов по имени</span><span class="sxs-lookup"><span data-stu-id="9d11a-113">Passing Arguments by Name</span></span>

<span data-ttu-id="9d11a-114">Кроме того, можно вызвать `Display` с аргументами, передаваемыми по имени, также разделенными запятыми, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="9d11a-114">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="9d11a-115">Передача аргументов по имени таким способом особенно полезна при вызове процедуры, имеющей более одного необязательного аргумента.</span><span class="sxs-lookup"><span data-stu-id="9d11a-115">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="9d11a-116">Если аргументы указываются по имени, не нужно использовать последовательные запятые для обозначения пропущенных аргументов.</span><span class="sxs-lookup"><span data-stu-id="9d11a-116">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="9d11a-117">Передача аргументов по имени также упрощает отслеживание передаваемых аргументов и тех, которые вы пропускаете.</span><span class="sxs-lookup"><span data-stu-id="9d11a-117">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="9d11a-118">Смешивание аргументов по положению и по имени</span><span class="sxs-lookup"><span data-stu-id="9d11a-118">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="9d11a-119">Аргументы можно указать как по положению, так и по имени в одном вызове процедуры, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="9d11a-119">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="9d11a-120">В предыдущем примере не требуется дополнительная запятая для размещения пропущенного `age` аргумента, так как `birth` передается по имени.</span><span class="sxs-lookup"><span data-stu-id="9d11a-120">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="9d11a-121">В версиях Visual Basic до 15,5, при указании аргументов в сочетании с аргументами "расположение" и "имя" все аргументы должны быть первыми.</span><span class="sxs-lookup"><span data-stu-id="9d11a-121">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="9d11a-122">После указания аргумента по имени все остальные аргументы должны передаваться по имени.</span><span class="sxs-lookup"><span data-stu-id="9d11a-122">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="9d11a-123">Например, при следующем вызове `Display` метода отображается ошибка компилятора [BC30241: Ожидается именованный аргумент](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="9d11a-123">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="9d11a-124">Начиная с Visual Basic 15,5, позиционированные аргументы могут следовать именованным аргументам, если конечные аргументы конца находятся в правильном положении.</span><span class="sxs-lookup"><span data-stu-id="9d11a-124">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="9d11a-125">При компиляции в разделе Visual Basic 15,5 предыдущий вызов `Display` метода компилируется успешно и больше не создает ошибку компилятора [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="9d11a-125">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="9d11a-126">Возможность смешивать и сопоставлять именованные и позиционированные аргументы в любом порядке особенно полезна, если нужно использовать именованный аргумент, чтобы сделать код более удобочитаемым.</span><span class="sxs-lookup"><span data-stu-id="9d11a-126">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="9d11a-127">Например, следующий `Person` конструктор класса требует два аргумента типа `Person` , оба из которых могут иметь значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="9d11a-127">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="9d11a-128">Использование смешанных именованных и позиционированных аргументов позволяет сделать код понятным, если `father` `mother` аргументы и имеют значение `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="9d11a-128">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="9d11a-129">Чтобы следовать аргументам с именованными аргументами, необходимо добавить в файл проекта Visual Basic ( \* VBPROJ) следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="9d11a-129">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="9d11a-130">Дополнительные сведения см. [в разделе Задание языковой версии Visual Basic](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="9d11a-130">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="9d11a-131">Ограничения на предоставление аргументов по имени</span><span class="sxs-lookup"><span data-stu-id="9d11a-131">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="9d11a-132">Аргументы нельзя передавать по имени, чтобы избежать ввода обязательных аргументов.</span><span class="sxs-lookup"><span data-stu-id="9d11a-132">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="9d11a-133">Можно опустить только необязательные аргументы.</span><span class="sxs-lookup"><span data-stu-id="9d11a-133">You can omit only the optional arguments.</span></span>

<span data-ttu-id="9d11a-134">Невозможно передать массив параметров по имени.</span><span class="sxs-lookup"><span data-stu-id="9d11a-134">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="9d11a-135">Это происходит потому, что при вызове процедуры вы предоставляете неопределенное число аргументов, разделенных запятыми, для массива параметров, и компилятор не может связать более одного аргумента с одним именем.</span><span class="sxs-lookup"><span data-stu-id="9d11a-135">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d11a-136">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9d11a-136">See also</span></span>

- [<span data-ttu-id="9d11a-137">Процедуры</span><span class="sxs-lookup"><span data-stu-id="9d11a-137">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9d11a-138">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="9d11a-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9d11a-139">Практическое руководство. Передача аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="9d11a-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="9d11a-140">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="9d11a-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="9d11a-141">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="9d11a-141">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="9d11a-142">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="9d11a-142">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="9d11a-143">Необязательно</span><span class="sxs-lookup"><span data-stu-id="9d11a-143">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="9d11a-144">ParamArray</span><span class="sxs-lookup"><span data-stu-id="9d11a-144">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
