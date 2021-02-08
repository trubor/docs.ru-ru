---
description: 'Дополнительные сведения о: #If... Then... #Else директивы'
title: '#Директивы If…Then…#Else'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: fd95d259315e0bd6fd6ab2a3f222288bb4726ce6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797254"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="cb49c-103">Директивы #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="cb49c-103">#If...Then...#Else Directives</span></span>

<span data-ttu-id="cb49c-104">Условно компилирует выбранные блоки кода Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cb49c-104">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb49c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb49c-105">Syntax</span></span>

```vb
#If expression Then
   statements
[ #ElseIf expression Then
   [ statements ]
...
#ElseIf expression Then
   [ statements ] ]
[ #Else
   [ statements ] ]
#End If
```

## <a name="parts"></a><span data-ttu-id="cb49c-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="cb49c-106">Parts</span></span>

`expression`  
<span data-ttu-id="cb49c-107">Требуется для `#If` `#ElseIf` операторов и, необязательно в других местах.</span><span class="sxs-lookup"><span data-stu-id="cb49c-107">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="cb49c-108">Любое выражение, состоящее только из одной или нескольких условных констант компилятора, литералов и операторов, которые имеют значение `True` или `False` .</span><span class="sxs-lookup"><span data-stu-id="cb49c-108">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="cb49c-109">Требуется для `#If` блока инструкций, необязательно в других местах.</span><span class="sxs-lookup"><span data-stu-id="cb49c-109">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="cb49c-110">Visual Basic строки программы или директивы компилятора, компилируемые, если связанное выражение имеет значение `True` .</span><span class="sxs-lookup"><span data-stu-id="cb49c-110">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="cb49c-111">Завершает `#If` блок операторов.</span><span class="sxs-lookup"><span data-stu-id="cb49c-111">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb49c-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb49c-112">Remarks</span></span>

<span data-ttu-id="cb49c-113">На поверхности поведение `#If...Then...#Else` директив выглядит так же, как и `If...Then...Else` инструкции.</span><span class="sxs-lookup"><span data-stu-id="cb49c-113">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="cb49c-114">Однако `#If...Then...#Else` директивы оценивают, что компилирует компилятор, тогда как `If...Then...Else` инструкции оценивают условия во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="cb49c-114">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="cb49c-115">Условная компиляция обычно используется для компиляции одной и той же программы для разных платформ.</span><span class="sxs-lookup"><span data-stu-id="cb49c-115">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="cb49c-116">Он также используется для предотвращения появления отладочного кода в исполняемом файле.</span><span class="sxs-lookup"><span data-stu-id="cb49c-116">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="cb49c-117">Код, исключенный во время условной компиляции, полностью опускается из финального исполняемого файла, поэтому он не влияет на размер и производительность.</span><span class="sxs-lookup"><span data-stu-id="cb49c-117">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="cb49c-118">Независимо от результата вычисления все выражения вычисляются с помощью `Option Compare Binary` .</span><span class="sxs-lookup"><span data-stu-id="cb49c-118">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="cb49c-119">`Option Compare`Инструкция не влияет на выражения в `#If` `#ElseIf` операторах и.</span><span class="sxs-lookup"><span data-stu-id="cb49c-119">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="cb49c-120">Не существует однострочной формы `#If` директив, `#Else` , `#ElseIf` и `#End If` .</span><span class="sxs-lookup"><span data-stu-id="cb49c-120">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="cb49c-121">Никакой другой код не может отображаться в той же строке, что и любая из директив.</span><span class="sxs-lookup"><span data-stu-id="cb49c-121">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="cb49c-122">Инструкции в блоке условной компиляции должны быть полными логическими операторами.</span><span class="sxs-lookup"><span data-stu-id="cb49c-122">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="cb49c-123">Например, невозможно условно компилировать только атрибуты функции, но можно условно объявить функцию вместе с ее атрибутами:</span><span class="sxs-lookup"><span data-stu-id="cb49c-123">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="cb49c-124">Пример</span><span class="sxs-lookup"><span data-stu-id="cb49c-124">Example</span></span>

<span data-ttu-id="cb49c-125">В этом примере `#If...Then...#Else` конструкция используется для определения необходимости компиляции определенных инструкций.</span><span class="sxs-lookup"><span data-stu-id="cb49c-125">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="cb49c-126">См. также</span><span class="sxs-lookup"><span data-stu-id="cb49c-126">See also</span></span>

- [<span data-ttu-id="cb49c-127">Директива #Const</span><span class="sxs-lookup"><span data-stu-id="cb49c-127">#Const Directive</span></span>](const-directive.md)
- [<span data-ttu-id="cb49c-128">Оператор If…Then…Else</span><span class="sxs-lookup"><span data-stu-id="cb49c-128">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="cb49c-129">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="cb49c-129">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
