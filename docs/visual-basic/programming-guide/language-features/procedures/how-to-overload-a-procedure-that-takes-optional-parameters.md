---
description: Дополнительные сведения см. в разделе как перегрузить процедуру, принимающую необязательные параметры (Visual Basic).
title: Практическое руководство. Перегрузка процедуры, которая принимает необязательные параметры
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: dccef9d27c08ede2f35edc02c8bd5116aa6969b2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472947"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="eaf49-103">Практическое руководство. Перегрузка процедуры, которая принимает один необязательный параметр (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaf49-103">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>

<span data-ttu-id="eaf49-104">Если процедура имеет один или несколько [необязательных](../../../language-reference/modifiers/optional.md) параметров, нельзя определить перегруженную версию, соответствующую любой из ее неявных перегрузок.</span><span class="sxs-lookup"><span data-stu-id="eaf49-104">If a procedure has one or more [Optional](../../../language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="eaf49-105">Дополнительные сведения см. в разделе "Неявные перегрузки для необязательных параметров" раздела [рекомендации по перегрузке процедур](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="eaf49-105">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="eaf49-106">Один необязательный параметр</span><span class="sxs-lookup"><span data-stu-id="eaf49-106">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="eaf49-107">Перегрузка процедуры, принимающей один необязательный параметр</span><span class="sxs-lookup"><span data-stu-id="eaf49-107">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="eaf49-108">Напишите `Sub` `Function` оператор объявления или, который содержит необязательный параметр в списке параметров.</span><span class="sxs-lookup"><span data-stu-id="eaf49-108">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="eaf49-109">Не используйте `Optional` в этой перегруженной версии ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="eaf49-109">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="eaf49-110">Перед `Sub` `Function` ключевым словом или зарезервированным словом [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="eaf49-110">Precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="eaf49-111">Напишите код процедуры, который должен выполняться, когда вызывающий код предоставляет необязательный аргумент.</span><span class="sxs-lookup"><span data-stu-id="eaf49-111">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="eaf49-112">При необходимости завершите процедуру `End Sub` `End Function` оператором или.</span><span class="sxs-lookup"><span data-stu-id="eaf49-112">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="eaf49-113">Напишите второй оператор объявления, идентичный первому объявлению, за исключением того, что он не включает необязательный параметр в список параметров.</span><span class="sxs-lookup"><span data-stu-id="eaf49-113">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="eaf49-114">Напишите код процедуры, который должен выполняться, когда вызывающий код не предоставляет необязательный аргумент.</span><span class="sxs-lookup"><span data-stu-id="eaf49-114">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="eaf49-115">При необходимости завершите процедуру `End Sub` `End Function` оператором или.</span><span class="sxs-lookup"><span data-stu-id="eaf49-115">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="eaf49-116">В следующем примере показана процедура, определенная с необязательным параметром, эквивалентным набором двух перегруженных процедур, и, наконец, примеры как недопустимых, так и допустимых перегруженных версий.</span><span class="sxs-lookup"><span data-stu-id="eaf49-116">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="eaf49-117">Несколько необязательных параметров</span><span class="sxs-lookup"><span data-stu-id="eaf49-117">Multiple Optional Parameters</span></span>  

 <span data-ttu-id="eaf49-118">Для процедуры с более чем одним необязательным параметром обычно требуется более двух перегруженных версий.</span><span class="sxs-lookup"><span data-stu-id="eaf49-118">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="eaf49-119">Например, если имеется два необязательных параметра, и вызывающий код может указать или опустить каждый из них независимо друг от друга, необходимы четыре перегруженных версии, по одной для каждого возможного сочетания указанных аргументов.</span><span class="sxs-lookup"><span data-stu-id="eaf49-119">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="eaf49-120">По мере увеличения числа необязательных параметров увеличивается сложность перегрузки.</span><span class="sxs-lookup"><span data-stu-id="eaf49-120">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="eaf49-121">Если некоторые сочетания передаваемых аргументов неприемлемы, для N необязательных параметров требуется 2 ^ N перегруженных версий.</span><span class="sxs-lookup"><span data-stu-id="eaf49-121">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="eaf49-122">В зависимости от характера процедуры, возможно, вы обнаружите, что четко логика позволяет определить все перегруженные версии.</span><span class="sxs-lookup"><span data-stu-id="eaf49-122">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="eaf49-123">Перегрузка процедуры, принимающей более одного необязательного параметра</span><span class="sxs-lookup"><span data-stu-id="eaf49-123">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="eaf49-124">Определите, какие сочетания предоставляемых необязательных аргументов приемлемы для логики процедуры.</span><span class="sxs-lookup"><span data-stu-id="eaf49-124">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="eaf49-125">Неприемлемое сочетание может возникнуть, если один необязательный параметр зависит от другого.</span><span class="sxs-lookup"><span data-stu-id="eaf49-125">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="eaf49-126">Например, если один из параметров принимает имя человека, а другой принимает его возраст, сочетание аргументов, которые указывают возраст, но пропускают имя, неприемлемо.</span><span class="sxs-lookup"><span data-stu-id="eaf49-126">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="eaf49-127">Для каждого допустимого сочетания указанных необязательных аргументов напишите `Sub` `Function` оператор объявления или, определяющий соответствующий список параметров.</span><span class="sxs-lookup"><span data-stu-id="eaf49-127">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="eaf49-128">Не используйте `Optional` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="eaf49-128">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="eaf49-129">В каждом объявлении перед `Sub` `Function` ключевым словом или зарезервированным словом [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="eaf49-129">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="eaf49-130">После каждого объявления напишите код процедуры, который должен выполняться, когда вызывающий код предоставляет список аргументов, соответствующий списку параметров этого объявления.</span><span class="sxs-lookup"><span data-stu-id="eaf49-130">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="eaf49-131">При необходимости Завершите каждую `End Sub` процедуру `End Function` оператором или.</span><span class="sxs-lookup"><span data-stu-id="eaf49-131">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf49-132">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="eaf49-132">See also</span></span>

- [<span data-ttu-id="eaf49-133">Процедуры</span><span class="sxs-lookup"><span data-stu-id="eaf49-133">Procedures</span></span>](./index.md)
- [<span data-ttu-id="eaf49-134">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="eaf49-134">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="eaf49-135">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="eaf49-135">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="eaf49-136">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="eaf49-136">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="eaf49-137">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="eaf49-137">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="eaf49-138">Рекомендации по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="eaf49-138">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="eaf49-139">Практическое руководство. Определение различных версий процедуры</span><span class="sxs-lookup"><span data-stu-id="eaf49-139">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="eaf49-140">Практическое руководство. Вызов перегруженной процедуры</span><span class="sxs-lookup"><span data-stu-id="eaf49-140">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="eaf49-141">Практическое руководство. Перегрузка процедуры, принимающей неопределенное число параметров</span><span class="sxs-lookup"><span data-stu-id="eaf49-141">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="eaf49-142">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="eaf49-142">Overload Resolution</span></span>](./overload-resolution.md)
