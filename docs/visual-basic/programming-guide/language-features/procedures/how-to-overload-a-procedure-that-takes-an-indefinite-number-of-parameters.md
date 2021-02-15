---
description: 'Дополнительные сведения о: как перегрузить процедуру, которая принимает неопределенное число параметров (Visual Basic)'
title: Практическое руководство. Перегрузка процедуры, принимающей неопределенное число параметров
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 97e391c2981760e012d56e1f93c24eb60ce3ebfe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460050"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="98933-103">Практическое руководство. Перегрузка процедуры, принимающей неопределенное число параметров (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98933-103">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>

<span data-ttu-id="98933-104">Если процедура имеет параметр [ParamArray](../../../language-reference/modifiers/paramarray.md) , нельзя определить перегруженную версию, принимающую одномерный массив для массива параметров.</span><span class="sxs-lookup"><span data-stu-id="98933-104">If a procedure has a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="98933-105">Дополнительные сведения см. в разделе "Неявные перегрузки для параметра ParamArray" раздела [рекомендации по перегрузке процедур](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="98933-105">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="98933-106">Перегрузка процедуры, принимающей переменное число параметров</span><span class="sxs-lookup"><span data-stu-id="98933-106">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="98933-107">Выясните, что процедура и вызов логики кода имеют преимущества от перегруженных версий больше, чем из `ParamArray` параметра.</span><span class="sxs-lookup"><span data-stu-id="98933-107">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="98933-108">См. раздел "Overloads and Парамаррайс" в разделе [рекомендации по перегрузке процедур](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="98933-108">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="98933-109">Определите, какое количество представленных значений должна принимать процедура в переменной части списка параметров.</span><span class="sxs-lookup"><span data-stu-id="98933-109">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="98933-110">Это может включать отсутствие значения и может включать в себя регистр одного одномерного массива.</span><span class="sxs-lookup"><span data-stu-id="98933-110">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="98933-111">Для каждого допустимого числа представленных значений напишите `Sub` `Function` оператор объявления или, определяющий соответствующий список параметров.</span><span class="sxs-lookup"><span data-stu-id="98933-111">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="98933-112">Не используйте в `Optional` `ParamArray` этой перегруженной версии ключевое слово или.</span><span class="sxs-lookup"><span data-stu-id="98933-112">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="98933-113">В каждом объявлении перед `Sub` `Function` ключевым словом или зарезервированным словом [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="98933-113">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="98933-114">После каждого объявления напишите код процедуры, который должен выполняться, когда вызывающий код предоставляет значения, соответствующие списку параметров этого объявления.</span><span class="sxs-lookup"><span data-stu-id="98933-114">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="98933-115">При необходимости Завершите каждую `End Sub` процедуру `End Function` оператором или.</span><span class="sxs-lookup"><span data-stu-id="98933-115">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98933-116">Пример</span><span class="sxs-lookup"><span data-stu-id="98933-116">Example</span></span>  

 <span data-ttu-id="98933-117">В следующем примере показана процедура, определенная с параметром [ParamArray](../../../language-reference/modifiers/paramarray.md) , а затем эквивалентный набор перегруженных процедур.</span><span class="sxs-lookup"><span data-stu-id="98933-117">The following example shows a procedure defined with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="98933-118">Невозможно перегрузить такую процедуру со списком параметров, принимающим одномерный массив для массива параметров.</span><span class="sxs-lookup"><span data-stu-id="98933-118">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="98933-119">Однако можно использовать сигнатуры других неявных перегрузок.</span><span class="sxs-lookup"><span data-stu-id="98933-119">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="98933-120">Это показано в следующих объявлениях.</span><span class="sxs-lookup"><span data-stu-id="98933-120">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="98933-121">Код в перегруженных версиях не должен проверять, предоставлен ли вызывающему коду одно или несколько значений для `ParamArray` параметра, или, если да, то сколько.</span><span class="sxs-lookup"><span data-stu-id="98933-121">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="98933-122">Visual Basic передает управление версии, соответствующей списку аргументов вызова.</span><span class="sxs-lookup"><span data-stu-id="98933-122">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="98933-123">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="98933-123">Compile the code</span></span>  

 <span data-ttu-id="98933-124">Так как процедура с `ParamArray` параметром эквивалентна набору перегруженных версий, нельзя перегружать такую процедуру со списком параметров, соответствующим любому из этих неявных перегрузок.</span><span class="sxs-lookup"><span data-stu-id="98933-124">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="98933-125">Дополнительные сведения см. [в разделе рекомендации по перегрузке процедур](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="98933-125">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="98933-126">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="98933-126">.NET Framework Security</span></span>  

 <span data-ttu-id="98933-127">Всякий раз при работе с массивом, который может быть неограниченным большим, существует риск перегрузки внутренней емкости приложения.</span><span class="sxs-lookup"><span data-stu-id="98933-127">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="98933-128">Если вы принимаете массив параметров, следует проверить длину массива, которому был передан вызывающий код, и предпринять соответствующие шаги, если оно слишком велико для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="98933-128">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98933-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="98933-129">See also</span></span>

- [<span data-ttu-id="98933-130">Процедуры</span><span class="sxs-lookup"><span data-stu-id="98933-130">Procedures</span></span>](./index.md)
- [<span data-ttu-id="98933-131">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="98933-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="98933-132">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="98933-132">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="98933-133">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="98933-133">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="98933-134">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="98933-134">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="98933-135">Рекомендации по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="98933-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="98933-136">Практическое руководство. Определение различных версий процедуры</span><span class="sxs-lookup"><span data-stu-id="98933-136">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="98933-137">Практическое руководство. Вызов перегруженной процедуры</span><span class="sxs-lookup"><span data-stu-id="98933-137">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="98933-138">Практическое руководство. Перегрузка процедуры, которая принимает необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="98933-138">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="98933-139">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="98933-139">Overload Resolution</span></span>](./overload-resolution.md)
