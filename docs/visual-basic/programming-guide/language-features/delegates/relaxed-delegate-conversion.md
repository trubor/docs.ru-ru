---
description: 'Дополнительные сведения о: неявное преобразование делегата (Visual Basic)'
title: Неявное преобразование делегата
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: 36917017cd29d2c71f0c04ca9545b7d4e90c644e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428497"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="229ca-103">Неявное преобразование делегата (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="229ca-103">Relaxed Delegate Conversion (Visual Basic)</span></span>

<span data-ttu-id="229ca-104">Неявное преобразование делегатов позволяет назначать процедуры и функции делегатам или обработчикам, даже если их сигнатуры не идентичны.</span><span class="sxs-lookup"><span data-stu-id="229ca-104">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="229ca-105">Таким образом, привязка к делегатам будет соответствовать привязке, уже разрешенной для вызовов методов.</span><span class="sxs-lookup"><span data-stu-id="229ca-105">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="229ca-106">Параметры и возвращаемый тип</span><span class="sxs-lookup"><span data-stu-id="229ca-106">Parameters and Return Type</span></span>  

 <span data-ttu-id="229ca-107">Вместо точного соответствия сигнатуры для ослабленного преобразования требуется выполнение следующих условий, если параметр `Option Strict` имеет значение `On` .</span><span class="sxs-lookup"><span data-stu-id="229ca-107">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="229ca-108">Должно существовать расширяющее преобразование из типа данных каждого параметра делегата в тип данных соответствующего параметра назначенной функции или `Sub` .</span><span class="sxs-lookup"><span data-stu-id="229ca-108">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="229ca-109">В следующем примере делегат `Del1` имеет один параметр — `Integer` .</span><span class="sxs-lookup"><span data-stu-id="229ca-109">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="229ca-110">Параметр `m` в назначенных лямбда-выражениях должен иметь тип данных, для которого существует расширяющее преобразование `Integer` , например `Long` или `Double` .</span><span class="sxs-lookup"><span data-stu-id="229ca-110">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="229ca-111">Сужающие преобразования разрешены, только если `Option Strict` для задано значение `Off` .</span><span class="sxs-lookup"><span data-stu-id="229ca-111">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="229ca-112">Расширяющее преобразование должно существовать в противоположном направлении от возвращаемого типа назначенной функции или `Sub` к типу возвращаемого значения делегата.</span><span class="sxs-lookup"><span data-stu-id="229ca-112">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="229ca-113">В следующих примерах текст каждого назначенного лямбда-выражения должен иметь тип данных, который расширяется до, `Integer` так как тип возвращаемого значения `del1` — `Integer` .</span><span class="sxs-lookup"><span data-stu-id="229ca-113">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="229ca-114">Если параметр `Option Strict` имеет значение `Off` , расширяющееся ограничение удаляется в обоих направлениях.</span><span class="sxs-lookup"><span data-stu-id="229ca-114">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="229ca-115">Пропуск спецификаций параметров</span><span class="sxs-lookup"><span data-stu-id="229ca-115">Omitting Parameter Specifications</span></span>  

 <span data-ttu-id="229ca-116">Ослабленные делегаты также позволяют полностью опускать спецификации параметров в назначенном методе:</span><span class="sxs-lookup"><span data-stu-id="229ca-116">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="229ca-117">Обратите внимание, что нельзя указать некоторые параметры и опустить другие.</span><span class="sxs-lookup"><span data-stu-id="229ca-117">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="229ca-118">Возможность опускать параметры полезна в таких ситуациях, как определение обработчика событий, в котором участвуют несколько сложных параметров.</span><span class="sxs-lookup"><span data-stu-id="229ca-118">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="229ca-119">Аргументы некоторых обработчиков событий не используются.</span><span class="sxs-lookup"><span data-stu-id="229ca-119">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="229ca-120">Вместо этого обработчик напрямую обращается к состоянию элемента управления, в котором регистрируется событие, и игнорирует аргументы.</span><span class="sxs-lookup"><span data-stu-id="229ca-120">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="229ca-121">Ослабленные делегаты позволяют опускать аргументы в таких объявлениях, если результат неоднозначности.</span><span class="sxs-lookup"><span data-stu-id="229ca-121">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="229ca-122">В следующем примере полностью указанный метод `OnClick` может быть переписан как `RelaxedOnClick` .</span><span class="sxs-lookup"><span data-stu-id="229ca-122">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="229ca-123">Примеры AddressOf</span><span class="sxs-lookup"><span data-stu-id="229ca-123">AddressOf Examples</span></span>  

 <span data-ttu-id="229ca-124">Лямбда-выражения используются в предыдущих примерах для упрощения просмотра связей типов.</span><span class="sxs-lookup"><span data-stu-id="229ca-124">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="229ca-125">Однако для назначений делегатов, которые используют, или, разрешены те же ограничения `AddressOf` `Handles` `AddHandler` .</span><span class="sxs-lookup"><span data-stu-id="229ca-125">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="229ca-126">В следующем примере функции,, `f1` `f2` `f3` и `f4` могут быть назначены `Del1` .</span><span class="sxs-lookup"><span data-stu-id="229ca-126">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="229ca-127">Следующий пример допустим только в том случае `Option Strict` , если параметр имеет значение `Off` .</span><span class="sxs-lookup"><span data-stu-id="229ca-127">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="229ca-128">Удаление возвращаемых функций</span><span class="sxs-lookup"><span data-stu-id="229ca-128">Dropping Function Returns</span></span>  

 <span data-ttu-id="229ca-129">Неявное преобразование делегата позволяет присвоить функцию `Sub` делегату, фактически игнорируя возвращаемое значение функции.</span><span class="sxs-lookup"><span data-stu-id="229ca-129">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="229ca-130">Однако нельзя присвоить значение `Sub` делегату функции.</span><span class="sxs-lookup"><span data-stu-id="229ca-130">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="229ca-131">В следующем примере адрес функции `doubler` назначается `Sub` делегату `Del3` .</span><span class="sxs-lookup"><span data-stu-id="229ca-131">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="229ca-132">См. также</span><span class="sxs-lookup"><span data-stu-id="229ca-132">See also</span></span>

- [<span data-ttu-id="229ca-133">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="229ca-133">Lambda Expressions</span></span>](../procedures/lambda-expressions.md)
- [<span data-ttu-id="229ca-134">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="229ca-134">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="229ca-135">Делегаты</span><span class="sxs-lookup"><span data-stu-id="229ca-135">Delegates</span></span>](index.md)
- [<span data-ttu-id="229ca-136">Практическое руководство. Передача процедур другой процедуре в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="229ca-136">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="229ca-137">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="229ca-137">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="229ca-138">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="229ca-138">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
