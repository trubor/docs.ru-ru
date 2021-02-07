---
description: Дополнительные сведения см. в списке параметров (Visual Basic)
title: Список параметров
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: f69063fac82887ba4da3119d8ec4fcac11b7f4c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741410"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="4d521-103">Список параметров (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d521-103">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="4d521-104">Указывает параметры, которые должны быть вызваны процедурой при ее вызове.</span><span class="sxs-lookup"><span data-stu-id="4d521-104">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="4d521-105">Несколько параметров разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="4d521-105">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="4d521-106">Ниже приведен синтаксис для одного параметра.</span><span class="sxs-lookup"><span data-stu-id="4d521-106">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d521-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4d521-107">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="4d521-108">Компоненты</span><span class="sxs-lookup"><span data-stu-id="4d521-108">Parts</span></span>

`attributelist`  
<span data-ttu-id="4d521-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4d521-109">Optional.</span></span> <span data-ttu-id="4d521-110">Список атрибутов, применяемых к этому параметру.</span><span class="sxs-lookup"><span data-stu-id="4d521-110">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="4d521-111">[Список атрибутов](attribute-list.md) необходимо заключить в угловые скобки (" `<` " и " `>` ").</span><span class="sxs-lookup"><span data-stu-id="4d521-111">You must enclose the [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="4d521-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4d521-112">Optional.</span></span> <span data-ttu-id="4d521-113">Указывает, что этот параметр не является обязательным при вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="4d521-113">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="4d521-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4d521-114">Optional.</span></span> <span data-ttu-id="4d521-115">Указывает, что процедура не может заменить или переназначить элемент переменной, лежащий в основе соответствующего аргумента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="4d521-115">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="4d521-116">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4d521-116">Optional.</span></span> <span data-ttu-id="4d521-117">Указывает, что процедура может изменить базовый элемент Variable в вызывающем коде так же, как и сам вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="4d521-117">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="4d521-118">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4d521-118">Optional.</span></span> <span data-ttu-id="4d521-119">Указывает, что последний параметр в списке параметров является необязательным массивом элементов указанного типа данных.</span><span class="sxs-lookup"><span data-stu-id="4d521-119">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="4d521-120">Это позволяет вызывающему коду передавать процедуре произвольное число аргументов.</span><span class="sxs-lookup"><span data-stu-id="4d521-120">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="4d521-121">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4d521-121">Required.</span></span> <span data-ttu-id="4d521-122">Имя локальной переменной, представляющей параметр.</span><span class="sxs-lookup"><span data-stu-id="4d521-122">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="4d521-123">Обязательный `Option Strict` , если имеет значение `On` .</span><span class="sxs-lookup"><span data-stu-id="4d521-123">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="4d521-124">Тип данных локальной переменной, представляющей параметр.</span><span class="sxs-lookup"><span data-stu-id="4d521-124">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="4d521-125">Требуется для `Optional` параметров.</span><span class="sxs-lookup"><span data-stu-id="4d521-125">Required for `Optional` parameters.</span></span> <span data-ttu-id="4d521-126">Любое константное или константное выражение, результатом которого является тип данных параметра.</span><span class="sxs-lookup"><span data-stu-id="4d521-126">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="4d521-127">Если тип — `Object` , или класс, интерфейс, массив или структура, значением по умолчанию может быть только `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="4d521-127">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d521-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="4d521-128">Remarks</span></span>

<span data-ttu-id="4d521-129">Параметры заключаются в круглые скобки и разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="4d521-129">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="4d521-130">Параметр может быть объявлен с любым типом данных.</span><span class="sxs-lookup"><span data-stu-id="4d521-130">A parameter can be declared with any data type.</span></span> <span data-ttu-id="4d521-131">Если не указать `parametertype` , по умолчанию используется значение `Object` .</span><span class="sxs-lookup"><span data-stu-id="4d521-131">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="4d521-132">Когда вызывающий код вызывает процедуру, он передает *аргумент* в каждый обязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="4d521-132">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="4d521-133">Дополнительные сведения см. в разделе [различия между параметрами и аргументами](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="4d521-133">For more information, see [Differences Between Parameters and Arguments](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="4d521-134">Аргумент, который вызывающий код передает каждому параметру, является указателем на базовый элемент в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="4d521-134">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="4d521-135">Если этот элемент является *неизменяемым* (константой, литералом, перечислением или выражением), любой код изменить его невозможно.</span><span class="sxs-lookup"><span data-stu-id="4d521-135">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="4d521-136">Если это элемент *переменной* (объявленная переменная, поле, свойство, элемент массива или элемент структуры), вызывающий код может изменить его.</span><span class="sxs-lookup"><span data-stu-id="4d521-136">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="4d521-137">Дополнительные сведения см. в разделе [различия между изменяемыми и неизменяемыми аргументами](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="4d521-137">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="4d521-138">Если передается элемент переменной `ByRef` , процедура также может изменить ее.</span><span class="sxs-lookup"><span data-stu-id="4d521-138">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="4d521-139">Дополнительные сведения см. в разделе [различия между передачей аргумента по значению и по ссылке](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="4d521-139">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="4d521-140">Правила</span><span class="sxs-lookup"><span data-stu-id="4d521-140">Rules</span></span>

- <span data-ttu-id="4d521-141">**Скобки.**</span><span class="sxs-lookup"><span data-stu-id="4d521-141">**Parentheses.**</span></span> <span data-ttu-id="4d521-142">Если указан список параметров, его необходимо заключить в круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="4d521-142">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="4d521-143">Если параметры отсутствуют, можно по-прежнему использовать круглые скобки, включающие пустой список.</span><span class="sxs-lookup"><span data-stu-id="4d521-143">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="4d521-144">Это повышает удобочитаемость кода путем уточнения того, что элемент является процедурой.</span><span class="sxs-lookup"><span data-stu-id="4d521-144">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="4d521-145">**Необязательные параметры.**</span><span class="sxs-lookup"><span data-stu-id="4d521-145">**Optional Parameters.**</span></span> <span data-ttu-id="4d521-146">При использовании `Optional` модификатора для параметра все последующие параметры в списке также должны быть необязательными и объявлены с помощью `Optional` модификатора.</span><span class="sxs-lookup"><span data-stu-id="4d521-146">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="4d521-147">Каждое объявление необязательного параметра должно предоставлять `defaultvalue` предложение.</span><span class="sxs-lookup"><span data-stu-id="4d521-147">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="4d521-148">Дополнительные сведения см. в разделе [необязательные параметры](../../programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4d521-148">For more information, see [Optional Parameters](../../programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="4d521-149">**Массивы параметров.**</span><span class="sxs-lookup"><span data-stu-id="4d521-149">**Parameter Arrays.**</span></span> <span data-ttu-id="4d521-150">`ByVal`Для параметра необходимо указать `ParamArray` .</span><span class="sxs-lookup"><span data-stu-id="4d521-150">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="4d521-151">`Optional`В одном списке параметров нельзя использовать и, и `ParamArray` .</span><span class="sxs-lookup"><span data-stu-id="4d521-151">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="4d521-152">Дополнительные сведения см. в разделе [массивы параметров](../../programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="4d521-152">For more information, see [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="4d521-153">**Механизм передачи.**</span><span class="sxs-lookup"><span data-stu-id="4d521-153">**Passing Mechanism.**</span></span> <span data-ttu-id="4d521-154">Механизмом по умолчанию для каждого аргумента является `ByVal` , что означает, что процедура не может изменить базовый элемент Variable.</span><span class="sxs-lookup"><span data-stu-id="4d521-154">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="4d521-155">Однако если элемент является ссылочным типом, процедура может изменить содержимое или члены базового объекта, даже если он не может заменить или переназначить сам объект.</span><span class="sxs-lookup"><span data-stu-id="4d521-155">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="4d521-156">**Имена параметров.**</span><span class="sxs-lookup"><span data-stu-id="4d521-156">**Parameter Names.**</span></span> <span data-ttu-id="4d521-157">Если тип данных параметра является массивом, `parametername` сразу после круглых скобок.</span><span class="sxs-lookup"><span data-stu-id="4d521-157">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="4d521-158">Дополнительные сведения об именах параметров см. в разделе [Имена объявленных элементов](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4d521-158">For more information on parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="4d521-159">Пример</span><span class="sxs-lookup"><span data-stu-id="4d521-159">Example</span></span>

<span data-ttu-id="4d521-160">В следующем примере показана `Function` процедура, определяющая два параметра.</span><span class="sxs-lookup"><span data-stu-id="4d521-160">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="4d521-161">См. также</span><span class="sxs-lookup"><span data-stu-id="4d521-161">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="4d521-162">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="4d521-162">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="4d521-163">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="4d521-163">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="4d521-164">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="4d521-164">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="4d521-165">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="4d521-165">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="4d521-166">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="4d521-166">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="4d521-167">Обзор атрибутов</span><span class="sxs-lookup"><span data-stu-id="4d521-167">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="4d521-168">Практическое руководство. Разбиение и объединение инструкций в коде</span><span class="sxs-lookup"><span data-stu-id="4d521-168">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
