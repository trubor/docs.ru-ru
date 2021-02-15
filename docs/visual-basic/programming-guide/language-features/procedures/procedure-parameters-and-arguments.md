---
description: 'Дополнительные сведения: параметры процедуры и аргументы (Visual Basic)'
title: Параметры и аргументы процедуры
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: c2239c76450f503e74dbf5f191cd212e05d11600
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423164"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="0e909-103">Параметры и аргументы процедуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e909-103">Procedure Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="0e909-104">В большинстве случаев для процедуры требуются некоторые сведения о обстоятельствах, в которых она была вызвана.</span><span class="sxs-lookup"><span data-stu-id="0e909-104">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="0e909-105">Процедура, выполняющая повторяющиеся или общие задачи, использует разные сведения для каждого вызова.</span><span class="sxs-lookup"><span data-stu-id="0e909-105">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="0e909-106">Эти сведения состоят из переменных, констант и выражений, которые передаются в процедуру при ее вызове.</span><span class="sxs-lookup"><span data-stu-id="0e909-106">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="0e909-107">*Параметр* представляет значение, которое процедура предполагает указать при ее вызове.</span><span class="sxs-lookup"><span data-stu-id="0e909-107">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="0e909-108">В объявлении процедуры определяются ее параметры.</span><span class="sxs-lookup"><span data-stu-id="0e909-108">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="0e909-109">Можно определить процедуру без параметров, один параметр или несколько.</span><span class="sxs-lookup"><span data-stu-id="0e909-109">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="0e909-110">Часть определения процедуры, указывающая параметры, называется *списком параметров*.</span><span class="sxs-lookup"><span data-stu-id="0e909-110">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="0e909-111">*Аргумент* представляет значение, указываемое в параметре процедуры при вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="0e909-111">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="0e909-112">Вызывающий код предоставляет аргументы при вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="0e909-112">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="0e909-113">Часть вызова процедуры, указывающая аргументы, называется *списком аргументов*.</span><span class="sxs-lookup"><span data-stu-id="0e909-113">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="0e909-114">На следующем рисунке показан код, вызывающий процедуру `safeSquareRoot` из двух различных мест.</span><span class="sxs-lookup"><span data-stu-id="0e909-114">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="0e909-115">Первый вызов передает значение переменной `x` (4,0) в параметр `number` , а возвращаемое значение в `root` (2,0) присваивается переменной `y` .</span><span class="sxs-lookup"><span data-stu-id="0e909-115">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="0e909-116">Второй вызов передает литеральное значение 9,0 в `number` , а затем присваивает возвращаемое значение (3,0) переменной `z` .</span><span class="sxs-lookup"><span data-stu-id="0e909-116">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Схема, показывающая передачу аргумента в параметр](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="0e909-118">Дополнительные сведения см. в разделе [различия между параметрами и аргументами](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="0e909-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="0e909-119">Тип данных параметра</span><span class="sxs-lookup"><span data-stu-id="0e909-119">Parameter Data Type</span></span>  

 <span data-ttu-id="0e909-120">Тип данных для параметра определяется с помощью `As` предложения в его объявлении.</span><span class="sxs-lookup"><span data-stu-id="0e909-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="0e909-121">Например, следующая функция принимает строку и целое число.</span><span class="sxs-lookup"><span data-stu-id="0e909-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="0e909-122">Если параметр проверки типов ([оператор Option строго](../../../language-reference/statements/option-strict-statement.md)) является `Off,` `As` предложением необязательным, за исключением того, что если какой-либо параметр использует его, все параметры должны использовать его.</span><span class="sxs-lookup"><span data-stu-id="0e909-122">If the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="0e909-123">Если проверка типа имеет значение `On` , `As` предложение является обязательным для всех параметров процедуры.</span><span class="sxs-lookup"><span data-stu-id="0e909-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="0e909-124">Если вызывающий код должен предоставить аргумент с типом данных, отличным от типа соответствующего параметра, например, `Byte` в качестве `String` параметра, необходимо выполнить одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="0e909-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="0e909-125">Указывайте только аргументы с типами данных, которые расширяются до типа данных параметра;</span><span class="sxs-lookup"><span data-stu-id="0e909-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="0e909-126">Задайте значение `Option Strict Off` , разрешающее неявные сужающие преобразования;</span><span class="sxs-lookup"><span data-stu-id="0e909-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="0e909-127">Используйте ключевое слово преобразования для явного преобразования типа данных.</span><span class="sxs-lookup"><span data-stu-id="0e909-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="0e909-128">Параметры типа</span><span class="sxs-lookup"><span data-stu-id="0e909-128">Type Parameters</span></span>  

 <span data-ttu-id="0e909-129">*Универсальная процедура* также определяет один или несколько *параметров типа* в дополнение к обычным параметрам.</span><span class="sxs-lookup"><span data-stu-id="0e909-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="0e909-130">Универсальная процедура позволяет вызывающему коду передавать различные типы данных при каждом вызове процедуры, чтобы можно было адаптировать типы данных к требованиям каждого отдельного вызова.</span><span class="sxs-lookup"><span data-stu-id="0e909-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="0e909-131">См. раздел [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0e909-131">See [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e909-132">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0e909-132">See also</span></span>

- [<span data-ttu-id="0e909-133">Процедуры</span><span class="sxs-lookup"><span data-stu-id="0e909-133">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0e909-134">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="0e909-134">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="0e909-135">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="0e909-135">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="0e909-136">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="0e909-136">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0e909-137">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="0e909-137">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0e909-138">Практическое руководство. Определение параметра для процедуры</span><span class="sxs-lookup"><span data-stu-id="0e909-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="0e909-139">Практическое руководство. Передача аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="0e909-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="0e909-140">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="0e909-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="0e909-141">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="0e909-141">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="0e909-142">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0e909-142">Type Conversions in Visual Basic</span></span>](../data-types/type-conversions.md)
